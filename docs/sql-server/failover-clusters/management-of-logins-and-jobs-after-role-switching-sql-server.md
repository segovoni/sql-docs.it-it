---
title: Gestione di account di accesso e di processi dopo un cambio di ruolo (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.suite: sql
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- role switching [SQL Server]
ms.assetid: fc2fc949-746f-40c7-b5d4-3fd51ccfbd7b
caps.latest.revision: 25
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 94f3340c0184142baefb5bde981e71a74e56b6a9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33032599"
---
# <a name="management-of-logins-and-jobs-after-role-switching-sql-server"></a>Gestione di account di accesso e di processi dopo un cambio di ruolo (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Quando si distribuisce una soluzione di recupero di emergenza o a disponibilità elevata per un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , è importante riprodurre le informazioni più significative archiviate per il database nei database **master** o **msdb** . In genere, tra queste informazioni sono inclusi i processi del database primario/principale e gli account di accesso di utenti o processi necessari per la connessione al database. È consigliabile duplicare queste informazioni in qualsiasi istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in cui viene ospitato un database secondario/mirror. Se possibile, dopo il cambio di ruolo, è opportuno riprodurre le informazioni a livello di programmazione nel nuovo database primario/principale.  
  
## <a name="logins"></a>Account di accesso  
 In tutte le istanze del server in cui viene ospitata una copia del database, è consigliabile riprodurre gli account di accesso con l'autorizzazione ad accedere al database principale. Quando il ruolo primario/principale cambia, solo gli utenti con account di accesso presenti nella nuova istanza del server primario/principale possono accedere al nuovo database primario/principale. Gli utenti i cui account di accesso non sono definiti nella nuova istanza del server primario/principale sono orfani e non possono accedere al database.  
  
 Se un utente è orfano, creare l'account di accesso nella nuova istanza del server primario/principale ed eseguire [sp_change_users_login](../../relational-databases/system-stored-procedures/sp-change-users-login-transact-sql.md). Per altre informazioni, vedere [Risolvere i problemi relativi agli utenti isolati &#40;SQL Server&#41;](../../sql-server/failover-clusters/troubleshoot-orphaned-users-sql-server.md).  
  
###  <a name="SSauthentication"></a> Account di accesso di applicazioni in cui viene utilizzata l'autenticazione di SQL Server o un account di accesso di Windows locale  
 Se in un'applicazione viene utilizzata l'autenticazione di SQL Server o un account di accesso di Windows locale, i SID non corrispondenti possono impedire la risoluzione in un'istanza remota di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]da parte dell'account di accesso dell'applicazione. In caso di SID non corrispondenti, l'account di accesso diventa un utente orfano nell'istanza del server remoto. Questo problema si può verificare quando tramite un'applicazione si effettua la connessione a un database di log shipping o con mirroring dopo un failover o a un database Sottoscrittore di replica inizializzato da un backup.  
  
 Per evitare questo problema, è consigliabile intraprendere misure preventive quando si configura un'applicazione di questo tipo per utilizzare un database ospitato da un'istanza remota di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La prevenzione comporta il trasferimento degli account di accesso e delle password dall'istanza locale di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] all'istanza remota di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per altre informazioni su come evitare questo problema, vedere l'articolo della Knowledge Base 918992 relativo alla[modalità di trasferimento degli account di accesso e delle password tra le istanze di SQL Server](http://support.microsoft.com/kb/918992/).  
  
> [!NOTE]  
>  Questo problema influisce sugli account di Windows locali in computer diversi. Tuttavia, non si verifica in caso di account di dominio, dal momento che il SID è identico in ogni computer.  
  
 Per altre informazioni, vedere la pagina relativa agli [utenti orfani con log shipping e mirroring del database](http://blogs.msdn.com/b/sqlserverfaq/archive/2009/04/13/orphaned-users-with-database-mirroring-and-log-shipping.aspx) (blog del motore di database).  
  
## <a name="jobs"></a>processi  
 I processi, ad esempio quelli di backup, richiedono una particolare attenzione. Dopo un cambio di ruolo, in genere il proprietario del database o l'amministratore di sistema deve ricreare i processi per il nuovo database primario/principale.  
  
 Se l'istanza del server primario/principale precedente è disponibile, è consigliabile eliminare i processi originali nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]in questione. Si noti che i processi nel database mirror attuale non vengono eseguiti poiché il database si trova nello stato RESTORING e, pertanto, non è disponibile.  
  
> [!NOTE]  
>  È possibile che istanze differenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] siano configurate in modo diverso, ad esempio con lettere di unità differenti. I processi di ogni partner devono supportare eventuali differenze di questo tipo.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione dei metadati quando si rende disponibile un database in un'altra istanza del server &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md)   
 [Risolvere i problemi relativi agli utenti isolati &#40;SQL Server&#41;](../../sql-server/failover-clusters/troubleshoot-orphaned-users-sql-server.md)  
  
  

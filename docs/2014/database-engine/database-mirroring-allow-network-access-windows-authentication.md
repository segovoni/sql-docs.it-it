---
title: Consenti accesso alla rete a un Database di Mirroring Endpoint tramite l'autenticazione di Windows (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Windows authentication [SQL Server]
- database mirroring [SQL Server], security
ms.assetid: 28c8fec5-5feb-4c84-8d72-f2bd1ae3b40d
caps.latest.revision: 31
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 29b1cdaeae798a73455df2d99046f3564abd0db6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37157102"
---
# <a name="allow-network-access-to-a-database-mirroring-endpoint-using-windows-authentication-sql-server"></a>Concessione dell'accesso alla rete a un endpoint per il mirroring del database utilizzando l'autenticazione di Windows (SQL Server)
  L'utilizzo dell'autenticazione di Windows per la connessione degli endpoint del mirroring di database di due istanze di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] richiede la configurazione manuale degli account di accesso nelle seguenti condizioni:  
  
-   Se l'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] è in esecuzione come servizi con diversi account di dominio (in domini uguali o attendibili), è necessario creare l'account di accesso di ogni account in **master** in ognuna delle istanze del server remoto e a quell'account di accesso devono essere concesse le autorizzazioni CONNECT sull'endpoint.  
  
-   Se l'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] è in esecuzione come account del servizio di rete, l'account di accesso di ogni account del computer host (*DomainName***\\***ComputerName$*) deve essere creato in **master** in ognuna delle istanze del server remoto e a quell'account di accesso devono essere concesse le autorizzazioni CONNECT sull'endpoint. Ciò avviene in quanto un'istanza del server che è in esecuzione con l'account del servizio di rete esegue l'autenticazione utilizzando l'account di dominio del computer host.  
  
> [!NOTE]  
>  Assicurarsi che sia disponibile un endpoint per ogni istanza del server. Per altre informazioni, vedere [Creare un endpoint del mirroring del database per l'autenticazione Windows &#40;Transact-SQL&#41;](database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md).  
  
### <a name="to-configure-logins-for-windows-authentication"></a>Per configurare gli account di accesso per l'autenticazione di Windows  
  
1.  Per l'account utente di ogni istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], creare un account di accesso nelle altre istanze di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Utilizzare un'istruzione [CREATE LOGIN](/sql/t-sql/statements/create-login-transact-sql) con la clausola FROM WINDOWS.  
  
     Per altre informazioni, vedere [Creazione di un account di accesso](../relational-databases/security/authentication-access/create-a-login.md).  
  
2.  Per assicurarsi inoltre che l'utente di accesso sia in grado di accedere all'endpoint, utilizzare l'istruzione [GRANT](/sql/t-sql/statements/grant-transact-sql) per concedere le autorizzazioni di connessione sull'endpoint per l'account di accesso. Si noti che la concessione di autorizzazioni di accesso per l'endpoint non è necessaria se l'utente è un amministratore.  
  
     Per altre informazioni, vedere [Grant a Permission to a Principal](../relational-databases/security/authentication-access/grant-a-permission-to-a-principal.md).  
  
## <a name="example"></a>Esempio  
 Nel seguente esempio [!INCLUDE[tsql](../includes/tsql-md.md)] viene creato un account di accesso [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] per un account utente denominato `Otheruser` che appartiene a un dominio denominato `Adomain`. Nell'esempio vengono quindi concesse all'utente autorizzazioni per la connessione a un endpoint di mirroring del database preesistente denominato `Mirroring_Endpoint`.  
  
```  
USE master;  
GO  
CREATE LOGIN [Adomain\Otheruser] FROM WINDOWS;  
GO  
GRANT CONNECT on ENDPOINT::Mirroring_Endpoint TO [Adomain\Otheruser];  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica di gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Mirroring del database &#40;SQL Server&#41;](database-mirroring/database-mirroring-sql-server.md)   
 [Sicurezza del trasporto per i gruppi di disponibilità AlwaysOn e mirroring del Database &#40;SQL Server&#41;](database-mirroring/transport-security-database-mirroring-always-on-availability.md)   
 [Endpoint del mirroring del database &#40;SQL Server&#41;](database-mirroring/the-database-mirroring-endpoint-sql-server.md)  
  
  

---
title: Reimpostazione della password - Analitica Platform System | Documenti Microsoft
description: La pagina di reimpostazione della Password consente di modificare la password per gli account amministratore usato dal sistema della piattaforma Analitica.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 63fbb097bf1ca926223ce7c0114c8da5d10cd969
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
ms.locfileid: "31539421"
---
# <a name="password-reset---analytics-platform-system"></a>Reimpostazione della password - Analitica Platform System
Il **di reimpostazione della Password** pagina consente di modificare la password per gli account amministratore usato dal sistema di piattaforma Analitica.  
  
> [!WARNING]  
> Utilizzare sempre il **Configuration Manager** per aggiornare la password dell'amministratore di dominio applicazione. Altri metodi non aggiorni tutti i componenti di sistema della piattaforma Analitica e potrebbe causare problemi di accesso dell'applicazione.  
  
Vengono fornite le password Analitica Platform System quando viene recapitato al dispositivo. Consente di modificare sempre le password con nuovi valori quando assumersi la responsabilità del dispositivo. Esistono tre le password per l'aggiornamento. Le password non deve essere identico a loro.  
  
**F <*xxxx*> \administrator.**  
Il **amministratore** del dominio applicazione.  
  
**.\Administrator**  
Locale **amministratore** account dei computer che ospitano le macchine virtuali.  
  
> [!IMPORTANT]  
> Per il dispositivo aggiornamento 1, **Configuration Manager** non correttamente non modifica la password dell'account di amministratore locale in tutta la PDW VM. Se necessario, contattare Microsoft per ulteriori istruzioni.  
  
**sa**  
Il **sa** account di accesso di SQL Server. **SA** è un membro del **sysadmin** ruolo predefinito del server e sia un amministratore di SQL Server. La password del **sa** account di accesso può inoltre essere modificata mediante il **ALTER LOGIN** istruzione.  
  
## <a name="password-requirements"></a>Requisiti della password  
Sia le credenziali di amministratore di dominio e le credenziali di amministratore di sistema sono conformi ai criteri di attendibilità di password per ogni tipo di credenziale. Quando si modificano le credenziali di amministratore di dominio, la nuova password viene aggiornata per il dominio in cui è necessario in SQL Server PDW.  
  
> [!IMPORTANT]  
> SQL Server PDW non supporta il carattere di segno di dollaro (**$**) in cui l'amministratore di dominio o una password di amministratore locale. I caratteri **^ % &** sono consentiti nelle password, ma PowerShell considera questi caratteri speciali. Se uno di questi caratteri vengono utilizzato per le password per l'amministratore di sistema o di SQL Server**sa** account (il **AdminPassword** e **PdwSAPassword** parametri durante la programma di installazione) per l'installazione, l'installazione, aggiornamento, REPLACENODE e l'applicazione di patch, tra cui avrà esito negativo. Per garantire una corretta esecuzione dell'aggiornamento quando le password corrente contengano caratteri non supportati, è possibile modificare le password in modo che non contengono tali caratteri prima di eseguire l'aggiornamento. Al termine dell'aggiornamento, è possibile impostare le password i relativi valori originali. Per ulteriori informazioni sui requisiti della password, vedere [ALTER LOGIN](../t-sql/statements/alter-login-transact-sql.md).  
  
## <a name="to-reset-a-password"></a>Per reimpostare una password  
  
1.  Connettersi al nodo di controllo e avviare il **Configuration Manager** (**dwconfig.exe**). Per altre informazioni, vedere [avviare Gestione configurazione &#40;Analitica Platform System&#41;](launch-the-configuration-manager.md).  
  
2.  Nel riquadro sinistro della finestra di **Configuration Manager**, fare clic su **di reimpostazione della Password**.  
  
3.  Selezionare il tipo di amministratore dal **Account** menu a discesa, quindi immettere la nuova password nel **Password** e **Conferma Password** caselle. Fare clic su **applica** per salvare le modifiche.  
  
    Le modifiche apportate a tali account non interessano tutte le sessioni attualmente attive, ma verranno applicate al successivo tentativo di accesso per ogni utente.  
  
    ![SQL Server DWConfig Password](./media/password-reset/SQL_Server_PDW_DWConfig_TopPW.png "SQL_Server_PDW_DWConfig_TopPW")  
  
## <a name="see-also"></a>Vedere anche  
[Impostare la Password di amministratore per l'accesso AD nodi in modalità ripristino servizi Directory &#40;modalità ripristino servizi directory&#41; &#40;Analitica Platform System&#41;](set-admin-password-for-logging-on-to-ad-nodes-in-directory-services-restore-mode.md)  
[Avviare Gestione configurazione &#40;Analitica Platform System&#41;](launch-the-configuration-manager.md)  
  

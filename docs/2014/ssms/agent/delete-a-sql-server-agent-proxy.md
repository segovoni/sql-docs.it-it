---
title: Eliminare un proxy di SQL Server Agent | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- deleting SQL Server Agent proxies
- proxies [SQL Server Agent], deleting
- removing SQL Server Agent proxies
ms.assetid: 9248841d-7294-47d4-94f3-b34a0521fabc
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3cb408f82e10f4abb57ebe010b63707b2b9d5f96
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37265772"
---
# <a name="delete-a-sql-server-agent-proxy"></a>Delete a SQL Server Agent Proxy
  In questo argomento viene descritto come eliminare un account proxy di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
     [Security](#Security)  
  
-   **Per eliminare un account proxy di SQL Server Agent utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   Quando si elimina un account proxy di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, assicurarsi che il proxy non faccia riferimento ad alcun passaggio di processo attivo. Per verificare eventuali passaggi di processo che fanno riferimento al proxy, fare clic con il pulsante destro del mouse sul proxy, scegliere **Proprietà** e quindi nella finestra di dialogo *Proprietà account proxy***nome_proxy** selezionare la pagina **Riferimenti**. Se si elimina un proxy, la finestra di dialogo **Elimina oggetto** consente di riassegnare tutti i passaggi di processo che utilizzano tale proxy.  
  
-   I proxy di[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent utilizzano le credenziali per archiviare le informazioni sugli account utente di Windows. L'utente specificato nella credenziale deve disporre dell'autorizzazione "accesso come processo batch" sul computer in cui è in esecuzione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent verifica l'accesso al sottosistema per un proxy e garantisce l'accesso al proxy ad ogni esecuzione del passaggio di processo. Se il proxy non dispone più di accesso al sottosistema, il passaggio di processo non viene eseguito correttamente. In caso contrario, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent rappresenta l'utente specificato nel proxy ed esegue il passaggio di processo.  
  
-   Se l'account di accesso per l'utente viene utilizzato per l'accesso al proxy oppure se l'utente appartiene a un qualsiasi ruolo che prevede l'accesso al proxy, l'utente potrà utilizzare il proxy in un passaggio di processo.  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
 Gli account proxy possono essere creati, modificati o eliminati unicamente dai membri del ruolo predefinito del server **sysadmin** .  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-delete-a-sql-server-agent-proxy-account"></a>Per eliminare un account proxy di SQL Server Agent  
  
1.  In **Esplora oggetti**fare clic sul segno più per espandere un server che contiene l'account proxy da eliminare.  
  
2.  Fare clic sul segno più per espandere **SQL Server Agent**.  
  
3.  Fare clic sul segno più per espandere la cartella **Proxy** .  
  
4.  Fare clic sul segno più per espandere il sottosistema che contiene l'account proxy da eliminare, ad esempio **ActiveX Script**.  
  
5.  Fare clic con il pulsante destro del mouse sull'account proxy da eliminare e quindi scegliere **Elimina**.  
  
6.  Nella finestra di dialogo **Elimina oggetto** verificare che sia selezionato l'account proxy corretto. Selezionare la casella di controllo **Riassegna a** per riassegnare i passaggi del processo che si riferiscono all'account proxy a un altro account.  
  
7.  Fare clic su **OK**.  
  
##  <a name="TsqlProcedure"></a> Uso di Transact-SQL  
  
#### <a name="to-delete-a-sql-server-agent-proxy-account"></a>Per eliminare un account proxy di SQL Server Agent  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra delle query e fare clic su **Esegui**.  
  
    ```  
    -- deletes the proxy "Catalog application proxy"  
    USE msdb ;  
    GO  
    EXEC dbo.sp_delete_proxy  
        @proxy_name = N'Catalog application proxy' ;  
    GO  
    ```  
  
 Per altre informazioni, vedere [sp_delete_proxy &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-proxy-transact-sql).  
  
  

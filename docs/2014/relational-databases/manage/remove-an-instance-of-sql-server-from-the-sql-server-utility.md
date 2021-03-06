---
title: Rimuovere un'istanza di SQL Server da Utilità SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.utility.remove.f1
ms.assetid: ae1d126a-46d2-47bf-b339-17c743df6491
caps.latest.revision: 7
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e7b657f69ae221044fcc0fa1211b21954b4ad1d0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37244621"
---
# <a name="remove-an-instance-of-sql-server-from-the-sql-server-utility"></a>Rimuovere un'istanza di SQL Server da Utilità SQL Server
  Usare i passaggi seguenti per rimuovere un'istanza gestita di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da Utilità [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Questa procedura rimuove l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dalla visualizzazione elenco del punto di controllo dell'utilità e arresta la raccolta dati in Utilità [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . L'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non viene disinstallata.  
  
> [!IMPORTANT]  
>  Prima di utilizzare questa procedura per rimuovere un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da Utilità [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , verificare che i servizi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e SQL Server Agent siano in esecuzione nell'istanza da rimuovere.  
  
1.  Da Esplora utilità in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]fare clic su **Istanze gestite**. Osservare la visualizzazione elenco delle istanze gestite di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nel riquadro del contenuto di Esplora utilità.  
  
2.  Nella colonna **Nome istanza di SQL Server** della visualizzazione elenco selezionare l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da rimuovere da Utilità [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Fare clic con il pulsante destro del mouse sull'istanza da rimuovere e scegliere **Rimuovi istanza gestita**.  
  
3.  Specificare credenziali con privilegi di amministratore per l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Fare clic su **Connetti**, verificare le informazioni nella finestra di dialogo **Connetti al server** , quindi fare clic su **Connetti**. Le informazioni di accesso verranno visualizzate nella finestra di dialogo **Rimuovi istanza gestita** .  
  
4.  Fare clic su **OK**per confermare l'operazione. Per uscire dall'operazione, scegliere **Annulla**.  
  
## <a name="manually-remove-a-managed-instance-of-sql-server-from-a-sql-server-utility"></a>Rimozione manuale di un'istanza gestita di SQL Server da un'Utilità SQL Server  
 Questa procedura rimuove l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dalla visualizzazione elenco del punto di controllo dell'utilità e arresta la raccolta dati in Utilità [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . L'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non viene disinstallata.  
  
 È possibile usare PowerShell per rimuovere un'istanza gestita di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da Utilità [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . lo script esegue le operazioni seguenti:  
  
-   Ottiene il punto di controllo dell'utilità tramite il nome dell'istanza del server.  
  
-   Rimuove l'istanza gestita di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da Utilità [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
```  
# Get Ucp connection  
$UcpServerInstanceName = "ComputerName\InstanceName";  
$UtilityInstance = new-object –Type Microsoft.SqlServer.Management.Smo.Server $UcpServerInstanceName;  
$UcpConnection = new-object -Type Microsoft.SqlServer.Management.Sdk.Sfc.SqlStoreConnection $UtilityInstance.ConnectionContext.SqlConnectionObject;  
$Utility = [Microsoft.SqlServer.Management.Utility.Utility]::Connect($UcpConnection);  
  
# Now remove the ManagedInstance from the SQL Server Utility  
$ServerInstanceName = "ComputerName\InstanceName";  
$Instance = new-object -Type Microsoft.SqlServer.Management.Smo.Server $ServerInstanceName;  
$InstanceConnection = new-object -Type Microsoft.SqlServer.Management.Sdk.Sfc.SqlStoreConnection $Instance.ConnectionContext.SqlConnectionObject;  
$ManagedInstance = $Utility.ManagedInstances[$ServerInstanceName];  
$ManagedInstance.Remove($InstanceConnection);  
```  
  
 Si tenga presente che è importante fare riferimento esattamente al nome dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] come viene archiviato in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Su un'istanza con distinzione tra maiuscole e minuscole di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è necessario specificare il nome dell'istanza usando la combinazione di maiuscole e minuscole esatta restituita da @@SERVERNAME. Per ottenere il nome dell'istanza per l'istanza gestita di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], eseguire la seguente query sull'istanza gestita:  
  
```  
select @@SERVERNAME AS instance_name  
```  
  
 A questo punto, l'istanza gestita di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene rimossa completamente dal punto di controllo dell'utilità. Al successivo aggiornamento dei dati per Utilità [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non risulterà più presente nella visualizzazione elenco. Il risultato è identico al caso in cui un utente esegue la rimozione dell'istanza gestita nell'interfaccia utente di SSMS.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo di Esplora utilità per gestire Utilità SQL Server](use-utility-explorer-to-manage-the-sql-server-utility.md)   
 [Risoluzione dei problemi relativi a Utilità SQL Server](../../database-engine/troubleshoot-the-sql-server-utility.md)  
  
  

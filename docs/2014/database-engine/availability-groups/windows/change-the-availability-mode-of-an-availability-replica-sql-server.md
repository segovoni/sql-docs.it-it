---
title: Modificare la modalità di disponibilità di una replica di disponibilità (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], availability modes
ms.assetid: c4da8f25-fb1b-45a4-8bf2-195df6df634c
caps.latest.revision: 35
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9d9a742003107a2416e55f7c4f3a473c430e04eb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37310421"
---
# <a name="change-the-availability-mode-of-an-availability-replica-sql-server"></a>Modificare la modalità di disponibilità di una replica di disponibilità (SQL Server)
  In questo argomento viene illustrato come modificare la modalità di disponibilità di una replica di disponibilità in un gruppo di disponibilità AlwaysOn in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]o PowerShell. La modalità di disponibilità è una proprietà della replica che determina se il commit della replica viene eseguito in modo asincrono o sincrono. La*modalità con commit asincrono* ottimizza le prestazioni a discapito della disponibilità elevata e supporta solo il failover manuale forzato (con possibile perdita di dati), generalmente denominato *failover forzato*. La*modalità con commit sincrono* privilegia la disponibilità elevata rispetto alle prestazioni e, una volta sincronizzata la replica secondaria, supporta il failover manuale e, facoltativamente, quello automatico.  
  

  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Prerequisites"></a> Prerequisiti  
  
-   È necessario essere connessi all'istanza del server che ospita la replica primaria.  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
 È necessaria l'autorizzazione ALTER AVAILABILITY GROUP nel gruppo di disponibilità, l'autorizzazione CONTROL AVAILABILITY GROUP, l'autorizzazione ALTER ANY AVAILABILITY GROUP o l'autorizzazione CONTROL SERVER.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 **Per modificare la modalità di disponibilità di un gruppo di disponibilità**  
  
1.  In Esplora oggetti connettersi all'istanza del server che ospita la replica primaria ed espandere l'albero del server.  
  
2.  Espandere il nodo **Disponibilità elevata AlwaysOn** e il nodo **Gruppi di disponibilità** .  
  
3.  Fare clic sul gruppo di disponibilità di cui si desidera modificare la replica.  
  
4.  Fare clic con il pulsante destro del mouse sulla replica e scegliere **Proprietà**.  
  
5.  Nella finestra di dialogo **Proprietà replica di disponibilità** utilizzare l'elenco a discesa **Modalità di disponibilità** per modificare la modalità di disponibilità di questa replica.  
  
##  <a name="TsqlProcedure"></a> Uso di Transact-SQL  
 **Per modificare la modalità di disponibilità di un gruppo di disponibilità**  
  
1.  Connettersi all'istanza del server che ospita la replica primaria.  
  
2.  Utilizzare l'istruzione [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) , come indicato di seguito:  
  
     ALTER AVAILABILITY GROUP *nome_gruppo* MODIFY REPLICA ON '*nome_server*'  
  
     WITH ( {  
  
     AVAILABILITY_MODE = { SYNCHRONOUS_COMMIT | ASYNCHRONOUS_COMMIT }  
  
     | FAILOVER_MODE = { AUTOMATIC | MANUAL }  
  
     } )  
  
     dove *group_name* è il nome del gruppo di disponibilità e *server_name* è il nome dell'istanza del server che ospita la replica da modificare.  
  
    > [!NOTE]  
    >  FAILOVER_MODE = AUTOMATIC è supportata solo se si specifica anche AVAILABILITY_MODE = SYNCHRONOUS_COMMIT.  
  
     Nell'esempio seguente, relativo alla replica primaria del gruppo di disponibilità `AccountsAG` , vengono impostate le modalità di disponibilità e di failover sul commit sincrono e il failover automatico, rispettivamente, per la replica ospitata dall'istanza del server `INSTANCE09` .  
  
    ```  
  
    ALTER AVAILABILITY GROUP AccountsAG MODIFY REPLICA ON 'INSTANCE09'  
       WITH (AVAILABILITY_MODE = SYNCHRONOUS_COMMIT);  
    ALTER AVAILABILITY GROUP AccountsAG MODIFY REPLICA ON 'INSTANCE09'  
       WITH (FAILOVER_MODE = AUTOMATIC);  
    ```  
  
##  <a name="PowerShellProcedure"></a> Utilizzo di PowerShell  
 **Per modificare la modalità di disponibilità di un gruppo di disponibilità**  
  
1.  Spostarsi nella directory (`cd`) dell'istanza del server che ospita la replica primaria.  
  
2.  Usare la `Set-SqlAvailabilityReplica` cmdlet con il `AvailabilityMode` parametro e, facoltativamente, il `FailoverMode` parametro.  
  
     Ad esempio, con il comando seguente si modifica la replica `MyReplica` nel gruppo di disponibilità `MyAg` in modo da utilizzare la modalità di disponibilità con commit asincrono e supportare il failover automatico.  
  
    ```  
    Set-SqlAvailabilityReplica -AvailabilityMode "SynchronousCommit" -FailoverMode "Automatic" `   
    -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\AvailabilityReplicas\MyReplica  
    ```  
  
    > [!NOTE]  
    >  Per visualizzare la sintassi di un cmdlet, usare il `Get-Help` cmdlet di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ambiente PowerShell. Per altre informazioni, vedere [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
 **Per impostare e utilizzare il provider PowerShell per SQL Server**  
  
-   [Provider PowerShell per SQL Server](../../../powershell/sql-server-powershell-provider.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica di gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Modalità di disponibilità (gruppi di disponibilità AlwaysOn)](availability-modes-always-on-availability-groups.md)   
 [Failover e modalità di Failover &#40;gruppi di disponibilità AlwaysOn&#41;](failover-and-failover-modes-always-on-availability-groups.md)  
  
  

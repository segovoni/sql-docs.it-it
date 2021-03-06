---
title: Creare un gruppo di disponibilità (SQL Server PowerShell) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], creating
ms.assetid: bc69a7df-20fa-41e1-9301-11317c5270d2
caps.latest.revision: 39
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 65663e51d915b86a796bb98126c9efeebf74bf14
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37273507"
---
# <a name="create-an-availability-group-sql-server-powershell"></a>Creare un gruppo di disponibilità (SQL Server PowerShell)
  In questo argomento si illustra come usare i cmdlet di PowerShell per creare e configurare un gruppo di disponibilità AlwaysOn usando PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Un *gruppo di disponibilità* permette di definire un set di database utente di cui sarà eseguito il failover come unità singola e un set di partner di failover, noti come *repliche di disponibilità*, che supportano il failover.  
  
> [!NOTE]  
>  Per un'introduzione ai gruppi di disponibilità, vedere [Panoramica di Gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).  
  

  
> [!NOTE]  
>  In alternativa all'uso dei cmdlet di PowerShell, è possibile usare la procedura guidata Crea gruppo di disponibilità o [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Per altre informazioni, vedere [Usare la finestra di dialogo Nuovo gruppo di disponibilità &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md) o [Creare un gruppo di disponibilità &#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md).  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
 Prima di iniziare a creare il primo gruppo di disponibilità, è consigliabile leggere questa sezione.  
  
###  <a name="PrerequisitesRestrictions"></a> Prerequisiti, restrizioni e raccomandazioni  
  
-   Prima di creare un gruppo di disponibilità, verificare che le istanze host di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] si trovino ognuna in un nodo WSCF (Windows Server Failover Clustering) diverso di un singolo cluster di failover WSFC. Inoltre, verificare che le istanze del server abbiano soddisfatto gli altri prerequisiti dell'istanza del server, che tutti gli altri requisiti di [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] siano soddisfatti e che si tengano presenti i consigli. Per altre informazioni è consigliabile leggere [Prerequisiti, restrizioni e consigli per i gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
 Sono necessarie l'appartenenza al ruolo predefinito del server **sysadmin** e l'autorizzazione server CREATE AVAILABILITY GROUP oppure l'autorizzazione ALTER ANY AVAILABILITY GROUP o CONTROL SERVER.  
  
###  <a name="SummaryPSStatements"></a> Riepilogo delle attività e cmdlet di PowerShell corrispondenti  
 Nella tabella seguente sono elencate le attività di base necessarie per la configurazione di un gruppo di disponibilità e sono indicate le attività supportate dai cmdlet di PowerShell. È necessario eseguire le attività [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] nell'ordine con cui sono elencate nella tabella.  
  
|Attività|Cmdlet di PowerShell (se disponibile) o istruzione Transact-SQL|Posizione in cui eseguire l'attività**<sup>*</sup>**|  
|----------|--------------------------------------------------------------------|-------------------------------------------|  
|Creare un endpoint del mirroring del database (una volta per ogni istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] )|`New-SqlHadrEndPoint`|Eseguire in ogni istanza del server in cui non è presente l'endpoint del mirroring del database.<br /><br /> Nota: Per modificare un endpoint del mirroring di database esistente, usare `Set-SqlHadrEndpoint`.|  
|Creare un gruppo di disponibilità|Usare innanzitutto il cmdlet `New-SqlAvailabilityReplica` con il parametro `-AsTemplate` per creare un oggetto della replica di disponibilità in memoria per ognuna delle due repliche di disponibilità che si desidera includere nel gruppo di disponibilità.<br /><br /> Quindi, creare il gruppo di disponibilità usando il `New-SqlAvailabilityGroup` cmdlet e riferimento a oggetti di replica di disponibilità.|Eseguire nell'istanza del server che dovrà ospitare la replica primaria iniziale.|  
|Creare un join della replica secondaria al gruppo di disponibilità|`Join-SqlAvailabilityGroup`|Eseguire in ogni istanza del server in cui è ospitata una replica secondaria.|  
|Preparare il database secondario|`Backup-SqlDatabase` e `Restore-SqlDatabase`|Creare i backup nell'istanza del server in cui è ospitata la replica primaria.<br /><br /> Ripristinare i backup in ogni istanza del server in cui è ospitata una replica secondaria, usando il parametro di ripristino `NoRecovery`. Se i percorsi di file differiscono tra i computer in cui sono ospitate la replica primaria e la replica secondaria di destinazione, usare anche il parametro di ripristino `RelocateFile`.|  
|Avviare la sincronizzazione dei dati creando un join di ogni database secondario al gruppo di disponibilità|`Add-SqlAvailabilityDatabase`|Eseguire in ogni istanza del server in cui è ospitata una replica secondaria.|  
  
 **<sup>*</sup>**  Per eseguire un'attività specifica, impostare la directory (`cd`) alle istanze del server indicate.  
  
###  <a name="PsProviderLinks"></a> Per impostare e usare il provider PowerShell per SQL Server  
  
-   [Provider PowerShell per SQL Server](../../../powershell/sql-server-powershell-provider.md)  
  
-   [Visualizzare la Guida di SQL Server PowerShell](../../../powershell/sql-server-powershell.md)  
  
##  <a name="PowerShellProcedure"></a> Utilizzo di PowerShell per creare e configurare un gruppo di disponibilità  
  
> [!NOTE]  
>  Per visualizzare la sintassi e un esempio di un cmdlet specifico, usare il `Get-Help` cmdlet di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ambiente PowerShell. Per altre informazioni, vedere [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
1.  Passare alla directory (`cd`) all'istanza del server che dovrà ospitare la replica primaria.  
  
2.  Creare un oggetto replica di disponibilità in memoria per la replica primaria.  
  
3.  Creare un oggetto replica di disponibilità in memoria per ognuna delle repliche secondarie.  
  
4.  Creare il gruppo di disponibilità.  
  
    > [!NOTE]  
    >  La lunghezza massima consentita per il nome del gruppo di disponibilità è 128 caratteri.  
  
5.  Creare un join della nuova replica secondaria al gruppo di disponibilità. Per altre informazioni, vedere [Creare un join di una replica secondaria a un gruppo di disponibilità &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md).  
  
6.  Per ogni database nel gruppo di disponibilità, creare un database secondario ripristinando i backup recenti del database primario, usando RESTORE WITH NORECOVERY.  
  
7.  Creare un join di ogni nuovo database secondario al gruppo di disponibilità. Per altre informazioni, vedere [Creare un join di una replica secondaria a un gruppo di disponibilità &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md).  
  
8.  Facoltativamente, utilizzare il Windows `dir` per verificare se il contenuto del nuovo gruppo di disponibilità.  
  
> [!NOTE]  
>  Se gli account del servizio [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] delle istanze del server sono eseguiti con account utente di dominio diversi, in ogni istanza del server creare un account di accesso per l'altra istanza del server e concedere a questo account l'autorizzazione CONNECT per l'endpoint del mirroring del database locale.  
  
##  <a name="ExampleConfigureGroup"></a> Esempio: Utilizzo di PowerShell per creare un gruppo di disponibilità  
 Nell'esempio di PowerShell seguente si crea e si configura un gruppo di disponibilità semplice denominato `MyAG` con due repliche di disponibilità e un database di disponibilità. Esempio:  
  
1.  Viene eseguito il backup di `MyDatabase` e del relativo log delle transazioni.  
  
2.  Consente di ripristinare `MyDatabase` relativa transazione e di log, utilizzando il `-NoRecovery` opzione.  
  
3.  Viene creata una rappresentazione in memoria della replica primaria, che sarà ospitata dall'istanza locale di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (denominata `PrimaryComputer\Instance`).  
  
4.  Viene creata una rappresentazione in memoria della replica secondaria, che sarà ospitata da un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (denominata `SecondaryComputer\Instance`).  
  
5.  Viene creato un nuovo gruppo di disponibilità denominato `MyAG`.  
  
6.  Viene creato un join della replica secondaria al gruppo di disponibilità.  
  
7.  Viene creato un join del database secondario al gruppo di disponibilità.  
  
```  
# Backup my database and its log on the primary  
Backup-SqlDatabase `  
    -Database "MyDatabase" `  
    -BackupFile "\\share\backups\MyDatabase.bak" `  
    -ServerInstance "PrimaryComputer\Instance"  
  
Backup-SqlDatabase `  
    -Database "MyDatabase" `  
    -BackupFile "\\share\backups\MyDatabase.log" `  
    -ServerInstance "PrimaryComputer\Instance" `  
    -BackupAction Log   
  
# Restore the database and log on the secondary (using NO RECOVERY)  
Restore-SqlDatabase `  
    -Database "MyDatabase" `  
    -BackupFile "\\share\backups\MyDatabase.bak" `  
    -ServerInstance "SecondaryComputer\Instance" `  
    -NoRecovery  
  
Restore-SqlDatabase `  
    -Database "MyDatabase" `  
    -BackupFile "\\share\backups\MyDatabase.log" `  
    -ServerInstance "SecondaryComputer\Instance" `  
    -RestoreAction Log `  
    -NoRecovery  
  
# Create an in-memory representation of the primary replica.  
$primaryReplica = New-SqlAvailabilityReplica `  
    -Name "PrimaryComputer\Instance" `  
    -EndpointURL "TCP://PrimaryComputer.domain.com:5022" `  
    -AvailabilityMode "SynchronousCommit" `  
    -FailoverMode "Automatic" `  
    -Version 12 `  
    -AsTemplate  
  
# Create an in-memory representation of the secondary replica.  
$secondaryReplica = New-SqlAvailabilityReplica `  
    -Name "SecondaryComputer\Instance" `  
    -EndpointURL "TCP://SecondaryComputer.domain.com:5022" `  
    -AvailabilityMode "SynchronousCommit" `  
    -FailoverMode "Automatic" `  
    -Version 12 `  
    -AsTemplate  
  
# Create the availability group  
New-SqlAvailabilityGroup `  
    -Name "MyAG" `  
    -Path "SQLSERVER:\SQL\PrimaryComputer\Instance" `  
    -AvailabilityReplica @($primaryReplica,$secondaryReplica) `  
    -Database "MyDatabase"  
  
# Join the secondary replica to the availability group.  
Join-SqlAvailabilityGroup -Path "SQLSERVER:\SQL\SecondaryComputer\Instance" -Name "MyAG"  
  
# Join the secondary database to the availability group.  
Add-SqlAvailabilityDatabase -Path "SQLSERVER:\SQL\SecondaryComputer\Instance\AvailabilityGroups\MyAG" -Database "MyDatabase"  
```  
  
##  <a name="RelatedTasks"></a> Attività correlate  
 **Per configurare un'istanza del server per gruppi di disponibilità AlwaysOn**  
  
-   [Abilitare e disabilitare la funzionalità Gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](enable-and-disable-always-on-availability-groups-sql-server.md)  
  
-   [Creare un Endpoint del mirroring per i gruppi di disponibilità AlwaysOn &#40;SQL Server PowerShell&#41;](database-mirroring-always-on-availability-groups-powershell.md)  
  
 **Per configurare le proprietà della replica e del gruppo di disponibilità**  
  
-   [Modificare la modalità di disponibilità di una replica di disponibilità &#40;SQL Server&#41;](change-the-availability-mode-of-an-availability-replica-sql-server.md)  
  
-   [Modificare la modalità di failover di una replica di disponibilità &#40;SQL Server&#41;](change-the-failover-mode-of-an-availability-replica-sql-server.md)  
  
-   [Creare o configurare un listener del gruppo di disponibilità &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [Configurare i criteri di Failover flessibili per controllare le condizioni per il Failover automatico (gruppi di disponibilità AlwaysOn)](configure-flexible-automatic-failover-policy.md)  
  
-   [Specifica dell'URL dell'endpoint quando si aggiunge o si modifica una replica di disponibilità &#40;SQL Server&#41;](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
-   [Configurare il backup su repliche di disponibilità &#40;SQL Server&#41;](configure-backup-on-availability-replicas-sql-server.md)  
  
-   [Configurare l'accesso in sola lettura in una replica di disponibilità &#40;SQL Server&#41;](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [Configurare il routing di sola lettura per un gruppo di disponibilità &#40;SQL Server&#41;](configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [Modificare il periodo di timeout della sessione per una replica di disponibilità &#40;SQL Server&#41;](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
 **Per completare la configurazione del gruppo di disponibilità**  
  
-   [Creare un join di una replica secondaria a un gruppo di disponibilità &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [Preparare manualmente un database secondario per un gruppo di disponibilità &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [Creare un join di un database secondario a un gruppo di disponibilità &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [Creare o configurare un listener del gruppo di disponibilità &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)  
  
 **Modalità alternative di creazione di un gruppo di disponibilità**  
  
-   [Usare la Creazione guidata Gruppo di disponibilità &#40;SQL Server Management Studio&#41;](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Utilizzare la finestra di dialogo Nuovo gruppo di disponibilità &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [Creare un gruppo di disponibilità &#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md)  
  
 **Per risolvere i problemi di configurazione di gruppi di disponibilità AlwaysOn**  
  
-   [Risolvere i problemi di configurazione di gruppi di disponibilità di AlwaysOn (SQL Server) eliminato](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
-   [Risolvere i problemi di un'operazione di aggiunta File non riuscita &#40;gruppi di disponibilità AlwaysOn&#41;](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
  
##  <a name="RelatedContent"></a> Contenuto correlato  
  
-   **Blog:**  
  
     [Su AlwaysON - HADRON serie: Utilizzo del Pool di lavoro per HADRON database abilitati](http://blogs.msdn.com/b/psssql/archive/2012/05/17/alwayson-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
     [Configurazione di AlwaysOn con PowerShell per SQL Server](http://blogs.msdn.com/b/sqlalwayson/archive/2012/02/03/configuring-alwayson-with-sql-server-powershell.aspx)  
  
     [SQL Server AlwaysOn Team blog: Il Blog ufficiale di SQL Server AlwaysOn Team](http://blogs.msdn.com/b/sqlalwayson/)  
  
     [Pagina relativa ai blog del Servizio Supporto Tecnico Clienti per gli ingegneri di SQL Server](http://blogs.msdn.com/b/psssql/)  
  
-   **Video:**  
  
     [Serie di Microsoft SQL Server nome in codice "Denali" AlwaysOn, parte 1: Presentazione della soluzione di disponibilità elevata di prossima generazione](http://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [Serie di Microsoft SQL Server nome in codice "Denali" AlwaysOn, parte 2: Creazione di una soluzione di disponibilità elevata critica tramite Alwasyon](http://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   **White paper:**  
  
     [Microsoft SQL Server AlwaysOn Solutions Guide for High Availability and Disaster Recovery](http://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [Pagina relativa ai white paper Microsoft per SQL Server 2012](http://msdn.microsoft.com/library/hh403491.aspx)  
  
     [Pagina relativa ai white paper del team di consulenza clienti di SQL Server](http://sqlcat.com/)  
  
## <a name="see-also"></a>Vedere anche  
 [Endpoint del mirroring del database &#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md)   
 [Panoramica di gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)  
  
  

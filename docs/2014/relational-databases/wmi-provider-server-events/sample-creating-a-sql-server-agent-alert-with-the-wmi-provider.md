---
title: 'Esempio: Creazione di un avviso SQL Server Agent tramite il Provider WMI per eventi del Server | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Agent [WMI]
- WMI Provider for Server Events, samples
- sample applications [WMI]
ms.assetid: d44811c7-cd46-4017-b284-c863ca088e8f
caps.latest.revision: 14
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 6c6a8ded031806322961d5f56a1b0ba28fe6dad3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37186218"
---
# <a name="sample-creating-a-sql-server-agent-alert-by-using-the-wmi-provider-for-server-events"></a>Esempio: Creazione di un avviso di SQL Server Agent tramite il provider WMI per eventi del server
  Un utilizzo comune del provider di eventi WMI consiste nel creare avvisi di SQL Server Agent in risposta a eventi specifici. Nell'esempio seguente viene presentato un avviso semplice che salva eventi Deadlock Graph XML in una tabella per l'analisi successiva. SQL Server Agent invia una richiesta WQL, riceve eventi WMI ed esegue un processo in risposta all'evento. Si noti che benché diversi oggetti di Service Broker siano interessati dall'elaborazione del messaggio di notifica, il provider di eventi WMI gestisce i dettagli della creazione e della gestione di tali oggetti.  
  
## <a name="example"></a>Esempio  
 Viene innanzitutto creata una tabella nel database `AdventureWorks` in cui includere l'evento Deadlock Graph. La tabella è costituita da due colonne: la colonna `AlertTime` contiene la durata di esecuzione dell'avviso, mentre la colonna `DeadlockGraph` contiene il documento XML che include l'evento Deadlock Graph.  
  
 Viene quindi creato l'avviso. Lo script crea innanzitutto il processo eseguito dall'avviso, aggiunge un passaggio del processo al processo e specifica come destinazione del processo l'istanza corrente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Lo script crea quindi l'avviso.  
  
 Il passaggio del processo recupera le **TextData** proprietà dell'istanza dell'evento WMI e inserisce tale valore nel **DeadlockGraph** colonna del **DeadlockEvents** tabella. Si noti che [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] converte in modo implicito la stringa in formato XML. Poiché utilizza il sottosistema [!INCLUDE[tsql](../../includes/tsql-md.md)], il passaggio del processo non specifica un proxy.  
  
 L'avviso esegue il processo ogni volta che viene registrato un evento di traccia Deadlock Graph. Per un avviso WMI, SQL Server Agent crea una query di notifica utilizzando lo spazio dei nomi e l'istruzione WQL specificati. Per questo avviso, SQL Server Agent esegue il monitoraggio dell'istanza predefinita nel computer locale. L'istruzione WQL richiede tutti gli eventi `DEADLOCK_GRAPH` nell'istanza predefinita. Per modificare l'istanza monitorata dall'avviso, sostituire il nome dell'istanza per `MSSQLSERVER` in `@wmi_namespace` per l'avviso.  
  
> [!NOTE]  
>  Per SQL Server Agent riceva eventi WMI, [!INCLUDE[ssSB](../../includes/sssb-md.md)] deve essere abilitata nel **msdb** e [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
USE AdventureWorks ;  
GO  
  
IF OBJECT_ID('DeadlockEvents', 'U') IS NOT NULL  
BEGIN  
    DROP TABLE DeadlockEvents ;  
END ;  
GO  
  
CREATE TABLE DeadlockEvents  
    (AlertTime DATETIME, DeadlockGraph XML) ;  
GO  
-- Add a job for the alert to run.  
  
EXEC  msdb.dbo.sp_add_job @job_name=N'Capture Deadlock Graph',   
    @enabled=1,   
    @description=N'Job for responding to DEADLOCK_GRAPH events' ;  
GO  
  
-- Add a jobstep that inserts the current time and the deadlock graph into  
-- the DeadlockEvents table.  
  
EXEC msdb.dbo.sp_add_jobstep  
    @job_name = N'Capture Deadlock Graph',  
    @step_name=N'Insert graph into LogEvents',  
    @step_id=1,   
    @on_success_action=1,   
    @on_fail_action=2,   
    @subsystem=N'TSQL',   
    @command= N'INSERT INTO DeadlockEvents  
                (AlertTime, DeadlockGraph)  
                VALUES (getdate(), N''$(ESCAPE_SQUOTE(WMI(TextData)))'')',  
    @database_name=N'AdventureWorks' ;  
GO  
  
-- Set the job server for the job to the current instance of SQL Server.  
  
EXEC msdb.dbo.sp_add_jobserver @job_name = N'Capture Deadlock Graph' ;  
GO  
  
-- Add an alert that responds to all DEADLOCK_GRAPH events for  
-- the default instance. To monitor deadlocks for a different instance,  
-- change MSSQLSERVER to the name of the instance.  
  
EXEC msdb.dbo.sp_add_alert @name=N'Respond to DEADLOCK_GRAPH',   
@wmi_namespace=N'\\.\root\Microsoft\SqlServer\ServerEvents\MSSQLSERVER',   
    @wmi_query=N'SELECT * FROM DEADLOCK_GRAPH',   
    @job_name='Capture Deadlock Graph' ;  
GO  
```  
  
## <a name="testing-the-sample"></a>Test dell'esempio  
 Per visualizzare l'esecuzione del processo, provocare un deadlock. Nelle [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], aprire due **Query SQL** schede e connettere entrambe le query alla stessa istanza. Eseguire lo script seguente in una delle schede delle query. Questo script produce un set di risultati e viene terminato.  
  
```  
USE AdventureWorks ;  
GO  
  
BEGIN TRANSACTION ;  
GO  
  
SELECT TOP(1) Name FROM Production.Product WITH (XLOCK) ;  
GO  
```  
  
 Eseguire lo script seguente nella seconda scheda della query. Lo script produce un set di risultati e quindi si blocca, in attesa di acquisire un blocco su `Production.Product`.  
  
```  
USE AdventureWorks ;  
GO  
  
BEGIN TRANSACTION ;  
GO  
  
SELECT TOP(1) Name FROM Production.Location WITH (XLOCK) ;  
GO  
  
SELECT TOP(1) Name FROM Production.Product WITH (XLOCK) ;  
GO  
```  
  
 Eseguire lo script seguente nella prima scheda della query. Questo script si blocca, in attesa di acquisire un blocco su `Production.Location`. Dopo un breve timeout, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sceglierà questo script o lo script nell'esempio come vittima del deadlock e terminerà la transazione.  
  
```  
SELECT TOP(1) Name FROM Production.Location WITH (XLOCK) ;  
GO  
```  
  
 Dopo avere provocato il deadlock, attendere alcuni momenti prima che SQL Server Agent attivi l'avviso ed esegua il processo. Esaminare il contenuto della tabella `DeadlockEvents` eseguendo lo script seguente:  
  
```  
SELECT * FROM DeadlockEvents ;  
GO  
```  
  
 La colonna `DeadlockGraph` deve contenere un documento XML indicante tutte le proprietà dell'evento Deadlock Graph.  
  
## <a name="see-also"></a>Vedere anche  
 [Concetti relativi al provider WMI per eventi del server](wmi-provider-for-server-events-concepts.md)  
  
  

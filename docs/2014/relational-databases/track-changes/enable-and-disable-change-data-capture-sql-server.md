---
title: Abilitare e disabilitare Change Data Capture (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- change data capture [SQL Server], enabling tables
- change data capture [SQL Server], enabling databases
- change data capture [SQL Server], disabling databases
- change data capture [SQL Server], disabling tables
ms.assetid: b741894f-d267-4b10-adfe-cbc14aa6caeb
caps.latest.revision: 13
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: e96cb5bb777544b8a3a390eee59a16e0213c857f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37309511"
---
# <a name="enable-and-disable-change-data-capture-sql-server"></a>Abilitare e disabilitare Change Data Capture (SQL Server)
  In questo argomento viene descritto come abilitare e disabilitare Change Data Capture per un database e una tabella.  
  
## <a name="enable-change-data-capture-for-a-database"></a>Abilitazione di Change Data Capture per un database  
 Prima che sia possibile creare un'istanza di acquisizione per singole tabelle, è innanzitutto necessario che un membro del ruolo predefinito del server `sysadmin` abiliti il database per Change Data Capture. Questa operazione viene eseguita eseguendo la stored procedure [sys.sp_cdc_enable_db &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-enable-db-transact-sql) nel contesto del database. Per determinare se un database è già abilitato, eseguire una query sulla colonna `is_cdc_enabled` nella vista del catalogo `sys.databases`.  
  
 Quando un database è abilitato per change data capture, il `cdc` dello schema, `cdc` utente, le tabelle di metadati e altri oggetti di sistema vengono create per il database. Il `cdc` schema contiene le tabelle di metadati di change data capture e, dopo che le tabelle di origine sono abilitate per change data capture, le singole tabelle delle modifiche fungono da repository per i dati delle modifiche. Il `cdc` schema contiene inoltre funzioni di sistema associate usate per eseguire query per i dati delle modifiche.  
  
 Change Data Capture richiede l'utilizzo esclusivo dello schema `cdc` e dell'utente `cdc`. Se in un database è attualmente presente uno schema o un utente di database denominato *cdc* , il database non può essere abilitato per Change Data Capture fino all'eliminazione o alla ridenominazione dello schema o dell'utente.  
  
 Per un esempio di abilitazione di un database, vedere il modello Enable Database for Change Data Capture.  
  
> [!IMPORTANT]  
>  Per individuare i modelli in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], scegliere **Esplora modelli**dal menu **Visualizza**, quindi selezionare **Modelli di SQL Server**. **Change Data Capture** è una sottocartella. che contiene tutti i modelli a cui si fa riferimento in questo argomento. È inoltre presente un'icona **Esplora modelli** sulla barra degli strumenti di [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] .  
  
```tsql  
-- ====  
-- Enable Database for CDC template   
-- ====  
USE MyDB  
GO  
EXEC sys.sp_cdc_enable_db  
GO  
```  
  
## <a name="disable-change-data-capture-for-a-database"></a>Disabilitazione di Change Data Capture per un database  
 Un membro del `sysadmin` ruolo predefinito del server può eseguire la stored procedure [Sys. sp_cdc_disable_db &#40;Transact-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-disable-db-transact-sql) nel contesto del database per disabilitare change data capture per un database. Non è necessario disabilitare singole tabelle prima di disabilitare il database. La disabilitazione del database consente di rimuovere tutti i metadati di acquisizione dei dati modifica associata, tra cui la `cdc` utente e schema di change data capture processi. Eventuali ruoli di controllo creati da Change Data Capture, tuttavia, non verranno rimossi automaticamente e devono essere eliminati in modo esplicito. Per determinare se un database è abilitato, eseguire una query sulla colonna `is_cdc_enabled` nella vista del catalogo sys.databases.  
  
 Se viene eliminato un database abilitato per Change Data Capture, i processi Change Data Capture vengono automaticamente rimossi.  
  
 Per un esempio di disabilitazione di un database, vedere il modello Disable Database for Change Data Capture.  
  
> [!IMPORTANT]  
>  Per individuare i modelli in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], scegliere **Esplora modelli**dal menu **Visualizza**, quindi fare clic su **Modelli di SQL Server**. **Change Data Capture** è una sottocartella contenente tutti i modelli a cui si fa riferimento in questo argomento. È inoltre presente un'icona **Esplora modelli** sulla barra degli strumenti di [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] .  
  
```tsql  
-- =======  
-- Disable Database for Change Data Capture template   
-- =======  
USE MyDB  
GO  
EXEC sys.sp_cdc_disable_db  
GO  
```  
  
## <a name="enable-change-data-capture-for-a-table"></a>Abilitazione di Change Data Capture per una tabella  
 Dopo avere abilitato per change data capture, i membri di un database di `db_owner` ruolo predefinito del database è possibile creare un'istanza di acquisizione per singole tabelle di origine usando la stored procedure `sys.sp_cdc_enable_table`. Per determinare se una tabella di origine è già stata abilitata per Change Data Capture, esaminare la colonna is_tracked_by_cdc nella vista del catalogo `sys.tables`.  
  
 Quando si crea un'istanza di acquisizione, è possibile specificare le opzioni seguenti:  
  
 `Columns in the source table to be captured`(Indici per tabelle con ottimizzazione per la memoria).  
  
 Per impostazione predefinita, tutte le colonne della tabella di origine vengono identificate come colonne acquisite. Se è necessario rilevare solo un subset di colonne, ad esempio per motivi di privacy o di prestazioni, usare il parametro *@captured_column_list* per specificare il subset di colonne.  
  
 `A filegroup to contain the change table.`  
  
 Per impostazione predefinita, la tabella delle modifiche si trova nel filegroup predefinito del database. I proprietari del database che vogliono controllare la posizione di singole tabelle delle modifiche possono usare il parametro *@filegroup_name* per specificare un determinato filegroup per la tabella delle modifiche associata all'istanza di acquisizione. È necessario che il filegroup specificato sia già presente. È in genere consigliabile inserire le tabelle delle modifiche in un filegroup distinto dalle tabelle di origine. Vedere le `Enable a Table Specifying Filegroup Option` modello per un esempio su come usare il *@filegroup_name* parametro.  
  
```tsql  
-- =========  
-- Enable a Table Specifying Filegroup Option Template  
-- =========  
USE MyDB  
GO  
  
EXEC sys.sp_cdc_enable_table  
@source_schema = N'dbo',  
@source_name   = N'MyTable',  
@role_name     = N'MyRole',  
@filegroup_name = N'MyDB_CT',  
@supports_net_changes = 1  
GO  
```  
  
 `A role for controlling access to a change table.`  
  
 Lo scopo del ruolo specificato consiste nel controllare l'accesso ai dati delle modifiche. Il ruolo specificato può essere un ruolo predefinito del server esistente o un ruolo del database. Se il ruolo specificato non è già presente, verrà automaticamente creato un ruolo del database con il nome indicato. I membri del ruolo `sysadmin` o `db_owner` dispongono di accesso completo ai dati nelle tabelle delle modifiche. Tutti gli altri utenti devono disporre dell'autorizzazione SELECT per tutte le colonne acquisite della tabella di origine. Inoltre, quando viene specificato un ruolo, gli utenti che non sono membri di entrambi i `sysadmin` o `db_owner` ruolo deve anche essere membri del ruolo specificato.  
  
 Se non si vuole usare un ruolo di controllo, impostare in modo esplicito il parametro *@role_name* su Null. Per un esempio di abilitazione di una tabella senza un ruolo di controllo, vedere il modello `Enable a Table Without Using a Gating Role`.  
  
```tsql  
-- =========  
-- Enable a Table Without Using a Gating Role template   
-- =========  
USE MyDB  
GO  
EXEC sys.sp_cdc_enable_table  
@source_schema = N'dbo',  
@source_name   = N'MyTable',  
@role_name     = NULL,  
@supports_net_changes = 1  
GO  
  
```  
  
 `A function to query for net changes.`  
  
 Un'istanza di acquisizione includerà sempre una funzione con valori di tabella per la restituzione di tutte le voci della tabella delle modifiche generate in un intervallo definito. Il nome di questa funzione viene creato aggiungendo il nome dell'istanza di acquisizione a "cdc.fn_cdc_get_all_changes_." Per altre informazioni, vedere [cdc.fn_cdc_get_all_changes_&#60;capture_instance&#62; &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql).  
  
 Se il parametro *@supports_net_changes* è impostato su 1, viene generata anche una funzione del rilevamento delle modifiche delta. Questa funzione restituisce solo una modifica per ogni riga distinta modificata nell'intervallo specificato nella chiamata. Per altre informazioni, vedere [cdc.fn_cdc_get_net_changes_&#60;capture_instance&#62; &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql).  
  
 Per supportare le query sulle modifiche delta, è necessario che la tabella di origine disponga di una chiave primaria o di un indice univoco per identificare le righe in modo univoco. Se viene usato un indice univoco, il nome dell'indice deve essere specificato con il parametro *@index_name* . Le colonne definite nella chiave primaria o nell'indice univoco devono essere incluse nell'elenco delle colonne di origine da acquisire.  
  
 Per un esempio di creazione di un'istanza di acquisizione con entrambe le funzioni di query, vedere il modello `Enable a Table for All and Net Changes Queries`.  
  
```tsql  
-- =============  
-- Enable a Table for All and Net Changes Queries template   
-- =============  
USE MyDB  
GO  
EXEC sys.sp_cdc_enable_table  
@source_schema = N'dbo',  
@source_name   = N'MyTable',  
@role_name     = N'MyRole',  
@supports_net_changes = 1  
GO  
```  
  
> [!NOTE]  
>  Se Change Data Capture è abilitato in una tabella con una chiave primaria esistente e non viene usato il parametro *@index_name* per identificare un indice univoco alternativo, la funzionalità Change Data Capture userà la chiave primaria. Non saranno consentite modifiche successive alla chiave primaria se prima non si disabilita Change Data Capture per la tabella. Questa regola è sempre valida, indipendentemente dal fatto che durante la configurazione di Change Data Capture sia stato o meno richiesto il supporto per le query sulle modifiche delta. Se in una tabella non è presente alcuna chiave primaria al momento dell'abilitazione di Change Data Capture, l'aggiunta successiva di una chiave primaria verrà ignorata da Change Data Capture. Poiché Change Data Capture non utilizzerà una chiave primaria creata in seguito all'abilitazione della tabella, la chiave e le colonne chiave possono essere rimosse senza restrizioni.  
  
## <a name="disable-change-data-capture-for-a-table"></a>Disabilitazione di Change Data Capture per una tabella  
 I membri del `db_owner` ruolo predefinito del database possono rimuovere un'istanza di acquisizione per singole tabelle di origine usando la stored procedure `sys.sp_cdc_disable_table`. Per determinare se una tabella di origine sia attualmente abilitata per Change Data Capture, esaminare la colonna `is_tracked_by_cdc` nella vista del catalogo `sys.tables`. Se in seguito alla disabilitazione non è presente alcuna tabella abilitata per il database, vengono rimossi anche i processi Change Data Capture.  
  
 Se viene eliminata una tabella abilitata per Change Data Capture, i metadati di Change Data Capture associati alla tabella vengono automaticamente rimossi.  
  
 Per un esempio di disabilitazione di una tabella, vedere il modello Disable a Capture Instance for a Table.  
  
```tsql  
-- =====  
-- Disable a Capture Instance for a Table template   
-- =====  
USE MyDB  
GO  
EXEC sys.sp_cdc_disable_table  
@source_schema = N'dbo',  
@source_name   = N'MyTable',  
@capture_instance = N'dbo_MyTable'  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Tenere traccia delle modifiche ai dati &#40;SQL Server&#41;](track-data-changes-sql-server.md)   
 [Informazioni su Change Data Capture &#40;SQL Server&#41;](../track-changes/about-change-data-capture-sql-server.md)   
 [Utilizzare i dati delle modifiche &#40;SQL Server&#41;](work-with-change-data-sql-server.md)   
 [Amministrare e monitorare Change Data Capture &#40;SQL Server&#41;](../track-changes/administer-and-monitor-change-data-capture-sql-server.md)  
  
  

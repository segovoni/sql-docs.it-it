---
title: core.sp_create_snapshot (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_create_snapshot
- sp_create_snapshot_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- management data warehouse, data collector stored procedures
- data collector [SQL Server], stored procedures
- core.sp_create_snapshot stored procedure
- sp_create_snapshot
ms.assetid: ff297bda-0ee2-4fda-91c8-7000377775e3
caps.latest.revision: 22
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 33ba9d69763a9d07cc9907aef60397b6c5b37eee
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "33238568"
---
# <a name="corespcreatesnapshot-transact-sql"></a>core.sp_create_snapshot (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Inserisce una riga nella vista core.snapshots del data warehouse di gestione. Questa procedura viene chiamata tutte le volte che un pacchetto di caricamento avvia il caricamento dei dati nel data warehouse di gestione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
core.sp_create_snapshot [ @collection_set_uid = ] 'collection_set_uid'  
    , [ @collector_type_uid = ] 'collector_type_uid'  
    ,[ @machine_name = ] 'machine_name'  
    , [ @named_instance = ] 'named_instance'  
    , [ @log_id = ] log_id  
    , [ @snapshot_id = ] snapshot_id OUTPUT  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @collection_set_uid =] '*collection_set_uid*'  
 GUID per il set di raccolta. *collection_set_uid* viene **uniqueidentifier** non prevede alcun valore predefinito. Per ottenere il GUID, eseguire una query sulla vista dbo.syscollector_collection_sets nel database msdb.  
  
 [ @collector_type_uid =] '*collector_type_uid*'  
 GUID per un tipo agente di raccolta. *collector_type_uid* viene **uniqueidentifier** non prevede alcun valore predefinito. Per ottenere il GUID, eseguire una query sulla vista dbo.syscollector_collector_types nel database msdb.  
  
 [ @machine_name=] '*nome_computer*'  
 Nome del server in cui risiede l'insieme di raccolta. *nome_computer* viene **sysname**, senza alcun valore predefinito.  
  
 [ @named_instance=] '*named_instance*'  
 Nome dell'istanza per l'insieme di raccolta. *named_instance* viene **sysname**, senza alcun valore predefinito.  
  
 [ @log_id = ] *log_id*  
 Identificatore univoco tramite cui viene eseguito il mapping al registro eventi del set di raccolta nel server da cui sono stati raccolti i dati. *log_id* viene **bigint** non prevede alcun valore predefinito. Per ottenere il valore per *log_id*, query sulla vista syscollector_execution_log nel database msdb.  
  
 [ @snapshot_id = ] *snapshot_id*  
 Identificatore univoco per una riga inserita nella vista snapshots. *snapshot_id* viene **int** e viene restituito come OUTPUT.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Remarks  
 Ogni volta che un pacchetto di caricamento inizia a caricare i dati nel data warehouse di gestione, il componente runtime dell'agente di raccolta dati chiama core.sp_create_snapshot.  
  
 Tramite questa procedura viene verificato quanto segue:  
  
-   Corrispondenza di collection_set_uid con una voce esistente nella tabella core.source_info_internal.  
  
-   Corrispondenza di collector_type_uid con una voce esistente nella vista core.supported_collector_types.  
  
 Se una delle due precedenti verifiche non ha esito positivo, la procedura ha esito negativo e viene restituito un errore.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza di **mdw_writer** (con autorizzazione EXECUTE) ruolo predefinito del database.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene creato uno snapshot per il set di raccolta Utilizzo disco, lo snapshot viene aggiunto al data warehouse di gestione e viene restituito l'identificatore dello snapshot. In questo esempio viene utilizzata l'istanza predefinita.  
  
```  
USE <management_data_warehouse>;  
DECLARE @snapshot_id int;  
EXEC core.sp_create_snapshot   
    @collection_set_uid = '7B191952-8ECF-4E12-AEB2-EF646EF79FEF',   
    @collector_type_uid = '302E93D1-3424-4BE7-AA8E-84813ECF2419',  
    @machine_name = '<computername>',  
    @named_instance = 'MSSQLSERVER',  
    @log_id = 11, -- ID of the log for the collection set  
    @snapshot_id = @snapshot_id OUTPUT;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Stored procedure dell'agente di raccolta dati &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [Data warehouse di gestione](../../relational-databases/data-collection/management-data-warehouse.md)  
  
  

---
title: Sys. query_store_query (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/29/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- QUERY_STORE_QUERY
- SYS.QUERY_STORE_QUERY_TSQL
- SYS.QUERY_STORE_QUERY
- QUERY_STORE_QUERY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- query_store_query catalog view
- sys.query_store_query catalog view
ms.assetid: bdee149e-7556-4fc3-8242-925dd4b7b6ac
caps.latest.revision: 15
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: d9d53bc6cd0219502698ba8a02b6ba19eaf5f34f
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "37985187"
---
# <a name="sysquerystorequery-transact-sql"></a>Sys. query_store_query (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Contiene informazioni sulle query e le statistiche di esecuzione runtime aggregate complessivo associato.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**query_id**|**bigint**|Chiave primaria.|  
|**query_text_id**|**bigint**|Chiave esterna. Crea un join al [query_store_query_text &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql.md)|  
|**context_settings_id**|**bigint**|Chiave esterna. Crea un join al [sys.query_context_settings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-context-settings-transact-sql.md).|  
|**object_id**|**bigint**|ID dell'oggetto di database che fa parte della query (stored procedure, trigger, funzioni definite dall'utente CLR/UDAgg, ecc.). 0 se non viene eseguita la query come parte di un oggetto di database (query ad hoc).|  
|**batch_sql_handle**|**varbinary(64)**|ID del batch di istruzione della query fa parte di. Popolato solo se la query fa riferimento a tabelle temporanee o variabili di tabella.|  
|**query_hash**|**binary(8)**|Hash MD5 della singola query, basata sull'albero query logica. Include gli hint per query optimizer.|  
|**is_internal_query**|**bit**|La query è stata generata internamente.|  
|**query_parameterization_type**|**tinyint**|Tipo di parametrizzazione:<br /><br /> 0: nessuno<br /><br /> 1-utente<br /><br /> 2-semplice<br /><br /> 3 – forzato|  
|**query_parameterization_type_desc**|**nvarchar(60)**|Descrizione testuale per il tipo di parametrizzazione automatica.|  
|**initial_compile_start_time**|**datetimeoffset**|Compilare ora di inizio.|  
|**last_compile_start_time**|**datetimeoffset**|Compilare ora di inizio.|  
|**last_execution_time**|**datetimeoffset**|Ora dell'ultima esecuzione si riferisce all'ultima ora di fine del piano di query /.|  
|**last_compile_batch_sql_handle**|**varbinary(64)**|Handle dell'ultimo batch SQL in cui query è stata usata l'ora dell'ultima. Può essere fornita come input per [DM exec_sql_text &#40;Transact-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md) per ottenere il testo completo del batch.|  
|**last_compile_batch_offset_start**|**bigint**|Informazioni che possono essere fornite a DM exec_sql_text insieme last_compile_batch_sql_handle.|  
|**last_compile_batch_offset_end**|**bigint**|Informazioni che possono essere fornite a DM exec_sql_text insieme last_compile_batch_sql_handle.|  
|**count_compiles**|**bigint**|Statistiche della compilazione.|  
|**avg_compile_duration**|**float**|Statistiche di compilazione in microsecondi.|  
|**last_compile_duration**|**bigint**|Statistiche di compilazione in microsecondi.|  
|**avg_bind_duration**|**float**|Statistiche di associazione in microsecondi.|  
|**last_bind_duration**|**bigint**|Statistiche di associazione.|  
|**avg_bind_cpu_time**|**float**|Statistiche di associazione.|  
|**last_bind_cpu_time**|**bigint**|Statistiche di associazione.|  
|**avg_optimize_duration**|**float**|Statistiche di ottimizzazione espressa in microsecondi.|  
|**last_optimize_duration**|**bigint**|Statistiche di ottimizzazione.|  
|**avg_optimize_cpu_time**|**float**|Statistiche di ottimizzazione espressa in microsecondi.|  
|**last_optimize_cpu_time**|**bigint**|Statistiche di ottimizzazione.|  
|**avg_compile_memory_kb**|**float**|Compilare le statistiche di memoria.|  
|**last_compile_memory_kb**|**bigint**|Compilare le statistiche di memoria.|  
|**max_compile_memory_kb**|**bigint**|Compilare le statistiche di memoria.|  
|**is_clouddb_internal_query**|**bit**|Sempre 0 in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in locale.|  
  
## <a name="permissions"></a>Autorizzazioni  
 Richiede la **VIEW DATABASE STATE** l'autorizzazione.  
  
## <a name="see-also"></a>Vedere anche  
 [sys.database_query_store_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [sys.query_context_settings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-context-settings-transact-sql.md)   
 [sys.query_store_plan &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md)   
 [sys.query_store_query_text &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql.md)   
 [sys.query_store_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-wait-stats-transact-sql.md)  
 [sys.query_store_runtime_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-transact-sql.md)   
 [sys.query_store_runtime_stats_interval &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md)   
 [Monitoraggio delle prestazioni tramite Archivio query](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Stored procedure di Archivio query &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)   
 [sys.fn_stmt_sql_handle_from_sql_stmt &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-stmt-sql-handle-from-sql-stmt-transact-sql.md)  
  
  

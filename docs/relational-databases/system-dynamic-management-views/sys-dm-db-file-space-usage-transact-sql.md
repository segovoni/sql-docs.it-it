---
title: sys.dm_db_file_space_usage (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_db_file_space_usage
- sys.dm_db_file_space_usage_TSQL
- sys.dm_db_file_space_usage
- dm_db_file_space_usage_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_file_space_usage dynamic management view
ms.assetid: 148a5276-a8d5-49d2-8146-3c63d24c2144
caps.latest.revision: 45
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 456c6bd1a7b83012d2791ec8340f98a06413b09f
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/23/2018
---
# <a name="sysdmdbfilespaceusage-transact-sql"></a>sys.dm_db_file_space_usage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce informazioni sull'utilizzo dello spazio per ogni file nel database.  
  
> [!NOTE]  
>  Per chiamare questo metodo dal [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] o [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilizzare il nome **sys.dm_pdw_nodes_db_file_space_usage**.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|database_id|**smallint**|ID del database.|  
|file_id|**smallint**|ID di file.<br /><br /> file_id viene eseguito il mapping a file_id in [Sys.dm io_virtual_file_stats](../../relational-databases/system-dynamic-management-views/sys-dm-io-virtual-file-stats-transact-sql.md) e a fileid in [sysfiles](../../relational-databases/system-compatibility-views/sys-sysfiles-transact-sql.md).|  
|filegroup_id|**smallint**|**Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> ID del filegroup.|  
|total_page_count|**bigint**|**Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Numero totale di pagine nel file.|  
|allocated_extent_page_count|**bigint**|**Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Numero totale di pagine negli extent allocati nel file.|  
|unallocated_extent_page_count|**bigint**|Numero totale di pagine negli extent non allocati nel file.<br /><br /> Non sono incluse le pagine inutilizzate negli extent allocati.|  
|version_store_reserved_page_count|**bigint**|Numero totale di pagine negli extent uniformi allocati per l'archivio delle versioni. Le pagine dell'archivio delle versioni non vengono mai allocate dagli extent misti.<br /><br /> Le pagine IAM non vengono incluse perché vengono sempre allocate dagli extent misti. Le pagine PFS vengono incluse se vengono allocate da un extent uniforme.<br /><br /> Per ulteriori informazioni, vedere [tran_version_store & #40; Transact-SQL & #41; ](../../relational-databases/system-dynamic-management-views/sys-dm-tran-version-store-transact-sql.md).|  
|user_object_reserved_page_count|**bigint**|Numero totale di pagine allocate da extent uniformi per gli oggetti utente nel database. Sono incluse nel conteggio le pagine non utilizzate da un extent allocato.<br /><br /> Le pagine IAM non vengono incluse perché vengono sempre allocate dagli extent misti. Le pagine PFS vengono incluse se vengono allocate da un extent uniforme.<br /><br /> È possibile utilizzare la colonna total_pages nella [allocation_units](../../relational-databases/system-catalog-views/sys-allocation-units-transact-sql.md) vista per restituire il conteggio delle pagine riservate di ogni unità di allocazione nell'oggetto utente del catalogo. Si noti, tuttavia, che la colonna total_pages include le pagine IAM.|  
|internal_object_reserved_page_count|**bigint**|Numero totale di pagine negli extent uniformi allocate per gli oggetti interni nel file. Sono incluse nel conteggio le pagine non utilizzate da un extent allocato.<br /><br /> Le pagine IAM non vengono incluse perché vengono sempre allocate dagli extent misti. Le pagine PFS vengono incluse se vengono allocate da un extent uniforme.<br /><br /> Non esistono viste del catalogo o oggetti a gestione dinamica che restituiscono il conteggio delle pagine di ogni oggetto interno.|  
|mixed_extent_page_count|**bigint**|Numero totale di pagine allocate e non allocate negli extent misti allocati nel file. Gli extent misti contengono le pagine allocate a oggetti diversi. In questo conteggio sono incluse tutte le pagine IAM nel file.|
|modified_extent_page_count|**bigint**|**Si applica a**: da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br />Numero totale di pagine modificate allocati extent del file dall'ultimo backup completo del database. Il conteggio delle pagine modificate può essere utilizzato per tenere traccia delle quantità delle modifiche differenziali del database dall'ultimo backup completo, per decidere se è necessario un backup differenziale.|
|pdw_node_id|**int**|**Si applica a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> L'identificatore per il nodo che utilizza questo tipo di distribuzione.|  
|distribution_id|**int**|**Si applica a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Id numerico univoco associata alla distribuzione.|  
  
## <a name="remarks"></a>Osservazioni  
 I conteggi di pagine vengono sempre eseguiti a livello di extent. I relativi valori saranno pertanto sempre multipli di otto. Agli extent contenenti le pagine di allocazione GAM (Global Allocation Map, mappa di allocazione globale) e SGAM (Shared Global Allocation Map, mappa di allocazione globale condivisa) vengono allocati extent uniformi. Non vengono inclusi nei conteggi di pagine precedentemente descritti. Per ulteriori informazioni sulle pagine ed extent, vedere [pagine e Guida all'architettura di extent](../../relational-databases/pages-and-extents-architecture-guide.md). 
  
 Il contenuto dell'archivio delle versioni corrente è [tran_version_store](../../relational-databases/system-dynamic-management-views/sys-dm-tran-version-store-transact-sql.md). Viene tenuto traccia delle pagine dell'archivio delle versioni a livello di file anziché a livello di sessione o attività in quanto tali pagine sono risorse globali. Una sessione può generare versioni, ma le versioni non possono essere rimosse al termine della sessione. È necessario considerare l'operazione di pulizia dell'archivio delle versioni come la transazione con esecuzione più lunga che deve accedere alla versione precedente. La transazione in esecuzione più lunga relativa alla versione pulizia dell'archivio può essere individuata visualizzando la colonna elapsed_time_seconds in [Sys.dm tran_active_snapshot_database_transactions](../../relational-databases/system-dynamic-management-views/sys-dm-tran-active-snapshot-database-transactions-transact-sql.md).  
  
 Frequenti variazioni nella colonna mixed_extent_page_count possono indicare un frequente utilizzo di pagine SGAM. In questo caso, è possibile rilevare numerose attese PAGELATCH_UP in cui la risorsa attesa è una pagina SGAM. Per altre informazioni, vedere [os_waiting_tasks &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-waiting-tasks-transact-sql.md), [DM os_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md), e [sys.dm_os_latch_ statistiche &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-latch-stats-transact-sql.md).  
  
## <a name="user-objects"></a>Oggetti utente  
 Gli oggetti seguenti vengono inclusi nei contatori di pagine degli oggetti utente:  
  
-   Tabelle e indici definiti dall'utente  
  
-   Tabelle e indici di sistema  
  
-   Tabelle e indici temporanei globali  
  
-   Tabelle e indici temporanei locali  
  
-   Variabili di tabella  
  
-   Tabelle restituite nelle funzioni con valori di tabella  
  
## <a name="internal-objects"></a>Oggetti interni  
 Gli oggetti interni sono solo in tempdb. Gli oggetti seguenti vengono inclusi nei contatori di pagine degli oggetti interni:  
  
-   Tabelle di lavoro per le operazioni di spooling o di cursore e l'archiviazione di LOB (Large Object) temporanei.  
  
-   File di lavoro per le operazioni quali un hash join  
  
-   Operazioni di ordinamento  
  
## <a name="relationship-cardinalities"></a>Cardinalità delle relazioni  
  
|From|Per|Relazione|  
|----------|--------|------------------|  
|sys.dm_db_file_space_usage.database_id, file_id|sys.dm_io_virtual_file_stats.database_id, file_id|Uno-a-uno|  
  
## <a name="permissions"></a>Autorizzazioni

In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], richiede `VIEW SERVER STATE` autorizzazione.   
In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], richiede il `VIEW DATABASE STATE` autorizzazione per il database.   

## <a name="examples"></a>Esempi  
  
### <a name="determing-the-amount-of-free-space-in-tempdb"></a>Determinazione dello spazio libero in tempdb  
 La query seguente restituisce il numero totale di pagine libere e lo spazio libero totale in megabyte (MB) disponibile in tutti i file **tempdb**.  
  
```sql
USE tempdb;  
GO  
SELECT SUM(unallocated_extent_page_count) AS [free pages],   
(SUM(unallocated_extent_page_count)*1.0/128) AS [free space in MB]  
FROM sys.dm_db_file_space_usage;  
```  

### <a name="determining-the-amount-of-space-used-by-user-objects"></a>Rilevamento della quantità di spazio utilizzata dagli oggetti utente  
 La query seguente restituisce il numero totale di pagine e lo spazio totale utilizzati dagli oggetti utente in tempdb.  
  
```sql  
USE tempdb;  
GO  
SELECT SUM(user_object_reserved_page_count) AS [user object pages used],  
(SUM(user_object_reserved_page_count)*1.0/128) AS [user object space in MB]  
FROM sys.dm_db_file_space_usage;
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Viste a gestione dinamica relative ai database &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)   
 [sys.dm_db_task_space_usage &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-task-space-usage-transact-sql.md)   
 [sys.dm_db_session_space_usage &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-session-space-usage-transact-sql.md)  

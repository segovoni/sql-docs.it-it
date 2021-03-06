---
title: Sys. Indexes (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 04/18/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.indexes
- indexes
- sys.indexes_TSQL
- indexes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.indexes catalog view
ms.assetid: 066bd9ac-6554-4297-88fe-d740de1f94a8
caps.latest.revision: 48
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 1a83f1addba51d14ced6d38aa18b5c5f2d1d9082
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33182457"
---
# <a name="sysindexes-transact-sql"></a>sys.indexes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Contiene una riga per ogni indice o heap di un oggetto in formato tabella, come una tabella, una vista o una funzione con valori di tabella.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|ID dell'oggetto a cui appartiene l'indice.|  
|**name**|**sysname**|Nome dell'indice. **nome** è univoco solo all'interno dell'oggetto.<br /><br /> NULL = Heap|  
|**index_id**|**int**|ID dell'indice. **index_id** è univoco solo all'interno dell'oggetto.<br /><br /> 0 = heap<br /><br /> 1 = indice cluster<br /><br /> > 1 = Indice non cluster|  
|**type**|**tinyint**|Tipo di indice:<br /><br /> 0 = heap<br /><br /> 1 = Cluster<br /><br /> 2 = Non cluster<br /><br /> 3 = XML<br /><br /> 4 = Spaziale<br /><br /> 5 = indice columnstore cluster. **Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> 6 = indice columnstore non cluster. **Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> 7 = indice hash non cluster. **Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**type_desc**|**nvarchar(60)**|Descrizione del tipo di indice:<br /><br /> HEAP<br /><br /> CLUSTERED<br /><br /> NONCLUSTERED<br /><br /> XML<br /><br /> SPATIAL<br /><br /> COLUMNSTORE cluster - **si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> COLUMNSTORE non cluster - **si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> HASH non cluster: Gli indici NONCLUSTERED HASH sono supportati solo nelle tabelle con ottimizzazione per la memoria. Nella vista sys.hash_indexes vengono mostrati gli indici hash correnti e le proprietà hash. Per altre informazioni, vedere [hash_indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-hash-indexes-transact-sql.md). **Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**is_unique**|**bit**|1 = Indice univoco.<br /><br /> 0 = Indice non univoco.<br /><br /> Sempre 0 per gli indici columnstore cluster.|  
|**data_space_id**|**int**|ID dello spazio dati per l'indice. Lo spazio dati può essere un filegroup o uno schema di partizione.<br /><br /> 0 = **object_id** è una funzione con valori di tabella o un indice in memoria.|  
|**IGNORE_DUP_KEY**|**bit**|1 = IGNORE_DUP_KEY è ON.<br /><br /> 0 = IGNORE_DUP_KEY è OFF.|  
|**is_primary_key**|**bit**|1 = L'indice fa parte di un vincolo PRIMARY KEY.<br /><br /> Sempre 0 per gli indici columnstore cluster.|  
|**is_unique_constraint**|**bit**|1 = L'indice fa parte di un vincolo UNIQUE.<br /><br /> Sempre 0 per gli indici columnstore cluster.|  
|**Fill_Factor su**|**tinyint**|> 0 = Percentuale FILLFACTOR utilizzata al momento della creazione o ricostruzione dell'indice.<br /><br /> 0 = Valore predefinito<br /><br /> Sempre 0 per gli indici columnstore cluster.|  
|**is_padded**|**bit**|1 = PADINDEX è ON.<br /><br /> 0 = PADINDEX è OFF.<br /><br /> Sempre 0 per gli indici columnstore cluster.|  
|**is_disabled**|**bit**|1 = L'indice è disabilitato.<br /><br /> 0 = L'indice non è disabilitato.|  
|**is_hypothetical**|**bit**|1 = L'indice è ipotetico e non può essere utilizzato direttamente come percorso di accesso ai dati. Gli indici ipotetici contengono le statistiche a livello di colonna.<br /><br /> 0 = L'indice non è ipotetico.|  
|**allow_row_locks**|**bit**|1 = L'indice consente blocchi di riga.<br /><br /> 0 = L'indice non consente blocchi di riga.<br /><br /> Sempre 0 per gli indici columnstore cluster.|  
|**allow_page_locks**|**bit**|1 = L'indice consente blocchi di pagina.<br /><br /> 0 = L'indice non consente blocchi di pagina.<br /><br /> Sempre 0 per gli indici columnstore cluster.|  
|**has_filter**|**bit**|1 = L'indice dispone di un filtro e contiene solo righe che soddisfanno la definizione del filtro.<br /><br /> 0 = L'indice non dispone di un filtro.|  
|**filter_definition**|**nvarchar(max)**|Espressione per il subset di righe incluso nell'indice filtrato.<br /><br /> NULL per l'heap o l'indice non filtrato.|  
|**auto_created**|**bit**|1 = è stato creato l'indice per l'ottimizzazione automatica.<br /><br />0 = indice è stato creato dall'utente.
  
## <a name="permissions"></a>Autorizzazioni  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono restituiti tutti gli indici per la tabella `Production.Product` nel database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
  
SELECT i.name AS index_name  
    ,i.type_desc  
    ,is_unique  
    ,ds.type_desc AS filegroup_or_partition_scheme  
    ,ds.name AS filegroup_or_partition_scheme_name  
    ,ignore_dup_key  
    ,is_primary_key  
    ,is_unique_constraint  
    ,fill_factor  
    ,is_padded  
    ,is_disabled  
    ,allow_row_locks  
    ,allow_page_locks  
FROM sys.indexes AS i  
INNER JOIN sys.data_spaces AS ds ON i.data_space_id = ds.data_space_id  
WHERE is_hypothetical = 0 AND i.index_id <> 0   
AND i.object_id = OBJECT_ID('Production.Product');  
GO  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo dell'oggetto &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys.index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)   
 [sys.xml_indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-xml-indexes-transact-sql.md)   
 [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.key_constraints &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-key-constraints-transact-sql.md)   
 [sys.filegroups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
 [sys.partition_schemes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-partition-schemes-transact-sql.md)   
 [L'esecuzione di query il catalogo di sistema SQL Server domande frequenti](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [OLTP in memoria &#40;ottimizzazione per la memoria&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  

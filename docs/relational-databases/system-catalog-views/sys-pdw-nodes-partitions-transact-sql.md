---
title: Sys.pdw_nodes_partitions (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.service: sql-data-warehouse
ms.component: system-objects
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: b4216752-4813-4b2c-b259-7d8ffc6cc190
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 697c602b41c1225202f12cae52297009ae1e99dc
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "37993899"
---
# <a name="syspdwnodespartitions-transact-sql"></a>sys.pdw_nodes_partitions (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contiene una riga per ogni partizione di tutte le tabelle e la maggior parte dei tipi di indici in una [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] database. Tutte le tabelle e indici contengono almeno una partizione, indipendentemente dal fatto che vengono partizionate in modo esplicito o meno.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|partition_id|`bigint`|ID della partizione. Valore univoco all'interno di un database.|  
|object_id|`int`|ID dell'oggetto a cui appartiene la partizione. Ogni tabella o vista è costituita da almeno una partizione.|  
|index_id|`int`|ID dell'indice all'interno dell'oggetto a cui appartiene la partizione.|  
|partition_number|`int`|Numero di partizione in base 1 all'interno dell'indice o heap di appartenenza. Per [!INCLUDE[ssSDW](../../includes/sssdw-md.md)], il valore di questa colonna è 1.|  
|hobt_id|`bigint`|ID dell'heap di dati o dell'albero B contenente le righe per la partizione.|  
|rows|`bigint`|Numero approssimativo di righe nella partizione. |  
|data_compression|`int`|Indica lo stato di compressione per ogni partizione:<br /><br /> 0 = NONE<br /><br /> 1 = ROW<br /><br /> 2 = PAGE<br /><br /> 3 = COLUMNSTORE|  
|data_compression_desc|`nvarchar(60)`|Indica lo stato di compressione per ogni partizione. I valori possibili sono NONE, ROW e PAGE.|  
|pdw_node_id|`int`|Identificatore univoco di un [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] nodo.|  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione CONTROL SERVER.  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  

### <a name="example-a-display-rows-in-each-partition-within-each-distribution"></a>Esempio a righe di visualizzazione in ogni partizione all'interno di ogni distribuzione 

Applicabile a: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]
 
Per visualizzare il numero di righe in ogni partizione all'interno di ogni distribuzione, usare [DBCC PDW_SHOWPARTITIONSTATS (SQL Server PDW)](../../t-sql/database-console-commands/dbcc-pdw-showpartitionstats-transact-sql.md) .

### <a name="example-b-uses-system-views-to-view-rows-in-each-partition-of-each-distribution-of-a-table"></a>Esempio b: viste di sistema viene utilizzata per visualizzare le righe in ogni partizione di ogni distribuzione di una tabella

Applicabile a: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]
 
Questa query restituisce il numero di righe in ogni partizione di ogni distribuzione della tabella `myTable`.  
 
```  
SELECT o.name, pnp.index_id, pnp.partition_id, pnp.rows,   
    pnp.data_compression_desc, pnp.pdw_node_id  
FROM sys.pdw_nodes_partitions AS pnp  
JOIN sys.pdw_nodes_tables AS NTables  
    ON pnp.object_id = NTables.object_id  
AND pnp.pdw_node_id = NTables.pdw_node_id  
JOIN sys.pdw_table_mappings AS TMap  
    ON NTables.name = TMap.physical_name 
    AND substring(TMap.physical_name,40, 10) = pnp.distribution_id 
JOIN sys.objects AS o  
    ON TMap.object_id = o.object_id  
WHERE o.name = 'myTable'  
ORDER BY o.name, pnp.index_id, pnp.partition_id;  
```    
  
## <a name="see-also"></a>Vedere anche  
 [SQL Data Warehouse e Parallel Data Warehouse viste del catalogo](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  


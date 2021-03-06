---
title: sys.pdw_nodes_tables (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-objects
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 473b5d14-171b-4a16-9195-acf36d3f786c
caps.latest.revision: 8
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 263e2edb61529a197815f95cc595dcb9b5949877
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38032116"
---
# <a name="syspdwnodestables-transact-sql"></a>sys.pdw_nodes_tables (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contiene una riga per ogni oggetto tabella che è proprietario di un'entità o in cui l'entità dispone dell'autorizzazione alcuni.  
  
|Nome colonna|Tipo di dati|Description|Intervallo|  
|-----------------|---------------|-----------------|-----------|  
|\<colonne ereditate >||Per un elenco delle colonne ereditate da questa vista, vedere [Sys. Objects](http://msdn.microsoft.com/en-us/c36fa71e-549a-4533-a6cd-1314d26f533f).||  
|lob_data_space_id|**int**||Sempre 0.|  
|filestream_data_space_id|**int**|ID dello spazio dati per un filegroup FILESTREAM o [!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|NULL|  
|max_column_id_used|**int**|ID di colonna massimo utilizzato dalla tabella.||  
|lock_on_bulk_load|**bit**|La tabella è bloccata durante il caricamento bulk.|TBD|  
|uses_ansi_nulls|**bit**|La tabella è stata creata con l'opzione di database SET ANSI_NULLS impostata su ON.|1|  
|is_replicated|**bit**|1 = tabella viene pubblicata tramite la replica.|0. replica non è supportata.|  
|has_replication_filter|**bit**|1 = La tabella è associata a un filtro di replica.|0|  
|is_merge_published|**bit**|1 = La tabella è stata pubblicata tramite una replica di tipo merge.|0. non è supportato.|  
|is_sync_tran_subscribed|**bit**|1 = La tabella è stata sottoscritta tramite una sottoscrizione ad aggiornamento immediato.|0. non è supportato.|  
|has_unchecked_assembly_data|**bit**|1 = La tabella contiene dati persistenti che dipendono da un assembly la cui definizione è stata modificata durante l'ultima esecuzione di ALTER ASSEMBLY. Verrà reimpostato su 0 dopo la successiva esecuzione di DBCC CHECKDB o DBCC CHECKTABLE con esito positivo.|0. Nessun supporto CLR.|  
|text_in_row_limit|**int**|0 = L'opzione Text in row non è impostata.|Sempre 0.|  
|large_value_types_out_of_row|**bit**|1 = I tipi per valori di grandi dimensioni vengono archiviati esternamente alla riga.|Sempre 0.|  
|is_tracked_by_cdc|**bit**|1 = tabella è abilitata per change data capture|Sempre 0; Nessun supporto di CDC.|  
|lock_escalation|**tinyint**|Il valore dell'opzione LOCK_ESCALATION per la tabella: 2 = AUTO|Sempre 2.|  
|lock_escalation_desc|**nvarchar(60)**|Una descrizione di testo dell'opzione lock_escalation.|Sempre ꞌAUTOꞌ.|  
|pdw_node_id|**int**|Identificatore univoco di un [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] nodo.|NOT NULL|  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Data Warehouse e Parallel Data Warehouse viste del catalogo](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  

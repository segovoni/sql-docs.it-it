---
title: Sys. sysindexes (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-compatibility-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sysindexes
- sysindexes_TSQL
- sys.sysindexes
- sys.sysindexes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysindexes system table
- sys.sysindexes compatibility view
ms.assetid: f483d89c-35c4-4a08-8f8b-737fd80d13f5
caps.latest.revision: 57
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 276d2bfd5374fc24b31648250b5ffcd1eefb1ac7
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33222002"
---
# <a name="syssysindexes-transact-sql"></a>sys.sysindexes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Include una riga per ogni indice e tabella del database corrente. Gli indici XML non sono supportati in questa vista. Tabelle e indici partizionati non sono completamente supportati in questa visualizzazione. Utilizzare il [Sys. Indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md) vista del catalogo.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**id**|**int**|ID della tabella alla quale appartiene l'indice.|  
|**status**|**int**|Informazioni sullo stato del sistema.<br /><br /> [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**first**|**binary(6)**|Puntatore alla prima pagina o alla pagina radice.<br /><br /> Non utilizzato quando **indid** = 0.<br /><br /> NULL = indice viene partizionato quando **indid** > 1.<br /><br /> NULL = la tabella viene partizionata quando **indid** è 0 o 1.|  
|**indid**|**smallint**|ID dell'indice:<br /><br /> 0 = heap<br /><br /> 1 = indice cluster<br /><br /> >1 = Indice non cluster|  
|**radice**|**binary(6)**|Per **indid** > = 1, **radice** è il puntatore alla pagina radice.<br /><br /> Non utilizzato quando **indid** = 0.<br /><br /> NULL = indice viene partizionato quando **indid** > 1.<br /><br /> NULL = la tabella viene partizionata quando **indid** è 0 o 1.|  
|**minlen**|**smallint**|Dimensioni minime di una riga.|  
|**keycnt**|**smallint**|Numero di chiavi.|  
|**GroupID**|**smallint**|ID del filegroup in cui l'oggetto è stato creato.<br /><br /> NULL = indice viene partizionato quando **indid** > 1.<br /><br /> NULL = la tabella viene partizionata quando **indid** è 0 o 1.|  
|**Dpages**|**int**|Per **indid** = 0 o **indid** = 1, **dpages** corrisponde al conteggio delle pagine di dati utilizzato.<br /><br /> Per **indid** > 1, **dpages** corrisponde al conteggio delle pagine di indice utilizzate.<br /><br /> 0 = l'indice viene partizionato quando **indid** > 1.<br /><br /> 0 = la tabella viene partizionata quando **indid** è 0 o 1.<br /><br /> Non restituisce risultati precisi se si verifica un overflow della riga.|  
|**reserved**|**int**|Per **indid** = 0 o **indid** = 1, **riservato** corrisponde al conteggio delle pagine allocate per tutti gli indici e i dati della tabella.<br /><br /> Per **indid** > 1, **riservato** corrisponde al conteggio delle pagine allocate per l'indice.<br /><br /> 0 = l'indice viene partizionato quando **indid** > 1.<br /><br /> 0 = la tabella viene partizionata quando **indid** è 0 o 1.<br /><br /> Non restituisce risultati precisi se si verifica un overflow della riga.|  
|**used**|**int**|Per **indid** = 0 o **indid** = 1, **utilizzato** corrisponde al conteggio totale delle pagine utilizzate per tutti i dati di indici e tabelle.<br /><br /> Per **indid** > 1, **utilizzato** corrisponde al conteggio delle pagine utilizzate per l'indice.<br /><br /> 0 = l'indice viene partizionato quando **indid** > 1.<br /><br /> 0 = la tabella viene partizionata quando **indid** è 0 o 1.<br /><br /> Non restituisce risultati precisi se si verifica un overflow della riga.|  
|**rowcnt**|**bigint**|Conteggio delle righe al livello dati basato su **indid** = 0 e **indid** = 1.<br /><br /> 0 = l'indice viene partizionato quando **indid** > 1.<br /><br /> 0 = la tabella viene partizionata quando **indid** è 0 o 1.|  
|**rowmodctr**|**int**|Conta il numero totale di righe inserite, eliminate o aggiornate a partire dall'ultimo aggiornamento delle statistiche per la tabella.<br /><br /> 0 = l'indice viene partizionato quando **indid** > 1.<br /><br /> 0 = la tabella viene partizionata quando **indid** è 0 o 1.<br /><br /> In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive, **rowmodctr** non è completamente compatibile con le versioni precedenti. Per altre informazioni, vedere la sezione Osservazioni.|  
|**reserved3**|**int**|Viene restituito 0.<br /><br /> [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**reserved4**|**int**|Viene restituito 0.<br /><br /> [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**xmaxlen**|**smallint**|Dimensioni massime di una riga.|  
|**maxirow**|**smallint**|Dimensioni massime di una riga di indice non foglia.<br /><br /> In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive, **maxirow** non è completamente compatibile con le versioni precedenti.|  
|**OrigFillFactor**|**tinyint**|Valore del fattore di riempimento originale utilizzato durante la creazione dell'indice. Questo valore non viene mantenuto. Può tuttavia risultare utile se è necessario ricreare un indice e non si ricorda il fattore di riempimento utilizzato.|  
|**StatVersion**|**tinyint**|Viene restituito 0.<br /><br /> [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**reserved2**|**int**|Viene restituito 0.<br /><br /> [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**FirstIAM**|**binary(6)**|NULL = l'indice viene partizionato.<br /><br /> [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**impid**|**smallint**|Flag di implementazione dell'indice.<br /><br /> Viene restituito 0.<br /><br /> [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**LockFlags**|**smallint**|Utilizzata per vincolare le granularità dei blocchi considerati per un indice. Per ridurre al minimo il costo di blocco, è possibile ad esempio impostare una tabella di ricerca essenzialmente di sola lettura per l'esecuzione del blocco solo a livello di tabella.|  
|**pgmodctr**|**int**|Viene restituito 0.<br /><br /> [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**Chiavi**|**varbinary(816)**|Elenco degli ID delle colonne che costituiscono la chiave dell'indice.<br /><br /> Restituisce NULL.<br /><br /> Per visualizzare le colonne chiave di indice, utilizzare [sysindexkeys](../../relational-databases/system-compatibility-views/sys-sysindexkeys-transact-sql.md).|  
|**name**|**sysname**|Nome dell'indice o della statistica. Restituisce NULL quando **indid** = 0. Modificare l'applicazione in uso in modo da eseguire la ricerca di un nome di heap NULL.|  
|**statblob**|**image**|BLOB (Binary Large Object) per statistiche.<br /><br /> Restituisce NULL.|  
|**maxlen**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**rows**|**int**|Conteggio delle righe al livello dati basato su **indid** = 0 e **indid** = 1, e il valore viene ripetuto per **indid** > 1.|  
  
## <a name="remarks"></a>Osservazioni  
 Le colonne definite come riservate non devono essere utilizzate.  
  
 Le colonne **dpages**, **riservato**, e **utilizzato** non restituirà risultati accurati se la tabella o l'indice contiene dati nell'unità di allocazione ROW_OVERFLOW. I conteggi delle pagine per ogni indice vengono inoltre rilevati separatamente e per la tabella di base non vengono aggregati. Per visualizzare i conteggi delle pagine, utilizzare il [allocation_units](../../relational-databases/system-catalog-views/sys-allocation-units-transact-sql.md) o [Sys. Partitions](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md) viste del catalogo, o [Sys.dm db_partition_stats](../../relational-databases/system-dynamic-management-views/sys-dm-db-partition-stats-transact-sql.md) vista a gestione dinamica.  
  
 In SQL Server 2000 e versioni precedenti, il [!INCLUDE[ssDE](../../includes/ssde-md.md)] gestisce contatori delle modifiche a livello di riga. Questi contatori vengono ora gestiti a livello di colonna. Pertanto, il **rowmodctr** colonna viene calcolata e produce i risultati sono simili ai risultati nelle versioni precedenti, ma non esattamente.  
  
 Se si utilizza il valore in **rowmodctr** per determinare quando aggiornare le statistiche, provare le soluzioni seguenti:  
  
-   Non eseguire alcuna operazione. Il nuovo **rowmodctr** valore spesso consentirà di stabilire quando aggiornare le statistiche, poiché il comportamento non è sufficientemente vicino i risultati delle versioni precedenti.  
  
-   Utilizzare AUTO_UPDATE_STATISTICS. Per ulteriori informazioni, vedere [statistiche](../../relational-databases/statistics/statistics.md).  
  
-   Determinare il momento dell'aggiornamento delle statistiche in base a un intervallo di tempo. Ad esempio, ogni ora, ogni giorno o ogni settimana.  
  
-   Determinare il momento dell'aggiornamento delle statistiche utilizzando informazioni a livello di applicazione. Ad esempio, ogni volta che il valore massimo di un **identità** modifiche apportate da più di 10.000, colonna o viene eseguita ogni volta che un inserimento bulk.  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Mapping di tabelle di sistema a viste di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)  
  
  

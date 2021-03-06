---
title: Sys. resource_stats (Database SQL di Azure) | Microsoft Docs
ms.custom: ''
ms.date: 04/06/2018
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.component: system-catalog-views
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- resource_stats
- sys.resource_stats
- sys.resource_stats_TSQL
- resource_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.resource_stats
- resource_stats
ms.assetid: 02379a1b-3622-4578-8c59-a1b8f1a17914
caps.latest.revision: 28
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: c2f8a0e0cebcf64bedac33861184e806f322d7d1
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38038850"
---
# <a name="sysresourcestats-azure-sql-database"></a>sys.resource_stats (Database SQL di Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Restituisce i dati di archiviazione e di utilizzo della CPU per un database SQL di Azure. I dati vengono raccolti e aggregati in intervalli di cinque minuti. Per ciascun database utente, è disponibile una riga per ogni finestra di segnalazione di cinque minuti in cui è presente una modifica nell'utilizzo della risorsa. I dati restituiti includono utilizzo della CPU, modifica delle dimensioni di archiviazione o database Modifica della SKU. I database inattivi senza modifiche potrebbero non avere righe per ogni intervallo di cinque minuti. I dati cronologici vengono mantenuti per circa 14 giorni.  
  
 Il **Sys. resource_stats** visualizzazione contiene diverse definizioni a seconda della versione del Server di Database SQL Azure che è associato il database. Prendere in considerazione queste differenze e le eventuali modifiche richieste dall'applicazione durante l'aggiornamento a una nuova versione del server.  
  
 La tabella seguente descrive le colonne disponibili in un server v12:  
  
|Colonne|Tipo di dati|Description|  
|----------------------------|---------------|-----------------|  
|start_time|**datetime**|Ora UTC che indica l'inizio dell'intervallo di reporting di 5 minuti.|  
|end_time|**datetime**|Ora UTC che indica la fine dell'intervallo di reporting di 5 minuti.|  
|database_name|**varchar**|Nome del database utente.|  
|sku|**varchar**|Livello di servizio del database. Di seguito sono indicati i valori possibili:<br /><br /> Standard<br /><br /> Standard<br /><br /> Premium<br /><br />Utilizzo generico<br /><br />Business Critical|  
|storage_in_megabytes|**float**|Dimensioni massime in megabyte per il periodo di tempo, tra cui i dati del database, indici, stored procedure e metadati di archiviazione.|  
|avg_cpu_percent|**numeric**|Percentuale dell'utilizzo medio del calcolo del limite del livello del servizio.|  
|avg_data_io_percent|**numeric**|Percentuale dell'utilizzo medio di I/O in base al limite del livello del servizio.|  
|avg_log_write_percent|**numeric**|Percentuale dell'utilizzo medio delle risorse di scrittura del limite del livello del servizio.|  
|max_worker_percent|**decimal(5,2)**|Massimi ruoli di lavoro simultanei (richieste) espresso in percentuale sulla base del limite del livello di servizio del database.<br /><br /> Valore massimo attualmente non viene calcolato per l'intervallo di cinque minuti sulla base dei campioni di 15 secondi di conteggi di lavoro simultanei.|  
|max_session_percent|**decimal(5,2)**|Numero massimo di sessioni simultaneo espresso in percentuale sulla base del limite del livello di servizio del database.<br /><br /> Valore massimo attualmente non viene calcolato per l'intervallo di cinque minuti sulla base dei campioni di 15 secondi di conteggi di sessioni simultanee.|  
|dtu_limit|**int**|Database max DTU impostazione corrente per il database durante questo intervallo. |  
  
> [!TIP]  
>  Per altre informazioni su questi limiti e i livelli di servizio, vedere gli argomenti [livelli di servizio](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/).  
    
## <a name="permissions"></a>Autorizzazioni  
 Questa vista è disponibile per tutti i ruoli utente con autorizzazioni sufficienti per connettersi a virtual **master** database.  
  
## <a name="remarks"></a>Note  
 I dati restituiti da **Sys. resource_stats** viene espresso come percentuale dei limiti massimi consentiti per il livello di prestazioni/livello di servizio in esecuzione.  
  
 Quando un database è un membro di un pool elastico, le statistiche di resource presentate come valori percentuali, sono espresse come percentuale del limite massimo per database impostato nella configurazione del pool elastico.  
  
 Per una vista più granulare di questi dati, usare **DM db_resource_stats** vista a gestione dinamica in un database utente. In questa vista acquisisce i dati ogni 15 secondi e conserva i dati cronologici per 1 ora.  Per altre informazioni, vedere [DM db_resource_stats &#40;Database SQL di Azure&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-resource-stats-azure-sql-database.md).  

## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono restituiti tutti i database che hanno una media di almeno l'80% di utilizzo del calcolo nell'ultima settimana.  
  
```sql  
DECLARE @s datetime;  
DECLARE @e datetime;  
SET @s= DateAdd(d,-7,GetUTCDate());  
SET @e= GETUTCDATE();  
SELECT database_name, AVG(avg_cpu_percent) AS Average_Compute_Utilization   
FROM sys.resource_stats   
WHERE start_time BETWEEN @s AND @e  
GROUP BY database_name  
HAVING AVG(avg_cpu_percent) >= 80  
```  
    
## <a name="see-also"></a>Vedere anche  
 [Livelli di servizio](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/)   
 [Limiti e le funzionalità del livello servizio](https://azure.microsoft.com/documentation/articles/sql-database-performance-guidance/)  
  
  

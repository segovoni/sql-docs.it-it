---
title: managed_backup.fn_get_health_status (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- fn_get_health_status_TSQL
- smart_admin.fn_get_health_status_TSQL
- smart_admin.fn_get_health_status
- fn_get_health_status
dev_langs:
- TSQL
helpviewer_keywords:
- smart_admin.fn_get_health_status
- fn_get_health_status
ms.assetid: b376711d-444a-4b5e-b483-8df323b4e31f
caps.latest.revision: 12
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 0fa9a510f2be08329173898b7e0e6794458ea8fe
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38041969"
---
# <a name="managedbackupfngethealthstatus-transact-sql"></a>managed_backup.fn_get_health_status (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Restituisce una tabella con 0, una o più righe del conteggio aggregato degli errori restituiti dagli eventi estesi per un periodo specificato.  
  
 La funzione viene utilizzata per indicare lo stato di integrità dei servizi di Smart Admin.  Il [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] è attualmente supportato in Smart Admin. Pertanto gli errori restituiti sono correlati al [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].  
  
 
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```sql  
managed_backup.fn_get_health_status([@begin_time = ] 'time_1' , [ @end_time = ] 'time_2')  
```  
  
##  <a name="Arguments"></a> Argomenti  
 [@begin_time]  
 L'inizio del periodo di tempo a partire dal quale viene eseguito il conteggio aggregato degli errori.  Il @begin_time parametro è DATETIME. Il valore predefinito è NULL. Quando il valore è NULL, la funzione elabora gli eventi restituiti fino a 30 minuti prima dell'ora corrente.  
  
 [ @end_time]  
 La fine del periodo di tempo nel quale viene eseguito il conteggio aggregato degli errori. Il @end_time parametro è DateTime e il valore predefinito NULL. Quando il valore è NULL, la funzione elabora gli eventi estesi fino all'ora corrente.  
  
## <a name="table-returned"></a>Tabella restituita  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|number_of_storage_connectivity_errors|INT|Numero di errori di connessione quando il programma si connette all'account di archiviazione di Windows Azure.|  
|number_of_sql_errors|INT|Numero di errori restituiti mentre il programma si connette al motore di SQL Server.|  
|number_of_invalid_credential_errors|INT|Numero di errori restituiti mentre il programma tenta di eseguire l'autenticazione utilizzando le credenziali SQL.|  
|number_of_other_errors|INT|Numero di errori di altre categorie oltre la connettività, SQL o le credenziali.|  
|number_of_corrupted_or_deleted_backups|INT|Numero di file di backup danneggiati o eliminati.|  
|number_of_backup_loops|INT|Il numero di analisi eseguite dall'agente di backup su tutti i database configurati con il [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].|  
|number_of_retention_loops|INT|Numero di analisi eseguite sui database per valutare il periodo di memorizzazione impostato.|  
  
## <a name="best-practices"></a>Procedure consigliate  
 Questi conteggi aggregati possono essere utilizzati per monitorare l'integrità del sistema. Ad esempio, se la colonna number_ of_retention_loops è 0 in 30 minuti, è possibile che la gestione della memorizzazione richieda del tempo o che addirittura non funzioni correttamente. Le colonne di errori diverse da zero possono indicare problemi e, per individuarli, è necessario verificare i registri eventi estesi. In alternativa, usare la stored procedure **managed_backup.sp_get_backup_diagnostics** per ottenere un elenco degli eventi estesi per trovare i dettagli dell'errore.  
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>Autorizzazioni  
 È necessario **seleziona** autorizzazioni nella funzione.  
  
## <a name="examples"></a>Esempi  
  
-   Nel seguente esempio vengono restituiti i conteggi aggregati degli errori per gli ultimi 30 minuti a partire dal momento in cui è iniziata l'esecuzione.  
  
    ```  
    SELECT *  
    FROM managed_backup.fn_get_health_status(NULL, NULL)  
  
    ```  
  
-   Nell'esempio seguente vengono restituiti i conteggi aggregati degli errori per la settimana corrente:  
  
    ```  
    Use msdb  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
    SELECT *  
    FROM managed_backup.fn_get_health_status(@startofweek, @endofweek)  
  
    ```  
  
  

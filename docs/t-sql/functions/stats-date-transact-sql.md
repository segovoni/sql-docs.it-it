---
title: STATS_DATE (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STATS_DATE_TSQL
- STATS_DATE
dev_langs:
- TSQL
helpviewer_keywords:
- statistical information [SQL Server], last time updated
- STATS_DATE function
- query optimization statistics [SQL Server], last time updated
- last time statistics updated
ms.assetid: f9ec3101-1e41-489d-b519-496a0d6089fb
caps.latest.revision: 43
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 44fc7524040db874abc5d596b641cba985dcf893
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="statsdate-transact-sql"></a>STATS_DATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce la data dell'aggiornamento più recente delle statistiche per una tabella o vista indicizzata.  
  
 Per ulteriori informazioni sull'aggiornamento delle statistiche, vedere [statistiche](../../relational-databases/statistics/statistics.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
STATS_DATE ( object_id , stats_id )  
```  
  
## <a name="arguments"></a>Argomenti  
 *object_id*  
 ID della tabella o della vista indicizzata contenente le statistiche.  
  
 *stats_id*  
 ID dell'oggetto statistiche.  
  
## <a name="return-types"></a>Tipi restituiti  
 Restituisce **datetime** in caso di esito positivo. Restituisce **NULL** in caso di errore.  
  
## <a name="remarks"></a>Osservazioni  
 È possibile utilizzare funzioni di sistema nell'elenco di selezione, nella clausola WHERE e in tutti i casi in cui è consentita un'espressione.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza al ruolo predefinito del database db_owner o l'autorizzazione per la visualizzazione dei metadati per la tabella o la vista indicizzata.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-return-the-dates-of-the-most-recent-statistics-for-a-table"></a>A. Recupero delle date delle statistiche più recenti per una tabella  
 L'esempio seguente restituisce la data dell'aggiornamento più recente di ogni oggetto statistiche nella tabella `Person.Address`.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT name AS stats_name,   
    STATS_DATE(object_id, stats_id) AS statistics_update_date  
FROM sys.stats   
WHERE object_id = OBJECT_ID('Person.Address');  
GO  
```  
  
 Se le statistiche corrispondono a un indice, il *stats_id* valore nel [Sys. Stats](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md) vista del catalogo è identico il *index_id* valore il [Sys. Indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md) vista del catalogo e la query seguente restituisce gli stessi risultati della query precedente. Se le statistiche non corrispondono a un indice, vengono restituite nei risultati di sys.stats ma non in quelli di sys.indexes.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT name AS index_name,   
    STATS_DATE(object_id, index_id) AS statistics_update_date  
FROM sys.indexes   
WHERE object_id = OBJECT_ID('Person.Address');  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="b-learn-when-a-named-statistics-was-last-updated"></a>B. Informazioni statistiche denominata dell'ultimo aggiornamento  
 Nell'esempio seguente crea statistiche per la colonna LastName della tabella DimCustomer. Viene quindi eseguita una query per visualizzare la data delle statistiche. È possibile aggiornamenti delle statistiche e viene eseguito di nuovo la query per visualizzare la data di aggiornamento.  
  
```  
  
--First, create a statistics object  
USE AdventureWorksPDW2012;  
GO  
CREATE STATISTICS Customer_LastName_Stats  
ON AdventureWorksPDW2012.dbo.DimCustomer (LastName)  
WITH SAMPLE 50 PERCENT;  
GO  
  
--Return the date when Customer_LastName_Stats was last updated  
USE AdventureWorksPDW2012;  
GO  
SELECT stats_id, name AS stats_name,   
    STATS_DATE(object_id, stats_id) AS statistics_date  
FROM sys.stats s  
WHERE s.object_id = OBJECT_ID('dbo.DimCustomer')  
    AND s.name = 'Customer_LastName_Stats';  
GO  
  
--Update Customer_LastName_Stats so it will have a different timestamp in the next query  
GO  
UPDATE STATISTICS dbo.dimCustomer (Customer_LastName_Stats);  
  
--Return the date when Customer_LastName_Stats was last updated.  
SELECT stats_id, name AS stats_name,   
    STATS_DATE(object_id, stats_id) AS statistics_date  
FROM sys.stats s  
WHERE s.object_id = OBJECT_ID('dbo.DimCustomer')  
    AND s.name = 'Customer_LastName_Stats';  
GO  
  
```  
  
### <a name="c-view-the-date-of-the-last-update-for-all-statistics-on-a-table"></a>C. Visualizza la data dell'ultimo aggiornamento per tutte le statistiche in una tabella  
 In questo esempio restituisce la data di quando ogni oggetto statistiche per la tabella DimCustomer dell'ultimo aggiornamento.  
  
```  
--Return the dates all statistics on the table were last updated.  
SELECT stats_id, name AS stats_name,   
    STATS_DATE(object_id, stats_id) AS statistics_date  
FROM sys.stats s  
WHERE s.object_id = OBJECT_ID('dbo.DimCustomer');  
GO  
```  
  
 Se le statistiche corrispondono a un indice, il *stats_id* valore nel [Sys. Stats](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md) vista del catalogo è identico il *index_id* valore il [Sys. Indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md) vista del catalogo e la query seguente restituisce gli stessi risultati della query precedente. Se le statistiche non corrispondono a un indice, vengono restituite nei risultati di sys.stats ma non in quelli di sys.indexes.  
  
```  
USE AdventureWorksPDW2012;  
GO  
SELECT name AS index_name,   
    STATS_DATE(object_id, index_id) AS statistics_update_date  
FROM sys.indexes   
WHERE object_id = OBJECT_ID('dbo.DimCustomer');  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)   
 [UPDATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/update-statistics-transact-sql.md)   
 [sp_autostats &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-autostats-transact-sql.md)   
 [Statistiche](../../relational-databases/statistics/statistics.md)  
  
  


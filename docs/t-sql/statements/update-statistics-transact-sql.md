---
title: UPDATE STATISTICS (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/04/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: t-sql|statements
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- UPDATE STATISTICS
- UPDATE_STATISTICS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- updating statistics
- query optimization statistics [SQL Server], updating
- UPDATE STATISTICS statement
- statistical information [SQL Server], updating
ms.assetid: 919158f2-38d0-4f68-82ab-e1633bd0d308
caps.latest.revision: 74
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: d662031dec5912311d252b3c5a44e2abc5059eba
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33074158"
---
# <a name="update-statistics-transact-sql"></a>UPDATE STATISTICS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Aggiorna le statistiche di ottimizzazione query in una tabella o una vista indicizzata. Per impostazione predefinita, Query Optimizer aggiorna già le statistiche come necessario per migliorare il piano di query. In alcuni casi è possibile migliorare le prestazioni di esecuzione delle query tramite UPDATE STATISTICS o la stored procedure [sp_updatestats](../../relational-databases/system-stored-procedures/sp-updatestats-transact-sql.md) per aggiornare le statistiche più di frequente rispetto agli aggiornamenti predefiniti.  
  
 Sebbene consenta di garantire che le query vengano compilate con statistiche aggiornate, l'aggiornamento delle statistiche causa la ricompilazione delle query. Si consiglia di non aggiornare le statistiche troppo frequentemente perché è necessario mantenere un equilibrio a livello di prestazioni tra la necessità di migliorare i piani di query e il tempo necessario per la ricompilazione delle query. Tale equilibrio dipende dall'applicazione in uso. Per le operazioni UPDATE STATISTICS è possibile usare tempdb per ordinare l'esempio di righe per la compilazione di statistiche.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
UPDATE STATISTICS table_or_indexed_view_name   
    [   
        {   
            { index_or_statistics__name }  
          | ( { index_or_statistics_name } [ ,...n ] )   
                }  
    ]   
    [    WITH   
        [  
            FULLSCAN   
              [ [ , ] PERSIST_SAMPLE_PERCENT = { ON | OFF } ]    
            | SAMPLE number { PERCENT | ROWS }   
              [ [ , ] PERSIST_SAMPLE_PERCENT = { ON | OFF } ]    
            | RESAMPLE   
              [ ON PARTITIONS ( { <partition_number> | <range> } [, …n] ) ]  
            | <update_stats_stream_option> [ ,...n ]  
        ]   
        [ [ , ] [ ALL | COLUMNS | INDEX ]   
        [ [ , ] NORECOMPUTE ]   
        [ [ , ] INCREMENTAL = { ON | OFF } ] 
        [ [ , ] MAXDOP = max_degree_of_parallelism ] 
    ] ;  
  
<update_stats_stream_option> ::=  
    [ STATS_STREAM = stats_stream ]  
    [ ROWCOUNT = numeric_constant ]  
    [ PAGECOUNT = numeric_contant ]  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
UPDATE STATISTICS schema_name . ] table_name   
    [ ( { statistics_name | index_name } ) ]  
    [ WITH   
       {  
              FULLSCAN   
            | SAMPLE number PERCENT   
            | RESAMPLE   
        }  
    ]  
[;]  
```  
  
## <a name="arguments"></a>Argomenti  
 *table_or_indexed_view_name*  
 Nome della tabella o della vista indicizzata che contiene l'oggetto statistico.  
  
 *index_or_statistics_name*  
 Nome dell'indice per cui aggiornare le statistiche o nome delle statistiche da aggiornare. Se *index_or_statistics_name* non viene specificato, Query Optimizer aggiorna tutte le statistiche per la tabella o la vista indicizzata. Sono incluse le statistiche create tramite l'istruzione CREATE STATISTICS, le statistiche di colonna singola create quando l'opzione AUTO_CREATE_STATISTICS è ON e quelle create per gli indici.  
  
 Per altre informazioni su AUTO_CREATE_STATISTICS, vedere [Opzioni ALTER DATABASE SET &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md). Per visualizzare tutti gli indici per una tabella o una vista, è possibile usare [sp_helpindex](../../relational-databases/system-stored-procedures/sp-helpindex-transact-sql.md).  
  
 FULLSCAN  
 Consente di calcolare le statistiche analizzando tutte le righe nella tabella o nella vista indicizzata. FULLSCAN e SAMPLE 100 PERCENT generano gli stessi risultati. Non è possibile utilizzare FULLSCAN con l'opzione SAMPLE.  
  
 SAMPLE *number* { PERCENT | ROWS }  
 Percentuale approssimativa o numero di righe presenti nella tabella o nella vista indicizzata utilizzate da Query Optimizer durante l'aggiornamento delle statistiche. Per PERCENT, *number* può essere compreso tra 0 e 100, mentre per ROWS *number* può essere compreso tra 0 e il numero totale di righe. La percentuale effettiva o il numero di righe campionate da Query Optimizer potrebbero non corrispondere alla percentuale o al numero specificato. Query Optimizer analizza ad esempio tutte le righe in una pagina di dati.  
  
 SAMPLE è utile per i casi speciali in cui il piano di query, basato sul campionamento predefinito, non è ottimale. Nella maggior parte delle situazioni, non è necessario specificare SAMPLE perché Query Optimizer utilizza il campionamento e determina le dimensioni del campione statisticamente significative per impostazione predefinita, come richiesto per creare piani di query di alta qualità. 
 
A partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], il campionamento dei dati per la generazione di statistiche avviene in parallelo, usando il livello di compatibilità 130, per migliorare le prestazioni della raccolta delle statistiche. Query optimizer userà le statistiche di esempio parallele, ogni volta che una dimensione di tabella supera una determinata soglia. 
   
 Questa opzione non può essere utilizzata quando viene specificata l'opzione FULLSCAN. Se non si specifica né SAMPLE né FULLSCAN, Query Optimizer utilizza i dati campionati e calcola le dimensioni del campione per impostazione predefinita.  
  
 Si sconsiglia di specificare 0 PERCENT o 0 ROWS. Se si specifica 0 PERCENT o ROWS, l'oggetto statistiche viene aggiornato ma non conterrà i dati delle statistiche.  
  
 Per la maggior parte dei carichi di lavoro, non è necessaria un'analisi completa e il campionamento predefinito è adeguato.  
Tuttavia, alcuni carichi di lavoro sensibili a distribuzioni dei dati con ampie variazioni potrebbero richiedere una dimensione maggiore di esempio, o anche un'analisi completa.  
Per altre informazioni, vedere il [blog di CSS SQL Escalation Services](http://blogs.msdn.com/b/psssql/archive/2010/07/09/sampling-can-produce-less-accurate-statistics-if-the-data-is-not-evenly-distributed.aspx).  
  
 RESAMPLE  
 Aggiorna ogni statistica utilizzando la frequenza di campionamento più recente.  
  
 L'utilizzo di RESAMPLE può comportare un'analisi di tabella completa. Per le statistiche per gli indici viene ad esempio utilizzata un'analisi di tabella completa per la frequenza di campionamento. Se non si specifica nessuna delle opzioni di campionamento, ovvero SAMPLE, FULLSCAN o RESAMPLE, Query Optimizer campiona i dati e calcola le dimensioni del campione per impostazione predefinita.  

PERSIST_SAMPLE_PERCENT = { ON | OFF }  
Se **ON**, le statistiche mantengono la percentuale di campionamento impostata per gli aggiornamenti successivi che non specificano in modo esplicito una percentuale di campionamento. Se **OFF**, la percentuale di campionamento delle statistiche viene reimpostata sul campionamento predefinito per gli aggiornamenti successivi che non la specificano in modo esplicito. Il valore predefinito è **OFF**. 
 
 > [!NOTE]
 > Se viene eseguita AUTO_UPDATE_STATISTICS, usa la percentuale di campionamento persistente, qualora disponibile, o la percentuale di campionamento predefinito se non disponibile.
 > Il comportamento di RESAMPLE non è interessato da questa opzione.
 
 > [!TIP] 
 > [DBCC SHOW_STATISTICS](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md) e [sys.dm_db_stats_properties](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-properties-transact-sql.md) espongono il valore di percentuale di campionamento persistente per la statistica selezionata.
 
 **Si applica a**: da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] (a partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 CU4) fino a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] (a partire da [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU1).  
 
 ON PARTITIONS ( { \<partition_number> | \<range> } [, …n] ) ] Forza la rielaborazione delle statistiche a livello foglia che coprono le partizioni specificate nella clausola ON PARTITIONS e successivamente ne determina il merge per compilare le statistiche globali. L'opzione WITH RESAMPLE è necessaria in quanto non è possibile eseguire il merge di statistiche di partizioni compilate con frequenze di campionamento differenti.  
  
**Si applica a**: da [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 ALL | COLUMNS | INDEX  
 Aggiornare tutte le statistiche esistenti, le statistiche create in una o più colonne o le statistiche create per gli indici. Se non si specifica nessuna delle opzioni, l'istruzione UPDATE STATISTICS aggiorna tutte le statistiche sulla tabella o sulla vista indicizzata.  
  
 NORECOMPUTE  
 Disabilitare l'opzione di aggiornamento automatico delle statistiche AUTO_UPDATE_STATISTICS per le statistiche specificate. Se viene specificata questa opzione, Query Optimizer completa l'aggiornamento di queste statistiche e disabilita gli aggiornamenti futuri.  
  
 Per riabilitare il comportamento dell'opzione AUTO_UPDATE_STATISTICS, rieseguire UPDATE STATISTICS senza l'opzione NORECOMPUTE oppure eseguire **sp_autostats**.  
  
> [!WARNING]  
> L'utilizzo di questa opzione può produrre piani di query non ottimali. È consigliabile limitare l'utilizzo di questa opzione e riservarne l'applicazione a un amministratore del sistema qualificato.  
  
 Per altre informazioni sull'opzione AUTO_STATISTICS_UPDATE, vedere [Opzioni ALTER DATABASE SET &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md).  
  
 INCREMENTAL = { ON | OFF }  
 Quando è impostata su **ON**, le statistiche vengono ricreate come statistiche per partizione. Quando è impostata su **OFF**, l'albero delle statistiche viene eliminato e le statistiche vengono rielaborate da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il valore predefinito è **OFF**.  
  
 Se le statistiche per partizione non sono supportate, viene generato un errore. Le statistiche incrementali non sono supportate per i seguenti tipi di statistiche:  
  
-   Statistiche create con indici che non hanno il partizionamento allineato con la tabella di base.  
-   Statistiche create per i database secondari leggibili Always On.  
-   Statistiche create per i database di sola lettura.  
-   Statistiche create per gli indici filtrati.  
-   Statistiche create per le viste.  
-   Statistiche create per le tabelle interne.  
-   Statistiche create con indici spaziali o indici XML.  
  
**Si applica a**: da [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]

MAXDOP = *max_degree_of_parallelism*  
**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (a partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 e [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3).  
  
 Esegue l'override dell'opzione di configurazione **max_degree_of_parallelism** per la durata dell'operazione statistica. Per altre informazioni, vedere [Configurare l'opzione di configurazione del server max degree of parallelism](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md). Utilizzare MAXDOP per limitare il numero di processori utilizzati durante l'esecuzione di un piano parallelo. Il valore massimo è 64 processori.  
  
 *max_degree_of_parallelism* può essere:  
  
 1  
 Disattiva la generazione di piani paralleli.  
  
 \>1  
 Consente di limitare al valore specificato, o a un valore più basso in base al carico di lavoro corrente del sistema, il numero massimo di processori usati in un'operazione parallela statistica.  
  
 0 (predefinito)  
 Utilizza il numero effettivo di processori o un numero inferiore in base al carico di lavoro corrente del sistema.  
  
 \<update_stats_stream_option> [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  

## <a name="remarks"></a>Remarks  
  
## <a name="when-to-use-update-statistics"></a>Utilizzo di UPDATE STATISTICS  
 Per altre informazioni sulle situazioni in cui usare UPDATE STATISTICS, vedere [Statistiche](../../relational-databases/statistics/statistics.md).  

## <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni  
* L'aggiornamento delle statistiche non è supportato per le tabelle esterne. Per aggiornare le statistiche in una tabella esterna, eliminare e ricreare le statistiche.  
* L'opzione MAXDOP non è compatibile con le opzioni STATS_STREAM, ROWCOUNT e PAGECOUNT.

## <a name="updating-all-statistics-with-spupdatestats"></a>Aggiornamento di tutte le statistiche con sp_updatestats  
 Per informazioni sull'aggiornamento delle statistiche per tutte le tabelle interne e definite dall'utente nel database, vedere la stored procedure [sp_updatestats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-updatestats-transact-sql.md). Il comando riportato di seguito chiama ad esempio sp_updatestats per aggiornare tutte le statistiche per il database.  
  
```sql  
EXEC sp_updatestats;  
```  
  
## <a name="determining-the-last-statistics-update"></a>Determinazione dell'ultimo aggiornamento delle statistiche  
 Per determinare la data dell'ultimo aggiornamento delle statistiche, usare la funzione [STATS_DATE](../../t-sql/functions/stats-date-transact-sql.md) .  
  
## <a name="pdw--sql-data-warehouse"></a>PDW / SQL Data Warehouse  
 La sintassi seguente non è supportata da PDW / SQL Data Warehouse  
  
```sql  
update statistics t1 (a,b);   
```  
  
```sql  
update statistics t1 (a) with sample 10 rows;  
```  
  
```sql  
update statistics t1 (a) with NORECOMPUTE;  
```  
  
```sql  
update statistics t1 (a) with INCREMENTAL=ON;  
```  
  
```sql  
update statistics t1 (a) with stats_stream = 0x01;  
```  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione ALTER per la tabella o la vista.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-update-all-statistics-on-a-table"></a>A. Aggiornamento di tutte le statistiche di una tabella  
 In questo esempio vengono aggiornate le statistiche per tutti gli indici della tabella `SalesOrderDetail`.  
  
```sql  
USE AdventureWorks2012;  
GO  
UPDATE STATISTICS Sales.SalesOrderDetail;  
GO  
```  
  
### <a name="b-update-the-statistics-for-an-index"></a>B. Aggiornamento delle statistiche per un indice  
 In questo esempio vengono aggiornate le statistiche relative all'indice `AK_SalesOrderDetail_rowguid` della tabella `SalesOrderDetail`.  
  
```sql  
USE AdventureWorks2012;  
GO  
UPDATE STATISTICS Sales.SalesOrderDetail AK_SalesOrderDetail_rowguid;  
GO  
```  
  
### <a name="c-update-statistics-by-using-50-percent-sampling"></a>C. Aggiornamento delle statistiche tramite un campionamento al 50 percento  
 Nell'esempio seguente vengono create e quindi aggiornate le statistiche per le colonne `Name` e `ProductNumber` della tabella `Product`.  
  
```sql  
USE AdventureWorks2012;  
GO  
CREATE STATISTICS Products  
    ON Production.Product ([Name], ProductNumber)  
    WITH SAMPLE 50 PERCENT  
-- Time passes. The UPDATE STATISTICS statement is then executed.  
UPDATE STATISTICS Production.Product(Products)   
    WITH SAMPLE 50 PERCENT;  
```  
  
### <a name="d-update-statistics-by-using-fullscan-and-norecompute"></a>D. Aggiornamento delle statistiche tramite le opzioni FULLSCAN e NORECOMPUTE  
 Nell'esempio seguente vengono aggiornate le statistiche `Products` della tabella `Product`, viene eseguita un'analisi completa di tutte le righe della tabella `Product`, quindi viene disattivato l'aggiornamento automatico delle statistiche di `Products`.  
  
```sql  
USE AdventureWorks2012;  
GO  
UPDATE STATISTICS Production.Product(Products)  
    WITH FULLSCAN, NORECOMPUTE;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="e-update-statistics-on-a-table"></a>E. Aggiornamento delle statistiche di una tabella  
 In questo esempio vengono aggiornate le statistiche `CustomerStats1` della tabella `Customer`.  
  
```sql  
UPDATE STATISTICS Customer ( CustomerStats1 );  
```  
  
### <a name="f-update-statistics-by-using-a-full-scan"></a>F. Aggiornare statistiche tramite un'analisi completa  
 L'esempio seguente aggiorna le statistiche `CustomerStats1` in base all'analisi di tutte le righe della tabella `Customer`.  
  
```sql  
UPDATE STATISTICS Customer (CustomerStats1) WITH FULLSCAN;  
```  
  
### <a name="g-update-all-statistics-on-a-table"></a>G. Aggiornamento di tutte le statistiche di una tabella  
 In questo esempio vengono aggiornate tutte le statistiche della tabella `Customer`.  
  
```sql  
UPDATE STATISTICS Customer;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Statistiche](../../relational-databases/statistics/statistics.md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [CREATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/create-statistics-transact-sql.md)   
 [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)   
 [DROP STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/drop-statistics-transact-sql.md)   
 [sp_autostats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-autostats-transact-sql.md)   
 [sp_updatestats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-updatestats-transact-sql.md)   
 [STATS_DATE &#40;Transact-SQL&#41;](../../t-sql/functions/stats-date-transact-sql.md)  
 [sys.dm_db_stats_properties &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-properties-transact-sql.md) [sys.dm_db_stats_histogram &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-histogram-transact-sql.md) 
  




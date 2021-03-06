---
title: TRUNCATE TABLE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- TRUNCATE
- TRUNCATE TABLE
- TRUNCATE_TSQL
- TRUNCATE_TABLE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- row removal [SQL Server], TRUNCATE TABLE statement
- table truncating [SQL Server]
- removing rows
- TRUNCATE TABLE statement
- deleting rows
- dropping rows
ms.assetid: 3d544eed-3993-4055-983d-ea334f8c5c58
caps.latest.revision: 41
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: df0f8d8aaf0302d6d854a5fa1a5b0c1eee9e9aef
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/04/2018
ms.locfileid: "37790892"
---
# <a name="truncate-table-transact-sql"></a>TRUNCATE TABLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Rimuove tutte le righe da una tabella o da partizioni specificate di una tabella senza registrare le eliminazioni delle singole righe. TRUNCATE TABLE è simile all'istruzione DELETE senza clausola WHERE. L'istruzione TRUNCATE TABLE è tuttavia più rapida e utilizza un numero minore di risorse di sistema e del log delle transazioni.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
TRUNCATE TABLE   
    [ { database_name .[ schema_name ] . | schema_name . } ]  
    table_name  
    [ WITH ( PARTITIONS ( { <partition_number_expression> | <range> }   
    [ , ...n ] ) ) ]  
[ ; ]  
  
<range> ::=  
<partition_number_expression> TO <partition_number_expression>  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
TRUNCATE TABLE [ { database_name . [ schema_name ] . | schema_name . ] table_name  
[;]  
```  
  
## <a name="arguments"></a>Argomenti  
 *database_name*  
 Nome del database.  
  
 *schema_name*  
 Nome dello schema a cui appartiene la tabella.  
  
 *table_name*  
 Nome della tabella da troncare o dalla quale vengono rimosse tutte le righe. *table_name* deve essere un valore letterale. *table_name* non può essere la funzione **OBJECT_ID()** o una variabile.  
  
 WITH ( PARTITIONS ( { \<*partition_number_expression*> | \<*range*> } [ , ...n ] ) )  
**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] alla [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658))
  
 Specifica le partizioni da troncare o da cui vengono rimosse tutte le righe. Se la tabella non è partizionata, l'argomento **WITH PARTITIONS** genera un errore. Se la clausola **WITH PARTITIONS** non viene specificata, viene troncata l'intera tabella.  
  
 *\<partition_number_expression>* può essere specificato nei modi seguenti: 
  
-   Specificare il numero di una partizione, ad esempio: `WITH (PARTITIONS (2))`  
  
-   Specificare i numeri di partizione per più partizioni singole separati da virgole, ad esempio: `WITH (PARTITIONS (1, 5))`  
  
-   Specificare sia intervalli sia singole partizioni, ad esempio: `WITH (PARTITIONS (2, 4, 6 TO 8))`  
  
-   *\<range>* può essere specificato sotto forma di numeri di partizione separati dalla parola **TO**, ad esempio: `WITH (PARTITIONS (6 TO 8))`  
  
 Per troncare una tabella partizionata, la tabella e gli indici devono essere allineati (partizionati nella stessa funzione di partizione).  
  
## <a name="remarks"></a>Remarks  
 Rispetto all'istruzione DELETE, TRUNCATE TABLE presenta i vantaggi seguenti:  
  
-   Richiede una minore quantità di spazio del log delle transazioni.  
  
     L'istruzione DELETE rimuove una riga alla volta e registra una voce nel log delle transazioni per ogni riga eliminata. L'istruzione TRUNCATE TABLE rimuove i dati tramite la deallocazione delle pagine di dati utilizzate per archiviare i dati della tabella. Solo le deallocazioni di pagina vengono registrate nel log delle transazioni.  
  
-   In genere utilizza meno blocchi.  
  
     Quando l'istruzione DELETE viene eseguita tramite un blocco di riga, ogni riga nella tabella viene bloccata per l'eliminazione. TRUNCATE TABLE blocca sempre la tabella e la pagina, incluso un blocco dello schema (SCH-M), ma non ogni riga.  
  
-   Senza eccezione, le pagine di zeri vengono mantenute nella tabella.  
  
     Dopo l'esecuzione di una istruzione DELETE, la tabella può ancora contenere pagine vuote. Ad esempio, le pagine vuote in un heap non possono essere deallocate senza almeno un blocco di tabella esclusivo (LCK_M_X). Se l'operazione di eliminazione non utilizza un blocco di tabella, la tabella (heap) conterrà molte pagine vuote. Per gli indici, l'operazione di eliminazione può tralasciare le pagine vuote, anche se queste pagine verranno deallocate velocemente da un processo di pulizia eseguito in background.  
  
 TRUNCATE TABLE rimuove tutte le righe da una tabella, ma non rimuove la struttura della tabella e le relative colonne, i vincoli, gli indici e così via. Per rimuovere la definizione della tabella in aggiunta ai relativi dati, utilizzare l'istruzione DROP TABLE.  
  
 Se la tabella include una colonna Identity, il contattore per quella colonna viene reimpostato sul valore di inizializzazione definito per la colonna. Se non è stato definito alcun valore di inizializzazione, viene utilizzato il valore predefinito 1. Per mantenere il contatore della tabella Identity, utilizzare l'istruzione DELETE.  
  
## <a name="restrictions"></a>Restrictions  
 Non è possibile utilizzare TRUNCATE TABLE sulle tabelle:  
  
-   a cui fa riferimento un vincolo FOREIGN KEY È possibile troncare una tabella con una chiave esterna che fa riferimento alla tabella stessa.  
  
-   che partecipano in una vista indicizzata  
  
-   che sono pubblicate tramite una replica transazionale o una replica di tipo merge.  
  
 Per le tabelle con una o più di queste caratteristiche, utilizzare l'istruzione DELETE come alternativa.  
  
 TRUNCATE TABLE non può attivare un trigger perché l'operazione non registra le eliminazioni delle singole righe. Per altre informazioni, vedere [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md). 
 
 In [!INCLUDE[sssdwfull](../../includes/sssdwfull-md.md)] e [!INCLUDE[sspdw](../../includes/sspdw-md.md)]:

- TRUNCATE TABLE non è consentita all'interno dell'istruzione EXPLAIN.

- TRUNCATE TABLE non può essere eseguita all'interno di una transazione.
  
## <a name="truncating-large-tables"></a>Troncamento delle tabelle di grandi dimensioni  
 In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è possibile eliminare o troncare le tabelle che includono più di 128 extent senza mantenere attivi blocchi simultanei in tutti gli extent necessari per l'eliminazione.  
  
## <a name="permissions"></a>Autorizzazioni  
 L'autorizzazione minima necessaria è ALTER su *table_name*. Le autorizzazioni per l'istruzione TRUNCATE TABLE vengono assegnate per impostazione predefinita ai membri del ruolo predefinito del server sysadmin, dei ruoli predefiniti del database db_owner e db_ddladmin e al proprietario della tabella e non sono trasferibili. È tuttavia possibile incorporare l'istruzione TRUNCATE TABLE all'interno di un modulo, ad esempio una stored procedure, e concedere le autorizzazioni necessarie al modulo tramite la clausola EXECUTE AS.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-truncate-a-table"></a>A. Troncare una tabella  
 Nell'esempio seguente vengono rimossi tutti i dati dalla tabella `JobCandidate`. Le istruzioni `SELECT` vengono inserite prima e dopo l'istruzione `TRUNCATE TABLE` per confrontare i risultati.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT COUNT(*) AS BeforeTruncateCount   
FROM HumanResources.JobCandidate;  
GO  
TRUNCATE TABLE HumanResources.JobCandidate;  
GO  
SELECT COUNT(*) AS AfterTruncateCount   
FROM HumanResources.JobCandidate;  
GO  
```  
  
### <a name="b-truncate-table-partitions"></a>B. Troncare le partizioni di una tabella  
  
**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] alla [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658))
  
 L'esempio seguente tronca le partizioni specificate di una tabella partizionata. La sintassi `WITH (PARTITIONS (2, 4, 6 TO 8))` consente di troncare i numeri di partizione 2, 4, 6, 7 e 8.  
  
```sql  
TRUNCATE TABLE PartitionTable1   
WITH (PARTITIONS (2, 4, 6 TO 8));  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)   
 [DROP TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-table-transact-sql.md)   
 [IDENTITY &#40;proprietà&#41; &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql-identity-property.md)  
  
  


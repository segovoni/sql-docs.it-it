---
title: INSERT (grafo SQL) | Microsoft Docs
description: Sintassi INSERT per le tabelle nodi e bordi di un grafo SQL.
ms.date: 05/12/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.custom: ''
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- INSERT statement [SQL Server], SQL graph
- SQL graph, INSERT statement
ms.assetid: ''
caps.latest.revision: 1
author: shkale-msft
ms.author: shkale
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2017 || = sqlallproducts-allversions
ms.openlocfilehash: 65f064f7893f9dde1f42d94daee1ec6207a0a868
ms.sourcegitcommit: a6596c62f607041c4402f7d5b41a232fca257c14
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36254553"
---
# <a name="insert-sql-graph"></a>INSERT (grafo SQL)
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

  Consente di aggiungere una o più righe a una tabella `node` o `edge` in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. 

> [!NOTE]   
>  Per istruzioni Transact-SQL standard, vedere [INSERT TABLE (Transact-SQL)](../../t-sql/statements/insert-transact-sql.md).
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="insert-into-node-table-syntax"></a>INSERT nella sintassi della tabella nodi 
La sintassi per l'inserimento in una tabella nodi è uguale a quella di una normale tabella. 

```  
[ WITH <common_table_expression> [ ,...n ] ]  
INSERT   
{  
        [ TOP ( expression ) [ PERCENT ] ]   
        [ INTO ]   
        { <object> | rowset_function_limited   
          [ WITH ( <Table_Hint_Limited> [ ...n ] ) ]  
        }  
    {  
        [ (column_list) ] | [(<edge_table_column_list>)]  
        [ <OUTPUT Clause> ]  
        { VALUES ( { DEFAULT | NULL | expression } [ ,...n ] ) [ ,...n     ]   
        | derived_table   
        | execute_statement  
        | <dml_table_source>  
        | DEFAULT VALUES   
        }  
    }  
}  
[;]  
  
<object> ::=  
{   
    [ server_name . database_name . schema_name .   
      | database_name .[ schema_name ] .   
      | schema_name .   
    ]  
    node_table_name  | edge_table_name
}  
  
<dml_table_source> ::=  
    SELECT <select_list>  
    FROM ( <dml_statement_with_output_clause> )   
      [AS] table_alias [ ( column_alias [ ,...n ] ) ]  
    [ WHERE <on_or_where_search_condition> ]  
        [ OPTION ( <query_hint> [ ,...n ] ) ]  

<on_or_where_search_condition> ::=
    {  <search_condition_with_match> | <search_condition> }

<search_condition_with_match> ::=
    { <graph_predicate> | [ NOT ] <predicate> | ( <search_condition> ) }
    [ AND { <graph_predicate> | [ NOT ] <predicate> | ( <search_condition> ) } ]
    [ ,...n ]

<search_condition> ::=
    { [ NOT ] <predicate> | ( <search_condition> ) }
    [ { AND | OR } [ NOT ] { <predicate> | ( <search_condition> ) } ]
    [ ,...n ]

<graph_predicate> ::=
    MATCH( <graph_search_pattern> [ AND <graph_search_pattern> ] [ , ...n] )

<graph_search_pattern>::=
    <node_alias> { { <-( <edge_alias> )- | -( <edge_alias> )-> } <node_alias> }

<edge_table_column_list> ::=
    ($from_id, $to_id, [column_list])

```  
  
 
## <a name="arguments"></a>Argomenti  
 Questo documento descrive gli argomenti relativi al grafo SQL. Per un elenco completo e una descrizione di argomenti supportati nell'istruzione INSERT, vedere [INSERT TABLE (Transact-SQL)](../../t-sql/statements/insert-transact-sql.md)

 INTO  
 Parola chiave facoltativa che può essere specificata tra `INSERT` e la tabella di destinazione.  
  
 *search_condition_with_match*   
 La clausola `MATCH` può essere usata in una sottoquery durante l'inserimento in una tabella nodi o bordi. Per la sintassi dell'istruzione `MATCH`, vedere [ GRAPH MATCH (Transact-SQL)](../../t-sql/queries/match-sql-graph.md)

 *graph_search_pattern*   
 Criterio di ricerca specificato per la clausola `MATCH` come parte del predicato del grafo.

 *edge_table_column_list*   
 Gli utenti devono specificare valori per `$from_id` e `$to_id` durante l'inserimento in un bordo. Se in queste colonne non viene specificato alcun valore o se vengono inseriti valori Null, viene restituito un errore. 
  

## <a name="remarks"></a>Remarks  
L'inserimento in un nodo corrisponde all'inserimento in qualsiasi tabella relazionale. I valori per la colonna $node_id vengono generati automaticamente.

Quando eseguono l'inserimento in una tabella bordi, gli utenti devono specificare valori per le colonne `$from_id` e `$to_id`.   

L'inserimento bulk per la tabella nodi rimane identico a quello di una tabella relazionale.

Prima dell'inserimento bulk in una tabella bordi, è necessario importare le tabelle nodi. I valori di `$from_id` e `$to_id` possono essere estratti dalla colonna `$node_id` della tabella nodi ed essere inseriti come bordi. 

  
### <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione INSERT per la tabella di destinazione.  
  
 Le autorizzazioni INSERT vengono assegnate per impostazione predefinita ai membri del ruolo predefinito del server **sysadmin** e ai membri dei ruoli predefiniti del database **db_owner** e **db_datawriter** nonché al proprietario della tabella. I membri dei ruoli **sysadmin**, **db_owner** e **db_securityadmin** e il proprietario della tabella possono trasferire le autorizzazioni ad altri utenti.  
  
 Per eseguire INSERT con l'opzione BULK della funzione OPENROWSET, è necessario essere un membro del ruolo predefinito del server **sysadmin** o **bulkadmin**.  
  

## <a name="examples"></a>Esempi  
  
#### <a name="a--insert-into-node-table"></a>A.  INSERT nella tabella nodi  
 Nell'esempio seguente viene creata una tabella nodi di persone in cui vengono inserite 2 righe.

 ```
 -- Create person node table
 CREATE TABLE dbo.Person (ID integer PRIMARY KEY, name varchar(50)) AS NODE;
 
 -- Insert records for Alice and John
 INSERT INTO dbo.Person VALUES (1, 'Alice');
 INSERT INTO dbo.Person VALUES (2,'John');
 ```
  
#### <a name="b--insert-into-edge-table"></a>B.  INSERT nella tabella bordi  
 Nell'esempio seguente viene creata una tabella bordi di amici in cui viene inserito un bordo.

 ```
 -- Create friend edge table
 CREATE TABLE dbo.friend (start_date DATE) AS EDGE;

 -- Create a friend edge, that connect Alice and John
 INSERT INTO dbo.friend VALUES ((SELECT $node_id FROM dbo.Person WHERE name = 'Alice'),
        (SELECT $node_id FROM dbo.Person WHERE name = 'John'), '9/15/2011');
 ```

  
## <a name="see-also"></a>Vedere anche  
 [INSERT TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)   
 [Graph Processing with SQL Server 2017](../../relational-databases/graphs/sql-graph-overview.md) (Elaborazione di grafi con SQL Server 2017)  



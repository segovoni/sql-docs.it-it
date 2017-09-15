---
title: COL_NAME (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- COL_NAME
- COL_NAME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- column properties [SQL Server]
- COL_NAME function
- column names [SQL Server]
- names [SQL Server], columns
ms.assetid: 214144ab-f2bc-4052-83cf-caf0a85c4cc6
caps.latest.revision: 28
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3028e409a8218b35bbf7cd4773e80ca27e8db8be
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="colname-transact-sql"></a>COL_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Restituisce il nome di una colonna corrispondente al numero di identificazione di tabella e al numero di identificazione di colonna specificati.
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
COL_NAME ( table_id , column_id )  
```  
  
## <a name="arguments"></a>Argomenti  
*table_id*  
Numero di identificazione della tabella contenente la colonna. *table_id* è di tipo **int**.
  
*column_id*  
Numero di identificazione della colonna. *column_id* parametro è di tipo **int**.
  
## <a name="return-types"></a>Tipi restituiti
**sysname**
  
## <a name="exceptions"></a>Eccezioni  
Restituisce NULL in caso di errore o se un chiamante non dispone dell'autorizzazione necessaria per visualizzare l'oggetto.
  
Un utente può visualizzare esclusivamente i metadati delle entità a sicurezza diretta di cui è proprietario o per cui ha ricevuto un'autorizzazione. Di conseguenza, le funzioni predefinite di creazione dei metadati come COL_NAME possono restituire NULL se l'utente non dispone di alcuna autorizzazione per l'oggetto. Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).
  
## <a name="remarks"></a>Osservazioni  
Il *table_id* e *column_id* insieme i parametri, generano una stringa del nome di colonna.
  
Per ulteriori informazioni su come ottenere i numeri di identificazione di tabelle e colonne, vedere [OBJECT_ID &#40; Transact-SQL &#41; ](../../t-sql/functions/object-id-transact-sql.md).
  
## <a name="examples"></a>Esempi  
Nell'esempio seguente viene restituito il nome della prima colonna della tabella `Employee` nel database `AdventureWorks2012`.
  
```sql
USE AdventureWorks2012;  
GO  
SET NOCOUNT OFF;  
GO  
SELECT COL_NAME(OBJECT_ID('HumanResources.Employee'), 1) AS 'Column Name';  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
`Column Name`
  
-----------------\-
  
`BusinessEntityID`
  
## <a name="examples"></a>Esempi

[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  

L'esempio seguente restituisce il nome della prima colonna in un campione `Employee` tabella.
  
```sql
-- Uses AdventureWorks  
  
SELECT COL_NAME(OBJECT_ID('dbo.FactResellerSales'), 1) AS FirstColumnName,  
COL_NAME(OBJECT_ID('dbo.FactResellerSales'), 2) AS SecondColumnName;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
ColumnName          
------------   
BusinessEntityID  
```  
  
## <a name="see-also"></a>Vedere anche
[Espressioni &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
[Funzioni per i metadati &#40; Transact-SQL &#41;](../../t-sql/functions/metadata-functions-transact-sql.md)  
[COLUMNPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/columnproperty-transact-sql.md)  
[COL_LENGTH &#40; Transact-SQL &#41;](../../t-sql/functions/col-length-transact-sql.md)
  
  


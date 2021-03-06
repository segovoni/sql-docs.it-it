---
title: WHILE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- WHILE_TSQL
- WHILE
dev_langs:
- TSQL
helpviewer_keywords:
- statements [SQL Server], repeated executions
- statement blocks [SQL Server]
- repeated statement executions
- nested WHILE loops
- WHILE keyword
ms.assetid: 52dd29ab-25d7-4fd3-a960-ac55c30c9ea9
caps.latest.revision: 40
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 5baed3f0a7ac80f948b511732662c4e7f59c0a25
ms.sourcegitcommit: a6596c62f607041c4402f7d5b41a232fca257c14
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36249303"
---
# <a name="while-transact-sql"></a>WHILE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Imposta una condizione per l'esecuzione ripetuta di un'istruzione o di un blocco di istruzioni di SQL. Le istruzioni vengono eseguite ripetutamente per tutto il tempo in cui la condizione specificata risulta vera. È possibile controllare l'esecuzione di istruzioni nel ciclo WHILE dall'interno del ciclo tramite le parole chiave BREAK e CONTINUE.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
WHILE Boolean_expression   
     { sql_statement | statement_block | BREAK | CONTINUE }  
  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
WHILE Boolean_expression   
     { sql_statement | statement_block | BREAK }  
  
```  
  
## <a name="arguments"></a>Argomenti  
 *Boolean_expression*  
 [Espressione](../../t-sql/language-elements/expressions-transact-sql.md) che restituisce **TRUE** o **FALSE**. Se l'espressione booleana include un'istruzione SELECT, tale istruzione deve essere racchiusa tra parentesi.  
  
 {*sql_statement* | *statement_block*}  
 Qualsiasi istruzione o serie di istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] valide definite con un blocco di istruzioni. Per definire un blocco di istruzioni, utilizzare le parole chiave per il controllo di flusso BEGIN ed END.  
  
 BREAK  
 Consente di uscire dal ciclo WHILE più interno. Vengono eseguite le istruzioni che si trovano dopo la parola chiave END, che segna la fine del ciclo.  
  
 CONTINUE  
 Consente il riavvio del ciclo WHILE, ignorando tutte le istruzioni che seguono la parola chiave CONTINUE.  
  
## <a name="remarks"></a>Remarks  
 Se due o più cicli WHILE sono nidificati, un'istruzione BREAK nel ciclo più interno passa al ciclo più esterno successivo. Vengono eseguite tutte le istruzioni successive al ciclo più interno, quindi viene riavviato il ciclo successivo più esterno.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-break-and-continue-with-nested-ifelse-and-while"></a>A. Utilizzo di BREAK e CONTINUE con cicli IF...ELSE e WHILE nidificati  
 Nell'esempio seguente, se il prezzo medio di listino di un prodotto è minore di `$300`, il ciclo `WHILE` raddoppia i prezzi e quindi seleziona il prezzo massimo. Se il prezzo massimo è minore o uguale a `$500`, il ciclo `WHILE` viene riavviato e il prezzo viene nuovamente raddoppiato. Questo ciclo continua a raddoppiare i prezzi fino a quando il prezzo massimo non supera `$500`, quindi il ciclo `WHILE` viene terminato e viene stampato un messaggio.  
  
```  
USE AdventureWorks2012;  
GO  
WHILE (SELECT AVG(ListPrice) FROM Production.Product) < $300  
BEGIN  
   UPDATE Production.Product  
      SET ListPrice = ListPrice * 2  
   SELECT MAX(ListPrice) FROM Production.Product  
   IF (SELECT MAX(ListPrice) FROM Production.Product) > $500  
      BREAK  
   ELSE  
      CONTINUE  
END  
PRINT 'Too much for the market to bear';  
```  
  
### <a name="b-using-while-in-a-cursor"></a>B. Utilizzo di WHILE in un cursore  
 Nell'esempio seguente viene utilizzata la funzione `@@FETCH_STATUS` per controllare le attività del cursore in un ciclo `WHILE`.  
  
```  
DECLARE Employee_Cursor CURSOR FOR  
SELECT EmployeeID, Title   
FROM AdventureWorks2012.HumanResources.Employee  
WHERE JobTitle = 'Marketing Specialist';  
OPEN Employee_Cursor;  
FETCH NEXT FROM Employee_Cursor;  
WHILE @@FETCH_STATUS = 0  
   BEGIN  
      FETCH NEXT FROM Employee_Cursor;  
   END;  
CLOSE Employee_Cursor;  
DEALLOCATE Employee_Cursor;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-simple-while-loop"></a>C. Ciclo WHILE semplice  
 Nell'esempio seguente, se il prezzo medio di listino di un prodotto è minore di `$300`, il ciclo `WHILE` raddoppia i prezzi e quindi seleziona il prezzo massimo. Se il prezzo massimo è minore o uguale a `$500`, il ciclo `WHILE` viene riavviato e il prezzo viene nuovamente raddoppiato. Questo ciclo continua a raddoppiare i prezzi fino a quando il prezzo massimo non supera `$500`, quindi si esce dal ciclo `WHILE`.  
  
```  
-- Uses AdventureWorks  
  
WHILE ( SELECT AVG(ListPrice) FROM dbo.DimProduct) < $300  
BEGIN  
    UPDATE dbo.DimProduct  
        SET ListPrice = ListPrice * 2;  
    SELECT MAX ( ListPrice) FROM dbo.DimProduct  
    IF ( SELECT MAX (ListPrice) FROM dbo.DimProduct) > $500  
        BREAK;  
END  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/alter-trigger-transact-sql.md)   
 [Elementi del linguaggio per il controllo di flusso &#40;Transact-SQL&#41;](~/t-sql/language-elements/control-of-flow.md)   
 [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)   
 [Cursori &#40;Transact-SQL&#41;](../../t-sql/language-elements/cursors-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)  
  
  



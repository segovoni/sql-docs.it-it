---
title: SE... ELSE (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/11/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- IF_TSQL
- IF
dev_langs:
- TSQL
helpviewer_keywords:
- IF...ELSE keyword
- ELSE (IF...ELSE) keyword
- ELSE keyword
- IF keyword
ms.assetid: 676c881f-dee1-417a-bc51-55da62398e81
caps.latest.revision: 49
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5ea7d020bc637ff2dda4ba0540de8385e99170cd
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="ifelse-transact-sql"></a>IF...ELSE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Impone le condizioni per l'esecuzione di un'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)]. L'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] che segue una parola chiave IF e le relative condizioni viene eseguita se le condizioni vengono soddisfatte, ovvero quando l'espressione booleana restituisce TRUE. La parola chiave facoltativa ELSE introduce un'altra istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] eseguita quando non viene soddisfatta la condizione IF, ovvero quando l'espressione booleana restituisce FALSE.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
IF Boolean_expression   
     { sql_statement | statement_block }   
[ ELSE   
     { sql_statement | statement_block } ]   
```  
  
## <a name="arguments"></a>Argomenti  
 *Espressione Boolean_expression*  
 Espressione che restituisce TRUE o FALSE. Se l'espressione booleana include un'istruzione SELECT, tale istruzione deve essere racchiusa tra parentesi.  
  
 { *sql_statement*| *statement_block* }  
 Qualsiasi istruzione o gruppo di istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] valido definito tramite un blocco di istruzioni. Le condizioni IF o ELSE possono influire sulle prestazioni di una sola istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)], a meno che non venga utilizzato un blocco di istruzioni.  
  
 Per definire un blocco di istruzioni, utilizzare le parole chiave per il controllo di flusso BEGIN ed END.  
  
## <a name="remarks"></a>Osservazioni  
 È possibile utilizzare un costrutto IF...ELSE in batch, stored procedure e query ad hoc. In caso di utilizzo in una stored procedure, questo costrutto viene in genere utilizzato per verificare l'esistenza di parametri.  
  
 È possibile nidificare condizioni IF dopo un'altra condizione IF o una parola chiave ELSE. Il limite del numero di livelli di nidificazione dipende dalla memoria disponibile.  
  
## <a name="example"></a>Esempio  
  
```  
IF DATENAME(weekday, GETDATE()) IN (N'Saturday', N'Sunday')
       SELECT 'Weekend';
ELSE 
       SELECT 'Weekday';
```  
  
 Per ulteriori esempi, vedere [ELSE &#40; se... ELSE &#41; &#40; Transact-SQL &#41; ](../../t-sql/language-elements/else-if-else-transact-sql.md).  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 L'esempio seguente usa `IF…ELSE` per determinare quale delle due risposte per indicare all'utente, in base al peso di un elemento di `DimProduct` tabella.  
  
```  
-- Uses AdventureWorksDW  
  
DECLARE @maxWeight float, @productKey integer  
SET @maxWeight = 100.00  
SET @productKey = 424  
IF @maxWeight <= (SELECT Weight from DimProduct 
                  WHERE ProductKey = @productKey)   
    (SELECT @productKey AS ProductKey, EnglishDescription, Weight, 
    'This product is too heavy to ship and is only available for pickup.' 
        AS ShippingStatus
    FROM DimProduct WHERE ProductKey = @productKey);  
ELSE  
    (SELECT @productKey AS ProductKey, EnglishDescription, Weight, 
    'This product is available for shipping or pickup.' 
        AS ShippingStatus
    FROM DimProduct WHERE ProductKey = @productKey);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [BEGIN... FINE &#40; Transact-SQL &#41;](../../t-sql/language-elements/begin-end-transact-sql.md)   
 [FINE &#40; BEGIN... FINE &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/end-begin-end-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [MENTRE &#40; Transact-SQL &#41;](../../t-sql/language-elements/while-transact-sql.md)   
 [CASE &#40; Transact-SQL &#41;](../../t-sql/language-elements/case-transact-sql.md)   
 [Il controllo di flusso Language &#40; Transact-SQL &#41; ](~/t-sql/language-elements/control-of-flow.md) [ELSE &#40; se... ELSE &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/else-if-else-transact-sql.md) 
  
  




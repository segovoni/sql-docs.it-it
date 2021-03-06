---
title: LEFT (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- LEFT
- LEFT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- character strings [SQL Server], LEFT
- characters [SQL Server], leftmost
- LEFT function
- leftmost character of expression
ms.assetid: 44a8c71b-63d8-458b-8b5d-99d570067c3c
caps.latest.revision: 48
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: a83289d8b97992ad27f31db130926e46e4871588
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/04/2018
ms.locfileid: "37791122"
---
# <a name="left-transact-sql"></a>LEFT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce la parte iniziale di una stringa di caratteri, di lunghezza pari al numero di caratteri specificato.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
LEFT ( character_expression , integer_expression )  
```  
  
## <a name="arguments"></a>Argomenti  
 *character_expression*  
 [Espressione](../../t-sql/language-elements/expressions-transact-sql.md) di dati di tipo carattere o binario. *character_expression* può essere una costante, una variabile o una colonna. *character_expression* può essere di qualsiasi tipo di dati, eccetto **text** o **ntext**, implicitamente convertibile in **varchar** o **nvarchar**. In alternativa usare la funzione [CAST](../../t-sql/functions/cast-and-convert-transact-sql.md) per convertire in modo esplicito *character_expression*.  
  
 *integer_expression*  
 Valore Integer positivo che specifica quanti caratteri di *character_expression* verranno restituiti. Se l'argomento *integer_expression* è negativo, viene restituito un errore. Se *integer_expression* è di tipo **bigint** e contiene un valore elevato, *character_expression* deve essere di un tipo di dati di grandi dimensioni, ad esempio **varchar(max)**.  
  
 Il parametro *integer_expression* considera un carattere surrogato UTF-16 come un solo carattere.  
  
## <a name="return-types"></a>Tipi restituiti  
 Restituisce **varchar** quando *character_expression* è un tipo di dati carattere non Unicode.  
  
 Restituisce **nvarchar** quando *character_expression* è un tipo di dati carattere Unicode.  
  
## <a name="remarks"></a>Remarks  
 Quando si usano le regole di confronto SC, il parametro *integer_expression* considera una coppia di surrogati UTF-16 come un solo carattere. Per altre informazioni, vedere [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md).  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-left-with-a-column"></a>A. Utilizzo di LEFT con una colonna  
 Nell'esempio seguente vengono restituiti i primi cinque caratteri di ciascun nome di prodotto nella tabella `Product` del database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
SELECT LEFT(Name, 5)   
FROM Production.Product  
ORDER BY ProductID;  
GO  
```  
  
### <a name="b-using-left-with-a-character-string"></a>B. Utilizzo di LEFT con una stringa di caratteri  
 Nell'esempio seguente viene utilizzata la funzione `LEFT` per ottenere i primi due caratteri della stringa di caratteri `abcdefg`.  
  
```  
SELECT LEFT('abcdefg',2);  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
--   
ab   
  
(1 row(s) affected)  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-using-left-with-a-column"></a>C. Utilizzo di LEFT con una colonna  
 Nell'esempio seguente vengono restituiti i primi cinque caratteri di ogni nome di prodotto.  
  
```  
-- Uses AdventureWorks  
  
SELECT LEFT(EnglishProductName, 5)   
FROM dbo.DimProduct  
ORDER BY ProductKey;  
```  
  
### <a name="d-using-left-with-a-character-string"></a>D. Utilizzo di LEFT con una stringa di caratteri  
 Nell'esempio seguente viene utilizzata la funzione `LEFT` per ottenere i primi due caratteri della stringa di caratteri `abcdefg`.  
  
```  
-- Uses AdventureWorks  
  
SELECT LEFT('abcdefg',2) FROM dbo.DimProduct;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
--   
ab  
```  
  
## <a name="see-also"></a>Vedere anche  
 [LTRIM &#40;Transact-SQL&#41;](../../t-sql/functions/ltrim-transact-sql.md)  
 [RIGHT &#40;Transact-SQL&#41;](../../t-sql/functions/right-transact-sql.md)  
 [RTRIM &#40;Transact-SQL&#41;](../../t-sql/functions/rtrim-transact-sql.md)  
 [STRING_SPLIT &#40;Transact-SQL&#41;](../../t-sql/functions/string-split-transact-sql.md)  
 [SUBSTRING &#40;Transact-SQL&#41;](../../t-sql/functions/substring-transact-sql.md)  
 [TRIM &#40;Transact-SQL&#41;](../../t-sql/functions/trim-transact-sql.md)  
 [CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)   
 [Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Funzioni per i valori stringa &#40;Transact-SQL&#41;](../../t-sql/functions/string-functions-transact-sql.md)  
  
  


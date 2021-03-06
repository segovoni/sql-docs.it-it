---
title: ALL (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- Azure SQL Database
- SQL Server (starting with 2008)
f1_keywords:
- ALL_TSQL
- ALL
dev_langs:
- TSQL
helpviewer_keywords:
- single-column set of values [SQL Server]
- ALL (Transact-SQL)
ms.assetid: 4b0c002e-1ffd-4425-a980-11fdc1f24af7
caps.latest.revision: 40
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 13b6ce54c65aaeeeb9c46836b79e6879f17915bf
ms.sourcegitcommit: a6596c62f607041c4402f7d5b41a232fca257c14
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36251613"
---
# <a name="all-transact-sql"></a>ALL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Confronta un valore scalare con un set di valori a colonna singola.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
scalar_expression { = | <> | != | > | >= | !> | < | <= | !< } ALL ( subquery )  
```  
  
## <a name="arguments"></a>Argomenti  
 *scalar_expression*  
 Qualsiasi [espressione](../../t-sql/language-elements/expressions-transact-sql.md) valida.  
  
 { = | <> | != | > | >= | !> | < | <= | !< }  
 Operatore di confronto.  
  
 *subquery*  
 Sottoquery che restituisce un set di risultati a colonna singola. Il tipo di dati della colonna restituita deve essere uguale a quello di *scalar_expression*.  
  
 Istruzione SELECT con restrizioni, in cui la clausola ORDER BY e la parola chiave INTO non sono consentite.  
  
## <a name="result-types"></a>Tipi restituiti  
 **Boolean**  
  
## <a name="result-value"></a>Valore restituito  
 Restituisce TRUE se il confronto specificato è TRUE per tutte le coppie (*scalar_expression ***,*** x)*, dove *x* è un valore del set di valori a colonna singola. In caso contrario restituisce FALSE.  
  
## <a name="remarks"></a>Remarks  
 ALL specifica che l'argomento *scalar_expression* deve essere confrontato in modo univoco con ogni valore restituito dalla sottoquery. Se ad esempio la sottoquery restituisce i valori 2 e 3, *scalar_expression* <= ALL (sottoquery) restituisce TRUE se il valore di *scalar_expression* è 2. Se la sottoquery restituisce i valori 2 e 3, *scalar_expression* = ALL (subquery) restituisce FALSE, in quanto alcuni valori della sottoquery (il valore 3) non soddisfano i criteri dell'espressione.  
  
 Per le istruzioni che specificano che l'argomento *scalar_expression* deve essere confrontato in modo univoco con un solo valore restituito dalla sottoquery, vedere [SOME &#124; ANY &#40;Transact-SQL&#41;](../../t-sql/language-elements/some-any-transact-sql.md).  
  
 Le informazioni contenute in questo sono rilevanti per l'utilizzo dell'opzione ALL con una sottoquery. L'opzione ALL può essere usata anche con [UNION](../../t-sql/language-elements/set-operators-union-transact-sql.md) e [SELECT](../../t-sql/queries/select-transact-sql.md).  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene creata una stored procedure che determina se tutti i componenti di una colonna `SalesOrderID` specificata nel database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] possono essere prodotti nel numero di giorni indicato. Nell'esempio viene utilizzata una sottoquery per creare un elenco contenente i numeri corrispondenti ai valori di `DaysToManufacture` per tutti i componenti della colonna `SalesOrderID` specifica e viene quindi verificato che tutti i valori di `DaysToManufacture` siano maggiori del numero di giorni specificato.  
  
```  
-- Uses AdventureWorks  
  
CREATE PROCEDURE DaysToBuild @OrderID int, @NumberOfDays int  
AS  
IF   
@NumberOfDays >= ALL  
   (  
    SELECT DaysToManufacture  
    FROM Sales.SalesOrderDetail  
    JOIN Production.Product   
    ON Sales.SalesOrderDetail.ProductID = Production.Product.ProductID   
    WHERE SalesOrderID = @OrderID  
   )  
PRINT 'All items for this order can be manufactured in specified number of days or less.'  
ELSE   
PRINT 'Some items for this order cannot be manufactured in specified number of days or less.' ;  
  
```  
  
 Per testare la procedura, eseguirla utilizzando il valore `SalesOrderID 49080`, a cui sono associati un componente che richiede `2` giorni e due componenti che richiedono 0 giorni. La prima istruzione, di seguito, soddisfa i criteri, mentre la seconda no.  
  
```  
EXECUTE DaysToBuild 49080, 2 ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `All items for this order can be manufactured in specified number of days or less.`  
  
```  
EXECUTE DaysToBuild 49080, 1 ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Some items for this order cannot be manufactured in specified number of days or less.`  
  
## <a name="see-also"></a>Vedere anche  
 [CASE &#40;Transact-SQL&#41;](../../t-sql/language-elements/case-transact-sql.md)   
 [Espressioni &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Funzioni predefinite &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)   
 [LIKE &#40;Transact-SQL&#41;](../../t-sql/language-elements/like-transact-sql.md)   
 [Operatori &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [WHERE &#40;Transact-SQL&#41;](../../t-sql/queries/where-transact-sql.md)   
 [IN &#40;Transact-SQL&#41;](../../t-sql/language-elements/in-transact-sql.md)  
  
  

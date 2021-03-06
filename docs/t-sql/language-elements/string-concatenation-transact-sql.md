---
title: + + (concatenazione di stringhe) (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 12/06/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- concatenation
- +
- string
dev_langs:
- TSQL
helpviewer_keywords:
- concatenation [SQL Server]
- string concatenation operators
- + (string concatenation)
ms.assetid: 35cb3d7a-48f5-4b13-926c-a9d369e20ed7
caps.latest.revision: 51
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: bfeb9186a0d49ff4136671504d8e92d1582c08ff
ms.sourcegitcommit: a6596c62f607041c4402f7d5b41a232fca257c14
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36240923"
---
# <a name="-string-concatenation-transact-sql"></a>+ (concatenazione di stringhe) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Operatore in un'espressione stringa che consente di concatenare in un'unica espressione due o più stringhe di tipo carattere o binario, colonne o una combinazione di nomi di colonna e stringhe (operatore di stringa).  Ad esempio `SELECT 'book'+'case';` restituisce `bookcase`.
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
expression + expression  
```  
  
## <a name="arguments"></a>Argomenti  
 *expression*  
 Qualsiasi [espressione](../../t-sql/language-elements/expressions-transact-sql.md) valida di uno dei tipi di dati della categoria di tipi di dati carattere e binari, tranne i tipi **image**, **ntext** o **text**. È necessario che alle due espressioni sia applicato lo stesso tipo di dati oppure che un'espressione possa essere convertita in modo implicito nel tipo di dati dell'altra espressione.  
  
 Per la concatenazione di stringhe binarie e dei caratteri tra le stringhe binarie, è necessario eseguire una conversione esplicita in dati di tipo carattere. Nell'esempio seguente viene illustrato quando è necessario eseguire la funzione `CONVERT` o `CAST` per la concatenazione binaria e quando invece l'uso di `CONVERT` o `CAST`non è richiesto.  
  
```  
DECLARE @mybin1 varbinary(5), @mybin2 varbinary(5)  
SET @mybin1 = 0xFF  
SET @mybin2 = 0xA5  
-- No CONVERT or CAST function is required because this example   
-- concatenates two binary strings.  
SELECT @mybin1 + @mybin2  
-- A CONVERT or CAST function is required because this example  
-- concatenates two binary strings plus a space.  
SELECT CONVERT(varchar(5), @mybin1) + ' '   
   + CONVERT(varchar(5), @mybin2)  
-- Here is the same conversion using CAST.  
SELECT CAST(@mybin1 AS varchar(5)) + ' '   
   + CAST(@mybin2 AS varchar(5))  
  
```  
  
## <a name="result-types"></a>Tipi restituiti  
 Viene restituito il tipo di dati dell'argomento con precedenza maggiore. Per altre informazioni, vedere [Precedenza dei tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-type-precedence-transact-sql.md).  
  
## <a name="remarks"></a>Remarks  
 L'operatore + di concatenazione delle stringhe ha un funzionamento diverso quando viene utilizzato con una stringa vuota, di lunghezza zero, rispetto a quando viene utilizzato con valori NULL, o sconosciuti. Una stringa di caratteri di lunghezza zero può essere specificata con due virgolette singole senza alcun carattere all'interno delle virgolette. Una stringa binaria di lunghezza zero può essere specificata con 0x senza alcun valore byte nella costante esadecimale. La concatenazione di una stringa di valore zero comporta sempre la concatenazione delle due stringhe specificate. Quando si utilizzano stringhe con un valore Null, il risultato della concatenazione dipende dalle impostazioni della sessione. Allo stesso modo di quanto accade per le operazioni aritmetiche eseguite su valori Null, in cui, quando un valore Null viene aggiunto a un valore noto, il risultato è in genere un valore sconosciuto, un'operazione di concatenazione di stringhe eseguita con un valore Null dovrebbe restituire un risultato Null. È tuttavia possibile modificare questo comportamento cambiando l'impostazione di `CONCAT_NULL_YIELDS_NULL` per la sessione corrente. Per altre informazioni, vedere [SET CONCAT_NULL_YIELDS_NULL &#40;Transact-SQL&#41;](../../t-sql/statements/set-concat-null-yields-null-transact-sql.md).  
  
 Se il risultato della concatenazione di stringhe supera il limite di 8.000 byte, il risultato viene troncato. Se tuttavia almeno una delle stringhe concatenate è un tipo di dati per valori di grandi dimensioni, il troncamento non avviene.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-string-concatenation"></a>A. Utilizzo della concatenazione di stringhe  
 Nell'esempio seguente viene creata una singola colonna sotto l'intestazione `Name` in base a più colonne di tipo carattere, con il cognome della persona seguito da una virgola, uno spazio e successivamente il nome. Il set di risultati è visualizzato in ordine alfabetico crescente in base prima al cognome e quindi al nome.  
  
```  
-- Uses AdventureWorks  
  
SELECT (LastName + ', ' + FirstName) AS Name  
FROM Person.Person  
ORDER BY LastName ASC, FirstName ASC;  
```  
  
### <a name="b-combining-numeric-and-date-data-types"></a>B. Combinazione di tipi di dati numeric e date  
 Nell'esempio seguente viene usata la funzione `CONVERT` per concatenare i tipi di dati **numeric** e **date**.  
  
```  
-- Uses AdventureWorks  
  
SELECT 'The order is due on ' + CONVERT(varchar(12), DueDate, 101)  
FROM Sales.SalesOrderHeader  
WHERE SalesOrderID = 50001;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 ------------------------------------------------  
 The order is due on 04/23/2007  
 (1 row(s) affected)
 ```  
  
### <a name="c-using-multiple-string-concatenation"></a>C. Utilizzo della concatenazione di più stringhe  
 Nell'esempio seguente vengono concatenate più stringhe per ottenere un'unica stringa di lunghezza maggiore per visualizzare il cognome e l'iniziale del nome dei vicepresidenti in [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)]. Vengono aggiunti una virgola dopo il cognome e un punto dopo l'iniziale del nome.  
  
```  
-- Uses AdventureWorks  
  
SELECT (LastName + ',' + SPACE(1) + SUBSTRING(FirstName, 1, 1) + '.') AS Name, e.JobTitle  
FROM Person.Person AS p  
    JOIN HumanResources.Employee AS e  
    ON p.BusinessEntityID = e.BusinessEntityID  
WHERE e.JobTitle LIKE 'Vice%'  
ORDER BY LastName ASC;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 Name               Title  
 -------------      ---------------`  
 Duffy, T.          Vice President of Engineering  
 Hamilton, J.       Vice President of Production  
 Welcker, B.        Vice President of Sales  

 (3 row(s) affected)
 ```  
 
### <a name="d-using-large-strings-in-concatenation"></a>D. Uso di stringhe di grandi dimensioni nella concatenazione
Nell'esempio seguente si concatenano più stringhe per formare una stringa lunga e quindi si prova a calcolare la lunghezza della stringa finale. La lunghezza del set di risultati finale è 16000, perché l'espressione di valutazione viene avviata da sinistra, ovvero @x + @z + @y => (@x + @z) + @y. In questo caso, il risultato di (@x + @z) viene troncato a 8000 byte, quindi @y viene aggiunto al set di risultati. Pertanto la lunghezza finale della stringa è 16000. Dato che @y è una stringa con tipo di dati per valori di grandi dimensioni non si verifica nessun troncamento.

```
DECLARE @x varchar(8000) = replicate('x', 8000)
DECLARE @y varchar(max) = replicate('y', 8000)
DECLARE @z varchar(8000) = replicate('z',8000)
SET @y = @x + @z + @y
-- The result of following select is 16000
SELECT len(@y) AS y
GO
```
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 y        
 -------  
 16000  
  
 (1 row(s) affected)
 ```  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="e-using-multiple-string-concatenation"></a>E. Utilizzo della concatenazione di più stringhe  
 Nell'esempio seguente vengono concatenate più stringhe per ottenere un'unica stringa di lunghezza maggiore per visualizzare il cognome e l'iniziale del nome dei vicepresidenti in un database di esempio. Vengono aggiunti una virgola dopo il cognome e un punto dopo l'iniziale del nome.  
  
```  
-- Uses AdventureWorks  
  
SELECT (LastName + ', ' + SUBSTRING(FirstName, 1, 1) + '.') AS Name, Title  
FROM DimEmployee  
WHERE Title LIKE '%Vice Pres%'  
ORDER BY LastName ASC;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Name               Title                                           
-------------      ---------------  
Duffy, T.          Vice President of Engineering  
Hamilton, J.       Vice President of Production  
Welcker, B.        Vice President of Sales  
```  
  
## <a name="see-also"></a>Vedere anche  
 [+= &#40;Assegnazione di concatenazione di stringhe&#41; &#40;Transact-SQL&#41;](../../t-sql/language-elements/string-concatenation-equal-transact-sql.md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)   
 [Conversione di tipi di dati &#40;motore di database&#41;](../../t-sql/data-types/data-type-conversion-database-engine.md)   
 [Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Espressioni &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Funzioni predefinite &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)   
 [Operatori &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [Istruzioni SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
  
  




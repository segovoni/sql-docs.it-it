---
title: STUFF (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- STUFF
- STUFF_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- deleting characters
- STUFF function
- length characters
- removing characters
- replacing characters
- characters [SQL Server], replacing
- inserting data
ms.assetid: abb0afa9-44f6-42a2-a871-5f471dfb222b
caps.latest.revision: 40
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: b651fdc2e6a4f5bfb7e6163de10e3fbbba751423
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/04/2018
ms.locfileid: "37787052"
---
# <a name="stuff-transact-sql"></a>STUFF (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  La funzione STUFF consente di inserire una stringa in un'altra stringa eliminando un numero di caratteri specificato nella posizione iniziale della prima stringa e inserendo la seconda stringa in tale posizione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
STUFF ( character_expression , start , length , replaceWith_expression )  
```  
  
## <a name="arguments"></a>Argomenti  
 *character_expression*  
 [Espressione](../../t-sql/language-elements/expressions-transact-sql.md) di dati di tipo carattere. *character_expression* può essere una costante, una variabile o una colonna di dati di tipo carattere o binario.  
  
 *start*  
 Valore intero che indica la posizione da cui iniziare le operazioni di eliminazione e inserimento. Se l'argomento *start* è negativo o zero, viene restituita una stringa Null. Se *start* è più lungo del primo argomento *character_expression*, viene restituita una stringa Null. *start* può essere di tipo **bigint**.  
  
 *length*  
 Valore intero che indica il numero di caratteri da eliminare. Se l'argomento *length* è negativo, viene restituita una stringa Null. Se *length* è più lungo della prima istanza di *character_expression*, l'eliminazione viene eseguita fino all'ultimo carattere dell'ultima istanza di *character_expression*.  Se *length* è zero, l'inserimento viene eseguito prima del primo carattere nella stringa. *length* può essere di tipo **bigint**.

 *replaceWith_expression*  
 [Espressione](../../t-sql/language-elements/expressions-transact-sql.md) di dati di tipo carattere. *character_expression* può essere una costante, una variabile o una colonna di dati di tipo carattere o binario. Questa espressione sostituisce un numero di caratteri pari a *length* in *character_expression* a partire da *start*. Se si specifica `NULL` come *replaceWith_expression* i caratteri vengono rimossi senza inserire nulla.   
  
## <a name="return-types"></a>Tipi restituiti  
 Restituisce dati di tipo carattere se *character_expression* è un tipo di dati carattere supportato. Restituisce dati binari se *character_expression* è un tipo di dati binary supportato.  
  
## <a name="remarks"></a>Remarks  
 Se la posizione iniziale o la lunghezza è negativa oppure la posizione iniziale è maggiore della lunghezza della prima stringa, viene restituita una stringa Null. Se la posizione iniziale è 0, viene restituito un valore Null. Se il numero di caratteri da eliminare è maggiore del numero di caratteri che compongono la prima stringa, l'eliminazione arriva fino al primo carattere della prima stringa.  

Viene generato un errore se il valore risultante è maggiore del massimo supportato dal tipo restituito.  
  
## <a name="supplementary-characters-surrogate-pairs"></a>Caratteri supplementari (coppie di surrogati)  
 Quando si usano regole di confronto SC, sia *character_expression* sia *replaceWith_expression* possono includere coppie di surrogati. Il parametro della lunghezza considererà ogni surrogato in *character_expression* come carattere singolo.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene restituita una stringa di caratteri ottenuta eliminando tre caratteri dalla prima stringa, `abcdef`, a partire dalla posizione `2`, in corrispondenza di `b`, e inserendo la seconda stringa nel punto in cui è stata eseguita l'eliminazione.  
  
```  
SELECT STUFF('abcdef', 2, 3, 'ijklmn');  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
---------   
aijklmnef   
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CONCAT &#40;Transact-SQL&#41;](../../t-sql/functions/concat-transact-sql.md)  
 [CONCAT_WS &#40;Transact-SQL&#41;](../../t-sql/functions/concat-ws-transact-sql.md)  
 [FORMATMESSAGE &#40;Transact-SQL&#41;](../../t-sql/functions/formatmessage-transact-sql.md)  
 [QUOTENAME &#40;Transact-SQL&#41;](../../t-sql/functions/quotename-transact-sql.md)  
 [REPLACE &#40;Transact-SQL&#41;](../../t-sql/functions/replace-transact-sql.md)  
 [REVERSE &#40;Transact-SQL&#41;](../../t-sql/functions/reverse-transact-sql.md)  
 [STRING_AGG &#40;Transact-SQL&#41;](../../t-sql/functions/string-agg-transact-sql.md)  
 [STRING_ESCAPE &#40;Transact-SQL&#41;](../../t-sql/functions/string-escape-transact-sql.md)  
 [TRANSLATE &#40;Transact-SQL&#41;](../../t-sql/functions/translate-transact-sql.md)  
 [Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Funzioni per i valori stringa &#40;Transact-SQL&#41;](../../t-sql/functions/string-functions-transact-sql.md)  

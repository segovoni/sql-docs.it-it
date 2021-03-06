---
title: ^ (OR esclusivo bit per bit) (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/10/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ^_TSQL
- Bitwise Exclusive OR
- Exclusive
- ^
- bitwise
- OR
dev_langs:
- TSQL
helpviewer_keywords:
- ^ (bitwise exclusive OR operator)
- OR operator
- exclusive OR mathematical operations
- bitwise exclusive OR (^)
ms.assetid: f38f0ad4-46d0-40ea-9851-0f928fda5293
caps.latest.revision: 44
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: eedfd53197aa4d990261f4e1c9bef097613d24b8
ms.sourcegitcommit: a6596c62f607041c4402f7d5b41a232fca257c14
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36257193"
---
# <a name="-bitwise-exclusive-or-transact-sql"></a>^ (OR esclusivo bit per bit) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Esegue un'operazione con OR esclusivo bit per bit tra due valori integer.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
expression ^ expression  
```  
  
## <a name="arguments"></a>Argomenti  
 *expression*  
 Qualsiasi [espressione](../../t-sql/language-elements/expressions-transact-sql.md) valida di qualsiasi tipo di dati della categoria Integer o del tipo di dati **bit**, **binary** o **varbinary**. *expression* viene considerato un numero binario per l'operazione bit per bit.  
  
> [!NOTE]  
>  In un'operazione bit per bit un solo valore *expression* può avere il tipo di dati **binary** o **varbinary**.  
  
## <a name="result-types"></a>Tipi restituiti  
 **int** se i valori di input sono **int**.  
  
 **smallint** se i valori di input sono **smallint**.  
  
 **tinyint** se i valori di input sono **tinyint**.  
  
## <a name="remarks"></a>Remarks  
 L'operatore bit per bit **^** esegue un'operazione logica OR esclusiva bit per bit tra due espressioni, considerando tutti i bit corrispondenti in entrambe le espressioni. I bit nel risultato sono impostati su 1 se il valore di un solo bit (per il bit in fase di risoluzione) nelle espressioni di input è uguale a 1. Se entrambi i bit hanno valore 0 o 1, il bit del risultato corrispondente verrà impostato su 0.  
  
 Se alle due espressioni viene applicato un tipo di dati Integer diverso, ad esempio se il tipo *expression* a sinistra è **smallint** e il tipo *expression* a destra è **int**, l'argomento del tipo di dati di livello inferiore viene convertito nel tipo di dati di livello superiore. In questo caso **smallint***expression* viene convertito in **int**.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene creata una tabella che usa il tipo di dati **int** per archiviare i valori originali e vengono inseriti due valori in una sola riga.  
  
```  
CREATE TABLE bitwise  
(   
a_int_value int NOT NULL,  
b_int_value int NOT NULL  
);  
GO  
INSERT bitwise VALUES (170, 75);  
GO  
```  
  
 La query seguente esegue l'operazione con OR esclusivo bit per bit sulle colonne `a_int_value` e `b_int_value`.  
  
```  
SELECT a_int_value ^ b_int_value  
FROM bitwise;  
GO  
```  
  
 Set di risultati:  
  
```  
-----------   
225           
  
(1 row(s) affected)  
```  
  
 La rappresentazione binaria di 170 (`a_int_value` o `A`) è `0000 0000 1010 1010`. La rappresentazione binaria di 75 (`b_int_value` o `B`) è `0000 0000 0100 1011`. L'esecuzione dell'operazione con OR esclusivo bit per bit su questi due valori genera il risultato binario `0000 0000 1110 0001`, che corrisponde al valore decimale 225.  
  
```  
(A ^ B)     
         0000 0000 1010 1010  
         0000 0000 0100 1011  
         -------------------  
         0000 0000 1110 0001  
```  
  

  
## <a name="see-also"></a>Vedere anche  
 [Espressioni &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Operatori &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [Operatori bit per bit &#40;Transact-SQL&#41;](../../t-sql/language-elements/bitwise-operators-transact-sql.md)   
 [^= &#40;Assegnazione OR esclusivo bit per bit&#41; &#40;Transact-SQL&#41;](../../t-sql/language-elements/bitwise-exclusive-or-equals-transact-sql.md)   
 [Operatori composti &#40;Transact-SQL&#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)  
  
  



---
title: SUBSTRING (espressione SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SUBSTRING function
- part of expression returned [Integration Services]
ms.assetid: 3a46748a-f5f8-4a6c-9108-673666754068
caps.latest.revision: 34
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: cc77781f2ee4a8a12a5c150ea29ebae3ca4d4cdf
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37241001"
---
# <a name="substring-ssis-expression"></a>SUBSTRING (espressione SSIS)
  Viene restituita la parte di un'espressione di caratteri che inizia in corrispondenza della posizione specificata e ha la lunghezza specificata. I parametri *position* e *length* devono restituire valori integer.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SUBSTRING(character_expression, position, length)  
```  
  
## <a name="arguments"></a>Argomenti  
 *character_expression*  
 Espressione di caratteri da cui estrarre i caratteri.  
  
 *position*  
 Numero intero che indica il punto iniziale della sottostringa.  
  
 *length*  
 Valore integer che specifica la lunghezza della sottostringa come numero di caratteri.  
  
## <a name="result-types"></a>Tipi restituiti  
 DT_WSTR  
  
## <a name="remarks"></a>Note  
 La funzione SUBSTRING utilizza un indice in base uno. Se *position* ha valore 1, la sottostringa inizia dal primo carattere in *character_expression*.  
  
 È possibile utilizzare SUBSTRING solo con il tipo di dati DT_WSTR. Se l'argomento *character_expression* è un valore letterale stringa o una colonna di dati con tipo di dati DT_STR, prima di eseguire l'operazione prevista da SUBSTRING verrà eseguito il cast implicito al tipo di dati DT_WSTR. Per gli altri tipi di dati è necessario il cast esplicito al tipo di dati DT_WSTR. Per altre informazioni, vedere [Tipi di dati di Integration Services](../data-flow/integration-services-data-types.md) e [Cast &#40;espressione SSIS&#41;](cast-ssis-expression.md).  
  
 Se l'argomento è Null, SUBSTRING restituirà Null.  
  
 Tutti gli argomenti nell'espressione possono utilizzare variabili e colonne.  
  
 Il valore dell'argomento *length* può superare la lunghezza della stringa. In questo caso la funzione restituisce la parte rimanente della stringa.  
  
## <a name="expression-examples"></a>Esempi di espressione  
 In questo esempio vengono restituiti due caratteri da un valore letterale stringa, a partire dal carattere 4. Il risultato restituito è "ph".  
  
```  
SUBSTRING("elephant",4,2)  
```  
  
 In questo esempio viene restituita la parte rimanente da un valore letterale stringa, a partire dal quarto carattere. Il risultato restituito è "phant". Se il valore dell'argomento *length* supera la lunghezza delle stringa, non si tratta di un errore.  
  
```  
SUBSTRING ("elephant",4,50)  
```  
  
 In questo esempio viene restituita la prima lettera della colonna **MiddleName** .  
  
```  
SUBSTRING(MiddleName,1,1)  
```  
  
 In questo esempio negli argomenti *position* e *length* vengono utilizzate alcune variabili. Se **Start** ha valore 1 e **Length** ha valore 5, la funzione restituirà i primi cinque caratteri nella colonna **Name** .  
  
```  
SUBSTRING(Name,@Start,@Length)  
```  
  
 In questo esempio vengono restituiti quattro caratteri nella variabile **PostalCode** , a partire dal sesto.  
  
```  
SUBSTRING (@PostalCode,6,4)  
```  
  
 In questo esempio viene restituita una stringa di lunghezza zero da un valore letterale stringa.  
  
```  
SUBSTRING ("Redmond",4,0)  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Le funzioni &#40;espressione di SSIS&#41;](functions-ssis-expression.md)  
  
  

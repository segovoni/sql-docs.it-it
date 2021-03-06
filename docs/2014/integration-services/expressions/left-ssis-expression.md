---
title: LEFT (espressione SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 5634dbfb-740d-4c93-8fd5-2854cc741327
caps.latest.revision: 12
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: da89c1a1740d8acd0f284d9cf1475d34ca651792
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37252593"
---
# <a name="left-ssis-expression"></a>LEFT (espressione SSIS)
  Viene restituito il numero specificato di caratteri della parte più a sinistra dell'espressione di caratteri indicata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
LEFT(character_expression,number)  
```  
  
## <a name="arguments"></a>Argomenti  
 *character_expression*  
 Espressione di caratteri da cui estrarre i caratteri.  
  
 *number*  
 Espressione integer in cui viene indicato il numero di caratteri da restituire.  
  
## <a name="result-types"></a>Tipi restituiti  
 DT_WSTR  
  
## <a name="remarks"></a>Note  
 Se *number* è maggiore della lunghezza di *character_expression*, la funzione restituisce *character_expression*.  
  
 Se *number* ha valore zero, la funzione restituirà una stringa di lunghezza zero.  
  
 Se *number* è un numero negativo, la funzione restituirà un errore.  
  
 L'argomento *number* accetta variabili e colonne.  
  
 È possibile utilizzare LEFT solo con il tipo di dati DT_WSTR. Se l'argomento *character_expression* è un valore letterale stringa o una colonna di dati con tipo di dati DT_STR, prima di eseguire l'operazione prevista da LEFT verrà eseguito il cast implicito al tipo di dati DT_WSTR. Per gli altri tipi di dati è necessario il cast esplicito al tipo di dati DT_WSTR. Per altre informazioni, vedere [Tipi di dati di Integration Services](../data-flow/integration-services-data-types.md) e [Cast &#40;espressione SSIS&#41;](cast-ssis-expression.md).  
  
 Se l'argomento è Null, verrà restituito Null da LEFT.  
  
## <a name="expression-examples"></a>Esempi di espressione  
 Nell'esempio seguente viene utilizzato un valore letterale stringa. Il risultato restituito sarà `"Mountain"`.  
  
```  
LEFT("Mountain Bike", 8)  
```  
  
## <a name="see-also"></a>Vedere anche  
 [DESTRA &#40;espressione di SSIS&#41;](right-ssis-expression.md)   
 [Le funzioni &#40;espressione di SSIS&#41;](functions-ssis-expression.md)  
  
  

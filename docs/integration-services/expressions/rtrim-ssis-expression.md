---
title: RTRIM (espressione SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: expressions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- RTRIM function
- trailing blanks
ms.assetid: 529bd43e-3f8a-4682-a33e-569176aa7fc4
caps.latest.revision: 38
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 19160454199b788867db0b458de628368c5a777d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="rtrim-ssis-expression"></a>RTRIM (espressione SSIS)
  Viene restituita un'espressione di caratteri dopo aver rimosso gli spazi finali.  
  
> [!NOTE]  
>  RTRIM non rimuove altri caratteri spazio quali i caratteri di tabulazione o avanzamento riga. Unicode offre elementi di codice per molti tipi diversi di spazi, ma questa funzione riconosce solo l'elemento di codice Unicode 0x0020. Quando stringhe DBCS (Double-Byte Character Set) vengono convertite in Unicode, possono includere caratteri spazio diversi da 0x0020 e la funzione non può rimuovere tali spazi. Per rimuovere qualsiasi tipo di spazi, è possibile utilizzare il metodo Microsoft Visual Basic .NET RTrim in uno script eseguito dal componente Script.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
RTRIM(character expression)  
```  
  
## <a name="arguments"></a>Argomenti  
 *character_expression*  
 Espressione di caratteri da cui rimuovere gli spazi.  
  
## <a name="result-types"></a>Tipi restituiti  
 DT_WSTR  
  
## <a name="remarks"></a>Remarks  
 È possibile utilizzare RTRIM solo con il tipo di dati DT_WSTR. Se l'argomento *character_expression* è un valore letterale stringa o una colonna di dati con tipo di dati DT_STR, prima di eseguire l'operazione prevista da RTRIM verrà eseguito il cast implicito al tipo di dati DT_WSTR. Per gli altri tipi di dati è necessario il cast esplicito al tipo di dati DT_WSTR. Per altre informazioni, vedere [Tipi di dati di Integration Services](../../integration-services/data-flow/integration-services-data-types.md) e [Cast &#40;espressione SSIS&#41;](../../integration-services/expressions/cast-ssis-expression.md).  
  
 Se l'argomento è Null, RTRIM restituirà Null.  
  
## <a name="expression-examples"></a>Esempi di espressione  
 In questo esempio vengono rimossi gli spazi finali da un valore letterale stringa. Il risultato restituito è "Hello".  
  
```  
RTRIM("Hello   ")  
```  
  
 In questo esempio vengono rimossi gli spazi finali dal risultato della concatenazione delle colonne **FirstName** e **LastName** .  
  
```  
RTRIM(FirstName + " " + LastName)  
```  
  
 In questo esempio vengono rimossi gli spazi finali dalla variabile **FirstName** .  
  
```  
RTRIM(@FirstName)  
```  
  
## <a name="see-also"></a>Vedere anche  
 [LTRIM &#40;espressione SSIS&#41;](../../integration-services/expressions/ltrim-ssis-expression.md)   
 [TRIM &#40;espressione SSIS&#41;](../../integration-services/expressions/trim-ssis-expression.md)   
 [Funzioni &#40;espressione SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  

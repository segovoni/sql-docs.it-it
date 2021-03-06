---
title: DATEPART (espressione SSIS) | Microsoft Docs
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
- dates [Integration Services], DATEPART
- DATEPART function
ms.assetid: 3e590094-fc49-4144-805f-fdc1bf2fe509
caps.latest.revision: 40
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c8309f3f4292795cebffe94f03e1418bb36d8929
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37209791"
---
# <a name="datepart-ssis-expression"></a>DATEPART (espressione SSIS)
  Restituisce un valore integer che rappresenta una parte di una data.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DATEPART(datepart, date)  
```  
  
## <a name="arguments"></a>Argomenti  
 *parte di una data*  
 Parametro che consente di specificare per quale parte della data si desidera restituire un nuovo valore.  
  
 *data*  
 Espressione che restituisce una data valida o una stringa con formato di data.  
  
## <a name="result-types"></a>Tipi restituiti  
 DT_I4  
  
## <a name="remarks"></a>Note  
 Se l'argomento è Null, DATEPART restituirà Null.  
  
 Per i valori letterali di data è necessario eseguire il cast esplicito a uno dei tipi di dati date. Per altre informazioni, vedere [Tipi di dati di Integration Services](../data-flow/integration-services-data-types.md).  
  
 Nella tabella seguente sono elencate le parti della data e le abbreviazioni riconosciute dall'analizzatore di espressioni. Per i nomi delle parti della data non viene fatta distinzione tra maiuscole e minuscole.  
  
|parte di una data|Abbreviazioni|  
|--------------|-------------------|  
|Year|yy, yyyy|  
|Quarter|qq, q|  
|Month|mm, m|  
|Dayofyear|dy, y|  
|Day|dd, d|  
|Week|wk, ww|  
|Giorno feriale|dw|  
|Ora|Hh|  
|Minuto|mi, n|  
|Secondo|ss, s|  
|Millisecond|Ms|  
  
## <a name="ssis-expression-examples"></a>Esempi di espressione SSIS  
 In questo esempio viene restituito un valore integer che rappresenta il mese in un valore letterale data. Se la data è in formato "mm/gg/aaaa", l'esempio restituirà 11.  
  
```  
DATEPART("month", (DT_DBTIMESTAMP)"11/04/2002")  
```  
  
 In questo esempio viene restituito un valore integer che rappresenta il giorno nella colonna **ModifiedDate** .  
  
```  
DATEPART("dd", ModifiedDate)  
```  
  
 In questo esempio viene restituito un valore integer che rappresenta l'anno nella data corrente.  
  
```  
DATEPART("yy",GETDATE())  
```  
  
## <a name="see-also"></a>Vedere anche  
 [DATEADD &#40;espressione di SSIS&#41;](dateadd-ssis-expression.md)   
 [DATEDIFF &#40;espressione di SSIS&#41;](datediff-ssis-expression.md)   
 [DAY &#40;espressione SSIS&#41;](day-ssis-expression.md)   
 [MONTH &#40;espressione SSIS&#41;](month-ssis-expression.md)   
 [YEAR &#40;espressione SSIS&#41;](year-ssis-expression.md)   
 [Le funzioni &#40;espressione di SSIS&#41;](functions-ssis-expression.md)  
  
  

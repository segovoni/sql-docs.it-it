---
title: DATEDIFF (espressione SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- DATEDIFF statement
- dates [Integration Services], DATEDIFF
ms.assetid: 449b327f-47c7-4709-8bc6-4ee9a35cc330
caps.latest.revision: 40
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 1158697fd2575d8ac08ff6df2972470a87daaf07
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2018
ms.locfileid: "35401833"
---
# <a name="datediff-ssis-expression"></a>DATEDIFF (espressione SSIS)
  Restituisce il numero di unità di data e ora trascorse tra due date specificate. Il parametro *datepart* identifica i limiti di data e ora da confrontare.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DATEDIFF(datepart, startdate, endate)  
```  
  
## <a name="arguments"></a>Argomenti  
 *datepart*  
 Parametro che specifica per quale parte della data si desidera eseguire il confronto e restituire un valore.  
  
 *startdate*  
 Data di inizio dell'intervallo.  
  
 *endate*  
 Data di fine dell'intervallo.  
  
## <a name="result-types"></a>Tipi restituiti  
 DT_I4  
  
## <a name="remarks"></a>Remarks  
 Nella tabella seguente sono elencate le parti della data e le abbreviazioni riconosciute dall'analizzatore di espressioni.  
  
|datepart|Abbreviazioni|  
|--------------|-------------------|  
|Year|yy, yyyy|  
|Quarter|qq, q|  
|Month|mm, m|  
|Dayofyear|dy, y|  
|Day|dd, d|  
|Week|wk, ww|  
|Giorno feriale|dw, w|  
|Ora|Hh|  
|Minuto|mi, n|  
|Secondo|ss, s|  
|Millisecond|Ms|  
  
 Se un argomento qualsiasi è Null, DATEDIFF restituirà Null.  
  
 Per i valori letterali di data è necessario eseguire il cast esplicito a uno dei tipi di dati date. Per altre informazioni, vedere [Tipi di dati di Integration Services](../../integration-services/data-flow/integration-services-data-types.md).  
  
 Se la data non è valida, l'ora o la data non è una stringa oppure la data di inizio o fine non è una data, verrà generato un errore.  
  
 Se la data di fine è anteriore a quella di inizio, la funzione restituirà un numero negativo. Se le date di inizio e di fine coincidono o rientrano nello stesso intervallo, la funzione restituirà zero.  
  
## <a name="ssis-expression-examples"></a>Esempi di espressione SSIS  
 In questo esempio viene calcolato il numero dei giorni tra due valori letterali di data. Se la data è in formato "mm/gg/aaaa", la funzione restituirà 7.  
  
```  
DATEDIFF("dd", (DT_DBTIMESTAMP)"8/1/2003", (DT_DBTIMESTAMP)"8/8/2003")  
```  
  
 In questo esempio viene restituito il numero dei mesi tra un valore letterale data e la data corrente.  
  
```  
DATEDIFF("mm", (DT_DBTIMESTAMP)"8/1/2003",GETDATE())  
```  
  
 In questo esempio viene restituito il numero delle settimane tra la data nella colonna **ModifiedDate** e quella nella variabile **YearEndDate** . Se **YearEndDate** ha tipo di dati **date** non sarà necessario eseguire un cast esplicito.  
  
```  
DATEDIFF("Week", ModifiedDate,@YearEndDate)  
```  
  
## <a name="see-also"></a>Vedere anche  
 [DATEADD &#40;espressione SSIS&#41;](../../integration-services/expressions/dateadd-ssis-expression.md)   
 [DATEPART &#40;espressione SSIS&#41;](../../integration-services/expressions/datepart-ssis-expression.md)   
 [DAY &#40;espressione SSIS&#41;](../../integration-services/expressions/day-ssis-expression.md)   
 [MONTH &#40;espressione SSIS&#41;](../../integration-services/expressions/month-ssis-expression.md)   
 [YEAR &#40;espressione SSIS&#41;](../../integration-services/expressions/year-ssis-expression.md)   
 [Funzioni &#40;espressione SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  

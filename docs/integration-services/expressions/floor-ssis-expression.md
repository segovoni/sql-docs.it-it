---
title: FLOOR (espressione SSIS) | Microsoft Docs
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
- largest integer less than or equal to expression
- FLOOR function [SSIS]
ms.assetid: 168084db-badd-40f2-87b4-1f5bc45c3e24
caps.latest.revision: 33
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3a79328a87c3b28f814c70c394b8a3e92aeaa6c7
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2018
ms.locfileid: "35411393"
---
# <a name="floor-ssis-expression"></a>FLOOR (espressione SSIS)
  Restituisce il più alto valore integer minore o uguale a un'espressione numerica specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
FLOOR(numeric_expression)  
```  
  
## <a name="arguments"></a>Argomenti  
 *numeric_expression*  
 Espressione numerica valida.  
  
## <a name="result-types"></a>Tipi restituiti  
 Tipo di dati numeric dell'espressione passata come argomento. Il risultato è rappresentato dalla parte intera del valore calcolato con tipo di dati corrispondente al tipo del parametro *numeric_expression*.  
  
## <a name="remarks"></a>Remarks  
 Se l'argomento è Null, FLOOR restituirà Null.  
  
## <a name="expression-examples"></a>Esempi di espressione  
 In questi esempi la funzione FLOOR viene applicata a valori positivi, negativi e zero.  
  
```  
FLOOR(123.45)  
```  
  
 Restituisce 123,00.  
  
```  
FLOOR(-123.45)  
```  
  
 Restituisce -124,00.  
  
```  
FLOOR(0.00)  
```  
  
 Restituisce 0,00.  
  
## <a name="see-also"></a>Vedere anche  
 [CEILING &#40;espressione SSIS&#41;](../../integration-services/expressions/ceiling-ssis-expression.md)   
 [Funzioni &#40;espressione SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  

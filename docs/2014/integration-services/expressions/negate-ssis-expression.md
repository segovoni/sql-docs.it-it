---
title: '- (negazione) (espressione SSIS) | Microsoft Docs'
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
- '- (negative)'
- negative operator (-)
ms.assetid: f0118dfc-aced-4de2-953e-5ebf9c962b8d
caps.latest.revision: 33
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: aceb64965279799f8e682b070752b25bec0eb37b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37215611"
---
# <a name="--negate-ssis-expression"></a>- (negazione) (espressione SSIS)
  Viene applicato un segno negativo a un'espressione numerica.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
-numeric_expression  
  
```  
  
## <a name="arguments"></a>Argomenti  
 *numeric_expression*  
 Espressione valida con qualsiasi tipo di dati numeric. Sono supportati solo i tipi di dati numeric con segno. Per altre informazioni, vedere [Tipi di dati di Integration Services](../data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Tipi restituiti  
 Restituisce il tipo di dati di *numeric_expression*.  
  
## <a name="expression-examples"></a>Esempi di espressione  
 In questo esempio viene applicato un segno negativo al valore della variabile **Counter** e viene aggiunto il valore letterale numerico 50.  
  
```  
-@Counter + 50  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Precedenza e associatività degli operatori](operator-precedence-and-associativity.md)   
 [Gli operatori &#40;espressione di SSIS&#41;](operators-ssis-expression.md)  
  
  

---
title: Precedenza e associatività degli operatori | Microsoft Docs
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
- associativity [Integration Services]
- precedence [Integration Services]
ms.assetid: 5094164f-dabc-45b5-b611-384feb2b3fe3
caps.latest.revision: 32
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 291f9f3e78d9e6fab8de3b14b78cf3f41a707d32
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2018
ms.locfileid: "35401583"
---
# <a name="operator-precedence-and-associativity"></a>Precedenza e associatività degli operatori
  Ogni operatore nel set di operatori supportato dall'analizzatore di espressioni ha una precedenza specifica nella gerarchia delle precedenze e prevede una direzione di valutazione. La direzione di valutazione di un operatore è l'associatività dell'operatore. Gli operatori con precedenza superiore vengono valutati prima di quelli con precedenza inferiore. Se un'espressione complessa include più operatori, l'ordine di esecuzione è determinato dalla precedenza degli operatori. L'ordine di esecuzione può modificare in modo significativo il valore restituito. Alcuni operatori hanno la stessa precedenza. Se un'espressione contiene più operatori con la stessa precedenza, gli operatori verranno valutati nell'ordine in cui compaiono, procedendo da sinistra a destra o da destra a sinistra.  
  
 Nella tabella seguente vengono elencate le precedenze degli operatori, dalla più alta alla più bassa. Gli operatori indicati sullo stesso livello hanno la stessa precedenza.  
  
|Simbolo operatore|Tipo di operazione|Associatività|  
|---------------------|-----------------------|-------------------|  
|( )|Espressione|Da sinistra a destra|  
|–, !, ~|Unaria|Da destra a sinistra|  
|cast|Unaria|Da destra a sinistra|  
|*, / ,%|Moltiplicazione|Da sinistra a destra|  
|+, –|Additive|Da sinistra a destra|  
|\<, >, \<=, >=|Relazionale|Da sinistra a destra|  
|==, !=|Uguaglianza|Da sinistra a destra|  
|&|AND bit per bit|Da sinistra a destra|  
|^|OR esclusivo bit per bit|Da sinistra a destra|  
|&#124;|OR inclusivo bit per bit|Da sinistra a destra|  
|&&|AND logico|Da sinistra a destra|  
|&#124;&#124;|OR logico|Da sinistra a destra|  
|? :|Espressione condizionale|Da destra a sinistra|  
  
## <a name="see-also"></a>Vedere anche  
 [Operatori &#40;espressione SSIS&#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  

---
title: Divisione (espressione SSIS) | Microsoft Docs
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
- / (divide)
- divide operator (/)
ms.assetid: 5bde9223-872d-443e-8a27-57735e1d8f3d
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a3dc1c33e2d3239311c14a6e0657a85775dc4e6a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37182678"
---
# <a name="divide-ssis-expression"></a>Divisione (espressione SSIS)
  Viene divisa la prima espressione numerica per la seconda.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
dividend / divisor  
  
```  
  
## <a name="arguments"></a>Argomenti  
 *dividend*  
 Espressione numerica da dividere. *dividend* può essere qualsiasi espressione numerica valida. Per altre informazioni, vedere [Tipi di dati di Integration Services](../data-flow/integration-services-data-types.md).  
  
 *divisor*  
 Espressione numerica per cui dividere il dividendo. *divisor* può essere qualsiasi espressione numerica valida, tranne zero.  
  
## <a name="result-types"></a>Tipi restituiti  
 Dipendenti dai tipi di dati dei due argomenti. Per altre informazioni, vedere [Tipi di dati nelle espressioni di Integration Services](integration-services-data-types-in-expressions.md).  
  
## <a name="remarks"></a>Note  
 Se uno degli operandi è Null, il risultato sarà Null.  
  
 La divisione per zero non è consentita. A seconda della modalità con cui viene valutata la sottoespressione *divisor* , può verificarsi uno degli errori seguenti:  
  
-   Se la sottoespressione *divisor* che restituisce zero è una costante, l'errore verrà rilevato in fase di progettazione, impedendo la convalida dell'espressione.  
  
-   Se la sottoespressione *divisor* che restituisce zero contiene variabili ma non colonne di input, il componente a cui appartiene l'espressione non supererà la convalida di pre-elaborazione, che avviene prima dell'esecuzione del pacchetto.  
  
-   Se nella sottoespressione *divisor* tramite cui viene restituito zero sono contenute colonne di input, l'errore verrà visualizzato in fase di esecuzione e verrà gestito secondo le regole del flusso degli errori del componente flusso di dati.  
  
## <a name="expression-examples"></a>Esempi di espressione  
 In questo esempio viene eseguita una divisione tra due valori letterali numerici.  
  
```  
25 / 5  
```  
  
 In questo esempio i valori nella colonna **ListPrice** vengono divisi per i valori nella colonna **StandardCost** .  
  
```  
ListPrice / StandardCost  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Precedenza e associatività degli operatori](operator-precedence-and-associativity.md)   
 [Gli operatori &#40;espressione di SSIS&#41;](operators-ssis-expression.md)  
  
  

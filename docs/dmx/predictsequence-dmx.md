---
title: PredictSequence (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 813641b7fa72405a0ba5a026e255f03feb94bd05
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "37992473"
---
# <a name="predictsequence-dmx"></a>PredictSequence (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Vengono stimati i valori di sequenza futuri per un set specificato di dati in sequenza.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
PredictSequence(<table column reference>)  
PredictSequence(\<table column reference, n>)  
PredictSequence(\<table column reference, n-start, n-end>)  
```  
  
## <a name="return-type"></a>Tipo restituito  
 Oggetto \<espressione di tabella >.  
  
## <a name="remarks"></a>Note  
 Se il *n* parametro è specificato, restituisce i valori seguenti:  
  
-   Se *n* è maggiore di zero, i valori di sequenza più probabili entro i prossimi *n* passaggi.  
  
-   Se entrambe *n-start* e *n-end* vengono specificati, la sequenza di valori da *n-start* al *n-end*.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene restituita una sequenza dei cinque prodotti che più probabilmente verranno acquistati da un cliente nel database [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] in base al modello di data mining Sequence Clustering.  
  
```  
SELECT  
  PredictSequence([Sequence Clustering].[v Assoc Seq Line Items],5)  
From  
  [Sequence Clustering]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Le estensioni di Data Mining di dati &#40;DMX&#41; riferimento alle funzioni](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Le funzioni &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [Funzioni di stima generale &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  

---
title: Elemento AlgorithmParameter (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- AlgorithmParameter Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AlgorithmParameter
helpviewer_keywords:
- AlgorithmParameter element
ms.assetid: 73211495-065c-43c6-a486-be6044617263
caps.latest.revision: 35
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fd5ee9ceb1c8d2455d7e9c087e12e2f59625b5ab
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37178858"
---
# <a name="algorithmparameter-element-assl"></a>Elemento AlgorithmParameter (ASSL)
  Definisce un parametro per l'algoritmo utilizzato da un [MiningModel](miningmodel-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<AlgorithmParameters>  
   <AlgorithmParameter>  
      <Name>...</Name>  
      <Value>...</Value>  
   </AlgorithmParameter>  
</AlgorithmParameters>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[AlgorithmParameters](../collections/algorithmparameters-element-assl.md)|  
|Elementi figlio|[Nome](../properties/name-element-assl.md), [valore](../properties/value-element-assl.md)|  
  
## <a name="remarks"></a>Note  
 Un elemento `AlgorithmParameter` è un parametro per un algoritmo del modello di data mining. `AlgorithmParameter` rappresenta il parametro come coppia nome/valore. Il set di parametri applicabili che un elemento `AlgorithmParameter` può rappresentare è dipendente dall'algoritmo. Per ulteriori informazioni sui parametri per un algoritmo specifico, vedere la documentazione appropriata relativa all'algoritmo.  
  
 I parametri dell'algoritmo disponibili, incluse le informazioni di convalida e visualizzazione, possono essere recuperati dal [DMSCHEMA_MINING_SERVICE_PARAMETERS](../../schema-rowsets/data-mining/dmschema-mining-service-parameters-rowset.md) set di righe dello schema.  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.AlgorithmParameter>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento MiningModel &#40;ASSL&#41;](miningmodel-element-assl.md)   
 [Elemento Algorithm &#40;ASSL&#41;](../properties/algorithm-element-assl.md)   
 [Gli oggetti &#40;ASSL&#41;](objects-assl.md)  
  
  

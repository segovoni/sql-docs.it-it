---
title: Elemento TargetType (ASSL) | Documenti Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: fe1e79254f4daef21634b4e9c5b2144c857bfee0
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34039395"
---
# <a name="targettype-element-assl"></a>Elemento TargetType (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Identifica il tipo di elemento dell'elemento identificato nel [destinazione](../../../analysis-services/scripting/properties/target-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Action>  
   ...  
   <TargetType>...</TargetType>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|Nessuno|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[Azione](../../../analysis-services/scripting/objects/action-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|*Cube*|La destinazione dell'azione è un cubo.|  
|*Celle*|La destinazione dell'azione è un sottocubo.|  
|*Set*|La destinazione dell'azione è un set.|  
|*Gerarchia*|La destinazione dell'azione è una gerarchia.|  
|*Level*|La destinazione dell'azione è un livello.|  
|*DimensionMembers*|La destinazione dell'azione sono i membri di una dimensione.|  
|*HierarchyMembers*|La destinazione dell'azione sono i membri di una gerarchia.|  
|*LevelMembers*|La destinazione dell'azione sono i membri di un livello.|  
|*AttributeMembers*|La destinazione dell'azione sono i membri di un attributo.|  
  
 L'enumerazione che corrisponde ai valori consentiti per **TargetType** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.ActionTargetType>.  
  
 L'elemento che corrisponde all'elemento padre **TargetType** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.Action>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

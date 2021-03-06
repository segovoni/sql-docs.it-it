---
title: Elemento HoldoutMaxPercent | Documenti Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 4c2b6c560d497bb1f5a54e704063459505d71229
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34032882"
---
# <a name="holdoutmaxpercent-element"></a>Elemento HoldoutMaxPercent
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Specifica la percentuale massima di case nell'origine dati che verrà utilizzato per la partizione di dati di controllo che contiene il set di test di un [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md) elemento. I rimanenti casi sono utilizzati per il training. Il valore 0 indica che il numero di casi che possono essere controllati come set di test è illimitato.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<MiningStructure>  
   ...  
   <ddl100_100:HoldoutMaxPercent>...</ddl100_100:HoldoutMaxPercent>  
   ...  
</MiningStructure>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Numero intero compreso tra 0 e 99.|  
|Valore predefinito|30|  
|Cardinalità|0-1: elemento facoltativo che può verificarsi una volta e una volta soltanto.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Se si specificano valori per entrambe **HoldoutMaxPercent** e **HoldoutMaxCases**, l'algoritmo consente di limitare il test è il più piccolo dei due valori.  
  
 Se **HoldoutMaxCases** è impostata sul valore predefinito pari a 0, e non è stato impostato un valore per **HoldoutMaxPercent**, l'algoritmo utilizza il set di dati completo per il training.  
  
 Le nuove proprietà **HoldoutMaxCases**, **HoldoutMaxPercent**, **HoldoutSeed**, o **HoldoutActualSize** sono disponibili solo in [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] e versioni successive. È pertanto necessario utilizzare per queste proprietà un prefisso con il nuovo spazio dei nomi, come illustrato nella descrizione della sintassi. In caso contrario, in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] viene restituito un errore.  
  
> [!NOTE]  
>  In [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] non supportava l'utilizzo di partizioni di controllo su una struttura di data mining. Pertanto, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istruzioni di Scripting Language (ASSL) contenenti uno dei parametri di controllo **HoldoutMaxCases**, **HoldoutMaxPercent**, **HoldoutSeed**, o **HoldoutActualSize**, non può essere utilizzato [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Se si utilizza uno di questi parametri di controllo in un'istruzione ASSL in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] restituirà un errore.  
  
 L'elemento che corrisponde all'elemento padre **HoldoutMaxPercent** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.MiningStructure>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](../../../analysis-services/scripting/properties/properties-assl.md)   
 [Elemento HoldoutMaxCases](../../../analysis-services/scripting/properties/holdoutmaxcases-element.md)   
 [Elemento HoldoutSeed](../../../analysis-services/scripting/properties/holdoutseed-element.md)   
 [Elemento HoldoutActualSize](../../../analysis-services/scripting/properties/holdoutactualsize-element.md)  
  
  

---
title: Elemento AggregationFunction (ASSL) | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0e465538b6528e26090f96786f98354b5253b9a7
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34032227"
---
# <a name="aggregationfunction-element-assl"></a>Elemento AggregationFunction (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Contiene la funzione di aggregazione da usare per il tipo di account.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Account>  
   ...  
   <AggregationFunction>...</AggregationFunction>  
   ...  
</Account>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*Sum*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Account](../../../analysis-services/scripting/objects/account-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il valore di questo elemento è limitato a una delle stringhe seguenti.  
  
|Value|Description|  
|-----------|-----------------|  
|*Sum*|La misura viene aggregata utilizzando il **somma** (funzione).|  
|*Count*|La misura viene aggregata utilizzando il **conteggio** (funzione).|  
|*Min*|La misura viene aggregata utilizzando il **Min** (funzione).|  
|*Max*|La misura viene aggregata utilizzando il **Max** (funzione).|  
|*DistinctCount*|La misura viene aggregata utilizzando il **DistinctCount** (funzione).|  
|*Nessuno*|Non viene eseguita alcuna aggregazione della misura.|  
|*AverageOfChildren*|La misura viene aggregata restituendo la media dei relativi membri figlio.|  
|*FirstChild*|La misura viene aggregata restituendone il primo membro figlio.|  
|*LastChild*|La misura viene aggregata restituendone l'ultimo membro figlio.|  
|*FirstNonEmpty*|La misura viene aggregata restituendone il primo membro non vuoto.|  
|*LastNonEmpty*|La misura viene aggregata restituendone l'ultimo membro non vuoto.|  
  
 L'enumerazione che corrisponde ai valori consentiti per **AggregationFunction** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.AggregationFunction>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento account &#40;ASSL&#41;](../../../analysis-services/scripting/collections/accounts-element-assl.md)   
 [Proprietà & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

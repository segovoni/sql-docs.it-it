---
title: Elemento AggregationFunction (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- AggregationFunction Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AggregationFunction
helpviewer_keywords:
- AggregationFunction element
ms.assetid: 40cfc7f9-1089-45f9-be90-a29770ed9682
caps.latest.revision: 39
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 90908001138f59d4270811376ac44025148889cf
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37308441"
---
# <a name="aggregationfunction-element-assl"></a>Elemento AggregationFunction (ASSL)
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
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*Sum*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Account](../objects/account-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il valore di questo elemento è limitato a una delle stringhe seguenti.  
  
|valore|Description|  
|-----------|-----------------|  
|*Sum*|Per l'aggregazione della misura viene utilizzata la funzione `Sum`.|  
|*Conteggio*|Per l'aggregazione della misura viene utilizzata la funzione `Count`.|  
|*Min*|Per l'aggregazione della misura viene utilizzata la funzione `Min`.|  
|*Max*|Per l'aggregazione della misura viene utilizzata la funzione `Max`.|  
|*DistinctCount*|Per l'aggregazione della misura viene utilizzata la funzione `DistinctCount`.|  
|*Nessuno*|Non viene eseguita alcuna aggregazione della misura.|  
|*AverageOfChildren*|La misura viene aggregata restituendo la media dei relativi membri figlio.|  
|*FirstChild*|La misura viene aggregata restituendone il primo membro figlio.|  
|*LastChild*|La misura viene aggregata restituendone l'ultimo membro figlio.|  
|*FirstNonEmpty*|La misura viene aggregata restituendone il primo membro non vuoto.|  
|*LastNonEmpty*|La misura viene aggregata restituendone l'ultimo membro non vuoto.|  
  
 L'enumerazione che corrisponde ai valori consentiti di `AggregationFunction` nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.AggregationFunction>.  
  
## <a name="see-also"></a>Vedere anche  
 [Account di elemento &#40;ASSL&#41;](../collections/accounts-element-assl.md)   
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  

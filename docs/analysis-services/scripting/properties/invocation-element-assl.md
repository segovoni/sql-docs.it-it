---
title: Elemento Invocation (ASSL) | Documenti Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a6bd0e8f75edf7562a85f670176eb11376900285
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34035702"
---
# <a name="invocation-element-assl"></a>Elemento Invocation (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Specifica come un [azione](../../../analysis-services/scripting/objects/action-element-assl.md) deve essere richiamato.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Action>  
   ...  
   <Invocation>...</Invocation>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*Interattivo*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[Azione](../../../analysis-services/scripting/objects/action-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 La chiamata di un'azione dipende dall'applicazione client. Il **chiamata** elemento suggerisce a un'applicazione client come un'azione deve essere gestita e non indica all'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] come richiamare un'azione.  
  
 Il valore di questo elemento è limitato a una delle stringhe nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|*Interattivo*|Richiamato in modo interattivo dall'utente.|  
|*Su apertura*|Richiamato quando un'applicazione client apre l'oggetto.|  
|*Batch*|Richiamato da un comando dell'elaborazione batch.|  
  
 L'enumerazione che corrisponde ai valori consentiti per **chiamata** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.Action>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

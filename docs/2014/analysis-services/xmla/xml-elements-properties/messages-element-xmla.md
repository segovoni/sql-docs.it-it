---
title: I messaggi di elemento (XMLA) | Microsoft Docs
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
- Messages Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Messages
- microsoft.xml.analysis.messages
- urn:schemas-microsoft-com:xml-analysis#Messages
helpviewer_keywords:
- Messages element
ms.assetid: 719d15ff-f18b-4c56-80ba-a9114c0b7d8a
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a0fbaba30716831ef34a40dd94c6c9b2ab507641
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37176778"
---
# <a name="messages-element-xmla"></a>Elemento Messages (XMLA)
  Contiene una raccolta di [messaggi](message-element-xmla.md) gli elementi restituiti da un'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] da un [Discover](../xml-elements-methods-discover.md) oppure [Execute](../xml-elements-methods-execute.md) (metodo) chiamare.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Resultset>  
   <Messages>  
      <Message>  
   </Messages>  
</Resultset>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Set di risultati](../xml-data-types/resultset-data-type-xmla.md)|  
|Elementi figlio|[Message](message-element-xmla.md)|  
  
## <a name="remarks"></a>Note  
 Questo elemento viene utilizzato nei casi in cui una chiamata al metodo `Discover` o un singolo comando XMLA all'interno di una chiamata al metodo `Execute` viene completato correttamente, ma con errori o avvisi. In questi casi, un `Messages` elemento viene aggiunto per il [radice](root-element-xmla.md) elemento dopo tutti gli altri elementi, che a sua volta contiene uno o più `Message` elementi. Ciascuna `Message` elemento rappresenta un singolo messaggio, un errore o avviso, restituito dalla [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  

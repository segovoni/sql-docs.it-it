---
title: Elemento RequestType (XMLA) | Microsoft Docs
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
- RequestType Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#RequestType
- urn:schemas-microsoft-com:xml-analysis#RequestType
- microsoft.xml.analysis.requesttype
helpviewer_keywords:
- RequestType element
ms.assetid: 54270a57-e327-4233-b4b2-d85b44652ac5
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d73bcac80918bc79064e0b6e1a4eabf315cdcd9a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37171192"
---
# <a name="requesttype-element-xmla"></a>Elemento RequestType (XMLA)
  Determina il tipo di metadati restituiti dai [Discover](../xml-elements-methods-discover.md) (metodo).  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Discover>  
   ...  
   <RequestType>...</RequestType>  
   ...  
</Discover>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|None|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Individuare](../xml-elements-methods-discover.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 L'elemento `RequestType` determina il set di righe dello schema da cui il metodo `Discover` restituisce i dati. Questa enumerazione è limitata ai nomi dei set di righe dello schema supportati dal [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Per altre informazioni sui set di righe dello schema, vedere [rowset dello Schema di Analysis Services](../../schema-rowsets/analysis-services-schema-rowsets.md).  
  
> [!NOTE]  
>  L'elemento `RequestType` enumera solo i nomi del set di righe dello schema. Se viene utilizzato il GUID del set di righe dello schema, si verifica un errore.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  

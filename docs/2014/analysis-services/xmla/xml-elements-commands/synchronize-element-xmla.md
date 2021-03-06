---
title: Elemento Synchronize (XMLA) | Microsoft Docs
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
- Synchronize Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.synchronize
- urn:schemas-microsoft-com:xml-analysis#Synchronize
- http://schemas.microsoft.com/analysisservices/2003/engine#Synchronize
helpviewer_keywords:
- Synchronize command
ms.assetid: 9401323c-feff-409a-a9da-94aee47e0563
caps.latest.revision: 15
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3f88b07721d391c1f834ed93d21039753728081d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37187098"
---
# <a name="synchronize-element-xmla"></a>Elemento Synchronize (XMLA)
  Consente di sincronizzare un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] database con un altro database esistente.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Command>  
   <Synchronize>  
      <Source>...</Source>  
      <SynchronizeSecurity>...</SynchronizeSecurity>  
      <ApplyCompression>...</ApplyCompression>  
      <Locations>...</Locations>  
   </Synchronize>  
</Command>  
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
|Elementi padre|[Command](../xml-elements-properties/command-element-xmla.md)|  
|Elementi figlio|[ApplyCompression](../xml-elements-properties/applycompression-element-xmla.md), [posizioni](../xml-elements-properties/locations-element-xmla.md), [origine](../xml-elements-properties/source-element-synchronize-xmla.md), [SynchronizeSecurity](../xml-elements-properties/security-element-xmla.md)|  
  
## <a name="remarks"></a>Note  
 Il comando `Synchronize` sincronizza il database di destinazione con un'istanza di origine e il database specificato nell'elemento `Source`. Facoltativamente, il comando `Synchronize` sincronizza partizioni remote definite sul database di origine.  
  
 A seconda della modalità di archiviazione utilizzata da oggetti archiviati nel file di backup, il comando `Synchronize` sincronizza le informazioni come elencato nella seguente tabella.  
  
|Modalità di archiviazione|Informazioni|  
|------------------|-----------------|  
|OLAP multidimensionale (MOLAP)|Dati di origine, aggregazioni e metadati|  
|OLAP ibrido (HOLAP)|Aggregazioni e metadati|  
|OLAP relazionale (ROLAP)|Metadati|  
  
 Durante l'esecuzione del comando `Synchronize`, viene inserito un blocco di lettura nel database di origine e un blocco di scrittura nel database di destinazione. Entrambi i blocchi vengono rilasciati dopo il completamento del comando `Synchronize`.  
  
 Per altre informazioni sulla sincronizzazione di database, vedere [backup, ripristino e sincronizzazione di database &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento di backup &#40;XMLA&#41;](backup-element-xmla.md)   
 [Elemento batch &#40;XMLA&#41;](batch-element-xmla.md)   
 [Elemento in parallelo &#40;XMLA&#41;](../xml-elements-properties/parallel-element-xmla.md)   
 [Elemento Restore &#40;XMLA&#41;](restore-element-xmla.md)   
 [I comandi &#40;XMLA&#41;](xml-elements-commands.md)  
  
  

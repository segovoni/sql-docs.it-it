---
title: Valore elemento (XMLA) | Microsoft Docs
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
- Value Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.value
- urn:schemas-microsoft-com:xml-analysis#Value
- http://schemas.microsoft.com/analysisservices/2003/engine#Value
helpviewer_keywords:
- Value element
ms.assetid: f87ca7f8-d9fe-4730-a706-5d50fcfe21df
caps.latest.revision: 14
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8defb7fe2115bd1ea9ccb7b3f23b0717db8b9aef
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37263249"
---
# <a name="value-element-xmla"></a>Elemento Value (XMLA)
  Contiene il valore desiderato di un [attributo](attribute-element-xmla.md) elemento da aggiungere a un [Inserisci](../xml-elements-commands/insert-element-xmla.md) comando, o un [celle](cell-element-xmla.md) elemento deve essere aggiornata da un [UpdateCells](../xml-elements-commands/updatecells-element-xmla.md)comando.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Attribute> <!-- or Cell --!>  
   ...  
   <Value>...</Value>  
   ...  
</Attribute>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Qualsiasi|  
|Valore predefinito|None|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Attributo](attribute-element-xmla.md), [cella](cell-element-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Per gli elementi `Attribute`, l'elemento `Value` contiene il valore desiderato che il membro deve contenere dopo l'esecuzione della commit del comando `Insert`. Per altre informazioni sull'inserimento di membri, vedere [inserimento, aggiornamento ed eliminazione di membri &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md).  
  
 Per gli elementi `Cell`, l'elemento `Value` contiene il valore desiderato che la cella deve contenere dopo l'esecuzione della commit del comando `UpdateCells`. Il valore effettivo archiviato nella tabella writeback per quella cella è la differenza tra il valore originale della cella e il valore desiderato della cella.  
  
 Il tipo di dati utilizzato da questo elemento deve corrispondere al tipo di dati della cella che deve essere aggiornata.  
  
 Per altre informazioni sull'aggiornamento di celle, vedere [Aggiornamento di celle &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/updating-cells-xmla.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento CellOrdinal &#40;XMLA&#41;](cellordinal-element-xmla.md)   
 [Inserire l'elemento &#40;XMLA&#41;](../xml-elements-commands/insert-element-xmla.md)   
 [Elemento UpdateCells &#40;XMLA&#41;](../xml-elements-commands/updatecells-element-xmla.md)   
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  

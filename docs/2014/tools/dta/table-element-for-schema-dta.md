---
title: Elemento di tabella per lo Schema (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Table element [DTA]
ms.assetid: a59e8319-05d1-47f3-af39-7d970ab8e7dc
caps.latest.revision: 13
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f58288d90c1a3158f4757856b51b7374ee07f167
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37187758"
---
# <a name="table-element-for-schema-dta"></a>Elemento Table per Schema (DTA)
  Specifica la tabella per l'ottimizzazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
<Schema>  
...code removed here...  
    <Table>...</Table>  
```  
  
## <a name="element-attributes"></a>Attributi elemento  
  
|attribute|Description|  
|---------------|-----------------|  
|`NumberOfRows`|Facoltativo. Valore intero che consente la simulazione di tabelle di diverse dimensioni.|  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|**Tipo di dati e lunghezza**|**string**, tra 1 e 255 caratteri.|  
|**Valore predefinito**|Nessuna.|  
|**Occorrenza**|Facoltativo. Elenca tutte le tabelle appropriate per il carico di lavoro.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elementi|  
|------------------|--------------|  
|**Elemento padre**|[Elemento schema per il Database &#40;DTA&#41;](schema-element-for-database-dta.md)|  
|**Elementi figlio**|[Nome di elemento per la tabella &#40;DTA&#41;](name-element-for-table-dta.md)|  
  
## <a name="remarks"></a>Note  
 Se non si specifica un elemento `Table`, l'Ottimizzazione guidata motore di database considererà ottimizzabili tutte le tabelle contenute nel database specificato.  
  
## <a name="example"></a>Esempio  
 Per un esempio d'uso, vedere [Elemento Server &#40;DTA&#41;](server-element-dta.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento ai file di input XML &#40;Ottimizzazione guidata motore di database&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  

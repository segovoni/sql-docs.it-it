---
title: Set di righe DISCOVER_SCHEMA_ROWSETS | Microsoft Docs
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
- DISCOVER_SCHEMA_ROWSETS
topic_type:
- apiref
helpviewer_keywords:
- DISCOVER_SCHEMA_ROWSETS rowset
ms.assetid: e5012aa0-6ef8-497f-96c1-2772e2394f62
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fa16f7ff677efd8e39367b9e618bdc95d778b405
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37220241"
---
# <a name="discoverschemarowsets-rowset"></a>Set di righe DISCOVER_SCHEMA_ROWSETS
  Restituisce nomi, restrizioni, descrizione e altre informazioni per tutti i valori di enumerazione ed eventuali valori di enumerazione specifici del provider supportati dal provider [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML for Analysis (XMLA).  
  
 Se si chiama il [Discover](../../xmla/xml-elements-methods-discover.md) metodo con il `DISCOVER_SCHEMA_ROWSETS` il valore di enumerazione nel [RequestType](../../xmla/xml-elements-properties/type-element-xmla.md) elemento, il `Discover` metodo restituisce il `DISCOVER_SCHEMA_ROWSETS` set di righe.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il set di righe DISCOVER_SCHEMA_ROWSETS contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Length|Description|  
|-----------------|--------------------|------------|-----------------|  
|`SchemaName`|`DBTYPE_WSTR`||Nome dello schema o della richiesta. Questa richiesta restituisce i valori nell'enumerazione *RequestTypes* .|  
|`SchemaGuid`|`DBTYPE_GUID`||GUID dello schema.|  
|`Restrictions`|`DBTYPE_HCHAPTER`||Matrice di restrizioni supportate dal provider.|  
|`Description`|`DBTYPE_WSTR`||Descrizione localizzabile dello schema.|  
|`RestrictionsMask`|`DBTYPE_UI8`|||  
  
 Questo set di righe dello schema non è ordinato.  
  
 Per un provider che supporta tre restrizioni per il set di righe dello schema DBSCHEMA_MEMBERS, la matrice `Restrictions` potrebbe restituire il risultato seguente. Gli elementi nel risultato fanno riferimento ai nomi delle colonne nello schema.  
  
```  
<Restrictions>  
      <CATALOG_NAME type="string" />   
      <SCHEMA_NAME type="string" />   
      <CUBE_NAME type="string" />   
</Restrictions>  
```  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il set di righe `DISCOVER_SCHEMA_ROWSETS` può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|`SchemaName`|`DBTYPE_WSTR`||  
  
## <a name="see-also"></a>Vedere anche  
 [XML per set di righe dello schema di analisi](xml-for-analysis-schema-rowsets.md)  
  
  

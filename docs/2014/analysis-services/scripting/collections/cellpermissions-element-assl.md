---
title: Elemento CellPermissions (ASSL) | Microsoft Docs
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
- CellPermissions Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CellPermissions
helpviewer_keywords:
- CellPermissions element
ms.assetid: 4a604f2f-f4c3-42bd-a42b-951263942cc6
caps.latest.revision: 37
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: dafcaf786d58fd8c1441c0f1df50aa5a7d47be31
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37176458"
---
# <a name="cellpermissions-element-assl"></a>Elemento CellPermissions (ASSL)
  Contiene la raccolta di autorizzazioni per le celle nell'oggetto associato [cubo](../objects/cube-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<CubePermission>  
   ...  
   <CellPermissions>  
      <CellPermission>...</CellPermission>  
   </CellPermissions>  
   ...  
</CubePermission>  
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
|Elementi padre|[CubePermission](../objects/cubepermission-element-assl.md)|  
|Elementi figlio|[Elemento CellPermission](../objects/cellpermission-element-assl.md)|  
  
## <a name="remarks"></a>Note  
 La raccolta può contenere fino a un `CellPermission` dell'oggetto per ogni valore di consentito il [accesso](../properties/access-element-assl.md) elemento.  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.CellPermissionCollection>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipo di dati Permission &#40;ASSL&#41;](../data-type/permission-data-type-assl.md)   
 [Le raccolte &#40;ASSL&#41;](collections-assl.md)  
  
  

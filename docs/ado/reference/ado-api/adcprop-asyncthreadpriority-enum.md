---
title: ADCPROP_ASYNCTHREADPRIORITY_ENUM | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADCPROP_ASYNCTHREADPRIORITY_ENUM
helpviewer_keywords:
- ADCPROP_ASYNCTHREADPRIORITY_ENUM [ADO]
ms.assetid: f0965617-17d8-41e0-98d0-f824274735a6
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7857e3b176191ba5b9c98a40c7f02abe666edec8
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35275230"
---
# <a name="adcpropasyncthreadpriorityenum"></a>ADCPROP_ASYNCTHREADPRIORITY_ENUM
Per un servizio dati di riferimento [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) dell'oggetto, specifica la priorità di esecuzione del thread asincrona che recupera i dati.  
  
 Utilizzare queste costanti con il **Recordset** "**priorità di Thread in Background**" proprietà dinamiche, che viene fatto riferimento nell'indice per ADO, OLE DB di proprietà dinamiche e documentata nel [ Servizio di cursore per OLE DB](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) documentazione.  
  
|Costante|valore|Description|  
|--------------|-----------|-----------------|  
|**adPriorityAboveNormal**|4|Imposta la priorità tra normale e massimo.|  
|**adPriorityBelowNormal**|2|Imposta la priorità tra più basso e normale.|  
|**adPriorityHighest**|5|Imposta la priorità più elevata possibile.|  
|**AdPriorityLowest**|1|Imposta la priorità sul livello minimo.|  
|**adPriorityNormal**|3|Imposta la priorità normale.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Package: **com.ms.wfc.data**  
  
|Costante|  
|--------------|  
|AdoEnums.AdcPropAsyncThreadPriority.ABOVENORMAL|  
|AdoEnums.AdcPropAsyncThreadPriority.BELOWNORMAL|  
|AdoEnums.AdcPropAsyncThreadPriority.HIGHEST|  
|AdoEnums.AdcPropAsyncThreadPriority.LOWEST|  
|AdoEnums.AdcPropAsyncThreadPriority.NORMAL|

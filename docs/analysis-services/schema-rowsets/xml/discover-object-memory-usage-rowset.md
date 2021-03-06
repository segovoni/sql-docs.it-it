---
title: Set di righe DISCOVER_OBJECT_MEMORY_USAGE | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 70a316189077598ee275074394a499d253fe2188
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34030482"
---
# <a name="discoverobjectmemoryusage-rowset"></a>Set di righe DISCOVER_OBJECT_MEMORY_USAGE
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Fornisce informazioni sulle risorse di memoria utilizzate dagli oggetti.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **DISCOVER_OBJECT_MEMORY_USAGE** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Lunghezza|Description|  
|-----------------|--------------------|------------|-----------------|  
|**OBJECT_PARENT_PATH**|**DBTYPE_WSTR**||Percorso dell'elemento padre dell'oggetto corrente.|  
|**OBJECT_ID**|**DBTYPE_WSTR**||ID dell'oggetto come definito in fase di creazione.|  
|**OBJECT_MEMORY_SHRINKABLE**|**DBTYPE_I8**||Quantità totale di memoria (byte) utilizzata da tutti gli oggetti compattabili posseduti direttamente dall'oggetto corrente. Il valore corrente non include la memoria utilizzata da oggetti posseduti da oggetti denominati di proprietà dell'oggetto corrente.|  
|**OBJECT_MEMORY_NONSHRINKABLE**|**DBTYPE_I8**||Quantità totale di memoria (byte) di tutti gli oggetti non compattabili posseduti direttamente dall'oggetto corrente. Il valore corrente non include la memoria utilizzata da oggetti posseduti da oggetti denominati di proprietà dell'oggetto corrente.|  
|**OBJECT_VERSION**|**DBTYPE_I4**||Numero di versione dei metadati dell'oggetto. Questo numero cambia ad ogni modifica dell'oggetto.|  
|**OBJECT_DATA_VERSION**|**DBTYPE_I4**||Numero di derivazione dei dati nell'oggetto. Questo numero aumenta ad ogni elaborazione dell'oggetto.|  
|**OBJECT_TYPE_ID**|**DBTYPE_I4**||Riservato per utilizzo interno.|  
|**OBJECT_TIME_CREATED**|**DBTYPE_DBTIMESTAMP**||L'ora UTC del server al momento della creazione dell'oggetto.|  
  
 Questo set di righe dello schema non è ordinato.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il **DISCOVER_OBJECT_MEMORY_USAGE** righe può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|**OBJECT_PARENT_PATH**|**DBTYPE_WSTR**|Facoltativa.|  
|**OBJECT_ID**|**DBTYPE_WSTR**|Facoltativo|  
  
## <a name="see-also"></a>Vedere anche  
 [XML for Analysis i rowset dello Schema](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  

---
title: Le proprietà del modello di data mining | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], properties
- data mining [Analysis Services], properties
- columns [data mining], properties
- Data Mining Designer
- properties [data mining]
ms.assetid: c5194619-8b31-42be-a95f-585711462945
caps.latest.revision: 31
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 731ce6e077040767fd5f1bd4eec05242977097a8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37330901"
---
# <a name="mining-model-properties"></a>Proprietà dei modelli di data mining
  I modelli di data mining dispongono dei tipi seguenti di proprietà:  
  
-   Proprietà ereditate dalla struttura di data mining tramite cui vengono definiti il tipo di dati e il tipo di contenuto dei dati utilizzati dal modello  
  
-   Proprietà correlate all'algoritmo utilizzato per creare il modello di data mining, inclusi eventuali parametri del cliente  
  
-   Proprietà che definiscono un filtro sul modello utilizzato per eseguire il training del modello.  
  
 Le proprietà di un modello di data mining vengono definite inizialmente quando si crea il modello; è tuttavia possibile modificare la maggior parte delle proprietà in un secondo momento, inclusi i parametri dell'algoritmo, i filtri e le proprietà di utilizzo delle colonne. Tramite la scheda **Modelli di data mining** di Progettazione modelli di data mining, AMO o XMLA è possibile modificare le proprietà dei modelli di data mining.  
  
 Quando si modifica qualsiasi proprietà di un modello, è necessario rielaborare quest'ultimo in modo che vi vengano implementate le modifiche. La rielaborazione è necessaria anche se la modifica riguarda solo i metadati, ad esempio l'aggiunta di un alias o di una descrizione di colonna.  
  
## <a name="properties-of-models"></a>Proprietà dei modelli  
 Nella tabella seguente vengono descritte le proprietà specifiche dei modelli di data mining. Esistono inoltre proprietà che è possibile impostare su singole colonne di data mining  
  
|Proprietà|Description|  
|--------------|-----------------|  
|**Algoritmo**|Imposta il tipo di algoritmo per il modello di data mining.|  
|**AlgorithmParameters**|Imposta i valori dei parametri di algoritmo disponibili per ogni tipo di algoritmo.|  
|**Filter**|Imposta un filtro che viene applicato ai dati utilizzati per il training e il test del modello di data mining. La definizione del filtro è archiviata con il modello e può essere utilizzata facoltativamente quando si creano query di stima oppure per testare l'accuratezza del modello.<br /><br /> Il filtro del modello non è facoltativo quando si esegue il training del modello.|  
|**Nome**|Imposta il nome del modello di data mining.|  
|**AllowDrillThrough**|Specifica se nel modello di data mining è consentito il drill-through.|  
  
## <a name="properties-of-model-columns"></a>Proprietà delle colonne del modello  
 È possibile impostare le proprietà specifiche del data mining elencate di seguito per ogni colonna di un modello di data mining. Le proprietà possono essere impostate su un valore diverso per ogni modello di data mining di una struttura di data mining.  
  
|Proprietà|Description|  
|--------------|-----------------|  
|**Descrizione**|Viene descritto lo scopo della colonna di data mining.|  
|**Nome**|Imposta il nome della colonna del modello di data mining. È possibile digitare un nuovo nome per fornire un alias per la colonna del modello di data mining.|  
|**ModelingFlags**|Imposta i flag specifici dell'algoritmo per la colonna.|  
|**SourceColumnID**|Indica il nome della colonna della struttura di data mining su cui si basa la colonna del modello.<br /><br /> Questa proprietà è di sola lettura.|  
|**Usage**|Imposta la modalità di utilizzo della colonna nel modello di data mining.|  
  
## <a name="see-also"></a>Vedere anche  
 [Colonne del modello di data mining](mining-model-columns.md)   
 [Strutture di data mining &#40;Analysis Services - Data Mining&#41;](mining-structures-analysis-services-data-mining.md)   
 [Procedure dettagliate e le attività del modello di data mining](mining-model-tasks-and-how-tos.md)   
 [Modificare le proprietà di un modello di Data Mining](change-the-properties-of-a-mining-model.md)   
 [Strumenti di Data Mining](data-mining-tools.md)   
 [Creare una struttura di Data Mining relazionale](create-a-relational-mining-structure.md)   
 [Creare un alias per una colonna di un modello](create-an-alias-for-a-model-column.md)  
  
  

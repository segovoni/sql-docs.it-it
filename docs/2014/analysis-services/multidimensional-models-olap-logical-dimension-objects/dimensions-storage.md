---
title: Dimensione di archiviazione | Microsoft Docs
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
helpviewer_keywords:
- dimensions [Analysis Services], storage
- storing data [Analysis Services]
- storage [Analysis Services], dimensions
- relational OLAP
- multidimensional OLAP
- MOLAP
- storing data [Analysis Services], dimensions
- ROLAP
ms.assetid: 8d74b932-2174-4e1f-8414-636455880b6a
caps.latest.revision: 30
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6462ebf90b7783260f7027d82b26be117ea0b5ce
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37153112"
---
# <a name="dimension-storage"></a>Archiviazione di dimensioni
  Dimensioni nel [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] supportano due modalità di archiviazione:  
  
-   OLAP relazionale (ROLAP)  
  
-   OLAP multidimensionale (MOLAP)  
  
 La modalità di archiviazione determina la posizione e la forma dei dati di una dimensione. MOLAP è la modalità di archiviazione predefinita per le dimensioni. **Argomenti correlati:**[elaborazione e modalità di archiviazione delle partizioni](../multidimensional-models-olap-logical-cube-objects/partitions-partition-storage-modes-and-processing.md)  
  
## <a name="molap"></a>MOLAP  
 I dati per una dimensione che utilizza la modalità MOLAP vengono archiviati in una struttura multidimensionale nell'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Tale struttura multidimensionale viene creata e popolata durante l'elaborazione della dimensione. Le dimensioni MOLAP garantiscono prestazioni di esecuzione delle query migliori rispetto alle dimensioni ROLAP.  
  
## <a name="rolap"></a>ROLAP  
 I dati per una dimensione che utilizza la modalità ROLAP vengono effettivamente archiviati nelle tabelle utilizzate per definire la dimensione. La modalità ROLAP può essere utilizzata per supportare dimensioni grandi senza duplicare quantità di dati elevate, a spese, però, delle prestazioni di esecuzione delle query. Poiché la dimensione si basa direttamente sulle tabelle della vista origine dati utilizzata per definire la dimensione, la modalità di archiviazione ROLAP supporta inoltre l'elaborazione OLAP in tempo reale.  
  
> [!IMPORTANT]  
>  Se una dimensione utilizza la modalità di archiviazione ROLAP ed è inclusa in un cubo che utilizza l'archiviazione MOLAP, qualsiasi modifica dello schema nella tabella di origine deve essere seguita dall'immediata elaborazione della dimensione. In caso contrario, i risultati delle query eseguite sui cubi potrebbero essere inconsistenti. **Argomento correlato:**[automatizzare Analysis Services le attività amministrative con SSIS](../instances/automate-analysis-services-administrative-tasks-with-ssis.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Elaborazione e modalità di archiviazione delle partizioni](../multidimensional-models-olap-logical-cube-objects/partitions-partition-storage-modes-and-processing.md)  
  
  

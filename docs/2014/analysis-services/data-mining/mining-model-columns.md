---
title: Colonne del modello di data mining | Microsoft Docs
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
- columns [data mining], mining model columns
- columns [data mining]
- REGRESSOR column
- columns [data mining], modeling flags
- modeling flags [data mining]
- MODEL_EXISTENCE_ONLY column
- usage property [data mining]
ms.assetid: fab47643-5bfd-424e-a0f7-69e665db6bab
caps.latest.revision: 38
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6067f165746f653819655063b9eb6798f23d3dc3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37326853"
---
# <a name="mining-model-columns"></a>Colonne del modello di data mining
  Un modello di data mining applica un algoritmo specifico ai dati rappresentati da una struttura di data mining. Analogamente alla struttura, il modello di data mining contiene colonne. Un modello di data mining è contenuto all'interno della struttura di data mining ed eredita tutti i valori delle proprietà definite dalla struttura. Nel modello possono essere utilizzate tutte le colonne contenute nella struttura di data mining o un subset delle colonne.  
  
 In una colonna di un modello di data mining è possibile definire due informazioni aggiuntive, cioè utilizzo e flag di modellazione.  
  
-   **Usage** è una proprietà che definisce il modo in cui il modello usa la colonna. Le colonne possono essere utilizzate come colonne di input, colonne chiave o colonne stimabili.  
  
-   I**flag di modellazione** offrono all'algoritmo altre informazioni sui dati definiti nella tabella del case per consentire la compilazione di un modello più preciso. È possibile definire flag di modellazione a livello di programmazione usando il linguaggio DMX (Data Mining Extensions) o tramite **Progettazione modelli di data mining** in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 Nell'elenco seguente vengono descritti i flag di modellazione che è possibile definire in una colonna di un modello di data mining.  
  
 `MODEL_EXISTENCE_ONLY`  
 Indica che la presenza dell'attributo è più importante rispetto ai valori nella colonna attributo. Si consideri, ad esempio, una tabella del case contenente un elenco di elementi ordinati associati a un cliente specifico. I dati della tabella includono tipo di prodotto, ID e costo di ogni elemento. Ai fini della modellazione, il fatto che il cliente abbia acquistato un determinato articolo potrebbe essere più importante rispetto al costo dell'articolo stesso. In questo caso, la colonna relativa al costo dovrebbe venire contrassegnata come `MODEL_EXISTENCE_ONLY`.  
  
 `REGRESSOR`  
 Indica che l'algoritmo può utilizzare la colonna specificata nella formula di regressione degli algoritmi di regressione. Questo flag è supportato dagli algoritmi [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees e [!INCLUDE[msCoName](../../includes/msconame-md.md)] Time Series.  
  
 Per altre informazioni sull'impostazione della proprietà di utilizzo e sulla definizione di flag di modellazione a livello di programmazione tramite DMX, vedere [CREATE MINING MODEL &#40;DMX&#41;](/sql/dmx/create-mining-model-dmx). Per altre informazioni sull'impostazione della proprietà di utilizzo e sulla definizione di flag di modellazione in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], vedere [Spostamento di oggetti di data mining](moving-data-mining-objects.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Algoritmi di Data Mining &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md)   
 [Strutture di data mining &#40;Analysis Services - Data Mining&#41;](mining-structures-analysis-services-data-mining.md)   
 [Modificare le proprietà di un modello di Data Mining](change-the-properties-of-a-mining-model.md)   
 [Escludere una colonna da un modello di Data Mining](exclude-a-column-from-a-mining-model.md)   
 [Colonne della struttura di data mining](mining-structure-columns.md)  
  
  

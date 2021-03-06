---
title: Calcoli (SSAS tabulare) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 738816e3-0e1d-44a5-8d1b-81068dce8ac0
caps.latest.revision: 18
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0628ad4360199ac1710ac9669e27c214287a0e9c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37261364"
---
# <a name="calculations-ssas-tabular"></a>Calcoli (SSAS tabulare)
  Dopo aver importato dati nel modello, è possibile aggiungere calcoli per aggregare, filtrare, estendere, combinare e proteggere tali dati. Nei modelli tabulari viene utilizzato DAX (Data Analysis Expressions), un linguaggio delle formule per la creazione di calcoli personalizzati. In un modello tabulare, i calcoli che vengono creati tramite formule DAX vengono usati in *Colonne calcolate*, *Misure*e *Filtri di riga*.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[La comprensione di DAX nei modelli tabulari di &#40;tabulare di SSAS&#41;](understanding-dax-in-tabular-models-ssas-tabular.md)|Viene descritto il linguaggio delle formule Data Analysis Expressions (DAX) utilizzato per creare calcoli per colonne calcolate, misure e filtri di riga nei modelli tabulari.|  
|[Compatibilità delle formule nella modalità DirectQuery](../dax-formula-compatibility-in-directquery-mode-ssas-2014.md)|Vengono descritte le differenze e vengono elencate le funzioni non supportate nella modalità DirectQuery e quelle supportate, ma che potrebbero restituire risultati diversi.|  
|[Data Analysis Expressions &#40;DAX&#41; riferimento](https://msdn.microsoft.com/library/gg413422(v=sql.120).aspx)|In questa sezione vengono fornite descrizioni dettagliate della sintassi, degli operatori e delle funzioni DAX.|  
  
> [!NOTE]  
>  In questa sezione non vengono fornite attività dettagliate per la creazione dei calcoli. Poiché i calcoli vengono specificati in colonne calcolate, misure e filtri di riga (nei ruoli), le istruzioni sulla posizione in cui creare formule DAX vengono fornite nelle attività correlate a tali funzionalità. Per altre informazioni, vedere [Creare una colonna calcolata &#40;SSAS tabulare&#41;](ssas-calculated-columns-create-a-calculated-column.md), [Creare e gestire misure &#40;SSAS tabulare&#41;](measures-ssas-tabular.md), e [Creare e gestire ruoli &#40;SSAS tabulare&#41;](roles-ssas-tabular.md).  
  
> [!NOTE]  
>  Mentre DAX può essere utilizzato anche per eseguire query su un modello tabulare, gli argomenti in questa sezione riguardano in particolare l'utilizzo di formule DAX per creare calcoli.  
  
  

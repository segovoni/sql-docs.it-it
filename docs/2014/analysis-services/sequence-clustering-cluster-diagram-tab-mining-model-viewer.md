---
title: Sequence Clustering scheda diagramma dei Cluster (Visualizzatore modello di Data Mining | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.sequenceclustering.diagrams.f1
ms.assetid: 4b705397-9af4-4678-9eda-149bc5d762fa
caps.latest.revision: 26
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 862dca35dcec3c1113117cf472b3866fb9df0be3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37257243"
---
# <a name="sequence-clustering-cluster-diagram-tab-mining-model-viewer"></a>Scheda Diagramma dei cluster in Sequence Clustering (Visualizzatore modello di data mining)
  La scheda **Diagramma dei cluster** in **Visualizzatore Microsoft Sequence Clustering** consente di visualizzare graficamente tutti i cluster contenuti nel modello Sequence Clustering.  
  
 Utilizzare questa vista di un modello Sequence Clustering per eseguire il drill-through da ogni cluster nei case di supporto, se il drill-through è stato abilitato. È anche possibile assegnare nomi descrittivi ai cluster e modificare la variabile ombreggiatura per valutare immediatamente la distribuzione di valori  
  
 **Per altre informazioni:** [Algoritmo Microsoft Sequence Clustering](data-mining/microsoft-sequence-clustering-algorithm.md), [Visualizzare un modello utilizzando il Visualizzatore Microsoft Sequence Clustering](data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)  
  
## <a name="options"></a>Opzioni  
 **Aggiorna contenuto visualizzatore**  
 Consente di ricaricare il modello di data mining nel visualizzatore.  
  
 **Modello di data mining**  
 Fare clic su un modello di data mining da visualizzare contenuto nella struttura di data mining corrente. Il modello di data mining verrà aperto nel visualizzatore associato.  
  
 **Visualizzatore**  
 Consente di scegliere un visualizzatore da utilizzare per l'esplorazione del modello di data mining selezionato. È possibile utilizzare il visualizzatore personalizzato o **Microsoft Generic Content Tree Viewer**. Se disponibili, è anche possibile utilizzare i visualizzatori plug-in.  
  
 **Eseguire lo zoom avanti**  
 Consente di eseguire lo zoom avanti del diagramma per ottenere una vista più dettagliata dei cluster.  
  
 **Eseguire lo zoom indietro**  
 Consente di eseguire lo zoom indietro del diagramma per vedere tutti i cluster nel modello.  
  
 **Copia parte visibile del grafico**  
 Consente di copiare la sezione visibile del diagramma negli Appunti.  
  
 **Copia grafico intero**  
 Consente di copiare tutto il diagramma negli Appunti.  
  
 **Scalabilità adatta il diagramma alla finestra**  
 Consente di eseguire lo zoom indietro del diagramma finché l'intero diagramma non si adatta alla schermata.  
  
 **Trovare il nodo**  
 Usare la finestra di dialogo **Trova nodo** per filtrare i cluster nel grafico e trovare più facilmente un cluster specifico. Per altre informazioni, vedere [Finestra di dialogo Trova nodo &#40;Visualizzatore modello di data mining&#41;](find-node-dialog-box-mining-model-viewer.md).  
  
 Si noti che in questo contesto viene eseguita solo la ricerca del nome del cluster, non degli attributi presenti all'interno; pertanto, questa opzione è più utile se sono stati assegnati nomi descrittivi al cluster. È possibile assegnare nomi ai cluster nel visualizzatore facendo clic con il pulsante destro del mouse su ogni cluster e selezionando **Rinomina**.  
  
 **Migliora Layout**  
 Consente di riordinare i cluster nel diagramma per migliorarne il layout.  
  
 **Density**  
 L'aspetto del grafico a barre della densità e i relativi valori dipendono dall'attributo selezionato in **Variabile ombreggiatura**.  
  
-   Se non è stato selezionato alcun stato dell'attributo come variabile ombreggiatura, per impostazione predefinita, l'ombreggiatura della densità applicata a ogni cluster rappresenta il supporto per il cluster, rispetto al popolamento complessivo di case.  
  
-   Quando si seleziona un attributo per **Variabile ombreggiatura**, è necessario selezionare anche un valore per **State** . In tal modo, il grafico a barre di densità viene aggiornato per mostrare la probabilità di questo stato. È possibile posizionare il mouse su qualsiasi singolo cluster per vedere la probabilità dello stato selezionato per il cluster.  
  
 **Variabile ombreggiatura**  
 Consente di selezionare un attributo dal modello di data mining da utilizzare per l'ombreggiatura del diagramma del cluster.  
  
 **State**  
 Consente di selezionare uno stato che corrisponde a **Variabile ombreggiatura**. Ad esempio, per visualizzare le sequenze in cui è incluso un particolare prodotto, è necessario selezionare la colonna [Product] come attributo per **Variabile ombreggiatura**e il nome di prodotto specifico come valore **State** .  
  
 **Collegamenti**  
 Le righe del diagramma indicano le associazioni tra i cluster di sequenza. È possibile modificare il numero di collegamenti mostrati dal visualizzatore regolando il dispositivo di scorrimento a destra dei cluster. Se si sposta il dispositivo di scorrimento verso il basso, vengono visualizzati solo i collegamenti più attendibili.  
  
## <a name="see-also"></a>Vedere anche  
 [Algoritmi di Data Mining &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Visualizzatori modello di data mining &#40;Progettazione modelli di Data Mining&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Visualizzatori modello di data mining](data-mining/data-mining-model-viewers.md)  
  
  

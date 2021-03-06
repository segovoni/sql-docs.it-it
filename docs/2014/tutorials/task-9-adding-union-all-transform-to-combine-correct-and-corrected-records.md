---
title: 'Attività 9: Aggiunta di Union All Trasforma per combina record corretti e con correzione | Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 24ba466d-a7d3-49e7-9111-b348399c9e58
caps.latest.revision: 7
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 76e76290206dd1618b37865f95ca17709faf2a6c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37220541"
---
# <a name="task-9-adding-union-all-transform-to-combine-correct-and-corrected-records"></a>Attività 9: Aggiunta della trasformazione Unione input multipli a Combina record corretti e con correzione
  In questa attività viene aggiunta la trasformazione Unione input multipli al flusso di dati. La trasformazione Unione input multipli consente di combinare più input in un unico output. Nello scenario attuale i record corretti e con correzione vengono combinati in un flusso.  
  
1.  Funzionalità di trascinamento **unione input multipli** trasformare dalla **comuni** sezione del **casella degli strumenti SSIS** per il **del flusso di dati** scheda e inserirlo sotto **Seleziona record corretti e**.  
  
2.  Fare doppio clic su **unione input multipli** trasformare nel **flusso di dati** scheda, quindi scegliere **rinominare**. Tipo di **combina record corretti e**, quindi premere **invio**.  
  
     ![Combina corretti e con correzione Reocrds](../../2014/tutorials/media/et-addinguattocombinecacrecords-01.jpg "combinare Reocrds corretti e con correzione")  
  
3.  Connettere **Seleziona record corretti e** al **combina record corretti e** nel **del flusso di dati** scheda usando il collegamento blu. Dovrebbero vedere le **selezione Input e Output** nella finestra di dialogo.  
  
4.  Nel **interdipendenze** finestra di dialogo **correggere** per **Output** e fare clic su **OK**.  
  
     ![Finestra di dialogo di selezione di Output di input](../../2014/tutorials/media/et-addinguattocombinecacrecords-02.jpg "Output finestra di dialogo di selezione di Input")  
  
5.  Spostare il connettore intitolato **corretti** a sinistra trascinando e rilasciando il punto alla fine del connettore a sinistra.  
  
     ![Connetti Correggi a combina corretto e con correzione](../../2014/tutorials/media/et-addinguattocombinecacrecords-03.jpg "Connetti Correggi a combina corretto e con correzione")  
  
6.  Se si seleziona **Seleziona record corretti e** trasformazione, si dovrebbe vedere un altro collegamento blu. Blu in trascinare **combina record corretti e**.  
  
     ![Connetti con correzione a combina corretto e con correzione](../../2014/tutorials/media/et-addinguattocombinecacrecords-04.jpg "Connetti con correzione a combina corretto e con correzione")  
  
7.  Ciò **connector** deve essere denominato **con correzione**. Poiché si hanno solo due condizioni **corretti** e **con correzione**, e una condizione è già stata utilizzata, il **selezione Input e Output** finestra di dialogo non viene visualizzata questa volta. Se i collegamenti si sovrappongono, spostarne uno a sinistra e l'altro a destra trascinando il collegamento a sinistra o a destra.  
  
## <a name="next-step"></a>Passaggio successivo  
 [Attività 10: Aggiunta della trasformazione Raggruppamento fuzzy per l'identificazione di duplicati](../../2014/tutorials/task-10-adding-fuzzy-group-transform-to-identify-duplicates.md)  
  
  

---
title: Modifica ed elaborazione del modello Market Basket (esercitazione intermedia di Data Mining) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b6019413-aebd-4ff7-831a-644572ad88b1
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f1f0fe6899be3f9828a8ba9d91f2c9abf7ba48b6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37246121"
---
# <a name="modifying-and-processing-the-market-basket-model-intermediate-data-mining-tutorial"></a>Modifica ed elaborazione del modello Market Basket (Esercitazione intermedia sul data mining)
  Prima di elaborare il modello di data mining di associazione creato, è necessario modificare i valori predefiniti di due parametri: *supporto tecnico* e *probabilità*.  
  
-   *Supporto* definisce la percentuale di case in cui una regola deve esistere prima che venga considerato valido. Sarà necessario specificare che la regola deve essere presente almeno nell'1% dei case.  
  
-   *Probabilità* definisce come è probabilmente un'associazione deve essere prima che venga considerato valido. Verrà presa in considerazione ogni associazione con almeno il 10% di probabilità.  
  
 Per altre informazioni sugli effetti di aumento o riduzione di supporto e probabilità, vedere [riferimento tecnico di Microsoft Association Rules algoritmo](../../2014/analysis-services/data-mining/microsoft-association-algorithm-technical-reference.md).  
  
 Dopo aver definito la struttura e parametri per il **Association** modello di data mining, verranno elaborati il modello.  
  
### <a name="to-adjust-the-parameters-of-the-association-model"></a>Per adattare i parametri del modello Association  
  
1.  Aprire il **modelli di Data Mining** scheda della finestra di progettazione modelli di Data Mining.  
  
2.  Fare doppio clic il **Association** colonna della griglia nella finestra di progettazione e selezionare **imposta parametri algoritmo per aprire i parametri dell'algoritmo** nella finestra di dialogo.  
  
3.  Nel **valore** colonna del **i parametri dell'algoritmo** dialogo casella, impostare i parametri seguenti:  
  
     MINIMUM_PROBABILITY = 0,1  
  
     MINIMUM_SUPPORT = 0,01  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-process-the-mining-model"></a>Per elaborare il modello di data mining  
  
1.  Nel **modello di Data Mining** dal menu del [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], selezionare **Elabora struttura di Data Mining e tutti i modelli.**  
  
2.  Nella finestra di avviso che chiede se si desidera compilare e distribuire il progetto, fare clic su **Sì**.  
  
     Il **Elabora struttura di Data Mining - Association** verrà visualizzata la finestra di dialogo.  
  
3.  Fare clic su **Esegui**.  
  
     Il **stato elaborazione** verrà visualizzata la finestra di dialogo per visualizzare le informazioni sull'elaborazione di modelli. L'elaborazione della nuova struttura e del nuovo modello potrebbe richiedere tempo.  
  
4.  Al termine dell'elaborazione, fare clic su **Close** per chiudere il **stato elaborazione** nella finestra di dialogo.  
  
5.  Fare clic su **Close** per uscire dalle **Elabora struttura di Data Mining - Association** nella finestra di dialogo.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
 [Esplorazione dei modelli Market Basket &#40;esercitazione intermedia sul Data Mining&#41;](../../2014/tutorials/exploring-the-market-basket-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Requisiti e considerazioni sull'elaborazione &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  

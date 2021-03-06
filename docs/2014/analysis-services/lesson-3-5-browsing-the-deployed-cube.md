---
title: Esplorazione del cubo distribuito | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 849c6109-1453-4fe4-a892-c49a982cfadb
caps.latest.revision: 23
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 96480e0303dbb3176ea9fd17b14536e84d9006c2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37253403"
---
# <a name="browsing-the-deployed-cube"></a>Esplorazione di un cubo distribuito
  Nell'attività seguente si esplorerà il cubo [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial. Poiché l'analisi confronta la misura in più dimensioni, verrà utilizzata una tabella pivot di Excel per esplorare i dati. L'utilizzo di una tabella pivot consente di posizionare cliente, data e informazioni sul prodotto su diversi assi in modo da potere visualizzare come cambia Internet Sales quando viene visualizzato in periodi di tempo, dati demografici del cliente e linee di prodotti specifici.  
  
### <a name="to-browse-the-deployed-cube"></a>Per esplorare il cubo distribuito  
  
1.  Per passare a Progettazione cubi in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], fare doppio clic sul cubo **[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial** nella cartella **Cubi** di Esplora soluzioni.  
  
2.  Aprire la scheda **Esplorazione** , quindi fare clic sul pulsante **Riconnetti** nella barra degli strumenti della finestra di progettazione.  
  
3.  Fare clic sull'icona Excel per avviare Excel utilizzando il database dell'area di lavoro come origine dati. Quando viene richiesto di abilitare le connessioni, fare clic su **Abilita**.  
  
4.  Nell'elenco di campi della tabella pivot espandere **Internet Sales**, quindi trascinare la misura **Sales Amount** nell'area **Valori** .  
  
5.  Nell'elenco di campi della tabella pivot espandere **Product**.  
  
6.  Trascinare la gerarchia utente **Product Model Lines** nell'area **Colonne** .  
  
7.  Nell'elenco di campi della tabella pivot espandere **Customer**e **Location**, quindi trascinare la gerarchia **Customer Geography** dalla cartella di visualizzazione Location della dimensione Customer all'area **Righe** .  
  
8.  Nell'elenco di campi della tabella pivot espandere **Order Date**, quindi trascinare la gerarchia **Order Date.Calendar Date** nell'area **Filtro report** .  
  
9. Fare clic sulla freccia a destra del filtro **Order Date.Calendar Date** nel riquadro Dati, deselezionare la casella di controllo relativa al livello **(Totale)** , espandere **2006**, **H1 CY 2006**e **Q1 CY 2006**, selezionare la casella di controllo relativa a **February 2006**e quindi fare clic su **OK**.  
  
     Verranno visualizzate le vendite realizzate nel mese di febbraio 2006 tramite Internet in base alla regione e alla linea di prodotti, come illustrato nella figura seguente.  
  
     ![Vendite Internet per regione e linea di prodotti](../../2014/tutorials/media/l3-cube-browser-finish.gif "vendite Internet per regione e linea di prodotti")  
  
## <a name="next-lesson"></a>Lezione successiva  
 [Lezione 4: Definizione di attributo avanzato e proprietà dimensione](../analysis-services/lesson-4-defining-advanced-attribute-and-dimension-properties.md)  
  
  

---
title: 'Analysis Services tutorial-lezione 12: analizzare in Excel | Microsoft Docs'
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d215045f87ed780a4adc97f9ae4fed9ac7e6991a
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38015996"
---
# <a name="analyze-in-excel"></a>Analizza in Excel

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

In questa lezione si userà l'analizza nella funzionalità di Excel per aprire Microsoft Excel, creare automaticamente una connessione all'area di lavoro modello e aggiungere automaticamente una tabella pivot al foglio di lavoro. La funzionalità Analizza in Excel offre un metodo rapido e semplice per testare l'efficacia della progettazione del modello prima di distribuirlo. In questa lezione non si esegue alcuna analisi dei dati. Lo scopo di questa lezione è acquisire familiarità con gli strumenti che è possibile utilizzare per testare la progettazione del modello.   
  
Per completare questa lezione, è necessario che Excel sia installato nello stesso computer di Visual Studio.
  
Tempo stimato per il completamento della lezione: **5 minuti**  
  
## <a name="prerequisites"></a>Prerequisiti  

Questo articolo fa parte di un'esercitazione di modellazione tabulare, che deve essere completata nell'ordine. Prima di eseguire le attività in questa lezione, è necessario avere completato la lezione precedente: [lezione 11: creare ruoli](../tutorial-tabular-1400/as-lesson-11-create-roles.md).  
  
## <a name="browse-using-the-default-and-internet-sales-perspectives"></a>Sfogliare il modello utilizzando la prospettiva predefinita e la prospettiva Internet Sales  

In queste prime attività, esplorare il modello usando la prospettiva predefinita, che include tutti gli oggetti modello, e anche tramite la prospettiva Internet Sales è in precedenza. La prospettiva Internet Sales esclude l'oggetto Customer table.  
  
#### <a name="to-browse-by-using-the-default-perspective"></a>Per sfogliare il modello tramite la prospettiva predefinita  
  
1.  Scegliere il **Model** menu > **analizza in Excel**.  
  
2.  Nella finestra di dialogo **Analizza in Excel** fare clic su **OK**.  
  
    Verrà visualizzata la finestra di Excel con una nuova cartella di lavoro. Viene creata una connessione all'origine dati utilizzando l'account utente corrente e la prospettiva predefinita viene utilizzata per definire campi visualizzabili. Una tabella pivot viene aggiunta automaticamente al foglio di lavoro.  
  
3.  In Excel, nelle **elenco campi tabella pivot**, si noti il **DimDate** e **FactInternetSales** vengono visualizzati i gruppi di misure. Il **DimCustomer**, **DimDate**, **DimGeography**, **DimProduct**, **DimProductCategory**, **DimProductSubcategory**, e **FactInternetSales** vengono visualizzate anche le tabelle con le rispettive colonne.  
  
4.  Chiudere Excel senza salvare la cartella di lavoro.  
  
#### <a name="to-browse-by-using-the-internet-sales-perspective"></a>Per sfogliare il modello tramite la prospettiva Internet Sales  
  
1.  Scegliere il **Model** menu e quindi fare clic su **analizza in Excel**.  
  
2.  Nella finestra di dialogo **Analizza in Excel** lasciare selezionata l'opzione **Utente di Windows corrente** , quindi nell'elenco a discesa **Prospettiva** selezionare **Internet Sales**e fare clic su **OK**. 
    
    ![as-lesson12-perspective](../tutorial-tabular-1400/media/as-lesson12-perspective.png)
    
3.  In Excel, in **PivotTable Fields**, notare che la tabella DimCustomer è esclusa dall'elenco dei campi.  
    
    ![campi come lesson12](../tutorial-tabular-1400/media/as-lesson12-fields.png)
    
4.  Chiudere Excel senza salvare la cartella di lavoro.  
  
## <a name="browse-by-using-roles"></a>Sfoglia tramite i ruoli  

I ruoli sono una parte importante di qualsiasi modello tabulare. Senza almeno un ruolo a cui gli utenti vengono aggiunti come membri, gli utenti non possono accedere e analizzare i dati usando il modello. La funzionalità Analizza in Excel consente di testare i ruoli che sono stati definiti dall'utente.  
  
#### <a name="to-browse-by-using-the-sales-manager-user-role"></a>Per esplorare utilizzando il ruolo utente Sales Manager  
  
1.  In SSDT scegliere il **Model** menu e quindi fare clic su **analizza in Excel**.  
  
2.  Nelle **specificare il nome utente o ruolo da utilizzare per connettersi al modello**, selezionare **ruolo**, quindi nella casella di riepilogo discesa, selezionare **responsabile vendite**e quindi fare clic su **OK**.  
  
    Verrà visualizzata la finestra di Excel con una nuova cartella di lavoro. Viene creata automaticamente una tabella pivot. L'elenco campi tabella Pivot include tutti i campi di dati disponibili nel nuovo modello.  
      
3.  Chiudere Excel senza salvare la cartella di lavoro.  
  
## <a name="whats-next"></a>Quali sono le operazioni successive?

Passare alla lezione successiva: [lezione 13: distribuire](../tutorial-tabular-1400/as-lesson-13-deploy.md).

  
  
  

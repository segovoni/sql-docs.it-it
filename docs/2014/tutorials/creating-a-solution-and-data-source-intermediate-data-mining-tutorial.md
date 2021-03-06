---
title: Creazione di una soluzione e origine dati (esercitazione intermedia di Data Mining) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 0488b231-1045-4169-aabb-c1005d86ca30
caps.latest.revision: 22
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 22bfe87f9d0cd09d2d7c7f650d500398b936cde0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37216241"
---
# <a name="creating-a-solution-and-data-source-intermediate-data-mining-tutorial"></a>Creazione di una soluzione e di un'origine dati (Esercitazione intermedia sul data mining)
  Per lavorare con il data mining, è innanzitutto necessario creare un progetto in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] usando il modello **multidimensionale di Analysis Services e progetto di Data Mining**. Quando si apre il modello, nella finestra di progettazione vengono caricati tutti gli schemi che potrebbero essere necessari per il data mining: origini dati, strutture di data mining, modelli di data mining e persino cubi nel caso in cui nella struttura di data mining vengano usati dati multidimensionali.  
  
 Quando si crea il progetto, la soluzione viene archiviata come file locale finché non viene distribuita. Quando si distribuisce la soluzione [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] cerca i [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server specificato nelle proprietà del progetto e crea un nuovo [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database con lo stesso nome del progetto. Per impostazione predefinita [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] utilizza le **localhost** istanza per i nuovi progetti. Se si usa un'istanza denominata o si specifica un nome diverso per l'istanza predefinita, è necessario impostare la proprietà del database di distribuzione del progetto sul percorso in cui creare gli oggetti di data mining.  
  
 Per altre informazioni sulle [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] progetti, vedere [creare un progetto di Analysis Services &#40;SSDT&#41;](../analysis-services/multidimensional-models/create-an-analysis-services-project-ssdt.md).  
  
### <a name="to-create-a-new-analysis-services-project-for-this-tutorial"></a>Per creare un nuovo progetto di Analysis Services per questa esercitazione  
  
1.  Aprire [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
2.  Scegliere **Nuovo** dal menu **File**e quindi fare clic su **Progetto**.  
  
3.  Selezionare **Progetto multidimensionale e di data mining di Analysis Services** nel riquadro **Modelli installati** .  
  
4.  Nella casella **Nome** assegnare al nuovo progetto il nome **DM Intermediate**.  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-change-the-instance-where-data-mining-objects-are-stored-optional"></a>Per modificare l'istanza in cui sono archiviati gli oggetti di data mining (facoltativo)  
  
1.  Nella [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]via il **Project** menu, fare clic su **proprietà**.  
  
2.  Fare clic su **Distribuzione** sul lato sinistro del riquadro **Pagine delle proprietà**.  
  
3.  Verificare che il nome di **Server** sia **localhost**. Se si usa un'altra istanza, digitarne il nome. Se si usa un'istanza denominata di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], digitare il nome del computer e quindi il nome dell'istanza. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-change-the-deployment-properties-for-a-project-optional"></a>Per modificare le proprietà di distribuzione di un progetto (facoltativo)  
  
1.  In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto, quindi scegliere **Proprietà**.  
  
     -oppure-  
  
     Nella [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]via il **Project** dal menu **proprietà**.  
  
2.  Fare clic su **Distribuzione** sul lato sinistro del riquadro **Pagine delle proprietà**.  
  
     Nel riquadro **Opzioni** selezionare **Modalità di distribuzione**e impostare le opzioni su **Distribuisci tutto** per sovrascrivere o su **Distribuisci solo modifiche** per aggiornare gli oggetti esistenti o aggiungere altri oggetti.  
  
## <a name="creating-a-data-source"></a>Creazione di un'origine dati  
 Nell'esercitazione di base sul Data Mining è stato creato un *zdroj dat* che archivia le informazioni di connessione per il [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] database. Eseguire gli stessi passaggi per creare l'origine dati [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] in questa soluzione.  
  
#### <a name="to-create-a-data-source"></a>Per creare un'origine dati  
  
-   [Creazione di un'origine dati &#40;esercitazione di base di Data Mining&#41;](../../2014/tutorials/creating-a-data-source-basic-data-mining-tutorial.md)  
  
 Un'unica origine dati può supportare più viste origine dati, ognuna delle quali può includere più tabelle. Tuttavia, poiché l'origine dati e vista origine dati vengono distribuite per i [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database insieme ai modelli di data mining creati dall'utente, come procedura consigliata è necessario includere in ogni vista origine dati solo le tabelle che sono necessari per ogni modello di data mining o gruppo di modelli.  
  
 Nelle lezioni successive verranno aggiunte alcune viste origine dati per supportare ognuno dei nuovi scenari. Solo nelle lezioni relative alle analisi degli acquisti e al clustering delle sequenze viene usata la stessa vista origine dati; diversamente, in ogni scenario viene usata una vista origine dati diversa. Le lezioni sono pertanto indipendenti l'una dall'altra e possono essere completate separatamente.  
  
|Scenario|Dati inclusi nella vista origine dati|  
|--------------|-------------------------------------------|  
|[Lezione 2: Compilazione di uno Scenario di previsione &#40;esercitazione intermedia sul Data Mining&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)|Report mensili sulle vendite per i modelli di bicicletta nelle diverse aree geografiche, raccolti come singola vista.|  
|[Lezione 3: Compilazione di uno Scenario Market Basket &#40;esercitazione intermedia sul Data Mining&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)|Tabella contenente un elenco di ordini cliente e tabella annidata che mostra i singoli acquisti per ciascun cliente.|  
|[Lezione 4: Compilazione di una Scenario di Clustering delle sequenze &#40;esercitazione intermedia sul Data Mining&#41;](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)|Gli stessi dati usati per il Market basket analysis, con l'aggiunta di un identificatore che mostra l'ordine in cui sono stati acquistati gli articoli.|  
|[Lezione 5: Creazione di reti neurali e modelli di regressione logistica &#40;esercitazione intermedia sul Data Mining&#41;](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)|Singola tabella contenente i dati preliminari sul monitoraggio delle prestazioni provenienti da un call center.|  
  
## <a name="next-lesson"></a>Lezione successiva  
 [Lezione 2: Compilazione di uno Scenario di previsione &#40;esercitazione intermedia sul Data Mining&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Progetti di Data Mining](../../2014/analysis-services/data-mining/data-mining-projects.md)   
 [Viste origine dati in modelli multidimensionali](../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)  
  
  

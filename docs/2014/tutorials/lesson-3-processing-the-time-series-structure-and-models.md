---
title: 'Lezione 3: Elaborazione della serie temporale di strutture e modelli | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 16e27b57-eae1-47a7-a02c-47b6ed487d87
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f69c21f87a56a65fabd781c18612e6b475ca85c0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37271987"
---
# <a name="lesson-3-processing-the-time-series-structure-and-models"></a>Lezione 3: Elaborazione di strutture e modelli Time Series
  In questa lezione si userà il [INSERT INTO &#40;DMX&#41; ](/sql/dmx/insert-into-dmx) istruzione per l'elaborazione della serie temporale, strutture e modelli creati di data mining.  
  
 Quando si elabora una struttura di data mining, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] legge i dati di origine e compila le strutture che supportano i modelli di data mining. È sempre necessario elaborare i modelli e le strutture di data mining al momento della creazione. Se si specifica una struttura di data mining utilizzando INSERT INTO, l'istruzione elabora la struttura e tutti i modelli di data mining associati.  
  
 Quando si aggiunge un modello di data mining a una struttura di data mining già elaborata, è possibile utilizzare l'istruzione `INSERT INTO MINING MODEL` per elaborare solo il nuovo modello di data mining utilizzando i dati esistenti.  
  
 Per altre informazioni sull'elaborazione dei modelli di data mining, vedere [considerazioni e requisiti di elaborazione &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md).  
  
## <a name="insert-into-statement"></a>Istruzione INSERT INTO  
 Per eseguire il training della struttura di data mining di serie temporali e tutti i modelli di data mining associati, usare il [INSERT INTO &#40;DMX&#41; ](/sql/dmx/insert-into-dmx) istruzione. Il codice nell'istruzione può essere suddiviso nelle parti seguenti.  
  
-   Identificazione della struttura di data mining  
  
-   Creazione di un elenco delle colonne nella struttura di data mining  
  
-   Definizione dei dati di training  
  
 Di seguito è riportato un esempio generico di istruzione `INSERT INTO`:  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
(  
   <mining structure columns>  
)  
OPENQUERY (<source data definition>)  
```  
  
 La prima riga del codice identifica la struttura di data mining di cui si eseguirà il training:  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
```  
  
 Le successive righe del codice specificano le colonne definite dalla struttura di data mining. È necessario che siano elencate tutte le colonne nella struttura di data mining e ogni colonna deve essere associata a una colonna nei dati della query di origine.  
  
```  
(  
   <mining structure columns>  
)  
```  
  
 Le ultime righe del codice definiscono i dati che verranno utilizzati per il training della struttura di data mining.  
  
```  
OPENQUERY (<source data definition>)  
```  
  
 In questa lezione si utilizzerà `OPENQUERY` per definire i dati di origine. Per altre informazioni sugli altri metodi di definizione di una query sui dati di origine, vedere [ &#60;query sull'origine dati&#62;](/sql/dmx/source-data-query).  
  
## <a name="lesson-tasks"></a>Argomenti della lezione  
 In questa lezione verrà eseguita l'attività seguente:  
  
-   Elaborare la struttura di data mining Forecasting_MIXED_Structure  
  
-   Elaborare i modelli di data mining correlati Forecasting_MIXED, Forecasting_ARIMA e Forecasting_ARTXP  
  
## <a name="processing-the-time-series-mining-structure"></a>Elaborazione della struttura di data mining di serie temporali  
  
#### <a name="to-process-the-mining-structure-and-related-mining-models-by-using-insert-into"></a>Per elaborare la struttura e i relativi modelli di data mining utilizzando INSERT INTO.  
  
1.  Nella **Esplora oggetti**, fare doppio clic sull'istanza di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], scegliere **nuova Query**, quindi fare clic su **DMX**.  
  
     Verrà avviato l'editor di query con una nuova query vuota.  
  
2.  Copiare l'esempio generico dell'istruzione INSERT INTO nella query vuota.  
  
3.  Sostituire quanto segue:  
  
    ```  
    [<mining structure>]  
    ```  
  
     con:  
  
    ```  
    Forecasting_MIXED_Structure  
    ```  
  
4.  Sostituire quanto segue:  
  
    ```  
    <mining structure columns>  
    ```  
  
     con:  
  
    ```  
    [ReportingDate],  
    [ModelRegion]   
    ```  
  
5.  Sostituire quanto segue:  
  
    ```  
    OPENQUERY(<source data definition>)  
    ```  
  
     con:  
  
    ```  
    OPENQUERY([Adventure Works DW 2008R2],'SELECT [ReportingDate], [ModelRegion], [Quantity], [Amount]  
    FROM vTimeSeries ORDER BY [ReportingDate]')  
    ```  
  
     La query di origine fa riferimento il [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] origine dati definita nel progetto di esempio IntermediateTutorial. Utilizza tale origine dati per accedere alla vista vTimeSeries contenente i dati di origine che verranno utilizzati per il training del modello di data mining. Se non ha familiarità con questo progetto o le viste, vedere[lezione 2: compilazione di uno Scenario di previsione &#40;esercitazione intermedia sul Data Mining dei dati&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md).  
  
     L'istruzione completa dovrebbe risultare analoga alla seguente:  
  
    ```  
    INSERT INTO MINING STRUCTURE [Forecasting_MIXED_Structure]  
    (  
       [ReportingDate],[ModelRegion],[Quantity],[Amount])  
    )  
    OPENQUERY(  
    [Adventure Works DW 2008R2],  
    'SELECT [ReportingDate],[ModelRegion],[Quantity],[Amount] FROM vTimeSeries ORDER BY [ReportingDate]'  
    )   
    ```  
  
6.  Nel **File** menu, fare clic su **Salva Dmxquery1.DMX**.  
  
7.  Nel **Salva con nome** della finestra di dialogo passare alla cartella appropriata e assegnare un nome di file `ProcessForecastingAll.dmx`.  
  
8.  Sulla barra degli strumenti, scegliere il **Execute** pulsante.  
  
 Al termine dell'esecuzione della query, è possibile creare stime utilizzando i modelli di data mining elaborati. Nella lezione successiva verranno create diverse stime basate sui modelli di data mining creati.  
  
## <a name="next-lesson"></a>Lezione successiva  
 [Lezione 4: Creazione di stime basate su serie temporali usando DMX](../../2014/tutorials/lesson-4-creating-time-series-predictions-using-dmx.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Requisiti e considerazioni sull'elaborazione &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)   
 [&#60;query sull'origine dati&#62;](/sql/dmx/source-data-query)   
 [LA FUNZIONE OPENQUERY &AMP;#40;DMX&AMP;#41;](/sql/dmx/source-data-query-openquery)  
  
  

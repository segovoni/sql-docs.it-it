---
title: 'Lezione 2: Aggiunta di modelli di Data Mining alla struttura di Data Mining Bike Buyer | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 03fe44c5-6452-4ed0-95f6-9682670c0f52
caps.latest.revision: 35
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 055450b7461accaa62b1c9bafe4273f6fc3f9dd7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37149552"
---
# <a name="lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure"></a>Lezione 2: Aggiunta di modelli di data mining alla struttura di data mining Bike Buyer
  In questa lezione verranno aggiunti due modelli di data mining alla struttura di data mining Bike Buyer creata [lezione 1: creazione della struttura di Data Mining Bike Buyer](../../2014/tutorials/lesson-1-creating-the-bike-buyer-mining-structure.md). Uno di questi modelli consentirà di esplorare i dati e l'altro di creare stime.  
  
 Per esplorare la modalità di potenziali clienti possono essere suddivise base alle rispettive caratteristiche, si creerà un modello di data mining basato sul [algoritmo Microsoft Clustering](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md). In una lezione successiva verrà esaminato il modo in cui questo algoritmo individua cluster di clienti che condividono caratteristiche simili. È possibile riscontrare, ad esempio, che determinati clienti tendono a vivere nelle stesse aree, a usare la bicicletta per recarsi al lavoro e ad avere una formazione scolastica analoga. Questi cluster possono essere utilizzati per comprendere più a fondo la correlazione tra vari clienti e queste informazioni possono essere utilizzate come base per una strategia di marketing rivolta a un particolare segmento di clientela.  
  
 Per stimare se un cliente potenziale è con maggiore probabilità acquisteranno una bicicletta, si creerà un modello di data mining basato sul [algoritmo Microsoft Decision Trees](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md). Questo algoritmo esamina le informazioni associate a ogni potenziale cliente e individua le caratteristiche utili per stimare se acquisterà una bicicletta, quindi confronta i valori delle caratteristiche dei precedenti acquirenti di biciclette con quelli dei nuovi potenziali clienti per stabilire se è probabile che questi ultimi acquistino una bicicletta.  
  
## <a name="alter-mining-structure-statement"></a>Istruzione ALTER MINING STRUCTURE  
 Per aggiungere un modello di data mining alla struttura di data mining, viene utilizzata la [ALTER MINING STRUCTURE &#40;DMX&#41;] (istruzione (~/dmx/alter-mining-structure-dmx.md). Il codice nell'istruzione può essere suddiviso nelle parti seguenti:  
  
-   Identificazione della struttura di data mining  
  
-   Denominazione del modello di data mining  
  
-   Definizione della colonna chiave  
  
-   Definizione della colonna di input e della colonna stimabile  
  
-   Identificazione delle modifiche a livello di algoritmo e parametri  
  
 Di seguito è riportato un esempio generico dell'istruzione ALTER MINING MODEL:  
  
```  
ALTER MINING STRUCTURE [<mining structure name>]  
ADD MINING MODEL [<mining model name>]  
(  
    [<key column>],  
    <mining model columns>,  
) USING <algorithm name>( <algorithm parameters> )  
WITH FILTER (<expression>)  
```  
  
 La prima riga del codice identifica la struttura di data mining esistente a cui verranno aggiunti i modelli di data mining:  
  
```  
ALTER MINING STRUCTURE [<mining structure name>]  
```  
  
 La riga successiva del codice indica il nome del modello di data mining che verrà aggiunto alla struttura di data mining:  
  
```  
ADD MINING MODEL [<mining model name>]  
```  
  
 Per informazioni sulla denominazione di un oggetto in DMX, vedere [identificatori &#40;DMX&#41;](/sql/dmx/identifiers-dmx).  
  
 Le successive righe del codice definiscono le colonne della struttura di data mining che verranno utilizzate dal modello di data mining:  
  
```  
[<key column>],  
<mining model columns>  
```  
  
 È possibile utilizzare solo colonne già esistenti nella struttura di data mining e la prima colonna nell'elenco deve essere la colonna chiave dalla struttura di data mining.  
  
 La riga successiva del codice definisce l'algoritmo di data mining che genera il modello di data mining e i parametri che è possibile impostare nell'algoritmo:  
  
```  
) USING <algorithm name>( <algorithm parameters> )  
```  
  
 Per altre informazioni sui parametri dell'algoritmo che è possibile modificare, vedere [algoritmo Microsoft Decision Trees](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md) e [algoritmo Microsoft Clustering](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md).  
  
 Per specificare che una colonna nel modello di data mining deve essere utilizzata per la stima, è possibile utilizzare la sintassi seguente:  
  
```  
<mining model column> PREDICT  
```  
  
 L'ultima riga del codice, che è facoltativa, definisce un filtro che viene applicato durante il training e il test del modello. Per altre informazioni su come applicare filtri ai modelli di data mining, vedere [filtri per i modelli di Data Mining &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md).  
  
## <a name="lesson-tasks"></a>Argomenti della lezione  
 In questa lezione verranno eseguite le attività seguenti:  
  
-   Aggiunta di un modello di data mining dell'albero delle decisioni alla struttura Bike Buyer mediante l'algoritmo [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees  
  
-   Aggiunta di un modello di data mining di clustering alla struttura Bike Buyer mediante l'algoritmo [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering  
  
-   Poiché si desidera visualizzare i risultati per tutti i casi, non verrà ancora aggiunto un filtro ai modelli.  
  
## <a name="adding-a-decision-tree-mining-model-to-the-structure"></a>Aggiunta di un modello di data mining dell'albero delle decisioni alla struttura  
 Il primo passaggio consiste nell'aggiunta di un modello di data mining basato sull'algoritmo [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees.  
  
#### <a name="to-add-a-decision-tree-mining-model"></a>Per aggiungere un modello di data mining dell'albero delle decisioni  
  
1.  Nella **Esplora oggetti**, fare doppio clic sull'istanza di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], scegliere **nuova Query**, quindi fare clic su **DMX** per aprire l'Editor di Query e una nuova query vuota.  
  
2.  Copiare l'esempio generico dell'istruzione ALTER MINING STRUCTURE nella query vuota.  
  
3.  Sostituire quanto segue:  
  
    ```  
    <mining structure name>   
    ```  
  
     con:  
  
    ```  
    [Bike Buyer]  
    ```  
  
4.  Sostituire quanto segue:  
  
    ```  
    <mining model name>   
    ```  
  
     con:  
  
    ```  
    Decision Tree  
    ```  
  
5.  Sostituire quanto segue:  
  
    ```  
    <mining model columns>,  
    ```  
  
     con:  
  
    ```  
    (  
       CustomerKey,  
       [Age],  
       [Bike Buyer] PREDICT,  
       [Commute Distance],  
       [Education],  
       [Gender],  
       [House Owner Flag],  
       [Marital Status],  
       [Number Cars Owned],  
       [Number Children At Home],  
       [Occupation],  
       [Region],  
       [Total Children],  
       [Yearly Income]  
    ```  
  
     In questo caso, la colonna `[Bike Buyer]` è stata designata come colonna PREDICT.  
  
6.  Sostituire quanto segue:  
  
    ```  
    USING <algorithm name>( <algorithm parameters> )   
    ```  
  
     con:  
  
    ```  
    Using Microsoft_Decision_Trees  
    WITH DRILLTHROUGH  
    ```  
  
     L'istruzione WITH DRILLTHROUGH consente di esplorare i case utilizzati per compilare il modello di data mining.  
  
     L'istruzione risultante dovrebbe essere la seguente:  
  
    ```  
    ALTER MINING STRUCTURE [Bike Buyer]  
    ADD MINING MODEL [Decision Tree]  
    (  
       CustomerKey,  
       [Age],  
       [Bike Buyer] PREDICT,  
       [Commute Distance],  
       [Education],  
       [Gender],  
       [House Owner Flag],  
       [Marital Status],  
       [Number Cars Owned],  
       [Number Children At Home],  
       [Occupation],  
       [Region],  
       [Total Children],  
       [Yearly Income]  
    ) USING Microsoft_Decision_Trees  
    WITH DRILLTHROUGH  
    ```  
  
7.  Nel **File** menu, fare clic su **Salva Dmxquery1.DMX**.  
  
8.  Nel **Salva con nome** della finestra di dialogo passare alla cartella appropriata e assegnare un nome di file `DT_Model.dmx`.  
  
9. Sulla barra degli strumenti, scegliere il **Execute** pulsante.  
  
## <a name="adding-a-clustering-mining-model-to-the-structure"></a>Aggiunta di un modello di data mining di clustering alla struttura  
 A questo punto è possibile aggiungere un modello di data mining alla struttura Bike Buyer mediante l'algoritmo [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering. Dato che il modello di data mining di clustering utilizzerà tutte le colonne definite nella struttura di data mining, è possibile utilizzare una procedura abbreviata per aggiungere il modello alla struttura omettendo la definizione delle colonne di data mining.  
  
#### <a name="to-add-a-clustering-mining-model"></a>Per aggiungere un modello di data mining di clustering  
  
1.  In **Esplora oggetti**, fare doppio clic sull'istanza di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], scegliere **nuova Query**, quindi fare clic su **DMX** per aprire l'editor di Query e una nuova query vuota.  
  
2.  Copiare l'esempio generico dell'istruzione ALTER MINING STRUCTURE nella query vuota.  
  
3.  Sostituire quanto segue:  
  
    ```  
    <mining structure name>   
    ```  
  
     con:  
  
    ```  
    [Bike Buyer]  
    ```  
  
4.  Sostituire quanto segue:  
  
    ```  
    <mining model>   
    ```  
  
     con:  
  
    ```  
    Clustering Model  
    ```  
  
5.  Eliminare quanto segue:  
  
    ```  
    (  
        [<key column>],  
        <mining model columns>,  
    )  
    ```  
  
6.  Sostituire quanto segue:  
  
    ```  
    USING <algorithm name>( <algorithm parameters> )  
    ```  
  
     con:  
  
    ```  
    USING Microsoft_Clustering  
    ```  
  
     L'istruzione completa dovrebbe risultare analoga alla seguente:  
  
    ```  
    ALTER MINING STRUCTURE [Bike Buyer]  
    ADD MINING MODEL [Clustering]  
    USING Microsoft_Clustering   
    ```  
  
7.  Nel **File** menu, fare clic su **Salva Dmxquery1.DMX**.  
  
8.  Nel **Salva con nome** della finestra di dialogo passare alla cartella appropriata e assegnare un nome di file `Clustering_Model.dmx`.  
  
9. Sulla barra degli strumenti, scegliere il **Execute** pulsante.  
  
 Nella lezione successiva verranno elaborati i modelli e la struttura di data mining.  
  
## <a name="next-lesson"></a>Lezione successiva  
 [Lezione 3: Elaborazione della struttura di data mining Bike Buyer](../../2014/tutorials/lesson-3-processing-the-bike-buyer-mining-structure.md)  
  
  

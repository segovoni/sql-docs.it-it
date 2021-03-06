---
title: Filtro di una regola di associazione di una modello di regole | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 28d3601b18f792b957627e63630806453d971110
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34014488"
---
# <a name="filter-a-rule-in-an-association-rules-model"></a>Filtrare una regola in un modello Association Rules
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  È possibile utilizzare i filtri con i modelli di associazione per limitare i risultati alle sole associazioni desiderate. È ad esempio possibile filtrare le regole in modo da visualizzare solo quelle che includono un prodotto specifico.  
  
 In Progettazione modelli di data mining è possibile filtrare le regole visualizzate usando i controlli nella scheda **Regole** del Visualizzatore [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules.  Si può anche creare una query sul modello per vedere solo il set di elementi che contiene un determinato valore.  
  
> [!NOTE]  
>  Questa opzione è disponibile solo per i modelli di data mining creati utilizzando l'algoritmo Microsoft Association Rules.  
  
### <a name="filter-a-rule-in-an-association-model"></a>Filtrare una regola in un modello di associazione  
  
1.  Aprire il modello di data mining utilizzando il **Visualizzatore Microsoft Association Rules**. Per eseguire questa operazione in SQL Server Management Studio, fare clic con il pulsante destro del mouse sul nome del modello e selezionare **Sfoglia**. Per eseguire questa operazione in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], fare doppio clic sulla struttura di data mining che contiene il modello e quindi fare clic sulla scheda **Visualizzatore modello di data mining** di **Progettazione modelli di data mining**.  
  
2.  Fare clic sulla scheda **Regole** del **Visualizzatore Microsoft Association Rules**.  
  
3.  Digitare una condizione per la regola nella casella **Filtro regola** . Una condizione potrebbe ad esempio essere "Bike Stand" che restituisce anche "Bike Stands".  
  
     Per la casella di testo **Filtro regola** sono supportate le espressioni regolari definite dal linguaggio .NET. È pertanto possibile utilizzare espressioni simili alla seguente: `((.Helmets.*Fenders.*)|(.*Fenders.*Helmets.*))`. Questa espressione restituisce tutti i set di elementi che includono attributi contenenti le parole Helmets e Fenders disposte in qualsiasi ordine.  
  
4.  Aumentare o ridurre il valore di **Probabilità minima**per visualizzare rispettivamente un numero minore o maggiore di regole.  
  
5.  Aumentare o ridurre il valore di **Priorità minima**per visualizzare rispettivamente un numero minore o maggiore di regole.  
  
6.  Selezionare una delle opzioni seguenti nell'area **Mostra**: **Mostra nome e valore dell'attributo**, **Mostra solo il nome dell'attributo**o **Mostra solo il valore dell'attributo**.  
  
7.  Aumentare o ridurre il valore di **Numero massimo di righe**rispettivamente per incrementare il numero totale di regole che soddisfano le condizioni specificate o limitare il numero di regole restituite. Le regole vengono ordinate in base alla probabilità. È pertanto possibile eliminare le regole aggiuntive che soddisfano le condizioni specificate in base alle probabilità o alla priorità.  
  
8.  Selezionare o deselezionare la casella di controllo **Mostra nomi lunghi** per specificare il modo in cui visualizzare i nomi delle regole.  
  
     Le regole verranno filtrate per visualizzare solo quelle che contengono l'elemento indicato. La condizione di filtro si applica ai valori di attributo prima o dopo il delimitatore della regola "->".  
  
    > [!NOTE]  
    >  Nella cache del visualizzatore viene memorizzato l'elenco iniziale di regole, basato su una query eseguita sul modello di data mining, che non viene aggiornato a meno che non si modifichino le condizioni della query impostando il numero massimo di righe, la probabilità, la priorità o la visualizzazione di nomi lunghi. Se, pertanto, si digita una condizione e la visualizzazione non viene aggiornata di conseguenza, è possibile fare in modo che l'aggiornamento dei dati venga eseguito selezionando e quindi deselezionando la casella di controllo **Mostra nomi lunghi** .  
  
### <a name="create-a-query-on-the-itemsets-in-an-association-model"></a>Creare una query sui set di elementi di un modello di associazione  
  
-   [Esempi di Query sul modello Association](../../analysis-services/data-mining/association-model-query-examples.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Procedure dettagliate e attività del visualizzatore modello di data mining](../../analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)   
 [Visualizzare un modello utilizzando il visualizzatore Microsoft Association Rules](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-association-rules-viewer.md)   
 [Lezione 3: Compilazione di uno Scenario Market Basket & #40; esercitazione intermedia di Data Mining & #41;](http://msdn.microsoft.com/library/651eef38-772e-4d97-af51-075b1b27fc5a)  
  
  

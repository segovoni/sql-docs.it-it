---
title: Rete neurale (Visualizzatore modello di Data Mining) | Microsoft Docs
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
- sql12.dm.miningmodeleditor.neuralnet.f1
ms.assetid: 18d87e7b-a821-40ea-9bd8-c6fecf189a1c
caps.latest.revision: 23
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7cb93ac76fb6213817dcef3530387772e099e0e9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37297411"
---
# <a name="neural-network-mining-model-viewer"></a>Rete neurale (Visualizzatore modello di data mining)
  Utilizzare il visualizzatore **Microsoft Neural Network** per esplorare i modelli di data mining basati sull'algoritmo [!INCLUDE[msCoName](../includes/msconame-md.md)] Neural Network o [!INCLUDE[msCoName](../includes/msconame-md.md)] Logistic Regression.  
  
 **Per altre informazioni:** [Algoritmo Microsoft Neural Network](data-mining/microsoft-neural-network-algorithm.md), [Algoritmo Microsoft Logistic Regression](data-mining/microsoft-logistic-regression-algorithm.md),[Visualizzare un modello utilizzando il Visualizzatore Microsoft Neural Network](data-mining/browse-a-model-using-the-microsoft-neural-network-viewer.md)  
  
## <a name="options"></a>Opzioni  
 **Aggiorna contenuto visualizzatore**  
 Consente di ricaricare il modello di data mining nel visualizzatore.  
  
 **Modello di data mining**  
 Consente di scegliere un modello di data mining da visualizzare tra quelli presenti nella struttura di data mining corrente. Il modello di data mining verrà aperto nel visualizzatore associato.  
  
 **Visualizzatore**  
 Consente di scegliere un visualizzatore da utilizzare per l'esplorazione del modello di data mining selezionato. È possibile utilizzare il visualizzatore personalizzato o **Microsoft Generic Content Tree Viewer**. Se disponibili, è anche possibile utilizzare i visualizzatori plug-in.  
  
 **Input**  
 Utilizzare quest'area per scegliere attributi di input e valori in modo da poter approfondire in un secondo momento il modo in cui questi influiscono sul risultato.  
  
|valore|Description|  
|-----------|-----------------|  
|**Attribute**|Consente di scegliere un attributo di input dall'elenco. Se si lascia l'impostazione predefinita,  **\<tutto >**, il grafico mostra un elenco di tutti gli attributi di input classificati in base alla relativa influenza sull'attributo stimabile.|  
|**Value**|Consente di scegliere un valore per l'attributo di input.|  
  
 **Output**  
 Utilizzare questi controlli per scegliere un attributo e un valore stimabili da analizzare e confrontare nel grafico a barre. Se non si modificano le selezioni, il grafico a barre consente di confrontare i due primi stati del risultato.  
  
|valore|Description|  
|-----------|-----------------|  
|**Attributo di output**|Consente di scegliere un attributo stimabile. Se la colonna non è stata definita come stimabile durante la creazione del modello, non è possibile aggiungerla in questo momento.|  
|**Valore 1**|Consente di scegliere uno stato dell'attributo stimabile da confrontare con lo stato contenuto in **Valore 2**.<br /><br /> È possibile confrontare uno qualsiasi dei due valori discreti o discretizzati; tuttavia, non è possibile confrontare un valore rispetto al relativo complemento, operazione che invece può essere effettuata in altri visualizzatori.|  
|**Valore 2**|Consente di scegliere uno stato dell'attributo stimabile da confrontare con lo stato contenuto in **Valore 1**.|  
  
 **Variabili**  
 In questa parte della scheda **Rete neurale** è contenuto un grafico a barre interattivo che rappresenta le risposte alle selezioni eseguite per gli attributi di input e del risultato. Poiché una rete neurale consente di calcolare la probabilità di influenza di un particolare valore su un determinato risultato, è possibile scegliere qualsiasi combinazione di input e nel grafico a barre verrà visualizzato il modo in cui tale combinazione influisce sulla coppia di risultati in fase di confronto.  
  
|valore|Description|  
|-----------|-----------------|  
|**Attribute**|Consente di visualizzare il nome dell'attributo di input selezionato in **Attributo**.|  
|**Value**|Consente di visualizzare il valore per l'attributo di input selezionato.|  
|**Predilige \<valore 1 >**|Visualizza una barra che indica il livello di influenza di questa particolare combinazione attributo-valore sul risultato di destinazione scelto in **Valore 1**.|  
|**Predilige \<valore 2 >**|Visualizza una barra che indica il livello di influenza di questa particolare combinazione attributo-valore sul risultato di destinazione scelto in **Valore 2**.|  
  
## <a name="see-also"></a>Vedere anche  
 [Algoritmi di Data Mining &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Visualizzatori modello di data mining &#40;Progettazione modelli di Data Mining&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Visualizzatori modello di data mining](data-mining/data-mining-model-viewers.md)  
  
  

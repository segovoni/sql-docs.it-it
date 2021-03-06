---
title: Lezione 9 creare prospettive | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4e917e817768571e1959ae6163743ecdad0409af
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38031619"
---
# <a name="lesson-8-create-perspectives"></a>Lezione 8: Creare prospettive
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

In questa lezione verrà creata una prospettiva Internet Sales. Una prospettiva consente di definire un subset visualizzabile di un modello in grado di offrire punti di vista mirati, specifici di un'attività aziendale o di un'applicazione del modello. Quando un utente si connette a un modello utilizzando una prospettiva, vengono visualizzati solo gli oggetti del modello (tabelle, colonne, misure, gerarchie e indicatori KPI) come campi definiti in tale prospettiva.  
  
La prospettiva Internet Sales che è creata in questa lezione escluderà l'oggetto tabella DimCustomer. Quando si crea una prospettiva che esclude determinati oggetti dalla visualizzazione, tali oggetti sono ancora presenti nel modello; tuttavia non sono visibili in un elenco di campi di un client di creazione di report. Le colonne e le misure calcolate incluse o meno in una prospettiva consentono ancora eseguire calcoli da dati di oggetto esclusi.  
  
Lo scopo di questa lezione è quello di descrivere come creare prospettive e di consentire di acquisire familiarità con gli strumenti di creazione di modelli tabulari. Se successivamente si espande questo modello per includere tabelle aggiuntive, è possibile creare ulteriori prospettive per definire punti di vista diversi del modello, ad esempio, vendite e inventario. Per altre informazioni, vedere [Prospettive](../analysis-services/tabular-models/perspectives-ssas-tabular.md).  
  
Tempo stimato per il completamento della lezione: **5 minuti**  
  
## <a name="prerequisites"></a>Prerequisiti  
Questo argomento fa parte di un'esercitazione relativa alla modellazione tabulare che deve essere completata nell'ordine specificato. Prima di eseguire le attività in questa lezione, è necessario avere completato la lezione precedente: [lezione 7: creare indicatori di prestazioni chiave](../analysis-services/lesson-7-create-key-performance-indicators.md).  
  
## <a name="create-perspectives"></a>Creare prospettive  
  
#### <a name="to-create-an-internet-sales-perspective"></a>Per creare una prospettiva Internet Sales  
  
1.  Scegliere il **modello** menu > **prospettive** > **crea e Gestisci**.  
  
2.  Nella finestra di dialogo **Prospettive** fare clic su **Nuova prospettiva**.  
  
3.  Fare doppio clic il **nuova prospettiva** sull'intestazione di colonna e quindi rinominarla **Internet Sales**.  
  
4.  Selezionare tutte le tabelle *eccetto* **DimCustomer**.  
  
    ![come-tabulare-lesson8-prospettive](../analysis-services/media/as-tabular-lesson8-perspectives.png)
  
    In una lezione successiva si utilizzerà l'analizza nella funzionalità di Excel per testare questa prospettiva. L'elenco campi tabella pivot di Excel includerà ogni le tabelle tranne DimCustomer.  

## <a name="whats-next"></a>Quali sono le operazioni successive?
Passare alla lezione successiva: [lezione 9: creare gerarchie](../analysis-services/lesson-9-create-hierarchies.md).
  
  
  
  

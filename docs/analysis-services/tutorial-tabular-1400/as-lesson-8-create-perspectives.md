---
title: 'Analysis Services tutorial lezione 8: creare prospettive | Microsoft Docs'
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 69511478e6580328776548d354e6801323a5f7e0
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "37973063"
---
# <a name="create-perspectives"></a>Creare prospettive

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

In questa lezione, si crea una prospettiva Internet Sales. Una prospettiva consente di definire un subset visualizzabile di un modello in grado di offrire punti di vista mirati, specifici di un'attività aziendale o di un'applicazione del modello. Quando un utente si connette a un modello utilizzando una prospettiva, vengono visualizzati solo gli oggetti del modello (tabelle, colonne, misure, gerarchie e indicatori KPI) come campi definiti in tale prospettiva. Per altre informazioni, vedere [prospettive](../tabular-models/perspectives-ssas-tabular.md).
  
La prospettiva Internet Sales che è creata in questa lezione esclude l'oggetto tabella DimCustomer. Quando si crea una prospettiva che esclude determinati oggetti dalla visualizzazione, quell'oggetto esiste ancora nel modello. Tuttavia, non visibile in un elenco di campi client reporting. Le colonne e le misure calcolate incluse o meno in una prospettiva consentono ancora eseguire calcoli da dati di oggetto esclusi.  
  
Lo scopo di questa lezione è quello di descrivere come creare prospettive e di consentire di acquisire familiarità con gli strumenti di creazione di modelli tabulari. Se successivamente si espande questo modello per includere tabelle aggiuntive, è possibile creare ulteriori prospettive per definire punti di vista diversi del modello, ad esempio, vendite e inventario.  
  
Tempo stimato per il completamento della lezione: **cinque minuti**  
  
## <a name="prerequisites"></a>Prerequisiti  

Questo articolo fa parte di un'esercitazione di modellazione tabulare, che deve essere completata nell'ordine. Prima di eseguire le attività in questa lezione, è necessario avere completato la lezione precedente: [lezione 7: creare indicatori di prestazioni chiave](../tutorial-tabular-1400/as-lesson-7-create-key-performance-indicators.md).  
  
## <a name="create-perspectives"></a>Creare prospettive  
  
#### <a name="to-create-an-internet-sales-perspective"></a>Per creare una prospettiva Internet Sales  
  
1.  Scegliere il **modello** menu > **prospettive** > **crea e Gestisci**.  
  
2.  Nella finestra di dialogo **Prospettive** fare clic su **Nuova prospettiva**.  
  
3.  Fare doppio clic il **nuova prospettiva** sull'intestazione di colonna e quindi rinominarla **Internet Sales**.  
  
4.  Selezionare tutte le tabelle *eccetto* **DimCustomer**.  
  
    ![prospettive come lesson8](../tutorial-tabular-1400/media/as-lesson8-perspectives.png)
  
    In una lezione successiva si userà l'analizza nella funzionalità di Excel per testare questa prospettiva. L'elenco campi tabella pivot di Excel include tutte le tabelle tranne DimCustomer.  

## <a name="whats-next"></a>Quali sono le operazioni successive?

[Lezione 9: Creare gerarchie](../tutorial-tabular-1400/as-lesson-9-create-hierarchies.md).
  
  
  
  

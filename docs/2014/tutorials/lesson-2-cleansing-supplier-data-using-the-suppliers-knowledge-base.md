---
title: 'Lezione 2: Pulizia dei dati fornitore mediante la Knowledge Base Suppliers | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 215c14de-fc3f-46de-a022-bf69b9ea2a96
caps.latest.revision: 7
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5708dfe72d3eaa745d1ffefd88147b3e72b7c46c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37191221"
---
# <a name="lesson-2-cleansing-supplier-data-using-the-suppliers-knowledge-base"></a>Lezione 2: Pulizia dei dati fornitore mediante la Knowledge Base Suppliers
  In questa lezione si puliscono i dati fornitore in un file di Excel utilizzando la **Suppliers** della knowledge base creata nella prima lezione. Pulizia dei dati in DQS include un' **processo computerizzato** che consente di analizzare la conformità dei dati alle informazioni in una knowledge base e un **processo interattivo** che consente di esaminare e modificare risultati dal processo computerizzato. Tramite la funzionalità di pulizia dei dati vengono identificati i dati errati nell'origine dati e, successivamente, vengono corretti o vengono forniti suggerimenti di correzione. Vengono inoltre standardizzati e arricchiti i dati dei clienti utilizzando i valori di dominio, i valori iniziali per sinonimi, le regole di dominio, le relazioni basate su termini e i dati di riferimento. È possibile approvare o rifiutare in modo interattivo le modifiche proposte dal processo computerizzato. Visualizzare [pulizia dei dati](http://msdn.microsoft.com/library/gg524800.aspx) per altri dettagli.  
  
 Nel processo computerizzato vengono utilizzati i seguenti valori soglia che è possibile configurare utilizzando l'apposita opzione nella pagina principale del client DQS.  
  
-   **Punteggio minimo per suggerimenti:** punteggio minimo o livello di probabilità utilizzato da DQS per suggerire sostituzioni per un valore.  
  
-   **Punteggio minimo per correzioni automatiche:** punteggio minimo o livello di probabilità utilizzato da DQS per correggere automaticamente un valore.  
  
 Visualizzare [configurare valori soglia per le attività di pulizia e corrispondenza](http://msdn.microsoft.com/library/hh510415.aspx) per informazioni dettagliate su come configurare queste impostazioni.  
  
 In questa lezione vengono effettuate le attività seguenti per pulire i dati di input utilizzando la Knowledge Base Suppliers.  
  
1.  Creare un progetto Data Quality per la pulizia, selezionare la Knowledge Base Suppliers come quella da utilizzare per analizzare e pulire i dati di origine in un file di Excel e selezionare l'attività di pulizia.  
  
2.  Eseguire il mapping delle colonne di Excel che si desidera pulire ai domini DQS singoli/composti appropriati nella Knowledge Base.  
  
3.  Eseguire l'attività di pulizia computerizzata. Tramite il processo computerizzato vengono visualizzate informazioni sulla qualità dei dati nel client Data Quality che possono essere utilizzate per pulire i dati in modo interattivo.  
  
4.  Visualizzare e gestire i risultati dell'attività di pulizia. È possibile esaminare i valori rilevati dal processo computerizzato come corretti, errati ma a cui è stata apportata una correzione, errati con un suggerimento di modifica o non validi. È possibile approvare o rifiutare in modo interattivo le modifiche correggendo o eseguendo l'override dei suggerimenti forniti dal processo computerizzato mediante il campo Correggi in.  
  
5.  Esportare i risultati dal processo di pulizia in un file di Excel.  
  
6.  Importare i valori dal progetto di pulizia nei domini per ampliare le informazioni nella Knowledge Base con nuovi valori, regole, correzioni e così via  
  
## <a name="next-step"></a>Passaggio successivo  
 [Attività 1: Creazione di un progetto Data Quality](../../2014/tutorials/task-1-creating-a-data-quality-project.md)  
  
  

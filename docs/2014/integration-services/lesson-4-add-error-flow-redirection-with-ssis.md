---
title: 'Lezione 4: Aggiunta del reindirizzamento del flusso di errore | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 0c8dbda2-75e3-4278-9b4e-dcd220c92522
caps.latest.revision: 23
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 230294eb45aec198ba5fd0cde396749bd0897b14
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37295091"
---
# <a name="lesson-4-adding-error-flow-redirection"></a>Lezione 4: Aggiunta del reindirizzamento del flusso degli errori
  Per gestire gli errori che si verificano durante il processo di trasformazione, [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] consente di decidere sulla base dei singoli componenti e delle singole colonne come gestire i dati che non possono essere trasformati. È possibile scegliere di ignorare un errore in alcune colonne, reindirizzare l'intera riga con esito negativo o interrompere l'esecuzione del componente. Per impostazione predefinita, tutti i componenti di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sono configurati in modo da interrompersi quando si verificano errori. L'arresto di un componente determina l'arresto del pacchetto e di conseguenza di tutte le elaborazioni successive.  
  
 Anziché arrestare l'esecuzione del pacchetto a causa degli errori, è consigliabile configurare e gestire potenziali errori di elaborazione nel momento stesso in cui si verificano durante la trasformazione. Sebbene sia possibile decidere di ignorare gli errori in modo da garantire l'esecuzione dei pacchetti, è talvolta opportuno reindirizzare la riga con esito negativo a un altro percorso di elaborazione in cui i dati e gli errori possono essere mantenuti e quindi essere esaminati e rielaborati in un momento successivo.  
  
 In questa lezione verranno illustrate le procedure per la creazione di una copia del pacchetto sviluppato in [Lesson 3: Adding Logging](lesson-3-add-logging-with-ssis.md). L'utilizzo di questo nuovo pacchetto consentirà di creare una versione danneggiata di uno dei file di dati di esempio. Durante l'esecuzione del pacchetto, il file danneggiato forzerà la generazione di un errore di elaborazione.  
  
 Per gestire i dati dell'errore verrà aggiunta e configurata una destinazione file flat che consente di scrivere in un file tutte le righe che non riescono a individuare un valore di ricerca nella trasformazione Lookup Currency Key.  
  
 Prima che i dati dell'errore vengano scritti nel file, si includerà un componente script che usa uno script per ottenere le descrizioni degli errori. La trasformazione Lookup Currency Key verrà quindi riconfigurata in modo che i dati che non possono essere elaborati vengano reindirizzati alla trasformazione Script.  
  
> [!IMPORTANT]  
>  Per eseguire questa esercitazione, è necessario il database di esempio **AdventureWorksDW2012** . Per altre informazioni sull'installazione e sulla distribuzione di **AdventureWorksDW2012**, vedere [Esempi di Reporting Services su CodePlex](http://go.microsoft.com/fwlink/p/?LinkId=526910).  
  
## <a name="tasks-in-lesson"></a>Argomenti della lezione  
 In questa lezione sono incluse le attività seguenti:  
  
-   [Passaggio 1: Copia del pacchetto della lezione 3](lesson-4-1-copying-the-lesson-3-package.md)  
  
-   [Passaggio 2: Creazione di un file danneggiato](lesson-4-2-creating-a-corrupted-file.md)  
  
-   [Passaggio 3: Aggiunta del reindirizzamento del flusso degli errori](lesson-4-3-adding-error-flow-redirection.md)  
  
-   [Passaggio 4: Aggiunta di una destinazione file flat](lesson-4-4-adding-a-flat-file-destination.md)  
  
-   [Passaggio 5: Test del pacchetto creato nell'esercitazione della lezione 4](lesson-4-5-testing-the-lesson-4-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>Inizio della lezione  
 [Passaggio 1: Copia del pacchetto della lezione 3](lesson-4-1-copying-the-lesson-3-package.md)  
  
  

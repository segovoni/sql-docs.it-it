---
title: 'Esercitazione SSIS: Creazione di un pacchetto ETL | Microsoft Docs'
ms.custom: ''
ms.date: 04/17/2018
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- SSIS, tutorials
- packages [Integration Services], tutorials
- Integration Services, tutorials
- SQL Server Integration Services, tutorials
- logs [Integration Services], tutorials
- walkthroughs [Integration Services]
ms.assetid: d6d5bb1f-4cb1-4605-9cd6-f60b858382c4
caps.latest.revision: 38
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 234b5a72f611ab2ac85db862c04af7d749e089ab
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2018
ms.locfileid: "35411733"
---
# <a name="ssis-how-to-create-an-etl-package"></a>Esercitazione SSIS: Creazione di un pacchetto ETL semplice

 > Per contenuti relativi alle versioni precedenti di SQL Server, vedere [Esercitazione SSIS: Creazione di un pacchetto ETL semplice](https://msdn.microsoft.com/library/ms169917(SQL.120).aspx).

In questa esercitazione viene illustrato come usare Progettazione [!INCLUDE[ssIS](../includes/ssis-md.md)] per creare un pacchetto semplice di [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Tale pacchetto preleva i dati da un file flat, li riformatta e quindi li inserisce in una tabella dei fatti. Nelle lezioni successive il pacchetto viene espanso per illustrare i loop, le configurazioni del pacchetto, la registrazione e il flusso degli errori.  
  
Contestualmente all'installazione dei dati di esempio usati nell'esercitazione, vengono installate anche le versioni complete dei pacchetti creati in ogni lezione. Questi pacchetti completi consentono di iniziare l'esercitazione dalla lezione desiderata. Se è la prima volta che si usano i pacchetti o il nuovo ambiente di sviluppo, è consigliabile iniziare dalla lezione 1.  

## <a name="what-is-sql-server-integration-services-ssis"></a>Definizione di SQL Server Integration Services (SSIS)

[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] (SSIS) è una piattaforma per la compilazione di soluzioni di integrazione di dati dalle prestazioni elevate, in cui sono incluse funzionalità per l'estrazione, la trasformazione e il caricamento (ETL) di pacchetti per il data warehousing. In SSIS sono disponibili strumenti grafici e procedure guidate per la compilazione e il debug di pacchetti, attività per l'esecuzione di funzioni di flusso di lavoro quali operazioni FTP, esecuzione di istruzioni SQL e invio di messaggi di posta elettronica, origini dei dati e destinazioni per l'estrazione e il caricamento dei dati, trasformazioni per la pulizia, l'aggregazione, l'unione e la copia dei dati, il servizio di gestione [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , per l'amministrazione dell'esecuzione e dell'archiviazione dei pacchetti, nonché API (Application Programming Interface) per la programmazione del modello a oggetti di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  

## <a name="what-you-learn"></a>Informazioni ottenute dall'esercitazione  
Il modo più efficace per acquisire familiarità con i nuovi strumenti e controlli e con le caratteristiche disponibili in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] consiste nell'usarli. Questa esercitazione illustra l'uso di Progettazione [!INCLUDE[ssIS](../includes/ssis-md.md)] per creare un pacchetto ETL semplice che include i cicli, le configurazioni, la logica del flusso degli errori e la registrazione.  
  
## <a name="requirements"></a>Requisiti  
Questa esercitazione è destinata agli utenti esperti nelle operazioni fondamentali sui database ma con una conoscenza limitata delle nuove funzionalità disponibili in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  

> [!IMPORTANT]
> Da un po' di tempo i file di esempio necessari per eseguire questa esercitazione non sono più disponibili online nella posizione precedente. Ci scusiamo per l'inconveniente. Ora si trovano in una nuova posizione. I collegamenti per il download sono stati aggiornati in questo articolo.

Per utilizzare l'esercitazione è necessario che nel sistema siano installati i componenti seguenti:  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] con il database **AdventureWorksDW2012** . Per scaricare il database **AdventureWorksDW2012**, scaricare `AdventureWorksDW2012.bak` dai [database di esempio AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) e ripristinare il backup.  

-   Dati di esempio I dati di esempio sono inclusi nei pacchetti di lezioni di [!INCLUDE[ssIS](../includes/ssis-md.md)] . Per scaricare i dati di esempio e i pacchetti di lezioni come file con estensione zip, vedere [SQL Server Integration Services Tutorial - Create a Simple ETL Package](https://www.microsoft.com/download/details.aspx?id=56827) (Esercitazione di SQL Server Integration Services - Creare un semplice pacchetto ETL).  

## <a name="lessons-in-this-tutorial"></a>Lezioni dell'esercitazione  
[Lezione 1: Creare un progetto e un pacchetto di base](../integration-services/lesson-1-create-a-project-and-basic-package-with-ssis.md)  
In questa lezione viene creato un pacchetto ETL semplice che estrae i dati da un unico file flat, li trasforma usando le trasformazioni Ricerca e infine carica il risultato in una destinazione tabella dei fatti.  
  
[Lezione 2: Aggiungere cicli con SSIS](../integration-services/lesson-2-adding-looping-with-ssis.md)  
In questa lezione si espande il pacchetto creato nella lezione 1 per usare le nuove funzionalità di ciclo che consentono di estrarre più file flat in un unico processo di flusso di dati.  
  
[Lezione 3: Aggiungere la registrazione con SSIS](../integration-services/lesson-3-add-logging-with-ssis.md)  
In questa lezione si espande il pacchetto creato nella lezione 2 per usare le nuove funzionalità di registrazione.  
  
[Lezione 4: Aggiungere il reindirizzamento del flusso errato con SSIS](../integration-services/lesson-4-add-error-flow-redirection-with-ssis.md)  
In questa lezione si espande il pacchetto creato nella lezione 3 per usare le nuove configurazioni di output degli errori.  
  
[Lezione 5: Aggiungere configurazioni del pacchetto SSIS per il modello di distribuzione del pacchetto](../integration-services/lesson-5-add-ssis-package-configurations-for-the-package-deployment-model.md)  
In questa lezione si espande il pacchetto creato nella lezione 4 per usare le nuove opzioni di configurazione del pacchetto.  
  
[Lezione 6: Usare parametri con il modello di distribuzione del progetto in SSIS](../integration-services/lesson-6-using-parameters-with-the-project-deployment-model-in-ssis.md)  
In questa lezione si espande il pacchetto creato nella lezione 5 per usare i nuovi parametri con il modello di distribuzione del progetto.  
  
  
  

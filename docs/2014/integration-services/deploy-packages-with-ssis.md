---
title: 'Esercitazione SSIS: Distribuzione di pacchetti | Microsoft Docs'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- deployment tutorial [Integration Services]
- deploying packages [Integration Services]
- SSIS, tutorials
- Integration Services, tutorials
- deploying packages [Integration Services], installing
- SQL Server Integration Services, tutorials
- walkthroughs [Integration Services]
- deployment utility [Integration Services]
- deploying packages [Integration Services], configurations
ms.assetid: de18468c-cff3-48f4-99ec-6863610e5886
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 68a9e0c00bc51d7bee4c083a8ccc4f65b85d4880
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37213431"
---
# <a name="ssis-tutorial-deploying-packages"></a>Esercitazione SSIS: Distribuzione di pacchetti
  [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] include strumenti che consentono di distribuire in modo semplice i pacchetti in un altro computer. Gli strumenti di distribuzione consentono inoltre di gestire eventuali dipendenze, ad esempio configurazioni e file necessari per il pacchetto. In questa esercitazione verrà illustrato come utilizzare tali strumenti per installare pacchetti e relative dipendenze in un computer di destinazione.  
  
 Verranno innanzitutto eseguite le attività di preparazione alla distribuzione. Verrà creato un nuovo progetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] al quale verranno aggiunti i pacchetti e i file di dati esistenti. Non verrà creato alcun nuovo pacchetto da zero, bensì si utilizzeranno solo i pacchetti completi creati appositamente ai fini di questa esercitazione. Non sarà necessario modificare le funzionalità dei pacchetti dell'esercitazione, tuttavia, dopo avere aggiunto i pacchetti al progetto, potrebbe risultare utile aprirli in Progettazione [!INCLUDE[ssIS](../includes/ssis-md.md)] ed esaminarne i contenuti. In questo modo sarà possibile acquisire familiarità con i tipi di dipendenze dei pacchetti, ad esempio i file di log, e con le interessanti caratteristiche dei pacchetti.  
  
 Ai fini della distribuzione, si procederà inoltre all'aggiornamento dei pacchetti affinché utilizzino le configurazioni. Queste ultime rendono le proprietà e gli oggetti dei pacchetti aggiornabili in fase di esecuzione. In questa esercitazione le configurazioni verranno utilizzate per aggiornare le stringhe di connessione di file di testo e di log e i percorsi dei file XML e XSD utilizzati dai pacchetti. Per altre informazioni, vedere [Configurazioni di pacchetto](../../2014/integration-services/package-configurations.md) e [Creazione di configurazioni dei pacchetti](../../2014/integration-services/create-package-configurations.md).  
  
 Dopo aver verificato che i pacchetti vengono eseguiti correttamente in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], si creerà un pacchetto di distribuzione da utilizzare per installare i pacchetti. Il pacchetto di distribuzione include i file del pacchetto e altri elementi aggiunti al progetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , le dipendenze del pacchetto incluse automaticamente da [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] e l'utilità di distribuzione compilata dall'utente. Per altre informazioni, vedere [Creazione di un'utilità di distribuzione](../../2014/integration-services/create-a-deployment-utility.md).  
  
 Il pacchetto di distribuzione verrà quindi copiato nel computer di destinazione su cui verrà eseguita l'Installazione guidata pacchetti che consente di installare i pacchetti e le relative dipendenze. I pacchetti verranno installati nel database msdb di SQL Server, mentre i file ausiliari e di supporto verranno installati nel file system. Poiché i pacchetti distribuiti utilizzano le configurazioni, sarà necessario aggiornare queste ultime in modo che riflettano i nuovi valori necessari per l'esecuzione corretta dei pacchetti nell'ambiente in cui sono stati installati.  
  
 I pacchetti verranno infine eseguiti in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] mediante l'Utilità di esecuzione pacchetti.  
  
 L'obiettivo di questa esercitazione è simulare la complessità delle problematiche di una possibile distribuzione reale. Se non è possibile distribuire i pacchetti in un altro computer è comunque possibile eseguire l'esercitazione installando i pacchetti nel database msdb nell'istanza locale di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]e quindi eseguirli in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] nella medesima istanza.  
  
## <a name="what-you-will-learn"></a>Lezioni dell'esercitazione  
 Il modo più efficace per acquisire familiarità con i nuovi strumenti e controlli e con le caratteristiche disponibili in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] consiste nell'usarli. Questa esercitazione consente di eseguire in modo semplificato i passaggi necessari per creare un progetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] e quindi aggiungervi i pacchetti e gli altri file necessari. Dopo aver completato il progetto, si procederà alla creazione di un pacchetto di distribuzione, alla copia del pacchetto nel computer di destinazione e quindi all'installazione in quest'ultimo dei pacchetti.  
  
## <a name="requirements"></a>Requisiti  
 Questa esercitazione è destinata agli utenti già esperti nelle operazioni di base sul file system, ma con una limitata conoscenza delle nuove caratteristiche disponibili in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Per comprendere meglio basic [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] concetti che verranno usati in questa esercitazione, si potrebbe risultare utile completare prima la seguente [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] esercitazioni: [esegue il SQL Server importazione / esportazione guidata](import-export-data/start-the-sql-server-import-and-export-wizard.md) e[ Esercitazione SSIS: Creazione di un pacchetto ETL semplice](../integration-services/ssis-how-to-create-an-etl-package.md).  
  
 **Computer di origine.** È necessario che nel computer in cui verrà creato il pacchetto di distribuzione siano installati i componenti seguenti:  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] con il database AdventureWorks. Per una maggiore sicurezza, i database di esempio non vengono installati per impostazione predefinita. È possibile scaricare il database di esempio dal [CodePlex](http://msftdbprodsamples.codeplex.com/releases/view/125550).  
  
-   È necessario disporre delle autorizzazioni per creare ed eliminare tabelle in AdventureWorks.  
  
-   Ai fini di questa esercitazione sono inoltre necessari dati di esempio, pacchetti completi, configurazioni e un file Leggimi. I file necessari vengono installati insieme agli esempi. Se non si riesce a individuare i dati di esempio, tornare alla procedura sopra indicata e completare l'installazione come descritto.  
  
-   Ambiente di sviluppo di Business Intelligence, [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
 **Computer di destinazione.** È necessario che nel computer in cui verranno distribuiti i pacchetti siano installati i componenti seguenti:  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] con il database AdventureWorks.  
  
-   [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)](Indici per tabelle con ottimizzazione per la memoria).  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
-   È necessario disporre delle autorizzazioni per creare ed eliminare tabelle in AdventureWorks per eseguire i pacchetti in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
-   È necessario disporre di lettura e l'autorizzazione di scrittura nella tabella sysssispackages di msdb[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database di sistema.  
  
 Se si prevede di distribuire i pacchetti nello stesso computer in cui si crea il pacchetto di distribuzione, è necessario che tale computer soddisfi i requisiti di entrambi i sistemi di origine e di destinazione.  
  
 **Tempo stimato per il completamento dell'esercitazione:** 2 ore  
  
## <a name="lessons-in-this-tutorial"></a>Lezioni dell'esercitazione  
 [Lezione 1: Preparazione alla creazione del pacchetto di distribuzione](../integration-services/lesson-1-preparing-to-create-the-deployment-bundle.md)  
 In questa lezione verrà preparata la distribuzione di una soluzione ETL creando un nuovo progetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] e aggiungendovi i pacchetti e gli altri file necessari.  
  
 [Lezione 2: Creazione del pacchetto di distribuzione](../integration-services/lesson-2-create-the-deployment-bundle-in-ssis.md)  
 In questa lezione verrà compilata un'utilità di distribuzione e verrà verificato che il pacchetto di distribuzione includa i file necessari.  
  
 [Lezione 3: Installazione dei pacchetti](../integration-services/lesson-3-install-ssis-package.md)  
 In questa lezione si procederà alla copia del pacchetto di distribuzione nel computer di destinazione, all'installazione e quindi all'esecuzione dei pacchetti.  
  
![Icona di Integration Services (piccola)](media/dts-16.gif "icona di Integration Services (piccola)")**rimangono fino a Date con Integration Services** <br /> Per i download, gli articoli, gli esempi e i video Microsoft più recenti, oltre alle soluzioni selezionate dalla community, visitare la pagina [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sul sito MSDN:<br /><br /> [Visita la pagina di Integration Services su MSDN](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Per ricevere una notifica automatica su questi aggiornamenti, sottoscrivere i feed RSS disponibili nella pagina.  
  
  

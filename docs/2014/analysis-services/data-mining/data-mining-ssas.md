---
title: Data Mining (SSAS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], about data mining
ms.assetid: b1c912da-72f6-4d96-89c8-55a2c4f19e88
caps.latest.revision: 28
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6ff1d223cee1ce86851b3021bad15582db156639
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37163432"
---
# <a name="data-mining-ssas"></a>Data mining (SSAS)
  In [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] è disponibile una piattaforma integrata per le soluzioni in cui è incorporato il data mining. Per creare soluzioni di Business Intelligence con analisi predittiva è possibile utilizzare i dati relazionali o del cubo.  
  
## <a name="benefits-of-data-mining"></a>Vantaggi del data mining  
 Nel data mining vengono utilizzati principi statistici analizzati in modo approfondito per individuare modelli nei dati, consentendo di prendere decisioni intelligenti sui problemi complessi. Applicando gli algoritmi di data mining di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ai dati, è possibile prevedere tendenze, identificare modelli, creare regole e indicazioni, analizzare la sequenza di eventi in set di dati complessi e acquisire nuovi approfondimenti.  
  
 In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]il data mining è efficace, accessibile e integrato con gli strumenti preferiti dagli utenti per l'analisi e la creazione di report. Per ottenere un'utile panoramica generale sul data mining che si desidera avviare, vedere i collegamenti di questa sezione.  
  
## <a name="key-data-mining-features"></a>Caratteristiche principali del data mining  
 In SQL Server sono disponibili le caratteristiche seguenti per il supporto di soluzioni di data mining integrate:  
  
-   Più origini dati: non è necessario creare un data warehouse o un cubo OLAP per eseguire il data mining. È possibile utilizzare dati tabulari forniti da provider esterni o disponibili in fogli di calcolo o addirittura file di testo. È anche possibile eseguire il processo di data mining di cubi OLAP creati in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Tuttavia, non è possibile usare i dati di un database in memoria.  
  
-   Pulizia dati integrata, gestione dati ed ETL: in Data Quality Services sono disponibili strumenti avanzati per il profiling e la pulizia dei dati. Integration Services può essere utilizzato per compilare processi ETL per la pulizia dei dati, nonché per la compilazione, l'elaborazione, il training e l'aggiornamento di modelli.  
  
-   Più algoritmi personalizzabili: oltre a fornire algoritmi quali quelli di clustering, reti neurali e alberi delle decisioni, la piattaforma supporta lo sviluppo di algoritmi plug-in personalizzati.  
  
-   Infrastruttura di test del modello: testare i modelli e i set di dati utilizzando importanti strumenti statistici come la convalida incrociata, le matrici di classificazione, i grafici di accuratezza e a dispersione. Creare e gestire facilmente i set di testing e di training.  
  
-   Esecuzione di query e drill-through: creare query di stima, recuperare schemi e statistiche del modello ed eseguire il drill-through nei dati del case.  
  
-   Strumenti client: oltre agli strumenti di sviluppo e progettazione forniti da SQL Server, è possibile utilizzare i componenti aggiuntivi Data mining per Excel per creare ed esplorare i modelli, nonché per eseguirvi query. In alternativa creare client personalizzati, inclusi i servizi Web.  
  
-   Supporto del linguaggio di scripting e API gestita: tutti gli oggetti di data mining sono completamente programmabili. La generazione di script è possibile tramite MDX, XMLA o le estensioni PowerShell per [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Utilizzare il linguaggio DMX (Data Mining Extensions) per eseguire query e generare script velocemente.  
  
-   Sicurezza e distribuzione: tramite [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]viene fornita la sicurezza basata su ruoli, incluse autorizzazioni separate relative al drill-through per i dati del modello e della struttura. Distribuzione semplice di modelli agli altri server, in modo che gli utenti possano accedere agli schemi o effettuare stime  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 Negli argomenti di questa sezione sono illustrate le caratteristiche principali di Data mining di SQL Server e le attività correlate.  
  
-   [Concetti di data mining](data-mining-concepts.md)  
  
-   [Algoritmi di Data Mining &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md)  
  
-   [Strutture di data mining &#40;Analysis Services - Data Mining&#41;](mining-structures-analysis-services-data-mining.md)  
  
-   [Modelli di data mining &#40;Analysis Services - Data Mining&#41;](mining-models-analysis-services-data-mining.md)  
  
-   [Test e convalida &#40;Data Mining&#41;](testing-and-validation-data-mining.md)  
  
-   [Query di data mining](data-mining-queries.md)  
  
-   [Soluzioni di data mining](data-mining-solutions.md)  
  
-   [Strumenti di data mining](data-mining-tools.md)  
  
-   [Architettura di data mining](data-mining-architecture.md)  
  
-   [Panoramica della sicurezza &#40;Data Mining&#41;](security-overview-data-mining.md)  
  
  

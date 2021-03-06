---
title: Introduzione a SQL Server Management Studio per Business Intelligence | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio for Integration Services
- SQL Server Management Studio for Reporting Services
- SQL Server Management Studio for Analysis Services
ms.assetid: ffaa77b7-03d0-4d7a-aa42-c5091a4f2ceb
caps.latest.revision: 28
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 98dab4db89917fd4ece162420baa29dfe6930a2e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37175184"
---
# <a name="introduction-to-sql-server-management-studio-for-business-intelligence"></a>Introduzione a SQL Server Management Studio per Business Intelligence
  Per accedere, configurare, gestire e amministrare [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] e [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], utilizzare [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Sebbene le tre tecnologie di Business Intelligence si basino tutte su [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], le attività amministrative associate a ciascuna di esse sono leggermente diverse.  
  
> [!NOTE]  
>  Per creare e modificare soluzioni [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]e [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , utilizzare [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]e non [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] è un ambiente di sviluppo basato su [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="managing-analysis-services-solutions-using-sql-server-management-studio"></a>Gestione di soluzioni Analysis Services tramite SQL Server Management Studio  
 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] consente di gestire oggetti di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , ad esempio eseguendo backup ed elaborando oggetti.  
  
 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] include un progetto script di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] in cui è possibile sviluppare e salvare script creati in MDX (Multidimensional Expressions), DMX (Data Mining Extensions) e XMLA (XML per Analysis). Usare i progetti script di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] per eseguire attività di gestione o ricreare oggetti, ad esempio database e cubi in istanze di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . È possibile, ad esempio, sviluppare uno script XMLA in un progetto script di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] per la creazione diretta di nuovi oggetti in un'istanza di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] esistente. È possibile salvare i progetti script di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] come parte di una soluzione e integrarli con il controllo del codice sorgente.  
  
 Per altre informazioni su come usare [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], vedere [progetto script Analysis Services in SQL Server Management Studio](../analysis-services/instances/analysis-services-scripts-project-in-sql-server-management-studio.md).  
  
## <a name="managing-integration-services-solutions-using-sql-server-management-studio"></a>Gestione di soluzioni Integration Services tramite SQL Server Management Studio  
 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] consente di usare il servizio [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] per gestire i pacchetti e monitorare i pacchetti in esecuzione. È inoltre possibile utilizzare [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] per organizzare pacchetti in cartelle, eseguire pacchetti, importare ed esportare pacchetti, eseguire la migrazione di pacchetti DTS (Data Transformation Services) e aggiornare pacchetti di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
## <a name="managing-reporting-services-projects-using-sql-server-management-studio"></a>Gestione di progetti di Reporting Services tramite SQL Server Management Studio  
 Utilizzare SQL Server Management Studio per abilitare le funzionalità di Reporting Services, amministrare il server e i database e gestire ruoli e processi.  
  
 Lo strumento consente di gestire pianificazioni condivise tramite la cartella Pianificazioni condivise e di gestire i database del server di report (ReportServer e ReportServerTempdb). È inoltre possibile creare un ruolo RSExecRole nel database di sistema Master quando si sposta un database del server di report in un'istanza nuova o diversa del Motore di database SQL Server ([!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)]). Per ulteriori informazioni su queste attività, vedere gli argomenti seguenti:  
  
-   [Reporting Services in SQL Server Management Studio &#40;SSRS&#41;](../reporting-services/tools/reporting-services-in-sql-server-management-studio-ssrs.md)  
  
-   [Amministrare un Database del Server di Report &#40;modalità nativa SSRS&#41;](../reporting-services/report-server/report-server-database-ssrs-native-mode.md)  
  
-   [Creare RSExecRole](../reporting-services/security/create-the-rsexecrole.md)  
  
 Per gestire il server è inoltre possibile abilitare e configurare numerose funzionalità, configurare le impostazioni predefinite del server e gestire ruoli e processi. Per ulteriori informazioni su queste attività, vedere gli argomenti seguenti:  
  
-   [Impostare le proprietà Server di Report &#40;Management Studio&#41;](../reporting-services/tools/set-report-server-properties-management-studio.md)  
  
-   [Creare, eliminare o modificare un ruolo &#40;Management Studio&#41;](../reporting-services/security/role-definitions-create-delete-or-modify.md)  
  
-   [Abilitare e disabilitare la stampa sul lato client per Reporting Services](../reporting-services/report-server/enable-and-disable-client-side-printing-for-reporting-services.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione multidimensionali di modelli di utilizzo di SQL Server Data Tools &#40;SSDT&#41;](../analysis-services/multidimensional-models/creating-multidimensional-models-using-sql-server-data-tools-ssdt.md)   
 [Reporting Services in SQL Server Data Tools &#40;SSDT&#41;](../reporting-services/tools/reporting-services-in-sql-server-data-tools-ssdt.md)  
  
  

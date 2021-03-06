---
title: File per la gestione di soluzioni e progetti | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- projects [SQL Server Management Studio], files
- .ssmssln files
- .ssmsmobileproj files
- .ssmsasproj files
- .ssmssqlproj files
- .sqlsuo files
- files [SQL Server Management Studio], projects
ms.assetid: e19d2859-0b97-4727-ac27-c4c226d86b2f
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b2e52799292a0272cc31efb6fb6d31ca5285731e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37257807"
---
# <a name="files-that-manage-solutions-and-projects"></a>File per la gestione di soluzioni e progetti
  In questo argomento vengono descritti i tipi di file specifici per [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Per impostazione predefinita, tutte le soluzioni e i relativi progetti vengono creati in \Documenti\SQL Server Management Studio Projects.  
  
## <a name="management-studio-solution-files"></a>File della soluzione di Management Studio  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] usa tipi di file diversi di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] o [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio. Ciò vuol dire che non è possibile aprire una soluzione [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] o in Visual Studio. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] I file della soluzione consentono a Esplora soluzioni di visualizzare un'interfaccia grafica per la gestione dei file.  
  
|Estensione|Tipo di file|Description|Creato da|  
|---------------|---------------|-----------------|----------------|  
|ssmssln|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Oggetto della soluzione|Offre l'ambiente con riferimenti alla posizione sul disco di progetti, elementi di progetto e soluzione di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] |[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]|  
  
## <a name="management-studio-project-files"></a>File del progetto di Management Studio  
 Mentre le soluzioni contengono i file della soluzione per la gestione degli oggetti presenti in una soluzione, i progetti contengono i file del progetto. Il tipo di file del progetto creato da [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] per un progetto dipende dal modello utilizzato per la creazione del progetto stesso. Nella tabella seguente viene descritto il tipo di file creato per ogni progetto.  
  
|Estensione|Modelli di progetto|  
|---------------|----------------------|  
|ssmssqlproj|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Progetto di script|  
|ssmsasproj|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Progetto di script|  
  
## <a name="location-of-solution-level-files"></a>Posizione dei file a livello di soluzione  
 Per impostazione predefinita, i file a livello di soluzione vengono creati nella directory fisica del primo progetto creato con la soluzione. È possibile specificare una directory per la soluzione creando una soluzione oppure specificare la directory quando si crea un nuovo progetto.  
  
 Se la struttura della directory è simile alla struttura logica visualizzata in Esplora soluzioni, è più facile individuare i file del progetto e della soluzione e condividerli con altri sviluppatori di un team.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestire file con codifica](manage-files-with-encoding.md)   
 [File esterni](miscellaneous-files.md)   
 [Esplora soluzioni](solution-explorer.md)   
 [Soluzioni di &#40;SQL Server Management Studio&#41;](solutions-sql-server-management-studio.md)   
 [I progetti &#40;SQL Server Management Studio&#41;](projects-sql-server-management-studio.md)   
 [Controllo del codice sorgente di Esplora soluzioni](../../database-engine/solution-explorer-source-control.md)  
  
  

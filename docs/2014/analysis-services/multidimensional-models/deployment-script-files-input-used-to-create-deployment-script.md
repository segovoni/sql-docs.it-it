---
title: Informazioni sui file di Input utilizzati per creare lo Script di distribuzione | Microsoft Docs
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
- input files [Analysis Services]
- Analysis Services Deployment Wizard, scripts
- deploying [Analysis Services], input files
- Analysis Services Deployment Wizard, input files
- scripts [Analysis Services], deployment
- Analysis Services deployments, input files
- modifying input files
ms.assetid: 20e080cd-6a0e-4591-b022-ea4cd3638e36
caps.latest.revision: 32
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8c9666014d613792c4c12f202ea5e0b790130b6e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37189038"
---
# <a name="understanding-the-input-files-used-to-create-the-deployment-script"></a>Informazioni sui file di input utilizzati per creare uno script di distribuzione
  Quando si compila un progetto di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] genera file XML per il progetto. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] inserisce questi file XML nella cartella di Output del [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] progetto. Per impostazione predefinita l'output è situato nella cartella \Bin. Nella tabella seguente vengono elencati i file XML creati da [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] .  
  
|File XMLA|Description|  
|---------------|-----------------|  
|\<*nome del progetto*>. asdatabase|Contiene le definizioni dichiarative per tutti gli oggetti [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] contenuti nel progetto.|  
|\<*nome del progetto*>. deploymenttargets|Contiene il nome dell'istanza [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] e del database in cui verranno creati gli oggetti [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|\<*nome del progetto*>. configsettings|Contiene le impostazioni specifiche all'ambiente, quali le informazioni sulla connessione all'origine dati e i percorsi di archiviazione degli oggetti. Le impostazioni in questo file sostituiscono le impostazioni nel \< *nome progetto*> file con estensione asdatabase.|  
|\<*nome del progetto*>. deploymentoptions|Contiene le opzioni di distribuzione, come ad esempio se la distribuzione è transazionale o se gli oggetti distribuiti vanno elaborati dopo la distribuzione.|  
  
> [!NOTE]  
>  Nei file di progetto di [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] non vengono mai archiviate password.  
  
## <a name="modifying-the-input-files"></a>Modifica del file di input  
 Modificando i valori nei file di input o i valori recuperati dai file di input, è possibile modificare la destinazione di distribuzione, le impostazioni di configurazione e le opzioni di distribuzione senza dover modificare l'intero \< *progetto nome*> file con estensione asdatabase (o un intero file script XMLA se si genera uno script da un oggetto esistente [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database). La possibilità di modificare singoli file facilita la creazione di script di distribuzione diversi per vari scopi.  
  
 Gli argomenti seguenti illustrano come modificare valori nei vari file di input:  
  
-   [Impostazione della destinazione di installazione](deployment-script-files-specifying-the-installation-target.md)  
  
-   [Impostazione delle opzioni di distribuzione dei ruoli e delle partizioni](deployment-script-files-partition-and-role-deployment-options.md)  
  
-   [Definizione delle impostazioni di configurazione per la distribuzione di soluzioni](deployment-script-files-solution-deployment-config-settings.md)  
  
-   [Impostazione delle opzioni di elaborazione](deployment-script-files-specifying-processing-options.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esegue la distribuzione guidata Analysis Services](running-the-analysis-services-deployment-wizard.md)   
 [Informazioni sullo script di distribuzione di Analysis Services](understanding-the-analysis-services-deployment-script.md)  
  
  

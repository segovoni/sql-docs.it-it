---
title: Gestire il servizio Integration Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Integration Services service, configuring
- services [Integration Services], configuring
ms.assetid: 45554117-a0df-4830-b41c-5ebb33b764a5
caps.latest.revision: 60
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5e356283274c7ea741acfabcd6d56cb6bc0db7ea
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37281517"
---
# <a name="manage-the-integration-services-service"></a>Gestione del servizio Integration Services
    
> [!IMPORTANT]  
>  In questo argomento viene illustrato il servizio [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , un servizio Windows per la gestione dei pacchetti di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] supporta il servizio per la compatibilità con le versioni precedenti di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. A partire da [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], è possibile gestire oggetti come i pacchetti del server Integration Services.  
  
 Quando viene installato il componente [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], viene installato anche il servizio [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Per impostazione predefinita, il servizio [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] viene avviato e impostato per l'avvio automatico. È tuttavia necessario installare [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] per utilizzare il servizio per la gestione di pacchetti [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] archiviati e in esecuzione.  
  
> [!NOTE]  
>  Non è possibile connettersi a un'istanza del [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] servizio le [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] versione di [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]. Vale a dire, nella **Connetti al Server** nella finestra di dialogo è possibile specificare il nome di un server in cui solo il [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] versione del [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] servizio è in esecuzione. Tuttavia, è possibile modificare il file di configurazione per il servizio e gestire i pacchetti vengono archiviati in un'istanza di [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] dal [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] versione di [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]. Per altre informazioni, vedere [Configurazione del servizio Integration Services &#40;SSIS&#41;](service/integration-services-service-ssis-service.md).  
  
 È possibile installare solo una singola istanza del servizio [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] in un computer. Il servizio non è specifico di una particolare istanza del [!INCLUDE[ssDE](../includes/ssde-md.md)]. Connettersi al servizio utilizzando il nome del computer sul quale è in esecuzione il servizio.  
  
 Per la gestione del servizio [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] è possibile usare uno dei seguenti snap-in di Microsoft Management Console (MMC): Gestione configurazione SQL Server o Servizi di SQL Server. Per gestire pacchetti in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], è prima di tutti necessario assicurarsi che il servizio sia avviato.  
  
 Per impostazione predefinita, il servizio [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] è configurato per gestire i pacchetti archiviati nel database msdb dell'istanza del [!INCLUDE[ssDE](../includes/ssde-md.md)] installata in contemporanea con [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Se contemporaneamente non viene installata alcuna istanza del [!INCLUDE[ssDE](../includes/ssde-md.md)], il servizio [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] è configurato per gestire i pacchetti contenuti nel database msdb dell'istanza predefinita locale del [!INCLUDE[ssDE](../includes/ssde-md.md)]. Per gestire pacchetti archiviati in un'istanza denominata o un'istanza remota del [!INCLUDE[ssDE](../includes/ssde-md.md)] o in più istanze del [!INCLUDE[ssDE](../includes/ssde-md.md)], è necessario modificare il file di configurazione per il servizio. Per altre informazioni, vedere [Configurazione del servizio Integration Services &#40;SSIS&#41;](service/integration-services-service-ssis-service.md).  
  
 Per impostazione predefinita, il servizio [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] è configurato in modo che i pacchetti in esecuzione vengano arrestati all'arresto del servizio. Il servizio [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], tuttavia, non attende che i pacchetti vengano arrestati e l'esecuzione di alcuni pacchetti potrebbe continuare dopo l'arresto del servizio [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
 Se il servizio [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] viene arrestato, è possibile continuare a eseguire pacchetti tramite l'Importazione/Esportazione guidata [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], Progettazione [!INCLUDE[ssIS](../includes/ssis-md.md)], l'Utilità di esecuzione pacchetti e l'utilità del prompt dei comandi **dtexec** (dtexec.exe). Non è tuttavia possibile eseguire il monitoraggio dei pacchetti in esecuzione.  
  
 Per impostazione predefinita, il servizio [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] viene eseguito nel contesto dell'account NETWORK SERVICE.  
  
 Il servizio [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] esegue registrazioni nel registro eventi di Windows. È possibile visualizzare gli eventi del servizio in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. È anche possibile visualizzare gli eventi del servizio utilizzando il Visualizzatore eventi di Windows.  
  
### <a name="to-set-properties-of-integration-services-service-using-the-services-snap-in"></a>Per impostare le proprietà del servizio Integration Services tramite lo snap-in Servizi  
  
-   [Impostare le proprietà del servizio Integration Services](../../2014/integration-services/set-the-properties-of-the-integration-services-service.md)  
  
### <a name="to-view-service-events-for-integration-services-service"></a>Per visualizzare gli eventi per il servizio di Integration Services  
  
-   [Visualizzare eventi per il servizio Integration Services](../../2014/integration-services/view-events-for-the-integration-services-service.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Servizio Integration Services &#40;servizio SSIS&#41;](service/integration-services-service-ssis-service.md)   
 [Configurazione dell'integrazione dei servizi del servizio &#40;servizio SSIS&#41;](configuring-the-integration-services-service-ssis-service.md)   
 [SQL Server importazione / esportazione guidata](import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md)   
 [Utilità dtexec](packages/dtexec-utility.md)   
 [Esecuzione di progetti e pacchetti](packages/run-integration-services-ssis-packages.md)  
  
  

---
title: Reporting Services le opzioni di configurazione (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.ins.instwizard.reportserverinstoptions.f1
helpviewer_keywords:
- Report Server Installation Options page [SQL Server Installation Wizard]
- report servers [Reporting Services], installing
- SQL Server Installation Wizard, Report Server Installation Options page
ms.assetid: e4561f6c-bc7f-467e-821a-cde8e5cd7391
caps.latest.revision: 43
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 8dff91a860d801257d9228dd904cbe36855504cc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37327081"
---
# <a name="reporting-services-configuration-options-ssrs"></a>Opzioni di configurazione di Reporting Services (SSRS)
  Usare la pagina **Configurazione di Reporting Services** dell'Installazione guidata di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per specificare le modalità di installazione e di configurazione di un'istanza del server di report. La disponibilità di un'opzione di installazione dipende dalle opzioni scelte in precedenza nella pagina **Selezione funzionalità** e dall'installazione o meno di un'istanza locale del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] contemporaneamente all'installazione del server di report.  
  
 In alcuni casi, se nel computer è installato un certificato Secure Sockets Layer (SSL) associato a un carattere jolly complesso, il programma di installazione creerà gli URL di Reporting Services utilizzando il prefisso HTTPS. Per altre informazioni sul mapping dei certificati agli URL di Reporting Services, vedere [configuri un Server di Report per connessioni Secure Sockets Layer (SSL)](http://go.microsoft.com/fwlink/?LinkId=199089) (http://go.microsoft.com/fwlink/?LinkId=199089) nella documentazione Online di SQL Server.  
  
 Per informazioni più recenti relative a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] e all'installazione e configurazione di questa versione, vedere [informazioni aggiuntive sull'installazione](http://go.microsoft.com/fwlink/?LinkId=207425) (http://go.microsoft.com/fwlink/?LinkId=207425).  
  
## <a name="options"></a>Opzioni  
  
### <a name="reporting-services-native-mode"></a>Modalità nativa di Reporting Services  
 Se non è possibile eseguire la configurazione predefinita del server di report poiché uno o più requisiti non vengono soddisfatti, l'Installazione guidata consentirà solo l'opzione di installazione minima. Al termine dell'installazione, sarà possibile copiare i file necessari e utilizzare Gestione configurazione Reporting Services per configurare un server di report in modalità nativa.  
  
> [!NOTE]  
>  La presenza di un file di database del server di report può impedire l'installazione se si seleziona una delle opzioni di installazione predefinite. Quando si seleziona un'opzione di installazione predefinita, il programma di installazione tenta di creare un database del server di report utilizzando il nome predefinito. Se è già presente un database con lo stesso nome, l'installazione avrà esito negativo e sarà necessario eseguirne il rollback. Per evitare questo problema, è possibile rinominare il database esistente prima di eseguire l'installazione oppure selezionare l'opzione **Solo installazione** in modo da poter specificare impostazioni personalizzate per il database al termine dell'installazione.  
  
#### <a name="install-and-configure"></a>Installazione e configurazione  
 Consente di installare un'istanza del server di report in modalità nativa utilizzando i valori predefiniti per i database del server di report, l'account del servizio e le prenotazioni di URL. Se si sceglie questa opzione, l'istanza del server di report è pronta per essere utilizzata al termine dell'installazione. Durante l'installazione viene creato un database del server di report utilizzando un'istanza locale di [!INCLUDE[ssDE](../../includes/ssde-md.md)] e viene configurato un server di report per l'utilizzo dei valori predefiniti.  
  
 Questa opzione è disponibile solo se i valori predefiniti utilizzati nell'installazione di un server di report sono validi per il sistema. Questa opzione è consigliabile per gli sviluppatori che desiderano installare tutti i componenti localmente e per gli utenti che desiderano valutare il software.  
  
 Per visualizzare le informazioni relative alle impostazioni predefinite usate durante l'installazione o per individuare i motivi per cui è impossibile installare la configurazione predefinita, fare clic su **Dettagli**. Per altre informazioni sulla configurazione predefinita per un server di report in modalità nativa, vedere [configurazione predefinita per un'installazione in modalità nativa (Reporting Services)](http://go.microsoft.com/fwlink/?LinkId=199091) (http://go.microsoft.com/fwlink/?LinkId=199091).  
  
#### <a name="install-only"></a>Solo installazione  
 Consente di installare i file di programma del server di report, di creare l'account del servizio del server di report e di registrare il provider di Strumentazione gestione Windows (WMI) per il server di report. Questa opzione di installazione viene definita installazione di tipo "solo file". Selezionare questa opzione se non si desidera utilizzare la configurazione predefinita. Se la configurazione predefinita non può essere installata o se si esegue l'installazione di un cluster di failover di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che include [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], questa è l'unica opzione disponibile. Per altre informazioni su un'installazione "solo file", vedere [modalità installazione (Reporting Services)](http://go.microsoft.com/fwlink/?LinkId=199093) (http://go.microsoft.com/fwlink/?LinkId=199093).  
  
 Al termine dell'installazione, è necessario creare il database del server di report e configurare quest'ultimo prima di utilizzarlo. Per configurare un server di report e creare il database, utilizzare Gestione configurazione Reporting Services. Per altre informazioni, vedere [procedura: creare un database del Server di Report (configurazione di Reporting Services)](http://go.microsoft.com/fwlink/?LinkId=199094) (http://go.microsoft.com/fwlink/?LinkId=199094) e [configura una connessione di Database Server di Report](http://go.microsoft.com/fwlink/?LinkId=199095) (http://go.microsoft.com/fwlink/?LinkId=199095).  
  
### <a name="reporting-services-sharepoint-mode"></a>Modalità SharePoint di Reporting Services  
  
#### <a name="install-only"></a>Solo installazione  
 Consente di installare i file di programma del server di report e i cmdlet di PowerShell. Al termine dell'installazione, sarà necessario avviare SharePoint Services per [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] e creare un'applicazione di servizio [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Per altre informazioni, vedere quanto riportato di seguito.  
  
-   [Installazione di Reporting Services Server di Report in modalità SharePoint per Power View e avvisi dati](http://go.microsoft.com/fwlink/?LinkId=207543) (http://go.microsoft.com/fwlink/?LinkId=207543).  
  
-   [Installare Reporting Services in modalità SharePoint come singola Server Farm](http://go.microsoft.com/fwlink/?LinkId=207544) (http://go.microsoft.com/fwlink/?LinkId=207544).  
  
-   [Server di Report (SSRS) Reporting](http://go.microsoft.com/fwlink/?LinkID=207244) (http://go.microsoft.com/fwlink/?LinkID=207244).  
  
## <a name="installing-the-reporting-services-add-in-for-sharepoint-technologies"></a>Installazione del componente aggiuntivo Reporting Services per le tecnologie SharePoint  
 A partire dalla versione [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , è possibile installare il componente aggiuntivo come parte dell'installazione di SQL Server, nella pagina Selezione funzionalità dell'Installazione guidata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 È tuttavia possibile installare il componente aggiuntivo di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] per SharePoint 2010 mediante uno dei metodi seguenti:  
  
-   Eseguire lo strumento di preparazione dei prodotti SharePoint 2010 **PreRequisiteInstaller.exe**.  
  
-   Eseguire l'installazione dal supporto di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Fare clic sul file **rsSharePoint.msi** nella cartella Setup nel supporto di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] al termine dell'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Scaricare e installare il componente aggiuntivo. Per altre informazioni, vedere [dove trovare il componente aggiuntivo di Reporting Services per prodotti SharePoint](http://go.microsoft.com/fwlink/?LinkID=208634) (http://go.microsoft.com/fwlink/?LinkID=208634).  
  
## <a name="see-also"></a>Vedere anche  
 [Avviare Gestione configurazione Reporting Services](http://go.microsoft.com/fwlink/?LinkId=199096)   
 [Creare un database del Server di Report (configurazione di Reporting Services)](http://go.microsoft.com/fwlink/?LinkId=199094)   
 [Eseguire l'aggiornamento e la migrazione di Reporting Services](http://go.microsoft.com/fwlink/?LinkID=245628)   
 [Installazione dal prompt dei comandi delle modalità SharePoint e nativa di Reporting Services](http://go.microsoft.com/fwlink/?LinkId=217620)  
  
  

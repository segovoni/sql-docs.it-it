---
title: Requisiti hardware e Software per Server di Analysis Services in modalità SharePoint (SQL Server 2014) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: fb86ca0a-518c-4c61-ae78-7680c57fae1f
caps.latest.revision: 17
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 2bd9afb97eae82bdb3bfe63859e9081dca5586b4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37232671"
---
# <a name="hardware-and-software-requirements-for-analysis-services-server-in-sharepoint-mode-sql-server-2014"></a>Requisiti hardware e software per il server Analysis Services in modalità SharePoint (SQL Server 2014)
  [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] supporta SharePoint 2010 e SharePoint 2013. [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013 viene eseguito all'esterno della farm di SharePoint sebbene possa essere installato nei server SharePoint. [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2010 viene eseguito nei server applicazioni in una farm di SharePoint 2010 e, per supportare le operazioni del server, vengono utilizzate le funzionalità e l'infrastruttura di SharePoint. Per installare [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] per qualsiasi versione di SharePoint, utilizzare l'Installazione guidata di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Al termine dell'installazione, eseguire le operazioni seguenti:  
  
-   Eseguire la versione dello strumento di configurazione di [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] appropriata per la versione di SharePoint.  
  
-   Per SharePoint 2013, installare il [installare o disinstallare PowerPivot per SharePoint Add-in &#40;SharePoint 2013&#41;](../../analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013.md).  

  
##  <a name="bkmk_sqleditions"></a> Requisiti relativi all'edizione di SQL Server  
 Funzionalità di business intelligence non sono tutti disponibili in tutte le edizioni di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Per informazioni dettagliate, vedere [funzionalità supportate dalle edizioni di SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md) e [edizioni e componenti di SQL Server 2014](../editions-and-components-of-sql-server-2016.md).  
  
 Vedere le note sulla versione corrente [Microsoft SQL Server 2014 Release Notes](http://go.microsoft.com/fwlink/?LinkID=296445).  
  

  
##  <a name="bkmk_sqllicense"></a> Licenza di SQL Server  
 Per ulteriori informazioni sulle licenza di SQL Server, vedere quanto riportato di seguito:  
  
-   [Foglio dati delle licenze di SQL Server 2014](http://download.microsoft.com/download/6/6/F/66FF3259-1466-4BBA-A505-2E3DA5B2B1FA/SQL_Server_2014_Licensing_Datasheet.pdf) (http://download.microsoft.com/download/6/6/F/66FF3259-1466-4BBA-A505-2E3DA5B2B1FA/SQL_Server_2014_Licensing_Datasheet.pdf).  
  
-   [Come acquistare: Modelli di licenza di SQL Server il supporto](http://www.microsoft.com/server-cloud/products/sql-server/buy.aspx#fbid=Zae0-E6r5oh) (http://www.microsoft.com/server-cloud/products/sql-server/buy.aspx#fbid=Zae0-E6r5oh).  
  

  
##  <a name="bkmk_ssas__sharepoint_2013"></a> Analysis Services installato in SharePoint 2013  
 Se il server Analysis Services viene installato in modalità SharePoint in un server autonomo, i requisiti minimi di sistema sono basati su [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], anziché sui requisiti del server SharePoint.  
  
 [Requisiti hardware e software per l'installazione di SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md)  
  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint registra un'esecuzione ottimale nei server aziendali di nuova generazione che offrono soglie RAM superiori e maggiori funzionalità di elaborazione. Per archiviare i dati di [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] in memoria vengono utilizzate grandi quantità di RAM. La RAM supporta la capacità di adattarsi alle modifiche strutturali. I processori aggiuntivi supportano le analisi con esecuzione prolungata di dati non elaborati e non aggregati. Per la struttura dei dati si presuppone un ambiente dinamico, in risposta a un'analisi dei dati guidata dall'utente avviata tramite un client o un'interfaccia front-end di Excel.  
  
> [!TIP]  
>  In [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint vengono utilizzate le cache L2 e L3. Per migliorare le prestazioni, prendere in considerazione l'utilizzo di processori con cache L2 e L3 più grandi.  
  
 Nella tabella seguente viene fornita una descrizione delle configurazioni hardware minima e consigliata per un server [!INCLUDE[ssGeminiShortvnext](../../includes/ssgeminishortvnext-md.md)] autonomo che non fa parte della farm di SharePoint:  
  
|Componente|Minimo|Consigliato|  
|---------------|-------------|-----------------|  
|Processore|Processore dual-core a 64 bit, 3 GHz.|16 core|  
|RAM|8 GB di RAM|64 GB di RAM|  
|Archiviazione|80 GB di archiviazione|Almeno 80 GB|  
  
 Se il server Analysis Services viene installato in modalità SharePoint in un server della farm di SharePoint, verificare i requisiti minimi di sistema per [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e per il server di SharePoint visitando i collegamenti seguenti:  
  
-   [Requisiti hardware e software per l'installazione di SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md)  
  
-   [Requisiti hardware e software per SharePoint 2013](http://technet.microsoft.com/library/cc262485\(office.15\).aspx).  
  
 Le indicazioni standard relative al software e all'hardware di SharePoint 2013 riguardano una soluzione di gestione documenti basata sul Web per un gruppo di lavoro o un team. Poiché nell'elaborazione di [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] impiega un'elevata quantità di dati, l'indicazione standard è sufficiente solo se il carico di lavoro complessivo è ridotto, ad esempio meno di 100 utenti o cartelle di lavoro. Per una distribuzione di [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] di dimensioni maggiori è richiesta una potenza di calcolo superiore.  
  

  
##  <a name="bkmk_ssas__sharepoint_2010"></a> Analysis Services installato in un Server SharePoint 2010  
 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2010 viene eseguito nei server applicazioni in una farm di SharePoint 2010 e, per supportare le operazioni del server, vengono utilizzate le funzionalità e l'infrastruttura di SharePoint. Nella tabella seguente sono riepilogati i requisiti relativi alle distribuzioni di SharePoint 2010:  
  
|Componente|Requisito|  
|---------------|-----------------|  
|Versione di SharePoint|SharePoint 2010 Enterprise con Excel Services, servizio di archiviazione sicura e Attestazioni per il servizio token Windows configurati nella stessa server farm.<br /><br /> SharePoint deve essere installato utilizzando l'opzione Server farm in Installazione di SharePoint (l'opzione di installazione autonoma di SharePoint non è supportata). [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] richiede un'infrastruttura di server farm per supportare l'accesso amministrativo e ai dati. L'installazione autonoma non fornisce questi servizi.<br /><br /> L'edizione Developer, eseguita in Windows 7 o Windows Vista, non è supportata per le installazioni del server [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)].|  
|Service Pack|È richiesto SharePoint Server 2010 Service Pack 1 (SP1).<br /><br /> È necessaria per SharePoint 2010 Service Pack 1 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] funzionalità.<br /><br /> È richiesto l'aggiornamento cumulativo di agosto 2010 di SharePoint 2010 o versione successiva in caso di aggiornamento da una versione precedente di [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] a [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]. È consigliabile installare l'aggiornamento cumulativo di agosto 2010 o versione successiva dopo l'installazione di SharePoint Service Pack 1. Una nuova installazione di [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] non richiede l'aggiornamento cumulativo. Per altre informazioni, vedere [agosto 2010 è stato rilasciato un aggiornamento cumulativo per SharePoint](http://blogs.technet.com/b/stefan_gossner/archive/2010/09/02/august-2010-cumulative-update-for-sharepoint-has-been-released.aspx).|  
|Applicazione Web SharePoint|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint 2010 supporta solo le applicazioni Web SharePoint configurate per l'autenticazione in modalità classica. Se si aggiunge [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint a una farm esistente, assicurarsi che l'applicazione Web con cui si intende utilizzarlo sia configurata per l'autenticazione in modalità classica. Per istruzioni su come controllare la modalità di autenticazione, vedere la sezione "verificare che l'applicazione Web utilizzi l'autenticazione in modalità classica" in [distribuire soluzioni PowerPivot in SharePoint](../../analysis-services/power-pivot-sharepoint/deploy-power-pivot-solutions-to-sharepoint.md).|  
|Provider di dati necessari per l'aggiornamento dei dati lato server [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]|Per l'aggiornamento dei dati lato server vengono ripetuti gli stessi passaggi per il recupero dei dati utilizzati per importare inizialmente i dati. Questo significa che i provider di dati utilizzati per importare i dati in una workstation client devono essere presenti anche nel server [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint.<br /><br /> Inoltre, utilizzando feed di dati in un server SharePoint è necessario disporre di ADO.NET Data Services. Questo software non viene installato tramite il programma di installazione dei prerequisiti di SharePoint. È necessario installare il software seguente manualmente.<br /><br /> Assembly di runtime di ADO.NET Data Services 3.5 SP1, utilizzati per esportare un elenco SharePoint come feed di dati. Scaricare e installare la versione che corrisponde al sistema operativo:<br /><br /> Per Windows Server 2008 R2, utilizzare [aggiornamento di ADO.NET Data Services per .NET Framework 3.5 SP1 per Windows 7 e windows Server 2008 R2 (http://go.microsoft.com/fwlink/?LinkId=182557)](http://go.microsoft.com/fwlink/?LinkId=182557). Windows Server 2008 R2 **SP1** contiene già il provider aggiornato.<br /><br /> Per Windows Server 2008, utilizzare [aggiornamento di ADO.NET Data Services per .NET Framework 3.5 SP1 per Windows 2000, Windows Server 2003, Windows XP, Windows Vista e Windows Server 2008 (http://go.microsoft.com/fwlink/?LinkId=158125)](http://go.microsoft.com/fwlink/?LinkId=158125).|  
  
 [Determinare l'Hardware e Software (requisiti (SharePoint 2010)http://go.microsoft.com/fwlink/?LinkId=169734)](http://go.microsoft.com/fwlink/?LinkId=169734)  
  
 
  
## <a name="additional-information"></a>Informazioni aggiuntive  
 Per informazioni sulle modifiche di SharePoint, vedere [modifiche da SharePoint 2010 a SharePoint 2013](http://technet.microsoft.com/library/ff607742\(office.15\).aspx) (http://technet.microsoft.com/library/ff607742(office.15).aspx).  
  

  
  

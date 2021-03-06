---
title: Creare report per dispositivi mobili con SQL Server Mobile Report Publisher | Microsoft Docs
description: Informazioni sui report per dispositivi mobili di Reporting Services, ottimizzati per i dispositivi mobili, connessi ai dati locali e provvisti di un'ampia gamma di visualizzazioni dei dati.
ms.custom: ''
ms.date: 03/30/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.component: mobile-reports
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
ms.assetid: a5a8dbf6-4c3a-435d-8188-d6656c32f229
caps.latest.revision: 35
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ef6d130944b67f35140652fcf81be27d1e4aae91
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33018638"
---
# <a name="create-mobile-reports-with-sql-server-mobile-report-publisher"></a>Creare report per dispositivi mobili con SQL Server Mobile Report Publisher
Informazioni su report per dispositivi mobili di [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] , ottimizzati per i dispositivi mobili e connessi ai dati locali, con un'ampia gamma di visualizzazioni dei dati. 

>[!NOTE]
>  è necessario eseguire la migrazione del contenuto di Datazen Server, ad esempio dashboard e indicatori KPI, a un server di SQL Server 2016 [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] ? Provare a usare [Migration Assistant di SQL Server per Datazen](https://www.microsoft.com/en-us/download/details.aspx?id=53128). 
 
![SS_MRP_LayoutTabSm](../../reporting-services/media/ss-mrp-layouttabsm.png)  

Con [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-long.md)]è possibile creare rapidamente report per dispositivi mobili di [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] , ottimizzati per i dispositivi mobili, oltre a un'ampia gamma di altri fattori di forma. I report per dispositivi mobili offrono un'ampia gamma di visualizzazioni, ad esempio grafici temporali, categorie e di confronto, mappe ad albero e mappe personalizzate. 

* È possibile connettere i report per dispositivi mobili a una gamma di origini dati, inclusi i dati locali di SQL Server e Analysis Services. 
* I report per dispositivi mobili possono essere disposti in un'area di progettazione con righe e colonne della griglia regolabili ed elementi flessibili che si adattano in modo ottimale agli schermi di qualsiasi dimensione. 
* È quindi possibile salvare i report per dispositivi mobili in un server di Reporting Services, visualizzarli e modificarli in un browser o nell'app Power BI per dispositivi mobili su iPad, iPhone, telefoni e tablet Android e dispositivi Windows 10.
  
## <a name="create-includessrsnoversionmdincludesssrsnoversion-mdmd--mobile-reports"></a>Creare report per dispositivi mobili di [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)]  
  
Questi articoli includono informazioni utili per iniziare.
-  Scaricare [SQL Server Mobile Report Publisher](http://go.microsoft.com/fwlink/?LinkID=733527)  
-  [Creare un report per dispositivi mobili di Reporting Services](../../reporting-services/mobile-reports/create-a-reporting-services-mobile-report.md)  
-  Blog di Christopher Finlan che descrive la[procedura dettagliata per creare report per dispositivi mobili e indicatori KPI in SQL Server 2016 Reporting Services](http://christopherfinlan.com/2015/12/21/how-to-create-mobile-reports-and-kpis-in-sql-server-reporting-services-2016-an-end-to-end-walkthrough/)   
- [Design first, or data first](../../reporting-services/mobile-reports/design-first-or-data-first-when-creating-in-reporting-services-mobile-reports.md)(Iniziare con la progettazione o con i dati): decidere se iniziare a progettare il report con dati simulati o con i propri dati.  
- [Dati per report di Reporting Services per dispositivi mobili](../../reporting-services/mobile-reports/data-for-reporting-services-mobile-reports.md): usare dati da set di dati condivisi o preparare dati da cartelle di lavoro di Excel per usarli nei report per dispositivi mobili.
- [How data refresh works in mobile reports and KPIs in Reporting Services](http://christopherfinlan.com/2016/02/10/so-refreshinghow-data-refresh-works-with-mobile-reports-and-kpis-in-reporting-services/) (Come funziona l'aggiornamento dei dati nei report per dispositivi mobili e negli indicatori KPI): blog di Christopher Finlan che descrive come impostare la memorizzazione nella cache di set di dati condivisi per controllare la frequenza dell'aggiornamento dei dati e velocizzare le prestazioni dei report.
- [Visualizations in mobile reports](../../reporting-services/mobile-reports/add-visualizations-to-reporting-services-mobile-reports.md)
- [Gauges in mobile reports](../../reporting-services/mobile-reports/add-gauges-to-mobile-reports-reporting-services.md)
- [Maps in mobile reports](../../reporting-services/mobile-reports/maps-in-reporting-services-mobile-reports.md)
- [Brand your web portal and mobile reports](../../reporting-services/branding-the-web-portal.md) (Personalizzare il portale Web e i report per dispositivi mobili) con i colori e il logo dell'organizzazione
  
## <a name="ssrs-mobile-reports-in-the-power-bi-mobile-apps"></a>Report per dispositivi mobili SSRS nelle app Power BI per dispositivi mobili

-  Vedere [Reporting Services mobile reports and KPIs in the iOS mobile app](https://powerbi.microsoft.com/documentation/powerbi-mobile-iphone-kpis-mobile-reports) (Report per dispositivi mobili e indicatori KPI di Reporting Services nell'app per dispositivi mobili iOS)
-  Vedere [Reporting Services mobile reports and KPIs in the Power BI app for Android devices](https://powerbi.microsoft.com/documentation/powerbi-mobile-android-kpis-mobile-reports) (Report per dispositivi mobili di Reporting Services e indicatori KPI nell'app Power BI per dispositivi Android)
-  Vedere [Report nell'app Power BI per dispositivi mobili per Windows 10](https://powerbi.microsoft.com/documentation/powerbi-mobile-win10-kpis-mobile-reports/)    

## <a name="see-also"></a>Vedere anche  
  
-   [Creare, modificare ed eliminare origini dati condivise (SSRS)](../../reporting-services/report-data/create-modify-and-delete-shared-data-sources-ssrs.md)  
-   [Gestire set di dati condivisi](../../reporting-services/report-data/manage-shared-datasets.md)  
-  [Usare gli indicatori KPI in Reporting Services](../../reporting-services/working-with-kpis-in-reporting-services.md)  
- [Abilitare un server di report per l'accesso a Power BI per dispositivi mobili](../../reporting-services/report-server/enable-a-report-server-for-power-bi-mobile-access.md)  

  
  


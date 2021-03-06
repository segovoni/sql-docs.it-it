---
title: Usare Sottoscrizioni personali (server di report in modalità nativa) | Microsoft Docs
ms.custom: ''
ms.date: 07/01/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: subscriptions
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [Reporting Services], My Subscriptions page
- My Subscriptions page [Reporting Services]
ms.assetid: e96623ba-677e-4748-8787-f32bed3b5c12
caps.latest.revision: 40
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 30a734780d7eb042d0502466bebfdacfa8f9af23
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33029448"
---
# <a name="use-my-subscriptions-native-mode-report-server"></a>Usare Sottoscrizioni personali (server di report in modalità nativa)
Nel portale Web di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] è disponibile la pagina **Sottoscrizioni personali** nella quale possono essere gestite tutte le sottoscrizioni di un utente. La pagina *Sottoscrizioni personali* consente infatti di visualizzare, modificare, abilitare, disabilitare ed eliminare le sottoscrizioni esistenti. Non è tuttavia possibile utilizzarla per creare sottoscrizioni.  Nella pagina Sottoscrizioni personali sono visualizzate solo le sottoscrizioni create dall'utente che vi accede. Non sono elencate né sottoscrizioni di proprietà di altri utenti, nemmeno se questi sono sottoscrittori delle sottoscrizioni elencate, né sottoscrizioni guidate dai dati.
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
  
Il campo di ricerca consente di filtrare dinamicamente l'elenco delle sottoscrizioni, dal momento che non è possibile individuare una sottoscrizione eseguendo ricerche per nome o altri tipi di ricerche, ad esempio in base al trigger, alle informazioni di stato e così via. Per altre informazioni, vedere [Creare e gestire sottoscrizioni per server di report in modalità nativa](../../reporting-services/subscriptions/create-and-manage-subscriptions-for-native-mode-report-servers.md).
  
## <a name="to-open-the-my-subscriptions-page"></a>Per aprire la pagina Sottoscrizioni personali  
1. Aprire il portale Web di [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] .
2. Fare clic su Impostazioni ![ssrs_portal_settings_gear](../../reporting-services/subscriptions/media/ssrs-portal-settings-gear.png) nella barra degli strumenti.
3. Fare clic su **Sottoscrizioni personali**.

Per altre informazioni, vedere [Web portal (SSRS Native Mode)](../../reporting-services/web-portal-ssrs-native-mode.md).

## <a name="use-windows-powershell-to-list-mysubscriptions"></a>Utilizzare Windows PowerShell per elencare MySubscriptions  
 ![Contenuto correlato di PowerShell](../../analysis-services/instances/install-windows/media/rs-powershellicon.jpg "Contenuto correlato di PowerShell")  
  
 Tramite il seguente script di PowerShell verrà restituito l'elenco delle sottoscrizioni e delle proprietà di sottoscrizione per l'utente corrente. Per altre informazioni, vedere [Metodo ReportingService2010.ListMySubscriptions](http://technet.microsoft.com/library/reportservice2010.reportingservice2010.listmysubscriptions.aspx).  
  
```  
#server -  all subscriptions of the current user at the given server or site  
$server="[server name]/reportserver"  
$rs2010 = New-WebServiceProxy -Uri "http://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential;  
  
$subscriptions=ListMySubscriptions(ItemPathOrSiteURL)  
$subscriptions | select Path, report, Description, Owner, SubscriptionID, lastexecuted,Status  
#uncomment the following to list all the subscription properties  
#$subscriptions

```  
  
## <a name="see-also"></a>Vedere anche  
 [Sottoscrizioni guidate dai dati](../../reporting-services/subscriptions/data-driven-subscriptions.md)   
 [Sottoscrizioni e recapito &#40;Reporting Services&#41;](../../reporting-services/subscriptions/subscriptions-and-delivery-reporting-services.md)   
 [old_Creare e gestire sottoscrizioni per server di report in modalità nativa](http://msdn.microsoft.com/en-us/7f46cbdb-5102-4941-bca2-5e0ff9012c6b)  
  
  

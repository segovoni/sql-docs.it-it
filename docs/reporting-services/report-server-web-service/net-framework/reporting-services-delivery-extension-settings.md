---
title: Impostazioni delle estensioni per il recapito di Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.component: report-server-web-service
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- XML Web service [Reporting Services], delivery extension settings
- Report Server Web service, delivery extension settings
- delivery [Reporting Services]
- network share delivery [Reporting Services]
- file share delivery [Reporting Services]
- e-mail [Reporting Services]
- mailing reports [Reporting Services]
- sharing reports
- extensions [Reporting Services], delivery
- mail [Reporting Services]
- Web service [Reporting Services], delivery extension settings
ms.assetid: 68c31a85-261c-4ec4-b8df-1f9842b46f8a
caps.latest.revision: 36
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: b123630580b2214dcbebefe9ecb72bb8ca158237
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33026418"
---
# <a name="reporting-services-delivery-extension-settings"></a>Impostazioni delle estensioni per il recapito di Reporting Services
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] include un'estensione per il recapito tramite posta elettronica e un'estensione per il recapito tramite condivisione file. Il recapito tramite posta elettronica consente di inviare un report a singoli utenti o gruppi tramite posta elettronica. Il recapito tramite condivisione file consente di inviare automaticamente i report visualizzabili a una condivisione nella rete. È possibile utilizzare una delle estensioni per il recapito supportate con sottoscrizioni standard o con sottoscrizioni guidate dai dati. Le impostazioni di recapito specifiche del tipo di estensione per il recapito vengono passate ogni volta che si chiamano i metodi <xref:ReportService2010.ReportingService2010.CreateSubscription%2A>, <xref:ReportService2010.ReportingService2010.CreateDataDrivenSubscription%2A>, <xref:ReportService2010.ReportingService2010.SetSubscriptionProperties%2A> e <xref:ReportService2010.ReportingService2010.SetDataDrivenSubscriptionProperties%2A>. Per recuperare un elenco di impostazioni per il recapito a livello di programmazione, utilizzare il metodo <xref:ReportService2010.ReportingService2010.GetExtensionSettings%2A>.  
  
> [!NOTE]  
>  Per le impostazioni delle estensioni per il recapito viene fatta distinzione tra maiuscole e minuscole.  
  
## <a name="e-mail-delivery-settings"></a>Impostazioni di recapito tramite posta elettronica  
 Nella tabella seguente sono elencate le impostazioni di recapito tramite posta elettronica per le sottoscrizioni che utilizzano la posta elettronica del server di report.  
  
|Impostazione|valore|  
|-------------|-----------|  
|**TO**|Indirizzo di posta elettronica visualizzato nella riga **A** del messaggio di posta elettronica. Se sono presenti più indirizzi di posta elettronica, vengono separati da un punto e virgola. Obbligatorio.|  
|**CC**|Indirizzo di posta elettronica visualizzato nella riga **Cc** del messaggio di posta elettronica. Se sono presenti più indirizzi di posta elettronica, vengono separati da un punto e virgola. Facoltativo.|  
|**BCC**|Indirizzo di posta elettronica visualizzato nella riga **Ccn** del messaggio di posta elettronica. Se sono presenti più indirizzi di posta elettronica, vengono separati da un punto e virgola. Facoltativo.|  
|**ReplyTo**|Indirizzo di posta elettronica visualizzato nell'intestazione **Risposta** del messaggio di posta elettronica. Il valore deve essere un singolo indirizzo di posta elettronica. Facoltativo.|  
|**IncludeReport**|Valore che indica se includere il report nel recapito tramite posta elettronica. Un valore **true** indica che il report viene recapitato nel corpo del messaggio di posta elettronica.|  
|**RenderFormat**|Nome dell'estensione per il rendering da utilizzare per generare il report visualizzabile. Il nome deve corrispondere a una delle estensioni per il rendering visibili installate nel server di report. Questo valore è obbligatorio se l'impostazione **IncludeReport** è impostata su **true**.|  
|**Priorità**|Priorità per l'invio del messaggio di posta elettronica. I valori validi sono **LOW**, **NORMAL** e **HIGH**. Il valore predefinito è **NORMAL**.|  
|**Oggetto**|Testo nella riga dell'oggetto del messaggio di posta elettronica.|  
|**Commento**|Testo incluso nel corpo del messaggio di posta elettronica.|  
|**IncludeLink**|Valore che indica se includere un collegamento al report nel corpo del messaggio di posta elettronica.|  
  
## <a name="file-share-delivery-settings"></a>Impostazioni di recapito tramite condivisione file  
 Nella tabella seguente sono elencate le impostazioni di recapito tramite condivisione file per le sottoscrizioni.  
  
|Impostazione|valore|  
|-------------|-----------|  
|**FILENAME**|Nome del file salvato nel disco.|  
|**FILEEXTN**|Indica se includere un'estensione di file per il report visualizzabile. Il valore è **true** o **false**.|  
|**PATH**|Percorso della cartella o percorso della condivisione file UNC in cui salvare il report.|  
|**RENDER_FORMAT**|Formato del report da salvare nel disco.|  
|**USERNAME**|Nome utente necessario per accedere al disco o alla risorsa di rete.|  
|**PASSWORD**|Password necessaria per accedere al disco o alla risorsa di rete.|  
|**WRITEMODE**|Modalità di scrittura da utilizzare per accedere al disco. I valori validi sono **None**, **Overwrite** e **AutoIncrement**.|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento tecnico &#40;SSRS&#41;](../../../reporting-services/technical-reference-ssrs.md)   
 [Creazione di applicazioni mediante il servizio Web e .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
  
  

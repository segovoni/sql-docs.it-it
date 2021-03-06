---
title: Proprietà di sistema del server di report | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- report servers [Reporting Services], properties
- system-specific properties [Reporting Services]
ms.assetid: cd874117-00e5-4ae6-8629-eb9ba9f40478
caps.latest.revision: 55
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: cc749db6d8eee973ef4c146d62ce5ebebda230e2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37276597"
---
# <a name="report-server-system-properties"></a>Proprietà di sistema del server di report
  I nomi di proprietà di sistema seguenti sono riservati. Non è possibile creare proprietà definite dall'utente con lo stesso nome. È possibile leggere o modificare numerose di queste proprietà utilizzando i metodi del servizio Web.  
  
## <a name="properties"></a>Proprietà  
  
|Proprietà|Description|  
|--------------|-----------------|  
|SiteName|Nome del sito del server di report visualizzato nell'interfaccia utente. Il valore predefinito è `Microsoft Report Server`. Questa proprietà può essere una stringa vuota. La lunghezza massima è di 8.000 caratteri.|  
|SystemSnapshotLimit|Numero massimo di snapshot archiviati per un report. I valori validi sono `-1` attraverso `2`,`147`,`483`,`647`. Se il valore è `-1`, non esiste un limite di snapshot.|  
|SystemReportTimeout|Valore di timeout  predefinito per l'elaborazione dei report, espresso in secondi, per tutti i report gestiti nello spazio dei nomi del server di report. È possibile eseguire l'override del valore a livello di report. Se questa proprietà è impostata, il server di report tenta di arrestare l'elaborazione di un report quando scade il tempo specificato. I valori validi sono `-1` attraverso `2`,`147`,`483`,`647`. Se il valore è `-1` durante l'elaborazione non si verifica alcun timeout dei report nello spazio dei nomi. Il valore predefinito è `1800`.|  
|UseSessionCookies|Indica se il server di report deve utilizzare cookie di sessione per le comunicazioni con i browser dei client. Il valore predefinito è `true`.|  
|SessionTimeout|Intervallo, in secondi, durante il quale una sessione rimane attiva. Il valore predefinito è `600`.|  
|EnableMyReports|Indica se la caratteristica Report personali è abilitata. Un valore di `true` indica che la funzionalità è abilitata.|  
|MyReportsRole|Nome del ruolo utilizzato durante la creazione dei criteri di sicurezza nelle cartelle Report personali dell'utente. Il valore predefinito è `My Reports Role`.|  
|EnableExecutionLogging|Indica se la registrazione per l'esecuzione di report è attivata. Il valore predefinito è `true`.|  
|ExecutionLogDaysKept|Numero di giorni durante i quali le informazioni sulle esecuzioni dei report vengono conservate nel log di esecuzione. I valori validi per questa proprietà includono `0` attraverso `2`,`147`,`483`,`647`. Se il valore è `0` le voci non vengono eliminate dalla tabella del log di esecuzione. Il valore predefinito è `60`.|  
|SnapshotCompression|Definisce come vengono compressi gli snapshot. Il valore predefinito è `SQL`. I valori validi sono i seguenti:<br /><br /> `SQL` = gli snapshot vengono compressi quando vengono archiviati nel database del server di report. Questa impostazione corrisponde al comportamento corrente.<br /><br /> **None** = gli snapshot non vengono compressi.<br /><br /> `All` = gli snapshot vengono compressi per tutte le opzioni di archiviazione, incluso il database del server di report o il file system.|  
|EnableClientPrinting|Determina se il controllo ActiveX RSClientPrint è disponibile per il download dal server di report. I valori validi sono `true` e `false`. Il valore predefinito è `true`. Per altre informazioni sulle impostazioni aggiuntive necessarie per questo controllo, vedere [Abilitare e disabilitare la stampa sul lato client per Reporting Services](../../report-server/enable-and-disable-client-side-printing-for-reporting-services.md).|  
|EnableIntegratedSecurity|Determina se la sicurezza integrata è supportata per le connessioni alle origini dati dei report. Il valore predefinito è `True`. I valori validi sono i seguenti:<br /><br /> `True` = la sicurezza integrata è abilitata.<br /><br /> `False` = la sicurezza integrata non è abilitata. Le origini dati dei report configurate per l'utilizzo della sicurezza integrata non verranno eseguite.|  
|EnableRemoteErrors|Include informazioni esterne sugli errori, ad esempio, informazioni sull'errore relative alle origini dati del report, nei messaggi di errore restituiti agli utenti che richiedono i report dai computer remoti. I valori validi sono `true` e `false`. Il valore predefinito è `false`. Per altre informazioni, vedere [Abilita errori remoti &#40;Reporting Services&#41;](../../report-server/enable-remote-errors-reporting-services.md).|  
  
## <a name="see-also"></a>Vedere anche  
 <xref:ReportService2010.ReportingService2010.GetSystemProperties%2A>   
 <xref:ReportService2010.ReportingService2010.SetSystemProperties%2A>   
 [Compilazione di applicazioni tramite servizio Web e .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md)   
 [Servizio Web ReportServer](../report-server-web-service.md)   
 [Riferimento tecnico &#40;SSRS&#41;](../../technical-reference-ssrs.md)  
  
  

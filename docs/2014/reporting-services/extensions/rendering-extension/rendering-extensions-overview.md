---
title: Cenni preliminari sulle estensioni per il rendering | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- formats [Reporting Services], rendering extensions
- rendering extensions [Reporting Services], about extensions
ms.assetid: 909356a0-4709-43e5-b597-33bd9bb22882
caps.latest.revision: 41
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: ec1f4499a76900684f541eba529b3e21afff5707
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37214691"
---
# <a name="rendering-extensions-overview"></a>Cenni preliminari sulle estensioni per il rendering
  Un'estensione per il rendering è un componente o un modulo di un server di report che consente di trasformare le informazioni sul layout e i dati del report in un formato specifico del dispositivo. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] include sette estensioni per il rendering: HTML, Excel, Word, CSV o Text, XML, Image e PDF. È possibile creare estensioni per il rendering aggiuntive per generare report in altri formati.  
  
> [!NOTE]  
>  Per determinare quali sono le estensioni per il rendering disponibili, è possibile visualizzare l'elenco delle estensioni installate nel file RSReportServer.config.  
  
 Nella tabella seguente sono descritte le estensioni per il rendering incluse in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
|Extension Name|Description|  
|--------------------|-----------------|  
|`XML`|Consente di eseguire il rendering di un report in formato XML. Il report viene aperto in un browser. Le trasformazioni aggiuntive applicate a questo output XML possono rappresentare un metodo efficace per evitare di sviluppare un'estensione per il rendering personalizzata.|  
|`CSV`|Consente di eseguire il rendering di un report in formato con valori delimitati da virgole. Il report viene aperto in uno strumento di visualizzazione associato ai formati di file CSV.|  
|`IMAGE`|Consente di eseguire il rendering di un report in un formato orientato alla pagina. Il formato viene visualizzato come **TIFF** nell'elenco a discesa Esporta della barra degli strumenti del report.|  
|`PDF`|Consente di eseguire il rendering di un report in Adobe Acrobat Reader. Il formato viene visualizzato come **File Acrobat (PDF)** nell'elenco a discesa Esporta della barra degli strumenti del report.|  
|`EXCEL`|Consente di eseguire il rendering di un report in formato [!INCLUDE[ofprexcel](../../../includes/ofprexcel-md.md)].|  
|`WORD`|Consente di eseguire il rendering di un report in formato [!INCLUDE[ofprword](../../../includes/ofprword-md.md)].|  
|`HTML 4.0` (parte dell'estensione per il rendering HTML)|HTML è il formato utilizzato per eseguire il rendering iniziale del report. Se il browser supporta il formato HTML 4.0, viene utilizzato questo formato. In caso contrario, viene utilizzato il formato HTML 3.2.|  
|`MHTML` (parte dell'estensione per il rendering HTML)|Consente di eseguire il rendering di un report in formato MHTML. Il report viene aperto in Internet Explorer. Il formato viene visualizzato come **Archivio Web** nell'elenco a discesa Esporta della barra degli strumenti del report.|  
|`NULL`|Non viene eseguito il rendering di un report in un formato specifico. Questa estensione per il rendering è utile per l'inserimento dei report nella cache. Il rendering Null deve essere utilizzato insieme a un'esecuzione o a un recapito pianificato.|  
  
 Per altre informazioni sui formati consigliati e il relativo uso, vedere [Esportazione di report &#40;Generatore report e SSRS&#41;](../../report-builder/export-reports-report-builder-and-ssrs.md).  
  
 Ognuna delle estensioni per il rendering implementate da [!INCLUDE[msCoName](../../../includes/msconame-md.md)] e fornite con [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] utilizza un set comune di interfacce. Questo garantisce che ogni estensione implementi funzionalità simili e riduce la complessità del codice di rendering nel nucleo del server di report.  
  
## <a name="rendering-object-model"></a>Modello a oggetti per il rendering  
 Quando un report viene elaborato, il risultato è un modello a oggetti esposto pubblicamente noto come Modello a oggetti per il rendering (ROM, Rendering Object Model). Il modello a oggetti per il rendering è una raccolta di classi che definiscono il contenuto, il layout e i dati di un report che è stato elaborato. Questo modello è disponibile per gli sviluppatori che desiderano progettare, sviluppare e distribuire estensioni per il rendering personalizzate per [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Il modello a oggetti per il rendering viene creato quando il server di report elabora la definizione XML di un report insieme ai dati del report definiti dall'utente. Al termine dell'elaborazione, il modello a oggetti pubblico viene utilizzato da un'estensione per il rendering per definire l'output del report. Le classi pubbliche disponibili del modello a oggetti per il rendering sono definite nello spazio dei nomi `Microsoft.ReportingServices.OnDemandReportRendering`.  
  
## <a name="writing-custom-rendering-extensions"></a>Creazione di estensioni per il rendering personalizzate  
 Prima di decidere di creare un'estensione per il rendering personalizzata, è consigliabile valutare alternative più semplici. È possibile effettuare le operazioni seguenti:  
  
-   Personalizzare l'output sottoposto a rendering specificando le impostazioni relative alle informazioni sui dispositivi per le estensioni esistenti.  
  
-   Aggiungere funzionalità di presentazione e formattazione personalizzate combinando XSLT (XSL Transformations, trasformazioni XSL) con l'output del formato di rendering XML.  
  
 La scrittura di un'estensione per il rendering personalizzata è complessa. Un'estensione per il rendering deve in genere supportare tutte le combinazioni possibili di elementi del report e richiede l'implementazione di centinaia di classi, interfacce, metodi e proprietà. Se è necessario eseguire il rendering di un report in un formato non incluso in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] e si decide di scrivere un'implementazione di codice gestito di un'estensione per il rendering, è necessario che il codice dell'estensione per il rendering implementi l'interfaccia `Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension`, richiesta dal server di report.  
  
 Per documentazione e white paper aggiuntivi su [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], vedere le più recenti risorse tecniche nel [sito Web di Reporting Services](http://go.microsoft.com/fwlink/?LinkId=19951).  
  
## <a name="see-also"></a>Vedere anche  
 [Implementazione di un'estensione per il rendering](implementing-a-rendering-extension.md)   
 [Libreria di estensioni di Reporting Services](../reporting-services-extension-library.md)  
  
  

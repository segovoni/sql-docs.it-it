---
title: Report click-through (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- clickthrough reports
- customizing clickthrough reports
- clickthrough reports, customizing
ms.assetid: cf2c396e-b0c6-41f9-8c45-ddc8406f7e85
caps.latest.revision: 28
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 2f8c96a114557bcef8252f2c21b70c9a50dbfb94
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37216651"
---
# <a name="clickthrough-reports-ssrs"></a>Report click-through (SSRS)
  Un report click-through è un report in cui vengono fornite informazioni dettagliate sui dati contenuti nel report principale. Il report click-through viene visualizzato quando l'utente fa clic sui dati interattivi visualizzati nel report principale. Questi report vengono generati automaticamente dal server di report. È, come la finestra di progettazione del modello, determinare ciò che viene visualizzato nei report click-through impostando il `DefaultDetailAttribute` e `DefaultAggregateAttribute` proprietà assegnate a un'entità nel modello di report.  
  
> [!NOTE]  
>  Report click-through non sono disponibili in tutte le edizioni di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Per un elenco delle funzionalità supportate dalle edizioni di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], vedere [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md). In caso di dubbi sull'edizione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] usata nell'organizzazione, contattare l'amministratore del database.  
  
## <a name="using-default-templates"></a>Utilizzo di modelli predefiniti  
 Per impostazione predefinita, nel server di report vengono generati due tipi di modello click-through per ogni entità: un modello a istanza singola e un modello a più istanze. L'elemento su cui si fa clic determina il modello che verrà utilizzato. Se la persona che legge il report fa clic su un attributo scalare, verrà utilizzato il modello a istanza singola. Se la persona che legge il report fa clic su un attributo di aggregazione, verrà utilizzato il modello a più istanze.  
  
#### <a name="single-instance-templates"></a>Modelli a istanza singola  
 In un modello a istanza singola vengono visualizzati tutti gli attributi dell'entità di destinazione e tutti gli attributi di aggregazione predefiniti specificati per le entità correlate che presentano una relazione uno-a-molti rispetto all'entità di destinazione. Un modello a istanza singola è simile all'immagine seguente.  
  
 ![Report click-through molti-a-uno.](../media/manytooneclickthrough.gif "Report click-through molti-a-uno.")  
  
#### <a name="multiple-instance-templates"></a>Modelli a più istanze  
 In un modello a più istanze vengono visualizzati solo gli attributi dettagli predefiniti dell'entità di destinazione e tutti gli attributi di aggregazione predefiniti specificati per le entità correlate che presentano una relazione uno-a-molti rispetto all'entità di destinazione. Un modello a più istanze è simile all'immagine seguente.  
  
 ![Report click-through molti-a-uno.](../media/onetomanyclickthrough.gif "Report click-through molti-a-uno.")  
  
## <a name="customizing-clickthrough-reports"></a>personalizzazione di report click-through  
 Anziché utilizzare i modelli predefiniti generati dal server di report, è possibile creare un report in Generatore report, utilizzarlo come report click-through personalizzato, quindi collegarlo al modello come report drill-through in Gestione report.  
  
 Per convertire un report di Generatore report in un report click-through, è necessario selezionare l'opzione **Consenti drill-through** nella finestra di dialogo **Proprietà** di Generatore report. Dopo aver selezionato questa opzione, un parametro drill-through viene aggiunto al report che non potrà più essere eseguito direttamente in Generatore report. Il parametro drill-through viene calcolato automaticamente dal server di report quando viene fatto clic su un elemento di un report di Generatore report.  
  
> [!IMPORTANT]  
>  L'entità primaria, o entità di base, utilizzata nel report deve corrispondere a quella a cui si collega il report.  
  
## <a name="see-also"></a>Vedere anche  
 [Collegare un report a un modello come report click-through](../link-a-report-to-a-model-as-a-clickthrough-report.md)  
  
  

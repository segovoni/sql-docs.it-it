---
title: Configurare le proprietà di esecuzione per un report (Gestione report) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- report execution properties [Reporting Services]
- reports [Reporting Services], properties
- reports [Reporting Services], execution options
ms.assetid: 73cc8dcc-ef80-40d7-9739-d33bba0eb28a
caps.latest.revision: 40
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: af4a6a8a01a5a07f0f050460f26998db2c1c8550
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37315411"
---
# <a name="configure-execution-properties-for-a-report--report-manager"></a>Configurare le proprietà di esecuzione per un report (Gestione report)
  È possibile impostare le opzioni di elaborazione di un report per specificare il momento in cui i dati vengono recuperati per un report specifico. Questa operazione risulta utile per pianificare l'elaborazione dei dati per un report se l'origine dati esterna viene aggiornata a intervalli stabiliti (ad esempio se un data warehouse viene aggiornato su base giornaliera o settimanale) e si desidera evitare l'overhead dovuto al recupero degli stessi dati ogni volta che un report viene richiesto. La pianificazione dell'elaborazione dei dati è utile anche se si desidera controllare il carico di elaborazione nel server di database esterno o quando si desidera fornire risultati coerenti per più utenti che devono utilizzare set di dati identici. Con dati volatili, un report su richiesta può generare risultati diversi anche a differenza di pochi minuti. Uno snapshot del report, invece, consente di eseguire confronti validi con altri report o strumenti analitici contenenti dati riferiti allo stesso momento nel tempo.  
  
 Il termine snapshot del report indica un report che include informazioni sul layout e i risultati di query recuperati in un momento specifico. Diversamente dai report su richiesta, per i quali vengono recuperati risultati di query aggiornati quando si seleziona il report, gli snapshot dei report vengono elaborati in base a una pianificazione e quindi salvati nel server di report. Quando si seleziona uno snapshot per la visualizzazione, il server di report recupera il report archiviato dal database del server di report e visualizza i dati e il layout del report aggiornati al momento della creazione dello snapshot.  
  
 Gli snapshot dei report non vengono salvati in un formato di rendering specifico, ma ne viene eseguito il rendering nel formato di visualizzazione finale, ad esempio HTML, solo quando vengono richiesti da un utente o un'applicazione. Il rendering posticipato rende uno snapshot portabile. È possibile eseguire il rendering del report nel formato corretto per il dispositivo o il browser da cui proviene la richiesta.  
  
### <a name="to-configure-report-processing-options"></a>Per configurare le opzioni relative all'elaborazione dei report  
  
1.  Avviare [Gestione report &#40;modalità nativa SSRS&#41;](../report-manager-ssrs-native-mode.md).  
  
2.  Selezionare e aprire il report per il quale si desidera impostare le opzioni di elaborazione.  
  
 Passare con il puntatore del mouse sul report, quindi fare clic sulla freccia a discesa.  
  
1.  Scegliere **Gestisci** dal menu a discesa, quindi selezionare la scheda **Opzioni di elaborazione** .  
  
2.  Fare clic su **Esegui il rendering del report da uno snapshot dell'esecuzione del report**, quindi selezionare una delle opzioni seguenti:  
  
    -   Se si desidera creare uno snapshot, selezionare **Usa la pianificazione seguente per creare snapshot dell'esecuzione del report**, quindi definire una pianificazione in base al report oppure selezionare un'opzione dall'elenco **Pianificazione condivisa** .  
  
    -   Se si desidera creare immediatamente uno snapshot, selezionare **Crea uno snapshot del report quando viene scelto il pulsante Applica in questa pagina**.  
  
3.  Fare clic su **Applica**.  
  
## <a name="see-also"></a>Vedere anche  
 [Impostare le proprietà di elaborazione dei Report](../report-server/set-report-processing-properties.md)   
 [Aprire e chiudere un Report &#40;gestione Report&#41;](../reports/open-and-close-a-report-report-manager.md)   
 [Contenuto della pagina &#40;gestione Report&#41;](../contents-page-report-manager.md)   
 [Gestione contenuto del Server di report &#40;modalità nativa SSRS&#41;](../report-server/report-server-content-management-ssrs-native-mode.md)   
 [Pagina delle proprietà Opzioni di elaborazione &#40;Gestione report&#41;](../processing-options-properties-page-report-manager.md)  
  
  

---
title: Editor attività lettore di dati WMI (pagina Opzioni WMI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.wmidatareadertask.wmiquery.f1
helpviewer_keywords:
- WMI Data Reader Task Editor
ms.assetid: 4b8d4716-882d-41b0-b77e-e0e2741a2cd5
caps.latest.revision: 39
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c4af6d3458cba6e622c117ace4add62127670f13
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37152412"
---
# <a name="wmi-data-reader-task-editor-wmi-options-page"></a>Editor attività Lettore di dati WMI (pagina Opzioni WMI)
  Usare la pagina **Opzioni WMI** della finestra di dialogo **Editor attività Lettore di dati WMI** per specificare l'origine della query WQL (Windows Management Instrumentation Query Language) e la destinazione del risultato della query.  
  
 Per ulteriori informazioni su questa attività, vedere [WMI Data Reader Task](control-flow/wmi-data-reader-task.md). Per altre informazioni su WQL (WMI Query Language), vedere l'argomento relativo a WMI (Windows Management Instrumentation) [Querying with WQL](http://go.microsoft.com/fwlink/?LinkId=79045)(Query con WQL) in MSDN Library.  
  
## <a name="static-options"></a>Opzioni statiche  
 **WMIConnectionName**  
 Selezionare una gestione connessione WMI nell'elenco o creare una nuova gestione connessione facendo clic su \<**Nuova connessione WMI**>.  
  
 **Argomenti correlati**: [Gestione connessione WMI](connection-manager/wmi-connection-manager.md), [Editor gestione connessione WMI](../../2014/integration-services/wmi-connection-manager-editor.md)  
  
 **WQLQuerySourceType**  
 Consente di selezionare il tipo di origine della query WQL eseguita dall'attività. Per questa proprietà sono disponibili le opzioni elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|**Input diretto**|Consente di impostare l'origine su una query WQL. Selezionando questo valore viene visualizzata l'opzione dinamica **WQLQuerySourceType**.|  
|**Connessione file**|Consente di selezionare un file contenente la query WQL. Selezionando questo valore viene visualizzata l'opzione dinamica **WQLQuerySourceType**.|  
|**Variabile**|Consente di impostare l'origine su una variabile che definisce la query WQL. Selezionando questo valore viene visualizzata l'opzione dinamica **WQLQuerySourceType**.|  
  
 **OutputType**  
 Consente di specificare se l'output deve essere una tabella di dati, un valore di proprietà o un nome e valore di proprietà.  
  
 **OverwriteDestination**  
 Consente di specificare se mantenere, sovrascrivere o accodare ai dati originali nel file o nella variabile di destinazione.  
  
 **DestinationType**  
 Consente di selezionare il tipo di destinazione della query WQL eseguita dall'attività. Per questa proprietà sono disponibili le opzioni elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|**Connessione file**|Selezionare un file in cui salvare i risultati della query WQL. Selezionando questo valore viene visualizzata l'opzione dinamica **DestinationType**.|  
|**Variabile**|Impostare la variabile in cui archiviare i risultati della query WQL. Selezionando questo valore viene visualizzata l'opzione dinamica **DestinationType**.|  
  
## <a name="wqlquerysourcetype-dynamic-options"></a>Opzioni dinamiche di WQLQuerySourceType  
  
### <a name="wqlquerysourcetype--direct-input"></a>WQLQuerySourceType = Input diretto  
 **WQLQuerySource**  
 Consente di specificare una query o di immettere una query nella finestra di dialogo **Query WQL** visualizzata facendo clic sul pulsante (...).  
  
### <a name="wqlquerysourcetype--file-connection"></a>WQLQuerySourceType = Connessione file  
 **WQLQuerySource**  
 Selezionare una gestione connessione file nell'elenco o fare clic su \<**Nuova connessione**> per creare una nuova gestione connessione.  
  
 **Argomenti correlati:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
### <a name="wqlquerysourcetype--variable"></a>WQLQuerySourceType = Variabile  
 **WQLQuerySource**  
 Selezionare una variabile nell'elenco oppure fare clic su \<**Nuova variabile**> per crearne una nuova.  
  
 **Argomenti correlati:** [Variabili di Integration Services &#40;SSIS&#41;](integration-services-ssis-variables.md), [Aggiungi variabile](../../2014/integration-services/add-variable.md)  
  
## <a name="destinationtype-dynamic-options"></a>Opzioni dinamiche di DestinationType  
  
### <a name="destinationtype--file-connection"></a>DestinationType = Connessione file  
 **Destinazione**  
 Selezionare una gestione connessione file nell'elenco o fare clic su \<**Nuova connessione**> per creare una nuova gestione connessione.  
  
 **Argomenti correlati:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
### <a name="destinationtype--variable"></a>DestinationType = Variabile  
 **Destinazione**  
 Selezionare una variabile nell'elenco oppure fare clic su \<**Nuova variabile**> per crearne una nuova.  
  
 **Argomenti correlati:** [Variabili di Integration Services &#40;SSIS&#41;](integration-services-ssis-variables.md), [Aggiungi variabile](../../2014/integration-services/add-variable.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento ai messaggi e agli errori di Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Editor attività lettore di dati WMI &#40;pagina Generale&#41;](general-page-of-integration-services-designers-options.md)   
 [Pagina espressioni](expressions/expressions-page.md)   
 [Attività Monitoraggio eventi WMI](control-flow/wmi-event-watcher-task.md)  
  
  

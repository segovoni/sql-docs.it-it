---
title: Usare SQL Server (XEvent) di eventi estesi per monitorare Analysis Services | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b57cc2fe-52dc-4fa9-8554-5a866e25c6d7
caps.latest.revision: 5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4aa591ff08106f7af8946d6725d8894c52149634
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37332801"
---
# <a name="use-sql-server-extended-events-xevents-to-monitor-analysis-services"></a>Utilizzare eventi estesi di SQL Server (XEvent) per il monitoraggio di Analysis Services
  Analysis Services fornisce funzionalità di traccia tramite l'utilizzo delle [eventi estesi](../../relational-databases/extended-events/extended-events.md).  
  
 Eventi estesi è un'infrastruttura evento estremamente scalabile e configurabile per i sistemi server. Si tratta di un sistema di monitoraggio delle prestazioni leggero in cui vengono utilizzate poche risorse per le prestazioni.  
  
 Tutti i servizi di analisi eventi possono essere acquisiti e indirizzare a consumer specifici, come definito in [eventi estesi](../../relational-databases/extended-events/extended-events.md), tramite XEvents.  
  
## <a name="initiating-extended-events-in-analysis-services"></a>Avvio di eventi estesi in Analysis Services  
 La traccia di eventi estesi viene abilitata utilizzando una specifica XMLA simile per creare un comando script dell'oggetto come illustrato di seguito:  
  
```  
<Execute …>  
   <Command>  
      <Batch …>  
         <Create …>  
            <ObjectDefinition>  
               <Trace>  
                  <ID>trace_id</ID>  
                  <Name>trace_name</Name>  
                  <ddl300_300:XEvent>  
                     <event_session …>  
                        <event package="AS" name="AS_event">  
                           <action package="PACKAGE0" …/>  
                        </event>  
                        <target package="PACKAGE0" name="asynchronous_file_target">  
                           <parameter name="filename" value="data_filename.xel"/>  
                           <parameter name="metadatafile" value="metadata_filename.xem"/>  
                        </target>  
                     </event_session>  
                  </ddl300_300:XEvent>  
               </Trace>  
            </ObjectDefinition>  
         </Create>  
      </Batch>  
   </Command>  
   <Properties></Properties>  
</Execute>  
  
```  
  
 A seconda delle necessità di traccia, gli elementi seguenti devono essere definiti dall'utente:  
  
 *trace_id*  
 Consente di definire l'identificatore univoco per questa traccia.  
  
 *trace_name*  
 Nome fornito a questa traccia; generalmente una definizione leggibile della traccia. È pratica comune usare il valore *trace_id* come nome.  
  
 *AS_event*  
 Evento di Analysis Services da esporre. Vedere [Eventi di traccia di Analysis Services](../trace-events/analysis-services-trace-events.md) per i nomi degli eventi.  
  
 *data_filename*  
 Nome del file in cui sono contenuti i dati degli eventi. Nel nome è incluso un suffisso timestamp per evitare la sovrascrittura dei dati qualora la traccia venga inviata ripetutamente.  
  
 *metadata_filename*  
 Nome del file in cui sono contenuti i metadati degli eventi. Nel nome è incluso un suffisso timestamp per evitare la sovrascrittura dei dati qualora la traccia venga inviata ripetutamente.  
  
## <a name="stopping-extended-events-in-analysis-services"></a>Arresto di eventi estesi in Analysis Services  
 Per arrestare l'oggetto traccia di eventi estesi è necessario eliminare tale oggetto utilizzando una specifica XMLA simile per eliminare un comando script dell'oggetto come illustrato di seguito:  
  
```  
<Execute xmlns="urn:schemas-microsoft-com:xml-analysis">  
   <Command>  
      <Batch …>  
         <Delete …>  
            <Object>  
               <TraceID>trace_id</TraceID>  
            </Object>  
         </Delete>  
      </Batch>  
   </Command>  
   <Properties></Properties>  
</Execute>  
  
```  
  
 A seconda delle necessità di traccia, gli elementi seguenti devono essere definiti dall'utente:  
  
 *trace_id*  
 Consente di definire l'identificatore univoco della traccia da eliminare.  
  
## <a name="see-also"></a>Vedere anche  
 [Eventi estesi](../../relational-databases/extended-events/extended-events.md)  
  
  

---
title: Proprietà traccia (scheda Selezione eventi) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.pro.traceproperties.eventsselection.f1
helpviewer_keywords:
- Trace Properties dialog box
ms.assetid: e1892f24-7272-4d5d-8926-6150cc82b2c3
caps.latest.revision: 24
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 033cde8c84edc6ceb7b0fb9686e31b6ce98ef1c8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37283827"
---
# <a name="trace-properties-events-selection-tab"></a>Proprietà traccia (scheda Selezione eventi)
  Usare la scheda **Selezione eventi** della finestra di dialogo **Proprietà traccia** per visualizzare o specificare le colonne di dati e gli eventi inseriti nella traccia.  
  
## <a name="options"></a>Opzioni  
 Colonna**Eventi**   
 È possibile specificare gli eventi inseriti nella traccia selezionando o deselezionando la casella di controllo nella colonna di evento. Le colonne**Eventi** sono organizzate in base alla categoria di evento. Le classi di evento specificate nel modello vengono selezionate automaticamente. Per altre informazioni, vedere [SQL Server Event Class Reference](../relational-databases/event-classes/sql-server-event-class-reference.md).  
  
 Colonne di dati  
 È possibile specificare le colonne di dati inseriti nella traccia selezionando la casella che corrisponde all'evento e alla colonna di dati necessari. Tutte le colonne di evento significative sono selezionate per impostazione predefinita per ogni evento incluso della traccia.  
  
 Per specificare i filtri, fare clic sull'intestazione della colonna di dati e immettere i criteri di filtro. Le colonne di dati filtrate sono contrassegnate da un'icona di filtro a sinistra dell'etichetta della colonna nella finestra di dialogo **Modifica filtro** . Per altre informazioni, vedere [SQL Server Profiler - Modifica filtro](../../2014/database-engine/sql-server-profiler-edit-filter.md).  
  
 **Mostra tutti gli eventi**  
 Consente di visualizzare tutti gli eventi disponibili. Per impostazione predefinita, vengono visualizzate solo le righe della griglia **Selezione eventi** selezionate. Deselezionare questa casella di controllo per nascondere tutti gli eventi non selezionati nella griglia **Selezione eventi** .  
  
 **Mostra tutte le colonne**  
 Consente di visualizzare tutte le colonne di dati disponibili. Per impostazione predefinita, vengono visualizzate solo le colonne di dati selezionate. Deselezionare questa casella di controllo per nascondere tutte le colonne di dati non selezionate nella griglia **Selezione eventi** .  
  
 **Filtri colonne**  
 Consente di aprire la finestra di dialogo **Modifica filtro** , utilizzabile per modificare i filtri delle colonne di dati.  
  
 **Organizza colonne**  
 Consente di modificare l'ordine delle colonne nella traccia e di raggruppare i risultati in base a una o più colonne.  
  
## <a name="see-also"></a>Vedere anche  
 [Specificare eventi e colonne di dati per un File di traccia &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)   
 [Organizzare le colonne visualizzate in una traccia &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/organize-columns-displayed-in-a-trace-sql-server-profiler.md)   
 [Filtrare gli eventi in una traccia &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md)   
 [Visualizzare informazioni sui filtri &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/view-filter-information-sql-server-profiler.md)   
 [Modificare un filtro &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/modify-a-filter-sql-server-profiler.md)   
 [Modelli e autorizzazioni di SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler.md)  
  
  

---
title: Modificare un modello di traccia (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- templates [SQL Server], traces
- trace templates [SQL Server]
- modifying traces
ms.assetid: b81df2a1-e202-43d8-92b0-0beb145f0116
caps.latest.revision: 25
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8079f4dfa5893915a10ae044045d1cc9eb59baa8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37299371"
---
# <a name="modify-a-trace-template-sql-server-profiler"></a>Modificare un modello di traccia (SQL Profiler)
  In questo argomento viene descritto come modificare un modello di traccia utilizzando [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)].  
  
### <a name="to-modify-a-trace-template"></a>Per modificare un modello di traccia  
  
1.  Scegliere **Modelli** dal menu **File**, quindi fare clic su **Modifica modello**.  
  
2.  Nella scheda **Generale** della finestra di dialogo **Proprietà modello di traccia** è possibile modificare il tipo di server e il nome del modello oppure scegliere di usare un modello predefinito per il tipo di server.  
  
3.  Nella scheda **Selezione eventi**usare il controllo griglia per aggiungere o rimuovere eventi e colonne di dati dal file di traccia, nel modo seguente.  
  
    -   Per aggiungere un evento, espandere la categoria di eventi appropriata nella colonna **Eventi** e quindi selezionare il nome dell'evento.  
  
    -   Quando si aggiunge un evento, tutte le colonne di dati significative vengono incluse per impostazione predefinita. Per rimuovere una colonna di dati per un evento da una traccia, deselezionare la casella di controllo nella colonna di dati per l'evento.  
  
    -   Per aggiungere i filtri, fare clic sul nome della colonna di dati e specificare i criteri del filtro nella finestra di dialogo **Modifica filtro** . È anche possibile fare clic con il pulsante destro del mouse sul nome della colonna di dati e scegliere **Modifica filtro colonne** per accedere alla finestra di dialogo **Modifica filtro** . Fare clic su **OK** per aggiungere il filtro.  
  
4.  Fare clic su **Salva**oppure su **Salva con nome**per salvare il modello di traccia con un altro nome.  
  
## <a name="see-also"></a>Vedere anche  
 [Specificare eventi e colonne di dati per un File di traccia &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)   
 [Derivare un modello da una traccia in esecuzione &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/derive-a-template-from-a-running-trace-sql-server-profiler.md)   
 [Derivare un modello da un file di traccia o da una tabella di traccia &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/derive-a-template-from-a-trace-file-or-trace-table-sql-server-profiler.md)   
 [Modelli e autorizzazioni di SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler.md)  
  
  

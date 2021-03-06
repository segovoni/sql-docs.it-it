---
title: SQL Server Profiler - configurazione riproduzione (opzioni di base di riproduzione) | Microsoft Docs
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
- sql12.pro.replay.generaloptions.f1
helpviewer_keywords:
- Replay Configuration dialog box
ms.assetid: 85a1dec6-9bbc-477a-86c5-b463db9ebb31
caps.latest.revision: 21
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cef06029d3ac1af86955f7a2df89fbe570c15245
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37178378"
---
# <a name="sql-server-profiler---replay-configuration-basic-replay-options"></a>SQL Server Profiler - Configurazione riproduzione (Opzioni di base di riproduzione)
  Nella finestra di dialogo **Configurazione riproduzione** usare la pagina **Opzioni di base di riproduzione** per specificare la modalità di riproduzione di un file o una tabella di traccia.  
  
 Per visualizzare questa finestra utilizzare [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] per aprire un file o una tabella di traccia che contiene gli eventi appropriati per la riproduzione. Per altre informazioni, vedere [Requisiti per la riproduzione](../tools/sql-server-profiler/replay-requirements.md). Con la tabella o il file di traccia aperto, scegliere **Avvia** dal menu **Riproduci**e quindi connettersi all'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] in cui riprodurre la traccia.  
  
## <a name="options"></a>Opzioni  
 **Server di riproduzione**  
 Consente di visualizzare l'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] a cui connettersi per la riproduzione.  
  
 **Cambia...**  
 Consente di aprire la finestra di dialogo **Connetti al server** per stabilire una connessione a un altro server.  
  
 **Salva nel file**  
 Consente di salvare i risultati di riproduzione in un file. [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] Consente di visualizzare la finestra di dialogo file standard, in cui è possibile specificare il percorso in cui salvare il file.  
  
 **Salva nella tabella**  
 Consente di salvare i risultati di riproduzione in una tabella. In [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] verrà visualizzata la finestra di dialogo di selezione della tabella in cui è possibile specificare la posizione in cui salvare la tabella.  
  
 **Numero di thread di riproduzione**  
 Consente di specificare il numero di thread di riproduzione da utilizzare simultaneamente. Un numero elevato determina un maggior consumo di risorse durante la riproduzione, ma la riproduzione viene eseguita in modo più veloce e simultaneo.  
  
 **Riproduci gli eventi nell'ordine in cui sono stati inseriti nella traccia**  
 Gli eventi vengono riprodotti in modo sequenziale. Utilizzare questa opzione per riprodurre una traccia a scopi di debug.  
  
 **Riproduci gli eventi usando più thread**  
 Gli eventi vengono riprodotti simultaneamente. Questa opzione offre una riproduzione più veloce rispetto alla riproduzione degli eventi sequenziale, ma non permette l'utilizzo a scopi di debug. Gli eventi vengono ordinati in base ai relativi identificatori di processo di sistema (SPID).  
  
 **Visualizza risultati di riproduzione**  
 Consente di visualizzare i risultati di riproduzione in [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Riprodurre una tabella di traccia &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md)   
 [Riprodurre un file di traccia &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md)   
 [Riprodurre le tracce](../tools/sql-server-profiler/replay-traces.md)  
  
  

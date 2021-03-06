---
title: Eseguire SQL Server Profiler | Microsoft Docs
ms.custom: ''
ms.date: 7/7/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.suite: sql
ms.technology: profiler
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Profiler [SQL Server Profiler], starting
- SQL Server Profiler, starting
- starting SQL Server Profiler
- Profiler [SQL Server Profiler], running
- SQL Server Profiler, running
- running SQL Server Profiler
ms.assetid: 22e57ffa-63b0-4de3-b92e-df297dda1226
caps.latest.revision: 25
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 250ea8227a4bd045883322ba2fec3e923336a5e2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33076824"
---
# <a name="run-sql-server-profiler"></a>Eseguire SQL Server Profiler
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  È possibile eseguire [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] in modi diversi per supportare la raccolta dell'output di traccia in svariati scenari. È possibile avviare [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] dal menu **Start** di Windows 10, dal menu **Strumenti** in Ottimizzazione guidata [!INCLUDE[ssDE](../../includes/ssde-md.md)] e da diversi punti all'interno di [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
Quando si avvia [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] per la prima volta e si sceglie **Nuova traccia** dal menu **File **, l'applicazione visualizza la finestra di dialogo** Connetti al server[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in cui è possibile specificare l'istanza di**  a cui connettersi.  
## <a name="to-start-sql-server-profiler-from-the-windows-10-start-menu"></a>Per avviare SQL Server Profiler dal menu Start di Windows 10  
-  Fare clic sull'icona **Start** di Windows oppure premere il tasto WINDOWS e digitare "SQL Server Profiler 17". Fare clic, quando viene visualizzato il riquadro **SQL Server Profiler 17**.   

## <a name="to-start-sql-server-profiler-in-database-engine-tuning-advisor"></a>Per avviare SQL Server Profiler in Ottimizzazione guidata motore di database  
-  Selezionare [!INCLUDE[ssDE](../../includes/ssde-md.md)] SQL Server Profiler **dal menu** Tools **di Ottimizzazione guidata**.  

## <a name="to-start-sql-server-profiler-in-sql-server-management-studio"></a>Avviare SQL Server Profiler in SQL Server Management Studio  
 È possibile avviare [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] da diverse posizioni in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Quando [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] viene avviato, carica il contesto di connessione, il modello di traccia e il contesto del filtro del punto di avvio. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Avvia ogni sessione di SQL Server Profiler nella rispettiva istanza e Profiler continua a essere eseguito se si arresta [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
### <a name="to-start-sql-server-profiler-from-the-tools-menu"></a>Per avviare SQL Server Profiler dal menu Strumenti  
-  Scegliere [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **Tools** menu, click **SQL Server Profiler**.  

### <a name="to-start-sql-server-profiler-from-the-query-editor"></a>Per avviare SQL Server Profiler dall'editor di query  
- In Editor di query fare clic con il pulsante destro del mouse e scegliere **Traccia query in SQL Server Profiler**.  

  > [!NOTE]  
  >  Il contesto di connessione è la connessione dell'editor, il modello di traccia è TSQL_SPs e il filtro applicato è SPID = finestra della query SPID.  
    
### <a name="to-start-sql-server-profiler-from-activity-monitor"></a>Per avviare SQL Server Profiler da Monitor attività  
- In Monitoraggio attività fare clic sul riquadro **Processi**, fare clic con il pulsante destro del mouse sul processo di cui si vuole modificare il profilo e quindi scegliere **Processo di traccia in SQL Server Profiler**.  

    > [!NOTE]  
    >  Quando viene selezionato un processo, il contesto di connessione è la connessione Esplora oggetti stabilita all'apertura di Monitor attività. Il modello di traccia è l'impostazione predefinita basata sul tipo di server e lo SPID corrisponde a quello del processo selezionato.  
    
## <a name="net-framework-security"></a>Sicurezza di .NET Framework  
- Nella modalità di autenticazione di Windows l'account utente usato per l'esecuzione di [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] deve avere l'autorizzazione per la connessione all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
- Per eseguire tracce con [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], gli utenti devono inoltre possedere l'autorizzazione ALTER TRACE.  

## <a name="next-steps"></a>Passaggi successivi  
 [Panoramica di SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)   
 [Utilizzo di SQL Server Management Studio](http://msdn.microsoft.com/library/f289e978-14ca-46ef-9e61-e1fe5fd593be)  

---
title: Ottimizzazione di un carico di lavoro | Documenti Microsoft
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: dta
ms.reviewer: ''
ms.suite: sql
ms.technology: performance
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- SQL Server 2016
helpviewer_keywords:
- workloads [SQL Server], tuning
ms.assetid: 6229bf3f-1182-4bc6-8451-cedc37f4b62e
caps.latest.revision: 25
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: cb21de806444d238c3a2b7d16caa2b6bd709b99a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33075710"
---
# <a name="lesson-1-1---tuning-a-workload"></a>Lezione 1-1: Ottimizzazione di un carico di lavoro
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Per individuare la migliore struttura fisica di database per l'esecuzione di query sulle tabelle e i database selezionati per l'ottimizzazione, è possibile utilizzare Ottimizzazione guidata motore di database.  
  
In questa attività viene utilizzato il database di esempio [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . Per una maggiore sicurezza, i database di esempio non vengono installati per impostazione predefinita. Per installare i database di esempio, vedere la pagina relativa all' [installazione dei database di esempio e degli esempi di SQL Server](http://sqlserversamples.codeplex.com).  
  
### <a name="tune-a-workload-transact-sql-script-file"></a>Per ottimizzare un file script Transact-SQL del carico di lavoro  
  
1.  Copiare una o più istruzioni SELECT di esempio da "A. Utilizzo dell'istruzione SELECT per il recupero di righe e colonne" in [Esempi di istruzioni SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-examples-transact-sql.md) e incollare le istruzioni nell'Editor di query di [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Salvare il file con il nome **MyScript.sql** in una directory in cui sia possibile trovarlo facilmente.  
  
2.  Avviare Ottimizzazione guidata motore di database. Vedere [Avvio dello strumento Ottimizzazione guidata motore di database](../../tools/dta/lesson-1-1-launching-database-engine-tuning-advisor.md).  
  
3.  Nel riquadro destro della GUI di Ottimizzazione guidata motore di database digitare **MySession** in **Nome sessione**.  
  
4.  Selezionare **File** per **Carico di lavoro**e fare clic sul pulsante **Consente di cercare un file di carico di lavoro** per trovare il file **MyScript.sql** salvato nel passaggio 1.  
  
5.  Selezionare [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] nell'elenco **Database per l'analisi del carico di lavoro** , selezionare [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] nella griglia **Selezionare i database e le tabelle da ottimizzare** e lasciare selezionata l'opzione **Salva log di ottimizzazione** . **Database per l'analisi del carico di lavoro** specifica il primo database al quale Ottimizzazione guidata motore di database si connette durante l'ottimizzazione di un carico di lavoro. Dopo l'inizio dell'ottimizzazione, Ottimizzazione guidata motore di database si connette ai database specificati dalle istruzioni `USE DATABASE` contenute nel carico di lavoro.  
  
6.  Selezionare la scheda **Opzioni di ottimizzazione** . In questa esercitazione non verranno impostate le opzioni di ottimizzazione, tuttavia è utile analizzare brevemente le opzioni di ottimizzazione predefinite. Premere F1 per visualizzare la Guida relativa a questa pagina a schede. Fare clic su **Opzioni avanzate** per visualizzare le opzioni di ottimizzazione aggiuntive. Fare clic su **?** nella finestra di dialogo **Opzioni di ottimizzazione avanzate** per ottenere informazioni sulle opzioni di ottimizzazione visualizzate. Fare clic su **Annulla** per chiudere la finestra di dialogo **Opzioni di ottimizzazione avanzate** lasciando selezionate le opzioni predefinite.  
  
7.  Fare clic sul pulsante **Avvia analisi** sulla barra degli strumenti. Durante l'esecuzione dell'analisi del carico di lavoro da parte di Ottimizzazione guidata motore di database, è possibile monitorarne lo stato nella scheda **Stato** . Dopo aver completato l'ottimizzazione, verrà visualizzata la scheda **Indicazioni**.  
  
    Se viene visualizzato un errore relativo alla data e ora di arresto dell'ottimizzazione, controllare l'impostazione **Data e ora arresto** nella scheda principale **Opzioni di ottimizzazione** . Verificare che i valori **Data e ora arresto** siano successivi alla data e all'ora correnti e, se necessario, modificarli.  
  
8.  Dopo aver completato l'analisi, salvare le indicazioni come script [!INCLUDE[tsql](../../includes/tsql-md.md)] scegliendo **Salva indicazioni** dal menu **Azioni** . Nella finestra di dialogo **Salva con nome** trovare la directory in cui si vuole salvare lo script delle indicazioni e digitare il nome file **MyRecommendations**.  
  
## <a name="summary"></a>Riepilogo  
In questo modo è stata completata l'ottimizzazione di un carico di lavoro di un'istruzione SELECT semplice sul database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . Ottimizzazione guidata motore di database accetta inoltre file di traccia e tabelle [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] come carichi di lavoro da ottimizzare. Nell'attività successiva verranno illustrate le procedure per visualizzare e interpretare le indicazioni scaturite dall'esercitazione sull'ottimizzazione.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
[Visualizzazione delle indicazioni di ottimizzazione](../../tools/dta/lesson-1-2-viewing-tuning-recommendations.md)  
  
  
  

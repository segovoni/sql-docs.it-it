---
title: Salvare i risultati della traccia in una tabella (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.suite: sql
ms.technology: profiler
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- saving traces
- traces [SQL Server], saving
ms.assetid: edbecf74-683b-4e43-a1ef-7a3d5f5e27f6
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0a6cc3ce79e82125e3f3141cbfbb2372c9cc45da
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33076940"
---
# <a name="save-trace-results-to-a-table-sql-server-profiler"></a>Salvare i risultati della traccia in una tabella (SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  In questo argomento viene descritta la procedura per salvare i risultati della traccia in una tabella di database mediante [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### <a name="to-save-trace-results-to-a-table"></a>Per salvare i risultati della traccia in una tabella  
  
1.  Scegliere **Nuova traccia** dal menu **File**e quindi connettersi a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     Verrà visualizzata la finestra di dialogo **Proprietà traccia**.  
  
    > [!NOTE]  
    >  Se l'opzione **Avvia traccia non appena viene stabilita una connessione**è selezionata, la finestra di dialogo **Proprietà traccia**non viene visualizzata e viene invece avviata la traccia. Per disabilitare questa impostazione, scegliere **Opzioni**dal menu **Strumenti**e deselezionare la casella di controllo **Avvia traccia non appena viene stabilita una connessione** .  
  
2.  Nella casella **Nome traccia** digitare il nome della traccia e quindi fare clic su **Salva nella tabella**.  
  
3.  Nella finestra di dialogo **Connetti al server** connettersi al database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che conterrà la tabella di traccia.  
  
4.  Nella finestra di dialogo **Tabella di destinazione** selezionare un database dall'elenco **Database**.  
  
5.  Nell'elenco **Proprietario** selezionare il proprietario della traccia.  
  
6.  Nell'elenco **Tabella** digitare o selezionare il nome della tabella per i risultati della traccia. Scegliere **OK.**  
  
7.  Nella finestra di dialogo **Proprietà traccia** selezionare la casella di controllo **Numero massimo di righe (in migliaia)** per specificare il numero massimo di righe da salvare.  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  

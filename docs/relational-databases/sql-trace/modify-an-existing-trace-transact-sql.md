---
title: Modificare una traccia esistente (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: sql-trace
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], modifying
- modifying traces
ms.assetid: 8792b43f-2510-44e3-9239-e73ad8227b89
caps.latest.revision: 18
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e22f460de2da214e10a2ef5855f04c026ea753f3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32971036"
---
# <a name="modify-an-existing-trace-transact-sql"></a>Modificare una traccia esistente (Transact-SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  In questo argomento viene descritto come utilizzare stored procedure per modificare una traccia esistente.  
  
### <a name="to-modify-an-existing-trace"></a>Per modificare una traccia esistente  
  
1.  Se la traccia è già in esecuzione, eseguire **sp_trace_setstatus** specificando **@status = 0** per arrestarla.  
  
2.  Per modificare eventi di traccia, eseguire **sp_trace_setevent** usando i parametri per specificare le modifiche. Nell'ordine i parametri sono i seguenti:  
  
    -   **@traceid** (ID traccia)  
  
    -   **@eventid** (ID evento)  
  
    -   **@columnid** (ID colonna)  
  
    -   **@on** (ON)  
  
     Quando si modifica il parametro **@on** , tenere presente l'interazione con il parametro **@columnid** :  
  
    |ON|ID colonna|Risultato|  
    |--------|---------------|------------|  
    |ON (**1**)|NULL|L'evento viene abilitato. Tutte le colonne vengono cancellate.|  
    ||NOT NULL|La colonna viene abilitata per l'evento specificato.|  
    |OFF (**0**)|NULL|L'evento viene disabilitato. Tutte le colonne vengono cancellate.|  
    ||NOT NULL|La colonna viene disabilitata per l'evento specificato.|  
  
> [!IMPORTANT]  
>  A differenza di quanto avviene con le normali stored procedure, i parametri di tutte le stored procedure di [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] (**sp_trace_* xx***) sono fortemente tipizzati e non supportano la conversione automatica del tipo di dati. Se tali parametri non vengono chiamati con i tipi di dati corretti per i parametri di input, come indicato nella descrizione dell'argomento, la stored procedure restituisce un errore.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [sp_trace_setstatus &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Stored procedure di SQL Server Profiler &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql.md)  
  
  

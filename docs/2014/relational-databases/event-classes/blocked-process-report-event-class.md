---
title: Classe di evento Blocked Process Report | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Blocked Process Report event class
ms.assetid: e8acb408-938d-4b36-81dd-04f087410cc5
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 42f2ddfeb6df940b03301a731ac2e868423ba112
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37298464"
---
# <a name="blocked-process-report-event-class"></a>Blocked Process Report - classe di evento
  La classe di evento **Blocked Process Report** indica che un'attività è stata bloccata per un periodo di tempo più lungo di quello specificato. Questa classe di evento non include attività di sistema o attività in attesa di risorse per le quali non sono rilevabili i deadlock.  
  
 Per configurare la soglia e la frequenza relative alla generazione di report, utilizzare il comando **sp_configure** per impostare l'opzione **blocked process threshold** . Per eseguire questa operazione occorrono pochi secondi. Per impostazione predefinita, non vengono generati report relativi ai processi bloccati. Per altre informazioni sull'opzione **blocked process threshold**, vedere [Opzione di configurazione del server blocked process threshold](../../database-engine/configure-windows/blocked-process-threshold-server-configuration-option.md).  
  
 Per informazioni su come filtrare i dati restituiti dalla classe di evento **Blocked Process Report**, vedere [Filtrare eventi in una traccia &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md), [Impostare un filtro di traccia &#40;Transact-SQL&#41;](../../ssms/agent/set-sql-server-alias-for-sql-server-agent-service-ssms.md) o [sp_trace_setfilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql).  
  
## <a name="blocked-process-report-event-class-data-columns"></a>Colonne di dati della classe di evento Blocked Process Report  
  
|Nome colonna di dati|Tipo di dati|Description|ID colonna|Filtrabile|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**DatabaseID**|**int**|ID del database in cui è stato acquisito il blocco. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] visualizza il nome del database se la colonna di dati **ServerName** è acquisita nella traccia e il server è disponibile. Determinare il valore per un database utilizzando la funzione DB_ID.|3|Sì|  
|**Durata**|**bigint**|Durata in millisecondi del blocco relativo al processo.|13|Sì|  
|**EndTime**|**datetime**|Ora di fine dell'evento. Questa colonna non viene popolata per le classi degli eventi di avvio, come **SQL:BatchStarting** o **SP:Starting**.|15|Sì|  
|**EventClass**|**int**|Tipo di evento = 137.|27|no|  
|**EventSequence**|**int**|Sequenza di un determinato evento all'interno della richiesta.|51|no|  
|**IndexID**|**int**|ID dell'indice dell'oggetto interessato dall'evento. Per determinare l'ID di indice di un oggetto, utilizzare la colonna **indid** della tabella di sistema **sysindexes** .|24|Sì|  
|**IsSystem**|**int**|Indica se l'evento è stato generato per un processo di sistema o un processo utente. 1 = sistema, 0 = utente.|60|Sì|  
|**LoginSid**|**image**|ID di sicurezza (SID) dell'utente connesso. Questo evento viene segnalato sempre dal thread di sistema. IsSystem = 1; SID = sa.|41|Sì|  
|**Mode**|**int**|Stato ricevuto o richiesto dall'evento.<br /><br /> 0=NULL<br /><br /> 1=Sch-S<br /><br /> 2=Sch-M<br /><br /> 3=S<br /><br /> 4=U<br /><br /> 5=X<br /><br /> 6=IS<br /><br /> 7=IU<br /><br /> 8=IX<br /><br /> 9=SIU<br /><br /> 10=SIX<br /><br /> 11=UIX<br /><br /> 12=BU<br /><br /> 13=RangeS-S<br /><br /> 14=RangeS-U<br /><br /> 15=RangeI-N<br /><br /> 16=RangeI-S<br /><br /> 17=RangeI-U<br /><br /> 18=RangeI-X<br /><br /> 19=RangeX-S<br /><br /> 20=RangeX-U<br /><br /> 21=RangeX-X|32|Sì|  
|**ObjectID**|**int**|ID assegnato dal sistema all'oggetto sul quale è stato acquisito il blocco, se disponibile e applicabile.|22|Sì|  
|**ServerName**|**nvarchar**|Nome dell'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tracciata.|26||  
|**SessionLoginName**|**nvarchar**|Nome dell'account di accesso dell'utente che ha avviato la sessione. Se ad esempio si stabilisce la connessione a SQL Server con l'account di accesso Login1 e si esegue un'istruzione con l'account di accesso Login2, **SessionLoginName** indica Login1 e **LoginName** indica Login2. In questa colonna sono visualizzati sia gli account di accesso di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] che quelli di Windows.|64|Sì|  
|**TextData**|**ntext**|Valore di testo che dipende dalla classe di evento acquisita nella traccia.|1|Sì|  
|**TransactionID**|**bigint**|ID della transazione assegnato dal sistema.|4|Sì|  
  
## <a name="see-also"></a>Vedere anche  
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  

---
title: Classe di evento Database Mirroring State Change | Microsoft Docs
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
- event notifications [SQL Server], database mirroring
- database mirroring [SQL Server], event notifications
- Database Mirroring State Change event class
ms.assetid: f936a99e-2a81-4768-8177-5c969bbe2e04
caps.latest.revision: 31
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e635ff34d280affd22d5f0d7854b3c8d7f1a717d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37257339"
---
# <a name="database-mirroring-state-change-event-class"></a>Database Mirroring State Change - classe di evento
  La classe di evento **Database Mirroring State Change** indica la variazione dello stato di un database con mirroring. Includere questa classe di evento nelle tracce che eseguono il monitoraggio delle condizioni dei database con mirroring.  
  
 Quando la classe di evento **Database Mirroring State Change** viene inclusa in una traccia, il relativo overhead è ridotto. L'overhead può essere maggiore se il valore dello stato dei database con mirroring aumenta.  
  
## <a name="data-database-mirroring-state-change-event-class-data-columns"></a>Colonne di dati della classe di evento Database Mirroring State Change  
  
|Nome colonna di dati|Tipo di dati|Description|ID colonna|Filtrabile|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**DatabaseID**|**int**|ID del database specificato nell'istruzione di *database* USE oppure il database predefinito se per un'istanza specifica l'istruzione di *database* USE non è stata eseguita. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] visualizza il nome del database se la colonna di dati **ServerName** è acquisita nella traccia e il server è disponibile. Determinare il valore per un database utilizzando la funzione DB_ID.|3|Sì|  
|**DatabaseName**|**nvarchar**|Nome del database con mirroring.|35|Sì|  
|**EventClass**|**int**|Tipo di evento = 167.|27|no|  
|**EventSequence**|**int**|Sequenza della classe di evento nel batch.|51|no|  
|**IntegerData**|**int**|ID di stato precedente.|25|Sì|  
|**IsSystem**|**int**|Indica se l'evento è stato generato per un processo di sistema o un processo utente. 1 = sistema, 0 = utente.|60|Sì|  
|**LoginSid**|**image**|ID di sicurezza (SID) dell'utente connesso. Queste informazioni sono disponibili nella vista del catalogo **sys.server_principals** . Il SID è univoco per ogni account di accesso nel server.|41|Sì|  
|**RequestID**|**int**|ID della richiesta contenente l'istruzione.|49|Sì|  
|**ServerName**|**nvarchar**|Nome dell'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracciata.|26|no|  
|**SessionLoginName**|**nvarchar**|Nome dell'account di accesso dell'utente che ha avviato la sessione. Se ad esempio si stabilisce la connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con l'account di accesso Login1 e si esegue un'istruzione con l'account di accesso Login2, **SessionLoginName** indica Login1 e **LoginName** indica Login2. In questa colonna sono visualizzati sia gli account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che quelli di Windows.|64|Sì|  
|**SPID**|**int**|ID della sessione in cui si è verificato l'evento.|12|Sì|  
|**StartTime**|**datetime**|Ora di inizio dell'evento, se disponibile.|14|Sì|  
|**State**|**Int**|Nuovo ID dello stato di mirroring:<br /><br /> 0 = Notifica Null<br /><br /> 1 = Server principale sincronizzato con il server di controllo del mirroring<br /><br /> 2 = Server principale sincronizzato senza il server di controllo del mirroring<br /><br /> 3 = Server mirror sincronizzato con il server di controllo del mirroring<br /><br /> 4 = Server mirror sincronizzato senza il server di controllo del mirroring<br /><br /> 5 = Perdita di connessione con il server principale<br /><br /> 6 = Perdita di connessione con il server mirror<br /><br /> 7 = Failover manuale<br /><br /> 8 = Failover automatico<br /><br /> 9 = Mirroring sospeso<br /><br /> 10 = Nessun quorum<br /><br /> 11 = Sincronizzazione del server mirror in corso<br /><br /> 12 = Server principale in esecuzione esposto|30|Sì|  
|**TextData**|**ntext**|Descrizione della variazione di stato.|1|Sì|  
|**TransactionID**|**bigint**|ID della transazione assegnato dal sistema.|4|Sì|  
  
## <a name="see-also"></a>Vedere anche  
 [Eventi estesi](../extended-events/extended-events.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  

---
title: Stati di mirroring (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- states [SQL Server], database mirroring
- PENDING_FAILOVER state
- mirroring states [SQL Server]
- DISCONNECTED state
- SYNCHRONIZING state
- SYNCHRONIZED state
- SUSPENDED state
- database mirroring [SQL Server], states
ms.assetid: 90062917-74f9-471b-b49e-bc153ae1a468
caps.latest.revision: 38
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 10cc3385d0bbcd7832533e1e375401b1b060c959
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37320722"
---
# <a name="mirroring-states-sql-server"></a>Stati di mirroring (SQL Server)
  Durante una sessione di mirroring del database, il database con mirroring si trova sempre in uno stato specifico, ovvero lo *stato di mirroring*. Lo stato del database riflette lo stato delle comunicazioni, il flusso di dati e la differenza nei dati tra i partner. La sessione di mirroring del database adotta lo stesso stato del database principale.  
  
 Nel corso della sessione di mirroring del database viene eseguito il monitoraggio reciproco delle istanze del server. Per eseguire il monitoraggio del database, i partner utilizzano lo stato di mirroring. Ad eccezione dello stato PENDING_FAILOVER, lo stato del database principale è sempre identico a quello del database mirror. Se per la sessione è impostato un server di controllo del mirroring, per eseguire il monitoraggio di tale server ciascun partner utilizza il relativo stato della connessione (CONNECTED o DISCONNECTED).  
  
 Gli stati di mirroring possibili del database sono i seguenti:  
  
|stato di mirroring|Description|  
|---------------------|-----------------|  
|SYNCHRONIZING|Il contenuto del database mirror è in ritardo rispetto a quello del database principale. Il server principale invia i record del log al server mirror, che applica le modifiche al database mirror ai fini del rollforward.<br /><br /> All'inizio di una sessione di mirroring, lo stato del database è SYNCHRONIZING. Il server principale soddisfa le richieste del database e il mirror tenta di aggiornarsi.|  
|SYNCHRONIZED|Quando il server mirror è sufficientemente aggiornato rispetto al server principale, lo stato di mirroring diventa SYNCHRONIZED. Il database resta in questo stato fino a quando il server principale continua a inviare modifiche al server mirror e quest'ultimo continua ad applicare le modifiche al database mirror.<br /><br /> Se la protezione delle transazioni è impostata su FULL, il failover automatico e quello manuale sono supportati nello stato SYNCHRONIZED, quindi non può verificarsi una perdita di dati dopo un failover.<br /><br /> Se la protezione delle transazioni è disattivata, è possibile che si verifichi la perdita di dati anche in stato SYNCHRONIZED.|  
|SUSPENDED|La copia mirror del database non è disponibile. Il database principale viene eseguito senza inviare log al server mirror. Tale condizione è nota come *esecuzione senza mirroring*. Si tratta dello stato attivo dopo un failover.<br /><br /> Una sessione può diventare SUSPENDED anche in seguito a errori di rollforward oppure se viene sospesa dall'amministratore.<br /><br /> Lo stato SUSPENDED è persistente in quanto non viene modificato in seguito a operazioni di chiusura e avvio dei partner.|  
|PENDING_FAILOVER|Questo stato viene applicato solo sul server principale dopo l'avvio di un failover, quando il server non è ancora passato al ruolo di mirror.<br /><br /> Quando il failover viene avviato, lo stato del database principale diventa PENDING_FAILOVER, vengono rapidamente interrotte eventuali connessioni utente e subito dopo il database assume il ruolo di mirror.|  
|DISCONNECTED|Le comunicazioni tra un partner e l'altro sono state interrotte.|  
  
## <a name="see-also"></a>Vedere anche  
 [Monitoraggio del mirroring del database &#40;SQL Server&#41;](database-mirroring-sql-server.md)  
  
  

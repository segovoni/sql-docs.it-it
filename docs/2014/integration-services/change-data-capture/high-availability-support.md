---
title: Supporto a disponibilità elevata | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 2e0f6d3f-0536-46d9-8630-835e199515bf
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 1ebf240434df77c1f860e31952f12ec3eb0d13a2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37271327"
---
# <a name="high-availability-support"></a>Supporto a disponibilità elevata
  Il servizio CDC per Oracle è progettato per la disponibilità elevata. Le funzionalità seguenti forniscono parte del supporto della disponibilità elevata:  
  
-   Nel servizio CDC per Oracle non viene utilizzata alcuna risorsa di file (locale o di altro tipo). L'intero stato è archiviato nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di destinazione. Ciò semplifica l'avvio del servizio in un computer diverso in cui viene utilizzata la stessa istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se si verifica un errore nel computer in cui viene eseguito il servizio. Per ridurre il tempo di recupero, le transazioni Oracle lunghe o con esecuzione prolungata vengono mantenute in una tabella di staging nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]di destinazione, evitando la necessità di rianalizzare molti log delle transazioni di Oracle in seguito a un errore (o un riavvio del servizio).  
  
-   Nel servizio CDC per Oracle è possibile utilizzare istanze cluster di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per permettere il recupero in caso di failover dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a un altro nodo del cluster. È sufficiente che l'amministratore del computer del servizio Oracle CDC specifichi le informazioni di connessione all'istanza cluster di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alla creazione di un servizio Oracle CDC.  
  
-   Il servizio CDC per Oracle può usare la [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] **AlwaysOn** funzionalità di mirroring del database. Il supporto richiede che MSXDBCDC e tutti i database CDC siano nello stesso gruppo di disponibilità. Richiede anche l'amministratore di Oracle CDC Service Computer specificare l'appropriato **AlwaysOn** informazioni di connessione per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gruppo di disponibilità (ad esempio, le proprietà di connessione `Failover_Partner and Network=dbmssocn`). In questo modo sarà possibile riprendere automaticamente l'elaborazione del servizio CDC in una replica secondaria dei database in seguito a un failover.  
  
-   È possibile configurare il servizio CDC per Oracle come risorsa del servizio generica in un cluster di failover di Windows (insieme a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]o separatamente), semplificando il failover e il fallback dell'elaborazione CDC con il cluster. Per configurare il servizio CDC per Oracle come risorsa in un cluster di failover, l'amministratore di sistema deve impostare il servizio CDC per Oracle come risorsa di servizio generico in ogni nodo nel cluster di failover.  
  
-   Il servizio CDC per Oracle supporta Oracle RAC che consente la comunicazione con il database Oracle e l'elaborazione di log anche quando uno dei nodi Oracle RAC non funziona.  
  
  

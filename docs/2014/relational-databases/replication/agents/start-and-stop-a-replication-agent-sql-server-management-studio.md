---
title: Avviare e arrestare un agente di replica (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- agents [SQL Server replication], stopping
- agents [SQL Server replication], starting
ms.assetid: 97977c4a-8c7c-4a22-9480-69aa812bd1e5
caps.latest.revision: 40
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 70011cb38e22d94b72eb41ccb01f10a7739c05d9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37281227"
---
# <a name="start-and-stop-a-replication-agent-sql-server-management-studio"></a>Avviare e arrestare un agente di replica (SQL Server Management Studio)
  Avviare e arrestare gli agenti dalla cartella **Processi** e dalla cartella **Replica** in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] and from Replica Monitor. Avviare e arrestare gli agenti e i processi seguenti:  
  
-   Agente snapshot, utilizzato da tutte le pubblicazioni.  
  
-   Agente di lettura log, utilizzato da tutte le pubblicazioni transazionali.  
  
-   Agente di lettura coda, utilizzato dalle pubblicazioni transazionali abilitate per le sottoscrizioni ad aggiornamento in coda.  
  
-   Agente di distribuzione, che consente di sincronizzare le sottoscrizioni con le pubblicazioni transazionali e snapshot.  
  
-   Agente di merge, che consente di sincronizzare le sottoscrizioni con le pubblicazioni di tipo merge.  
  
-   Processi di manutenzione della replica.  
  
 Per altre informazioni sull'avvio dell'agente di merge e dell'agente di distribuzione, vedere [Sincronizzare una sottoscrizione push](../synchronize-a-push-subscription.md) e [Sincronizzare una sottoscrizione pull](../synchronize-a-pull-subscription.md). Per altre informazioni sui processi di manutenzione, vedere [Eseguire processi di manutenzione della replica &#40;SQL Server Management Studio&#41;](../../../ssms/sql-server-management-studio-ssms.md).  
  
 Per informazioni sull'avvio di Monitoraggio replica, vedere [Avviare Monitoraggio replica](../monitor/start-the-replication-monitor.md).  
  
### <a name="to-start-and-stop-a-snapshot-agent-or-log-reader-agent-from-management-studio"></a>Per avviare e arrestare un agente snapshot o un agente di lettura log da Management Studio  
  
1.  Connettersi al server di pubblicazione in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]e quindi espandere il nodo del server e la cartella **Replica** .  
  
2.  Espandere la cartella **Pubblicazioni locali** e quindi fare clic con il pulsante destro del mouse su una pubblicazione.  
  
3.  Scegliere **Visualizza stato agente snapshot** o **Visualizza stato agente di lettura log**.  
  
4.  Fare clic su **Avvia** o su **Arresta**.  
  
### <a name="to-start-and-stop-a-queue-reader-agent-from-management-studio"></a>Per avviare e arrestare un agente di lettura coda da Management Studio  
  
1.  Connettersi al server di distribuzione in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]e quindi espandere il nodo del server.  
  
2.  Espandere la cartella **SQL Server Agent** e quindi la cartella **Processi** .  
  
3.  Fare clic con il pulsante destro del mouse sul processo dell'agente e quindi scegliere **Avvia processo** o **Arresta processo**. Il nome del processo relativo all'agente di lettura coda si trova nel form **[\<Server di distribuzione>].\<numero intero>**.  
  
### <a name="to-start-and-stop-a-snapshot-agent-log-reader-agent-or-queue-reader-agent-from-replication-monitor"></a>Per avviare e arrestare un agente snapshot, un agente di lettura log o un agente di lettura coda da Monitoraggio replica  
  
1.  Espandere un gruppo di server di pubblicazione nel riquadro sinistro, espandere un server di pubblicazione e quindi fare clic su una pubblicazione.  
  
2.  Fare clic sulla scheda **Agenti** .  
  
3.  Fare clic con il pulsante destro del mouse su un agente e quindi scegliere **Avvia agente** o **Arresta agente**.  
  
## <a name="see-also"></a>Vedere anche  
 [Monitoraggio della replica](../monitoring-replication.md)   
 [Concetti di base relativi ai file eseguibili dell'agente di replica](../concepts/replication-agent-executables-concepts.md)   
 [Replication Agents Overview](replication-agents-overview.md)  
  
  

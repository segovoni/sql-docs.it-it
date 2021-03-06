---
title: Visualizzare le informazioni ed eseguire attività relative a un server di pubblicazione (Monitoraggio replica) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Publishers [SQL Server replication], Replication Monitor tasks
- viewing Publisher information
- Publishers [SQL Server replication], viewing information
ms.assetid: 1e777e95-377a-4de3-b965-867464aadaaf
caps.latest.revision: 37
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fc7dbc752e1eb6efafdd415cd88b2351fe6b99c6
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37357393"
---
# <a name="view-information-and-perform-tasks-for-a-publisher-replication-monitor"></a>Visualizzare le informazioni e eseguire attività relative a un server di pubblicazione (Monitoraggio replica)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  In Monitoraggio replica sono disponibili le schede seguenti in cui vengono visualizzate informazioni sul server di pubblicazione selezionato:  
  
-   **Pubblicazioni**  
  
     In questa scheda vengono visualizzate informazioni su tutte le pubblicazioni del server di pubblicazione selezionato.  
  
-   **Elenco verifica sottoscrizioni**  
  
     In questa scheda vengono visualizzate informazioni sulle sottoscrizioni di tutte le pubblicazioni disponibili sul server di pubblicazione selezionato che presentano errori, avvisi o un livello di prestazioni insufficiente. Questa scheda non viene visualizzata per i server di distribuzione che eseguono versioni di SQL Server precedenti a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
-   Scheda**Agenti**   
  
     In questa scheda vengono visualizzate informazioni dettagliate su agenti e processi utilizzati da tutti i tipi di replica. La scheda consente anche di avviare e arrestare ciascun agente e processo.  
  
 Per visualizzare ulteriori informazioni sulle opzioni disponibili nelle singole schede, fare clic sulla scheda nel riquadro destro e quindi su **?** nella barra dei menu. Per informazioni sull'avvio di Monitoraggio replica, vedere [Avviare Monitoraggio replica](../../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
### <a name="to-view-information-and-perform-tasks-for-a-publisher"></a>Per visualizzare informazioni ed eseguire attività relative a un server di pubblicazione  
  
1.  Espandere un gruppo di server di pubblicazione nel riquadro sinistro e quindi fare clic su un server di pubblicazione.  
  
2.  Per visualizzare informazioni su tutte le pubblicazioni, fare clic sulla scheda **Pubblicazioni** .  
  
3.  Per visualizzare informazioni sulle sottoscrizioni, fare clic sulla scheda **Elenco verifica sottoscrizioni** . In questa scheda, è inoltre possibile accedere a informazioni più dettagliate ed eseguire altre attività.  
  
    -   Per visualizzare informazioni dettagliate sull'agente associato a una sottoscrizione, fare clic con il pulsante destro del mouse sulla sottoscrizione e quindi scegliere **Visualizza dettagli**.  
  
    -   Per visualizzare le proprietà di una sottoscrizione, fare clic con il pulsante destro del mouse sulla sottoscrizione e quindi scegliere **Proprietà**.  
  
    -   Per sincronizzare una sottoscrizione push, fare clic con il pulsante destro del mouse sulla sottoscrizione e quindi scegliere **Avvia sincronizzazione**.  
  
    -   Per reinizializzare una sottoscrizione, fare clic con il pulsante destro del mouse sulla sottoscrizione e quindi scegliere **Reinizializza sottoscrizione**.  
  
4.  Per visualizzare informazioni sugli agenti, fare clic sulla scheda **Agenti** . In questa scheda è inoltre possibile accedere a informazioni più dettagliate ed eseguire altre attività:  
  
    -   Per visualizzare informazioni dettagliate su un agente, ad esempio messaggi informativi ed eventuali messaggi di errore, fare clic con il pulsante destro del mouse sull'agente e quindi scegliere **Visualizza dettagli**.  
  
    -   Per visualizzare informazioni dettagliate sul processo eseguito dall'agente, ad esempio la pianificazione, i dettagli sui passaggi del processo e così via, fare clic con il pulsante destro del mouse sull'agente e quindi scegliere **Proprietà**.  
  
    -   Per gestire i profili dell'agente, fare clic con il pulsante destro del mouse sull'agente e quindi scegliere **Profilo agente**. Per altre informazioni, vedere [Usare i profili agenti di replica](../../../relational-databases/replication/agents/work-with-replication-agent-profiles.md).  
  
    -   Per avviare un agente non in esecuzione, fare clic con il pulsante destro del mouse sull'agente e quindi scegliere **Avvia agente**.  
  
    -   Per arrestare l'esecuzione di un agente, fare clic con il pulsante destro del mouse sull'agente e quindi scegliere **Arresta agente**.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzare e modificare le proprietà del server di pubblicazione e del database di distribuzione](../../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [Monitoraggio della replica](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  

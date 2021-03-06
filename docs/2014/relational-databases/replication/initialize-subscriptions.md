---
title: Inizializzare le sottoscrizioni | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.initializesubscriptions.f1
ms.assetid: 7b170e4e-470d-4828-a9ed-7435b0b03514
caps.latest.revision: 23
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6e80b04a7ba6d62ba57d237a61d5fc8b5bec6ec0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37240561"
---
# <a name="initialize-subscriptions"></a>Inizializzazione sottoscrizioni
  È necessario inizializzare i Sottoscrittori prima che possano iniziare a ricevere dati replicati. Non è necessario un set di dati iniziale, ma è necessario che il Sottoscrittore disponga almeno dello schema per ogni oggetto replicato, nonché delle tabelle dei metadati e delle procedure necessarie per la replica.  
  
## <a name="options"></a>Opzioni  
 **Proprietà sottoscrizione**  
 Selezionare la casella di controllo nella colonna **Inizializza** per ogni Sottoscrittore che necessita di un set di dati iniziale. Se la casella di controllo non è selezionata, verranno inizializzati solo i metadati e le procedure della replica. Per altre informazioni sull'inizializzazione di una sottoscrizione senza uno snapshot, vedere [Inizializzare una sottoscrizione transazionale senza uno snapshot](initialize-a-transactional-subscription-without-a-snapshot.md).  
  
 Selezionare **Immediatamente** nell'elenco a discesa della colonna **Quando** per fare in modo che l'agente di merge o l'agente di distribuzione trasferisca i file di snapshot al Sottoscrittore al termine della procedura guidata. Selezionare **Alla prima sincronizzazione** per fare in modo che l'agente trasferisca i file alla successiva esecuzione pianificata dell'agente. L'opzione **Immediatamente** non è disponibile per le sottoscrizioni pull di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]. L'agente di merge e l'agente di distribuzione non vengono eseguiti nelle istanze di [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]. È pertanto necessario inizializzare la sottoscrizione utilizzando un altro metodo.  
  
> [!NOTE]  
>  Durante la procedura guidata è possibile che venga richiesto di selezionare la connessione al server di distribuzione per consentire l'avvio del processo appropriato per l'agente di distribuzione o l'agente di merge.  
  
## <a name="see-also"></a>Vedere anche  
 [Create a Pull Subscription](create-a-pull-subscription.md)   
 [Create a Push Subscription](create-a-push-subscription.md)   
 [Inizializzare una sottoscrizione](initialize-a-subscription.md)   
 [Sottoscrizione delle pubblicazioni](subscribe-to-publications.md)  
  
  

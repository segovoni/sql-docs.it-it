---
title: Profili agenti (agente singolo) | Microsoft Docs
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
- sql12.rep.profiles.perfprofileagentname.f1
helpviewer_keywords:
- Agent Profile dialog box
ms.assetid: 22713555-c496-4ce1-8ec7-4ae75cfadca8
caps.latest.revision: 17
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 33d8a5564d6153a48da93da9b9a89ec3892a25a9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37284957"
---
# <a name="agent-profiles-single-agent"></a>Profili agenti (agente singolo)
  Utilizzare la finestra di dialogo **Profili agenti** per gestire i profili per un agente. I profili agenti consentono di gestire facilmente i parametri di run-time per ogni agente. Ogni agente dispone di un profilo predefinito e alcuni agenti dispongono di profili predefiniti aggiuntivi. L'agente di merge, ad esempio, dispone di un profilo "collegamento lento" dedicato alle connessioni a larghezza di banda ridotta. I profili predefiniti sono sufficienti per la maggior parte delle applicazioni, ma è possibile creare profili definiti dall'utente, che consentono di personalizzare il funzionamento degli agenti.  
  
## <a name="options"></a>Opzioni  
 **Predefinito per i nuovi agenti**  
 Consente di selezionare il profilo che verrà utilizzato durante la creazione dei processi per un dato tipo di agente. Se ad esempio si creano varie sottoscrizioni a una pubblicazione di tipo merge, il processo dell'agente di merge per ogni sottoscrizione utilizzerà il profilo selezionato. Per modificare il profilo di processi esistenti, selezionare un profilo e quindi fare clic su **Modifica agenti esistenti**.  
  
 **Nome**  
 Nome del profilo.  
  
 **Tipo**  
 Tipo di profilo: **Utente** (definito dall'utente) o **Sistema** (predefinito).  
  
 **Proprietà (...)**  
 Fare clic su questo pulsante per visualizzare i valori utilizzati per ogni parametro nel profilo agente.  
  
 **Nuova**  
 Fare clic su questo pulsante per creare un nuovo profilo.  
  
 **Elimina**  
 Selezionare un profilo definito dall'utente e quindi fare clic su **Elimina** per eliminarlo. I profili predefiniti non possono essere eliminati.  
  
 **Modifica agenti esistenti**  
 Selezionare un profilo e quindi fare clic su **Modifica agenti esistenti** per specificare che tutti i processi esistenti per un dato tipo di agente devono utilizzare il profilo selezionato. Se ad esempio sono state create varie sottoscrizioni a una pubblicazione di tipo merge e si desidera modificare il profilo per specificare che il processo dell'agente di merge per ogni sottoscrizione deve utilizzare il **Profilo agente a collegamento lento**, selezionare tale profilo e quindi fare clic su **Modifica agenti esistenti**.  
  
## <a name="see-also"></a>Vedere anche  
 [Usare i profili agenti di replica](agents/work-with-replication-agent-profiles.md)   
 [Panoramica degli agenti di replica](agents/replication-agents-overview.md)   
 [Profili degli agenti di replica](agents/replication-agent-profiles.md)  
  
  

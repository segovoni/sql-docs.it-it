---
title: Sicurezza agente di lettura log | Microsoft Docs
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
- sql12.rep.security.LRA.f1
helpviewer_keywords:
- Log Reader Agent Security dialog box
ms.assetid: d6981e74-ddb8-41b8-9ea1-56c2ece63b8a
caps.latest.revision: 19
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: aaefce06d1306e03b6efb89214191902f6c920ca
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37175728"
---
# <a name="log-reader-agent-security"></a>Sicurezza agente di lettura log
  La finestra di dialogo **Sicurezza agente di lettura log** consente di specificare i valori seguenti:  
  
-   L'account di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows utilizzato per l'esecuzione dell'agente di lettura log nel server di distribuzione. L'account di Windows è detto anche *account di processo*, poiché si tratta dell'account con cui viene eseguito il processo dell'agente.  
  
-   Il contesto in cui l'agente di lettura log stabilisce le connessioni al server di pubblicazione di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . La connessione può essere stabilita tramite rappresentazione dell'account di Windows oppure nel contesto di un account di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] specificato dall'utente.  
  
    > [!NOTE]  
    >  L'agente di lettura log stabilisce le connessioni al server di pubblicazione anche se il server di pubblicazione e il server di distribuzione si trovano sullo stesso computer. L'agente di lettura log stabilisce inoltre le connessioni al server di distribuzione, sempre tramite la rappresentazione dell'account di Windows utilizzato per l'esecuzione dell'agente.  
  
     Per i server di pubblicazione Oracle specificare un contesto utilizzato dall'agente di lettura log per creare la connessione al server di pubblicazione nella finestra di dialogo **Proprietà server di pubblicazione** , disponibile tramite la finestra di dialogo **Proprietà server di distribuzione** . Per altre informazioni, vedere [View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md).  
  
 Tutti gli account devono essere validi e per ogni account deve essere stata specificata la password corretta. Gli account e le password vengono convalidati solo dopo l'avvio dell'esecuzione di un agente.  
  
## <a name="options"></a>Opzioni  
 **Account processo**  
 Consente di immettere un account di Windows utilizzato per l'esecuzione dell'agente di lettura log nel server di distribuzione. L'account di Windows specificato deve essere almeno membro del ruolo predefinito del database **db_owner** nel server di distribuzione.  
  
 **Password** e **Conferma password**  
 Immettere la password per l'account di Windows.  
  
 **Connessione al server di pubblicazione**  
 Consente di specificare se l'agente di lettura log deve stabilire connessioni al server di pubblicazione tramite la rappresentazione dell'account specificato nella casella di testo **Account processo** o tramite un account di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Se si seleziona l'opzione per l'utilizzo di un account di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , immettere un account di accesso e una password di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] consiglia di scegliere di rappresentare l'account di Windows anziché di utilizzare un account di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 L'account di Windows o l'account di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizzato per la connessione deve essere almeno un membro del ruolo del database predefinito **db_owner** nel database di pubblicazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestire gli account di accesso e le password nella replica](security/manage-logins-and-passwords-in-replication.md)   
 [Modello di sicurezza dell'agente di replica](security/replication-agent-security-model.md)   
 [Panoramica degli agenti di replica](agents/replication-agents-overview.md)   
 [Procedure consigliate per la sicurezza della replica](security/replication-security-best-practices.md)  
  
  

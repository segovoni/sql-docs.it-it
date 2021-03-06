---
title: Piano di manutenzione (pagina Report e registrazione) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: maintenance-plans
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.swb.maint.reportinglogging.f1
ms.assetid: 3a30b17a-3deb-446f-900a-62f88934a90f
caps.latest.revision: 22
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: f9f4464692191446897d4b7222c359c1fac922f9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32947282"
---
# <a name="maintenance-plan-reporting-and-logging-page"></a>Piano di manutenzione (pagina Report e registrazione)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Utilizzare la finestra di dialogo **Report e registrazione** per configurare i report e i log generati durante l'esecuzione dei piani di manutenzione.  
  
## <a name="options"></a>Opzioni  
 **Genera report in un file di testo**  
 Consente di specificare se si vuole che [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] crei un report in un file di testo.  
  
 **Crea nuovo file**  
 Consente di creare un nuovo file di report per ogni esecuzione del piano di manutenzione. Per impostazione predefinita, i file di report vengono creati nel computer sul quale viene eseguita l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contenente il piano di manutenzione corrente, nella cartella specificata come cartella dei log predefinita durante l'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Per specificare una cartella diversa, immettere il percorso completo nella casella di testo **Cartella** oppure fare clic sul pulsante "**...**" e selezionare la cartella desiderata.  
  
 **Accoda a file**  
 Consente di accodare il report generato da ogni esecuzione del piano al file specificato nella casella di testo **Nome file** . È inoltre possibile specificare un file facendo clic sul pulsante Sfoglia (...) e selezionando un file nella finestra di dialogo visualizzata.  
  
 **Invia report a destinatario di posta elettronica**  
 Consente di trasmettere tramite posta elettronica il risultato dell'esecuzione di un piano di manutenzione. Questa opzione è disponibile solo se l'opzione Posta elettronica database è abilitata e configurata correttamente.  
  
 **Operatore agente**  
 Consente di selezionare un operatore agente nell'elenco come destinatario del messaggio di posta elettronica. Questa opzione è disponibile solo se la posta elettronica è abilitata e configurata correttamente.  
  
 **Registra informazioni estese**  
 Consente di includere maggiori informazioni nel log. Se questa opzione viene selezionata, le dimensioni della cronologia del piano di manutenzione archiviato risulteranno maggiori.  
  
 **Accedi a server remoto**  
 Consente di registrare la cronologia del piano di manutenzione in un server remoto.  
  
 **Connessione**  
 Consente di specificare le informazioni di connessione da utilizzare per la registrazione in un server remoto.  
  
 **Nuova**  
 Consente di visualizzare la finestra di dialogo **Proprietà connessione** . utilizzata per configurare le informazioni per una nuova connessione per la registrazione in un server remoto.  
  
## <a name="see-also"></a>Vedere anche  
 [Piani di manutenzione](../../relational-databases/maintenance-plans/maintenance-plans.md)   
 [Posta elettronica database](../../relational-databases/database-mail/database-mail.md)  
  
  

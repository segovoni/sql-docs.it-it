---
title: Cartella snapshot | Microsoft Docs
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.rep.replicationutilities.specifysnapshotfolder.f1
ms.assetid: 3eb1b73f-ddb3-4d09-be6e-811c414698e9
caps.latest.revision: 23
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 15d9b418efba107afad627159450ce45e08da94e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37296551"
---
# <a name="snapshot-folder"></a>Cartella snapshot
  La pagina **Cartella snapshot** viene visualizzata nella Configurazione guidata distribuzione e nella Creazione guidata nuova pubblicazione. Il percorso specificato per la cartella snapshot verrà utilizzato come percorso predefinito per tutti i server di pubblicazione abilitati nella procedura guidata. La cartella snapshot predefinita non si applica ai server di pubblicazione abilitati successivamente tramite la finestra di dialogo **Proprietà server di distribuzione** . Questa impostazione predefinita può essere sostituita per qualsiasi server di pubblicazione nella pagina **Server di pubblicazione** della Configurazione guidata distribuzione o della finestra di dialogo **Proprietà server di distribuzione** .  
  
 La cartella snapshot è semplicemente una directory designata come condivisione. Gli agenti che eseguono letture e scritture in questa cartella devono disporre di autorizzazioni sufficienti per accedervi. Per altre informazioni sulle impostazioni di sicurezza appropriate per la cartella, vedere [Proteggere la cartella snapshot](security/secure-the-snapshot-folder.md). Prima di implementare la replica è necessario verificare che gli agenti di replica possano connettersi alla cartella snapshot. Accedere con l'account che verrà utilizzato da ogni agente e quindi tentare di accedere alla cartella snapshot.  
  
## <a name="options"></a>Opzioni  
 **Snapshot folder**  
 Consente di immettere il percorso della cartella in cui archiviare i file di snapshot.  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] consiglia di usare una condivisione di rete come percorso della cartella snapshot. I percorsi locali, ovvero quelli che iniziano con una lettera di unità, ad esempio C:\\, non sono accessibili agli agenti in altri computer.  
  
## <a name="see-also"></a>Vedere anche  
 [Posizioni alternative della cartella snapshot](alternate-snapshot-folder-locations.md)   
 [Configura distribuzione](configure-distribution.md)   
 [Configurare la pubblicazione e la distribuzione](configure-publishing-and-distribution.md)   
 [Visualizzare e modificare le proprietà del server di pubblicazione e del database di distribuzione](view-and-modify-distributor-and-publisher-properties.md)   
 [Inizializzare una sottoscrizione con uno snapshot](initialize-a-subscription-with-a-snapshot.md)  
  
  

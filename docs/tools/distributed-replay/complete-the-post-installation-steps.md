---
title: Completare i passaggi di post-installazione | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.suite: sql
ms.technology: install
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 0a788a2a-9b4f-4bfc-b1b5-83eeb1ea9ab2
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 1b30c4ab640baca8ecfaaf39961038f2db98f599
ms.sourcegitcommit: abd71294ebc39695d403e341c4f77829cb4166a8
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2018
ms.locfileid: "36927062"
---
# <a name="complete-the-post-installation-steps"></a>Completare i passaggi successivi all'installazione
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Dopo aver installato il componente Riesecuzione distribuita, è necessario modificare gli account del controller e del servizio client relativi.  
  
### <a name="to-complete-the-post-installation-steps"></a>Per completare i passaggi di post-installazione  
  
1.  **Creare regole del firewall**: nei computer controller e client è necessario consentire il traffico in ingresso attraverso il firewall per il servizio corrispondente. Specificare le regole del firewall per i file eseguibili del servizio, all'interno delle cartelle di installazione.  
  
    1.  Per il servizio controller, creare una regola per **DReplayController.exe**, che si trova nella cartella di installazione. Il comando seguente, ad esempio, abilita questa regola, dove `%InstallPath%` è la cartella di installazione del servizio:  
  
         `netsh advfirewall firewall add rule name="allow dreplay controller" dir=in program="%InstallPath%\DReplayController\DReplayController.exe" action=allow`  
  
    2.  Per il servizio client, in ogni computer client creare una regola per **DReplayClient.exe**, che si trova nella cartella di installazione. Il comando seguente, ad esempio, abilita questa regola, dove `%InstallPath%` è la cartella di installazione del servizio:  
  
         `netsh advfirewall firewall add rule name="allow dreplay client" dir=in program="%InstallPath%\DReplayClient\DReplayClient.exe" action=allow`  
  
2.  **Concedere a ogni client le autorizzazioni per il server di destinazione**: al termine dell'installazione del servizio client nei computer client, è necessario aggiungere manualmente gli account del servizio client al ruolo sysadmin nell'istanza di destinazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="net-framework-security"></a>Sicurezza di .NET Framework  
 Per installare qualsiasi funzionalità di Riesecuzione distribuita, è necessario disporre di autorizzazioni di amministratore. Solo un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che dispone di autorizzazioni sysadmin può aggiungere gli account del servizio client al ruolo del server sysadmin del server di prova. Per alcune considerazioni relative alla sicurezza di Riesecuzione distribuita, vedere [Distributed Replay Security](../../tools/distributed-replay/distributed-replay-security.md).  
  
  

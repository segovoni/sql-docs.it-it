---
title: Regole di installazione | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- SCC
- System Configuration Check, Setup
helpviewer_keywords:
- System Configuration Check page [SQL Server Installation Wizard]
- SQL Server Installation Wizard, System Configuration Check page
- SCC [SQL Server]
ms.assetid: 168c0445-5651-42fc-91f4-d9f27d9e2281
caps.latest.revision: 49
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: df13e2ac5e6caf247f633e7f59ac397b2c5d22c7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37251493"
---
# <a name="install-rules"></a>Regole di installazione
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Il programma di installazione convalida la configurazione del computer prima che venga completata l'operazione di installazione. Durante l'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene eseguita l'analisi del computer in cui verrà installato [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tramite Controllo configurazione sistema. Questo strumento consente di verificare le condizioni che impediscono la corretta operazione di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Prima dell'avvio dell'installazione guidata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], lo strumento recupera le informazioni sullo stato di ciascun elemento. Il risultato viene confrontato con i requisiti, quindi vengono fornite indicazioni per la rimozione di eventuali problemi che impediscono di proseguire.  
  
 Con il controllo della configurazione di sistema viene generato un report con una breve descrizione di ogni regola eseguita, nonché lo stato dell'esecuzione. Il report controllo configurazione sistema si trova nel percorso % programfiles %\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\< aaaammgg_hhmm >\\.  
  
 Prima di eseguire l'operazione di installazione, esaminare i seguenti argomenti:  
  
1.  [Requisiti hardware e software per l'installazione di SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md)  
  
2.  [Funzionalità supportate dalle edizioni di SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
  
3.  [Considerazioni sulla sicurezza per un'installazione di SQL Server](../../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
4.  [Versioni in lingua locale di SQL Server](../../../2014/sql-server/install/local-language-versions-in-sql-server.md)  
  
 Altri riferimenti:  
  
1.  [Aggiornamenti di versione ed edizione supportati](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)  
  
2.  [Operazioni preliminari all'installazione del clustering di failover](../failover-clusters/install/before-installing-failover-clustering.md)  
  
## <a name="additional-rule-topics"></a>Argomenti aggiuntivi relativi alle regole  
 Vedere gli argomenti seguenti per le regole del programma di installazione specifiche di uno scenario:  
  
-   [Regole di installazione](../../../2014/sql-server/install/installation-rules.md)  
  
-   [Le regole di funzionalità &#40;eseguire l'aggiornamento&#41;](../../../2014/sql-server/install/feature-rules-upgrade.md)  
  
-   [Regole di aggiornamento delle edizioni](../../../2014/sql-server/install/edition-upgrade-rules.md)  
  
-   [Regole di disinstallazione](../../../2014/sql-server/install/uninstallation-rules.md)  
  
-   [Regole di preparazione immagine](../../../2014/sql-server/install/prepare-image-rules.md)  
  
-   [Regole di completamento immagine](../../../2014/sql-server/install/complete-image-rules.md)  
  
  

---
title: Installare la replica di SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- components [SQL Server replication]
- command line installations [SQL Server replication]
- installing replication
- replication [SQL Server], installing
- command prompt [SQL Server replication]
ms.assetid: c50ad078-060b-4a8d-ad45-9e31a8d85729
caps.latest.revision: 40
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 70978d835a5c63589de69ad48fbeeef690dfef2c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37278228"
---
# <a name="install-sql-server-replication"></a>Installare la replica di SQL Server
  I componenti della replica possono essere installati mediante l'Installazione guidata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o dal prompt dei comandi. L'installazione della replica può essere eseguita durante l'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]oppure durante la modifica di un'istanza esistente.  
  
 Dopo aver installato i componenti della replica, è necessario configurare il server per poter utilizzare la replica. Per altre informazioni, vedere [Configura distribuzione](../../relational-databases/replication/configure-distribution.md) nella documentazione online di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!IMPORTANT]  
>  Se si installano componenti di replica quando si modifica un'istanza esistente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è necessario arrestare e riavviare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent al termine dell'installazione, per fare in modo che [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent riconosca i sottosistemi dell'agente di replica e sia in grado di chiamare gli agenti di replica dai passaggi di processo.  
  
## <a name="installing-replication-by-using-setup"></a>Installazione della replica mediante l'utilizzo del programma di installazione  
 **Per installare la replica durante l'installazione di una nuova istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**  
  
-   Per installare i componenti della replica, inclusi gli oggetti RMO (Replication Management Objects), selezionare **Replica di SQL Server** nella pagina **Selezione funzionalità** dell'Installazione guidata.  
  
## <a name="installing-replication-from-the-command-prompt"></a>Installazione della replica dal prompt dei comandi  
 **Per installare la replica durante l'installazione di una nuova istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**  
  
-   Visualizzare [installare SQL Server 2014 dal Prompt dei comandi](install-sql-server-from-the-command-prompt.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Installare SQL Server 2014](install-sql-server.md)   
 [Installare SQL Server 2014 dal Prompt dei comandi](install-sql-server-from-the-command-prompt.md)   
 [Funzionalità supportate dalle edizioni di SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
  
  

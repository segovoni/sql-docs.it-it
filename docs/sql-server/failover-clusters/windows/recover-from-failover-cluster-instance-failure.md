---
title: Recuperare da un errore dell'istanza del cluster di failover | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- clusters [SQL Server], recovery from failure
- failover clustering [SQL Server], recovery from failure
- hardware failures [SQL Server]
- recovering failover cluster failures [SQL Server]
ms.assetid: 3d151d0c-e841-4325-8606-c094de37d7d1
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: bfa246842ff120aecb6ce5a58eaf6aad43b9f8b3
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34772107"
---
# <a name="recover-from-failover-cluster-instance-failure"></a>Recuperare da un errore dell'istanza del cluster di failover
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  In questo argomento viene descritta la modalità di recupero dagli errori del cluster tramite lo snap-in Gestione cluster di failover quando si verifica il failover in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Lo snap-in Gestione cluster di failover è l'applicazione di gestione cluster per il servizio Windows Server Failover Clustering (WSFC).  
  
-   [Recuperare da un errore irreversibile](#Scenario1)  
  
-   [Recuperare da un errore software](#Scenario2)  
  
##  <a name="Scenario1"></a> Recuperare da un errore irreversibile  
 Eseguire i passi di seguito riportati per recuperare da un errore irreversibile. Questo errore può essere provocato, ad esempio, dall'errore di un controller del disco o del sistema operativo. In questo caso il problema dipende da un errore hardware nel nodo 1 di un cluster a due nodi.  
  
1.  Dopo l'errore del Nodo 1, l'istanza FCI di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] genera un errore sul Nodo 2.  
  
2.  Rimuovere il Nodo 1 dall'istanza FCI. A tale scopo, aprire lo snap-in Gestione cluster di failover dal Nodo 2, fare clic con il pulsante destro del mouse sul Nodo 1, quindi fare clic su **Sposta azioni**, quindi scegliere **Rimuovi nodo**.  
  
3.  Verificare che il Nodo 1 sia stato rimosso dalla definizione del cluster.  
  
4.  Installare il nuovo componente hardware per sostituire quello danneggiato nel Nodo 1.  
  
5.  Tramite lo snap-in Gestione cluster di failover, aggiungere il Nodo 1 al cluster esistente. Per altre informazioni, vedere [Operazioni preliminari all'installazione del clustering di failover](../../../sql-server/failover-clusters/install/before-installing-failover-clustering.md).  
  
6.  Assicurarsi che gli account amministratore siano gli stessi in tutti i nodi del cluster.  
  
7.  Eseguire il programma di installazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] per aggiungere il Nodo 1 all'istanza FCI. Per altre informazioni, vedere [Aggiungere o rimuovere nodi in un cluster di failover di SQL Server &#40;programma di installazione&#41;](../../../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md).  
  
##  <a name="Scenario2"></a> Recuperare da un errore reversibile  
 Eseguire i passi di seguito riportati per recuperare da un errore reversibile. In questo caso, l'errore dipende dalla mancata disponibilità o dall'interruzione del collegamento del Nodo 1, che tuttavia non è danneggiato. L'errore può essere causato da un errore del sistema operativo, da un errore hardware o da un errore dell'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
1.  Dopo l'errore del Nodo 1, l'istanza FCI genera un errore sul Nodo 2.  
  
2.  Risolvere il problema del Nodo 1.  
  
3.  Accertarsi che tutti i nodi siano online e il servizio WSFC sia funzionante.  
  
4.  Eseguire il failover di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nel nodo recuperato.  
  
  

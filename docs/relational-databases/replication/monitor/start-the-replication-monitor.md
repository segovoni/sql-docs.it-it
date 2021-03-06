---
title: Avviare Monitoraggio replica | Microsoft Docs
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
- Replication Monitor, starting
ms.assetid: e037bd27-cc87-4ee9-9e5f-83f6d717cfa4
caps.latest.revision: 36
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 22cd471b9b1b7c2b779c12967bb1ea1b9163678c
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37351673"
---
# <a name="start-the-replication-monitor"></a>Avvio di Monitoraggio replica
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  È possibile avviare Monitoraggio replica da [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] in qualsiasi istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]oppure dal prompt dei comandi. Dopo l'avvio di Monitoraggio replica, aggiungere uno o più server di pubblicazione da monitorare. Per altre informazioni, vedere [Aggiungere e rimuovere server di pubblicazione da Monitoraggio replica](../../../relational-databases/replication/monitor/add-and-remove-publishers-from-replication-monitor.md).  
  
### <a name="to-start-replication-monitor-from-sql-server-management-studio"></a>Per avviare Monitoraggio replica da SQL Server Management Studio  
  
1.  Connettersi a un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]e quindi espandere il nodo del server.  
  
2.  Fare clic con il pulsante destro del mouse sulla cartella **Replica** o una delle relative sottocartelle e quindi scegliere **Avvia Monitoraggio replica**.  
  
### <a name="to-start-replication-monitor-from-the-command-prompt"></a>Per avviare Monitoraggio replica dal prompt dei comandi  
  
1.  Al prompt dei comandi passare alla directory di installazione degli strumenti. Il percorso predefinito è [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]Tools\Binn\  
  
2.  Eseguire sqlmonitor.exe.  
  
## <a name="see-also"></a>Vedere anche  
 [Monitoraggio della replica](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  

---
title: Proprietà SQL Server Agent (pagina Avanzate) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.ag.agent.advanced.f1
ms.assetid: a4d798ee-4c18-40d4-b6af-63d17503738c
caps.latest.revision: 16
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3825ba87f9012a7dcc33fb8585a2d2c4f83e9d6e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37328841"
---
# <a name="sql-server-agent-properties-advanced-page"></a>Proprietà SQL Server Agent (pagina Avanzate)
  Usare questa pagina per visualizzare e modificare le proprietà avanzate del servizio [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
## <a name="options"></a>Opzioni  
 **Inoltro eventi SQL Server**  
 Le opzioni di questa categoria consentono di attivare e configurare l'inoltro di eventi.  
  
 **Inoltra eventi a un altro server**  
 Gli eventi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent vengono inoltrati a un server diverso.  
  
 **Server**  
 Consente di selezionare il nome del server al quale inoltrare gli eventi.  
  
 **Eventi non gestiti**  
 Solo gli eventi non gestiti vengono inoltrati al server specificato. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent inoltra solo gli eventi ai quali non risponde alcun avviso.  
  
 **Tutti gli eventi**  
 Vengono inoltrati tutti gli eventi. Quando un avviso nell'istanza locale risponde a un evento, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent inoltra l'evento ed elabora l'avviso.  
  
 **Eventi con gravità maggiore o uguale a**  
 Vengono inoltrati solo gli eventi il cui livello di gravità e maggiore o uguale al livello specificato.  
  
 **Condizione di inattività CPU**  
 Le opzioni di questa categoria consentono di definire le condizioni in base alle quali [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent esegue i processi pianificati per l'esecuzione in base alla pianificazione di inattività della CPU.  
  
 **Imposta condizione di inattività CPU**  
 Consente di definire le condizioni in base alle quali [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent considera la CPU come inattiva.  
  
 **L'utilizzo medio della CPU è inferiore al**  
 La percentuale di utilizzo della CPU al di sotto della quale la CPU viene considerata inattiva.  
  
 **per almeno**  
 Periodo di tempo durante il quale l'utilizzo medio della CPU deve essere al di sotto del livello specificato prima che [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent esegua i processi in base alla pianificazione di inattività della CPU.  
  
## <a name="see-also"></a>Vedere anche  
 [Creare e collegare pianificazioni ai processi](create-and-attach-schedules-to-jobs.md)   
 [Gestione di eventi](manage-events.md)  
  
  

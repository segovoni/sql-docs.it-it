---
title: Configurare WMI per mostrare lo stato del server in Strumenti SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- WMI Provider for Server Events, setting permissions
- WMI permissions [SQL Server]
ms.assetid: 7e97197b-ed4d-40d1-9a52-9ab1d92401d7
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f081326d98ed3a7c8a95acb4dd2071a5ec7c8101
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33040168"
---
# <a name="configure-wmi-to-show-server-status-in-sql-server-tools"></a>Configurazione di WMI per mostrare lo stato del server in Strumenti SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
In questo argomento viene descritto come configurare WMI per mostrare lo stato del server negli strumenti di SQL Server in [!INCLUDE[ssCurrent](../includes/sscurrent_md.md)]. Durante la connessione ai server i componenti Server registrati e Esplora oggetti di [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)], nonché Gestione configurazione [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] , utilizzano Strumentazione gestione Windows (WMI) per ottenere lo stato dei servizi [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] (MSSQLSERVER) e [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] Agent (MSSQLSERVER). Per visualizzare lo stato del servizio, l'utente deve disporre dei diritti per accedere in remoto all'oggetto WMI. Per configurare questa autorizzazione, nel server deve essere installato WMI.  
  
## <a name="SSMSProcedure"></a>Per configurare l'autorizzazione WMI  
  
1.  Scegliere **Esegui** dal menu **Start**nel server remoto.  
  
2.  Nella casella **Apri** digitare **wmimgmt.msc**e fare clic su **OK**.  
  
3.  Nel programma **Windows Management Infrastructure** fare clic con il pulsante destro del mouse su **Controllo WMI (Locale)** e scegliere **Proprietà**.  
  
4.  Nella scheda **Sicurezza** della finestra di dialogo **Proprietà - Controllo WMI (Locale)** espandere **Radice**e fare clic su **CIMV2**.  
  
5.  Fare clic sul pulsante **Sicurezza** per aprire la finestra di dialogo **Sicurezza per ROOT\CIMV2** .  
  
6.  Aggiungere un gruppo o un utente alla casella **Nomi utente o gruppo** e selezionarlo.  
  
7.  Nella casella **Autorizzazioni per***<group or user>* selezionare la colonna **Consenti** per l'autorizzazione **Abilita remoto** relativa agli utenti per i quali si vuole rilevare in remoto lo stato del servizio.  
  
## <a name="see-also"></a>Vedere anche  
[Avvio, arresto o sospensione del servizio SQL Server Agent](../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md)  
  

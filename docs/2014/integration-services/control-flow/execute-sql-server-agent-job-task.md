---
title: Attività Esegui processo di SQL Server Agent | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executesqlserveragentjobtask.f1
helpviewer_keywords:
- Execute SQL Server Agent Job task [Integration Services]
- jobs [Integration Services]
- SQL Server Agent [Integration Services]
ms.assetid: 3aa3bc0e-1a1c-452e-81b8-b4e3422ea053
caps.latest.revision: 43
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ead21855d754a9e5b48572e5576b311db5b32983
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37173262"
---
# <a name="execute-sql-server-agent-job-task"></a>Attività Esegui processo di SQL Server Agent
  L'attività Esegui processo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent consente di eseguire processi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent è un servizio di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows per l'esecuzione di processi definiti in un'istanza di SQL Server. È possibile creare processi che eseguono istruzioni Transact-SQL e script ActiveX, attività di manutenzione della replica e di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] oppure pacchetti. È anche possibile configurare un processo per il monitoraggio di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e la generazione di avvisi. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] I processi di Agent vengono generalmente usati per rendere automatiche le attività più ripetitive. Per altre informazioni, vedere [Implementazione di processi](../../ssms/agent/implement-jobs.md).  
  
 Tramite l'attività Esegui processo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, un pacchetto può eseguire attività amministrative correlate ai componenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Un processo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent può ad esempio eseguire una stored procedure di sistema quale **sp_enum_dtspackages** per ottenere l'elenco dei pacchetti di una cartella.  
  
> [!NOTE]  
>  È possibile eseguire automaticamente processi amministrativi locali o multiserver solo se [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent è in esecuzione.  
  
 Questa attività incapsula la procedura di sistema **sp_start_job** e passa il nome del processo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alla procedura come argomento. Per altre informazioni, vedere [sp_start_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql).  
  
## <a name="configuring-the-execute-sql-server-agent-job-task"></a>Configurazione dell'attività Esegui processo di SQL Server Agent  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../../includes/ssis-md.md)] . Questa attività è disponibile nella sezione **Attività di manutenzione** della **casella degli strumenti** di Progettazione [!INCLUDE[ssIS](../../../includes/ssis-md.md)] .  
  
 Per ulteriori informazioni sulle proprietà che è possibile impostare in Progettazione [!INCLUDE[ssIS](../../../includes/ssis-md.md)] , fare clic sull'argomento seguente:  
  
-   [Attività Esegui processo di SQL Server Agent &#40;Piano di manutenzione&#41;](../../relational-databases/maintenance-plans/execute-sql-server-agent-job-task-maintenance-plan.md)  
  
 Per altre informazioni sull'impostazione di queste proprietà in Progettazione [!INCLUDE[ssIS](../../../includes/ssis-md.md)] , fare clic sull'argomento seguente:  
  
-   [Impostare le proprietà di un'attività o di un contenitore](../set-the-properties-of-a-task-or-container.md)  
  
  

---
title: Creare processi | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], creating
- SQL Server Agent jobs, creating
ms.assetid: 465fb7fc-7622-4252-a178-ea51691c935b
caps.latest.revision: 3
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: a3176bc790660d9a8583962880288e26b8051e79
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33040748"
---
# <a name="create-jobs"></a>Crea processi
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In [Istanza gestita di database SQL di Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) sono attualmente supportate la maggior parte delle funzionalità di SQL Server Agent, ma non tutte. Per informazioni dettagliate, vedere [Differenze T-SQL tra Istanza gestita del database SQL di Azure e SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Un processo include una serie di operazioni specificate eseguite in sequenza da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent. Tramite un processo è possibile eseguire un'ampia gamma di attività, inclusa l'esecuzione di script [!INCLUDE[tsql](../../includes/tsql_md.md)] , applicazioni da riga di comando, script Microsoft ActiveX, pacchetti Integration Services, comandi e query di Analysis Services o attività di replica. I processi possono eseguire attività ripetitive o pianificabili e inviare agli utenti notifiche automatiche sullo stato del processo tramite la generazione di avvisi, semplificando significativamente l'amministrazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .  
  
Per creare un processo, è necessario che l'utente sia membro di uno dei ruoli predefiniti del database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent o del ruolo predefinito del server **sysadmin** . Un processo può essere modificato solo dal proprietario o dai membri del ruolo **sysadmin** . I membri del ruolo **sysadmin** possono assegnare la proprietà di un processo ad altri utenti ed eseguire qualsiasi processo, indipendentemente dal proprietario. Per altre informazioni sui ruoli predefiniti del database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent, vedere [Ruoli di database predefiniti di SQL Server Agent](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
È possibile creare processi da eseguire nell'istanza locale di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] oppure in più istanze all'interno di un'organizzazione. Per eseguire i processi in più server, è necessario impostare almeno un server master e uno o più server di destinazione. Per altre informazioni sui server master e di destinazione, vedere [Amministrazione automatizzata in un'organizzazione](../../ssms/agent/automated-administration-across-an-enterprise.md)  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] In Agent i dati relativi al processo e ai passaggi di processo vengono registrati nella cronologia processo.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|||  
|-|-|  
|**Descrizione**|**Argomento**|  
|Viene illustrato come creare un processo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent.|[Creazione di un processo](../../ssms/agent/create-a-job.md)|  
|Viene descritto come riassegnare la proprietà dei processi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent a un altro utente.|[Give Others Ownership of a Job](../../ssms/agent/give-others-ownership-of-a-job.md)|  
|Viene descritto come impostare il log di cronologia processi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent.|[Set Up the Job History Log](../../ssms/agent/set-up-the-job-history-log.md)|  
  
## <a name="see-also"></a>Vedere anche  
[Gestire passaggi di processo](../../ssms/agent/manage-job-steps.md)  
[Amministrazione automatizzata in un'organizzazione](../../ssms/agent/automated-administration-across-an-enterprise.md)  
[Creazione e collegamento di pianificazioni ai processi](../../ssms/agent/create-and-attach-schedules-to-jobs.md)  
[Esecuzione di processi](../../ssms/agent/run-jobs.md)  
[Visualizzare o modificare processi](../../ssms/agent/view-or-modify-jobs.md)  
  

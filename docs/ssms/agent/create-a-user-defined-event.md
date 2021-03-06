---
title: Creare un evento definito dall'utente | Microsoft Docs
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
- SQL Server Agent alerts, user-defined events
- user-defined events [SQL Server]
- multiple language support [SQL Server], alerts
- languages [SQL Server], alerts
- severity levels [SQL Server]
- global considerations [SQL Server], alerts
- events [SQL Server], user-defined
- SQL Server Agent alerts, multiple-language environments
- alerts [SQL Server], user-defined events
- alerts [SQL Server], multiple-language environments
- custom events [SQL Server Agent]
- international considerations [SQL Server], alerts
ms.assetid: 03d71a35-97fa-4bba-aa9a-23ac9c9cf879
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 5f1783fd0a0326ca2b74b3199033545e9b5d96d8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33044098"
---
# <a name="create-a-user-defined-event"></a>Creazione di un evento definito dall'utente
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In [Istanza gestita di database SQL di Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) sono attualmente supportate la maggior parte delle funzionalità di SQL Server Agent, ma non tutte. Per informazioni dettagliate, vedere [Differenze T-SQL tra Istanza gestita del database SQL di Azure e SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Per monitorare eventi diversi da quelli predefiniti da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], è possibile creare eventi definiti dall'utente. È inoltre possibile assegnare un livello di gravità a ogni evento definito dall'utente.  
  
> [!NOTE]  
> Quando si usa [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)], selezionare l'opzione **Scrivi nel registro eventi delle applicazioni di Windows** per ogni messaggio di evento definito dall'utente, in modo da assicurarsi che i messaggi vengano registrati. Per impostazione predefinita, i messaggi definiti dall'utente con livello di gravità minore di 19 non vengono inviati al registro delle applicazioni di [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows quando si verificano. Tali messaggi non generano quindi avvisi di SQL Server Agent.  
  
È necessario che agli eventi definiti dall'utente sia associato un numero di messaggio univoco. Tali numeri devono essere maggiori di 50.000. È possibile definire messaggi per l'evento in più lingue. Prima di potere aggiungere messaggi in altre lingue, è tuttavia necessario che sia disponibile un messaggio **En-US** .  
  
Se si amministra un ambiente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] multilingue, creare messaggi definiti dall'utente in ciascuna lingua supportata. Ad esempio se si crea un nuovo messaggio dell'evento che verrà utilizzato sia in un server con sistema operativo in inglese che in un server con sistema operativo in tedesco, utilizzare lo stesso numero di messaggio e lo stesso livello di gravità per entrambi, ma assegnare una lingua diversa a ognuno di essi.  
  
Nelle attività riportate di seguito sono disponibili informazioni su come creare eventi definiti dall'utente e avvisi in risposta a tali eventi.  
  
**Per creare un avviso in base a un numero di messaggio**  
  
-   [SQL Server Management Studio](../../ssms/agent/create-an-alert-using-an-error-number.md)  
  
-   [Transact-SQL](http://msdn.microsoft.com/en-us/d9b41853-e22d-4813-a79f-57efb4511f09)  
  
**Per creare un avviso in base ai livelli di gravità**  
  
-   [SQL Server Management Studio](../../ssms/agent/create-an-alert-using-severity-level.md)  
  
-   [Transact-SQL](http://msdn.microsoft.com/en-us/d9b41853-e22d-4813-a79f-57efb4511f09)  
  
**Per definire la risposta a un avviso**  
  
-   [SQL Server Management Studio](../../ssms/agent/define-the-response-to-an-alert-sql-server-management-studio.md)  
  
-   [Transact-SQL](http://msdn.microsoft.com/en-us/0525e0a2-ed0b-4e69-8a4c-a9e3e3622fbd)  
  
**Per creare un messaggio di errore relativo a un evento definito dall'utente**  
  
-   [Transact-SQL](http://msdn.microsoft.com/en-us/54746d30-f944-40e5-a707-f2d9be0fb9eb)  
  
**Per modificare un messaggio di errore relativo a un evento definito dall'utente**  
  
-   [Transact-SQL](http://msdn.microsoft.com/en-us/1b28f280-8ef9-48e9-bd99-ec14d79abaca)  
  
**Per eliminare un messaggio di errore relativo a un evento definito dall'utente**  
  
-   [Transact-SQL](http://msdn.microsoft.com/en-us/17287a15-cdde-43d1-bb18-9f920bc15db8)  
  
**Per disabilitare o riattivare un avviso**  
  
-   [SQL Server Management Studio](../../ssms/agent/disable-or-reactivate-an-alert.md)  
  
-   [Transact-SQL](http://msdn.microsoft.com/en-us/4bbaeaab-8aca-4c9e-abc1-82ce73090bd3)  
  
## <a name="see-also"></a>Vedere anche  
[sp_update_alert (Transact-SQL)](http://msdn.microsoft.com/en-us/4bbaeaab-8aca-4c9e-abc1-82ce73090bd3)  
  

---
title: dbo.sysjobs (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sysjobs
- sysjobs_TSQL
- dbo.sysjobs
- dbo.sysjobs_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysjobs system table
ms.assetid: e244a6a5-54c2-47a6-8039-dd1852b0ae59
caps.latest.revision: 17
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8c5988e84db07845a42c689f58cb5ddfb45cdf8b
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33259641"
---
# <a name="dbosysjobs-transact-sql"></a>dbo.sysjobs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Archivia le informazioni su tutti i processi pianificati da eseguire tramite [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Questa tabella è archiviata nel **msdb** database.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**job_id**|**uniqueidentifier**|ID univoco del processo.|  
|**originating_server_id**|**int**|ID del server di provenienza del processo.|  
|**name**|**sysname**|Nome del processo|  
|**enabled**|**tinyint**|Indica se il processo è abilitato per l'esecuzione.|  
|**description**|**nvarchar(512)**|Descrizione del processo.|  
|**start_step_id**|**int**|ID del passaggio del processo da cui deve iniziare l'esecuzione.|  
|**category_id**|**int**|ID della categoria del processo.|  
|**owner_sid**|**varbinary(85)**|ID di sicurezza (SID) del proprietario del processo.|  
|**notify_level_eventlog**|**int**|**Maschera di bit** che indica in quali circostanze un evento di notifica deve essere registrato nel registro applicazioni di Microsoft Windows:<br /><br /> **0** non = mai<br /><br /> **1** = in caso di esito positivo processo<br /><br /> **2** = in caso di esito negativo del processo<br /><br /> **3** = ogni volta che il completamento del processo (indipendentemente dal risultato del processo)|  
|**notify_level_email**|**int**|Maschera di bit che indica le condizioni per l'invio di un messaggio di posta elettronica di notifica al termine di un processo:<br /><br /> **0** non = mai<br /><br /> **1** = in caso di esito positivo processo<br /><br /> **2** = in caso di esito negativo del processo<br /><br /> **3** = ogni volta che il completamento del processo (indipendentemente dal risultato del processo)|  
|**notify_level_netsend**|**int**|Maschera di bit che indica le condizioni per l'invio di un messaggio in rete al termine di un processo:<br /><br /> **0** non = mai<br /><br /> **1** = in caso di esito positivo processo<br /><br /> **2** = in caso di esito negativo del processo<br /><br /> **3** = ogni volta che il completamento del processo (indipendentemente dal risultato del processo)|  
|**notify_level_page**|**int**|Maschera di bit che indica le condizioni per l'invio di un messaggio su cercapersone al termine di un processo:<br /><br /> **0** non = mai<br /><br /> **1** = in caso di esito positivo processo<br /><br /> **2** = in caso di esito negativo del processo<br /><br /> **3** = ogni volta che il completamento del processo (indipendentemente dal risultato del processo)|  
|**notify_email_operator_id**|**int**|Nome di posta elettronica dell'operatore a cui inviare la notifica.|  
|**notify_netsend_operator_id**|**int**|ID del computer o dell'utente utilizzato quando si invia un messaggio in rete.|  
|**notify_page_operator_id**|**int**|ID del computer o dell'utente utilizzato quando si invia un messaggio su cercapersone.|  
|**delete_level**|**int**|**Maschera di bit** che indica in quali circostanze il processo di eliminazione di un processo viene completato:<br /><br /> **0** non = mai<br /><br /> **1** = in caso di esito positivo processo<br /><br /> **2** = in caso di esito negativo del processo<br /><br /> **3** = ogni volta che il completamento del processo (indipendentemente dal risultato del processo)|  
|**date_created**|**datetime**|Data di creazione del processo.|  
|**date_modified**|**datetime**|Data dell'ultima modifica del processo.|  
|**version_number**|**int**|Versione del processo.|  
  
  

---
title: dbo.syssubsystems (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dbo.syssubsystems
- syssubsystems
- syssubsystems_TSQL
- dbo.syssubsystems_TSQL
dev_langs: TSQL
helpviewer_keywords: syssubsystems system table
ms.assetid: 114b3d55-1ad6-4777-b868-8ef0c86ba596
caps.latest.revision: "14"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ac5beab5a0c45bc14155d241af7884274a4606ba
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="dbosyssubsystems-transact-sql"></a>dbo.syssubsystems (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene informazioni su tutti i sottosistemi proxy di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent disponibili. Il **syssubsystems** tabella è archiviata nel **msdb** database.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**subsystem_id**|**int**|ID del sottosistema.|  
|**sottosistema**|**nvarchar (40)**|Nome del sottosistema.|  
|**description_id**|**int**|ID della riga nel messaggio il **Sys. Messages** vista del catalogo che contiene la descrizione del sottosistema.|  
|**subsystem_dll**|**nvarchar(255)**|Posizione del file dll del sottosistema.|  
|**agent_exe**|**nvarchar(255)**|Percorso completo del file eseguibile che utilizza il sottosistema.|  
|**start_entry_point**|**nvarchar (30)**|Funzione richiamata quando il sottosistema viene inizializzato.|  
|**event_entry_point**|**nvarchar (30)**|Funzione richiamata quando viene eseguito un passaggio del sottosistema.|  
|**stop_entry_point**|**nvarchar (30)**|Funzione richiamata quando l'esecuzione di un sottosistema viene interrotta.|  
|**max_worker_threads**|**int**|Numero massimo di passaggi simultanei per un sottosistema specifico.|  
  
## <a name="remarks"></a>Osservazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server può accedere a questa tabella.  
  
## <a name="see-also"></a>Vedere anche  
 [dbo.sysproxysubsystem &#40; Transact-SQL &#41;](../../relational-databases/system-tables/dbo-sysproxysubsystem-transact-sql.md)   
 [dbo.sysproxies &#40; Transact-SQL &#41;](../../relational-databases/system-tables/dbo-sysproxies-transact-sql.md)   
 [Sys. Messages &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md)  
  
  
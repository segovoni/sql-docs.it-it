---
title: MSagent_profiles (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSagent_profiles
- MSagent_profiles_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSagent_profiles system table
ms.assetid: 4ab1b2ae-b6d9-42b7-9b31-98547dbb7f99
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e3b246b0c174838529dd5e0c6c38bd633c0a90b8
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39101379"
---
# <a name="msagentprofiles-transact-sql"></a>MSagent_profiles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **MSagent_profiles** tabella contiene una riga per ogni profilo di agente di replica definito. Questa tabella è archiviata nel **msdb** database.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**profile_id**|**int**|ID del profilo.|  
|**profile_name**|**sysname**|Nome di profilo univoco per il tipo di agente.|  
|**agent_type**|**int**|Tipo di agente:<br /><br /> **1** = agente snapshot<br /><br /> **2** = agente di lettura log<br /><br /> **3** = agente di distribuzione<br /><br /> **4** = agente di merge<br /><br /> **9** = agente di lettura coda|  
|**type**|**int**|Tipo di profilo:<br /><br /> **0** = sistema**1** = personalizzato|  
|**description**|**nvarchar(3000)**|Descrizione del profilo.|  
|**def_profile**|**bit**|Indica se il profilo corrisponde al profilo predefinito per il tipo di agente specificato.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  

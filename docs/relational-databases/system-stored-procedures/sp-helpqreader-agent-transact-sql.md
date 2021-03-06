---
title: sp_helpqreader_agent (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_helpqreader_agent_TSQL
- sp_helpqreader_agent
helpviewer_keywords:
- sp_helpqreader_agent
ms.assetid: 8e74e1aa-e95b-4183-8017-bf123439b08d
caps.latest.revision: 21
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: be49f8a6303096487ef2c36593280fcc72e38a91
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32995948"
---
# <a name="sphelpqreaderagent-transact-sql"></a>sp_helpqreader_agent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce le proprietà dell'agente di lettura coda. Questa stored procedure viene eseguita nel database di distribuzione del server di distribuzione oppure in qualsiasi database del server di pubblicazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_helpqreader_agent [ [ @frompublisher = ] frompublisher ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@frompublisher=** ] *frompublisher*  
 Specifica se la stored procedure viene chiamata nel server di pubblicazione o nel server di distribuzione. *frompublisher* è di tipo bit e il valore predefinito pari a 0. **1** significa che la stored procedure viene chiamata dal server di pubblicazione, e **0** significa che la stored procedure viene chiamata dal server di distribuzione.  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**id**|**int**|ID dell'agente.|  
|**name**|**Nvarchar (100)**|Nome dell'agente.|  
|**job_id**|**uniqueidentifier**|ID univoco del processo dell'agente.|  
|**job_login**|**nvarchar(512)**|È l'account di Windows con cui viene eseguito l'agente di distribuzione, viene restituito nel formato *dominio*\\*username*.|  
|**job_password**|**sysname**|Per motivi di sicurezza, un valore di **\* \* \* \* \* \* \* \* \* \*** è sempre restituito.|  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_helpqreader_agent** viene utilizzata nella replica transazionale.  
  
## <a name="permissions"></a>Autorizzazioni  
 Quando il valore di *frompublisher* è **1**, solo i membri del **sysadmin** al server di pubblicazione o i membri del ruolo predefinito del server di **db_owner**ruolo predefinito del database nel database di pubblicazione possono eseguire **sp_helpqreader_agent**. In caso contrario, solo i membri del **sysadmin** al server di distribuzione o i membri del ruolo predefinito del server di **db_owner** ruolo predefinito del database nel database di distribuzione possono eseguire **sp_helpqreader_ agente**.  
  
## <a name="see-also"></a>Vedere anche  
 [Abilitare le sottoscrizioni aggiornabili per le pubblicazioni transazionali](../../relational-databases/replication/publish/enable-updating-subscriptions-for-transactional-publications.md)  
  
  

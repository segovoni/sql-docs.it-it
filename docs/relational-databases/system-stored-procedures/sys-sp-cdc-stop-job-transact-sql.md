---
title: sp_cdc_stop_job (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.sp_cdc_stop_job_TSQL
- sys.sp_cdc_stop_job
- sp_cdc_stop_job_TSQL
- sp_cdc_stop_job
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cdc_stop_job
ms.assetid: 421fc21c-c7a4-407c-8b31-359273b68c63
caps.latest.revision: 18
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 8f9ac01b53e3d7823fb00e68d49f9a4905ddac96
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33255734"
---
# <a name="sysspcdcstopjob-transact-sql"></a>sys.sp_cdc_stop_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Arresta un processo di pulizia o di acquisizione di Change Data Capture per il database corrente.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sys.sp_cdc_stop_job [ [ @job_type = ] 'job_type' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [[  **@job_type=** ] **' * * * job_type*']  
 Tipo di processo da aggiungere. *job_type* viene **nvarchar(20)** con valore predefinito è **acquisire**. Gli input validi sono **acquisire** e **pulizia**.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="remarks"></a>Osservazioni  
 sys.sp_cdc_stop_job può essere utilizzato da un amministratore per arrestare in modo esplicito il processo di acquisizione o di pulizia.  
  
## <a name="permissions"></a>Autorizzazioni  
 Richiede l'appartenenza al ruolo predefinito del database db_owner.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene arrestato il processo di pulizia per il database `AdventureWorks2012`.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sys.sp_cdc_stop_job @job_type = N'capture';  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [dbo. cdc_jobs &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md)   
 [Sys. sp_cdc_start_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-start-job-transact-sql.md)  
  
  

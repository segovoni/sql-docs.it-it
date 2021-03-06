---
title: sys.sp_xtp_control_query_exec_stats (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 10/13/2015
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.sp_xtp_control_query_exec_stats_TSQL
- sys.sp_xtp_control_query_exec_stats
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_xtp_control_query_exec_stats
ms.assetid: 4838125d-ad1e-479e-b7d2-42655e8f4f02
caps.latest.revision: 16
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 23301458684008945c057aa1d7f9f97380a9cb68
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38055849"
---
# <a name="sysspxtpcontrolqueryexecstats-transact-sql"></a>sys.sp_xtp_control_query_exec_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  Abilita la raccolta per statistiche di query di tutte le stored procedure compilate in modo nativo per l'istanza o stored procedure specifiche compilate in modo nativo.  
  
 Le prestazioni diminuiscono quando si abilita la raccolta delle statistiche. Se è necessario risolvere il problema di una o poche stored procedure compilate in modo nativo, è possibile abilitare la raccolta delle statistiche solo per tali stored procedure compilate in modo nativo.  
  
 Per abilitare la raccolta delle statistiche a livello di routine per tutte le stored procedure compilate in modo nativo, vedere [Sys. sp_xtp_control_proc_exec_stats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-xtp-control-proc-exec-stats-transact-sql.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
sp_xtp_control_query_exec_stats [ [ @new_collection_value = ] collection_value ],  
[ [ @database_id = ] database_id   
[ , [ @xtp_object_id = ] procedure_id ] ,   
[ @old_collection_value] ]  
```  
  
## <a name="arguments"></a>Argomenti  
 @new_collection_value = *valore*  
 Determina se la raccolta delle statistiche a livello di stored procedure è attivata (1) o disattivata (0).  
  
 @new_collection_value è impostato su zero quando [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene avviato.  
  
 @database_id = = *database_id*, @xtp_object_id = *procedure_id*  
 L'ID database e l'ID oggetto per la stored procedure compilata in modo nativo. Se la raccolta delle statistiche è abilitata per l'istanza di ([Sys. sp_xtp_control_proc_exec_stats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-xtp-control-proc-exec-stats-transact-sql.md)), le statistiche per una stored procedure compilata in modo nativo vengono raccolte. La disabilitazione della raccolta delle statistiche dell'istanza non disabilita la raccolta delle statistiche delle singole stored procedure compilate in modo nativo.  
  
 Uso [Sys. Databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md), [Procedures &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-procedures-transact-sql.md), [DB_ID &#40;Transact-SQL&#41;](../../t-sql/functions/db-id-transact-sql.md), oppure [OBJECT_ID &#40;Transact-SQL&#41; ](../../t-sql/functions/object-id-transact-sql.md) per ottenere gli ID per un database e la stored procedure.  
  
 @old_collection_value = *valore*  
 Restituisce lo stato corrente.  
  
## <a name="return-code"></a>Codice restituito  
 0 per l'esito positivo. Diverso da zero per l'esito negativo.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza al ruolo predefinito sysadmin.  
  
## <a name="code-sample"></a>Codice di esempio  
 Il seguente esempio di codice indica come abilitare la raccolta per statistiche di tutte le stored procedure compilate in modo nativo per l'istanza e per una stored procedure specifica compilata in modo nativo.  
  
```sql   
DECLARE @c bit  
  
EXEC [sys].[sp_xtp_control_query_exec_stats] @new_collection_value = 1;  
  
EXEC sp_xtp_control_query_exec_stats @old_collection_value=@c output;  
SELECT @c AS 'collection status';  
  
EXEC [sys].[sp_xtp_control_query_exec_stats] @new_collection_value = 1,   
@database_id = 5, @xtp_object_id = 341576255;  
  
EXEC sp_xtp_control_query_exec_stats @database_id = 5,   
@xtp_object_id = 341576255, @old_collection_value=@c output;  
  
SELECT @c AS 'collection status';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [OLTP in memoria &#40;ottimizzazione per la memoria&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  

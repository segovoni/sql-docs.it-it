---
title: sp_add_log_shipping_alert_job (Transact-SQL) | Microsoft Docs
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
- sp_add_log_shipping_alert_job_TSQL
- sp_add_log_shipping_alert_job
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_log_shipping_alert_job
ms.assetid: dd95d96e-8963-4aa9-bdcc-3e4b1bc002d3
caps.latest.revision: 21
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: be9abd34c98c4a76aca48e95bc3ce30c0cc0ffcd
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33237082"
---
# <a name="spaddlogshippingalertjob-transact-sql"></a>sp_add_log_shipping_alert_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Questa stored procedure verifica se è stato creato un processo di gestione degli avvisi nel server corrente. Se non esiste un processo di avviso, questa stored procedure crea il processo di avviso e aggiunge l'ID di processo per il **log_shipping_monitor_alert** tabella. Il processo di gestione degli avvisi è abilitato per impostazione predefinita e viene eseguito in base a una frequenza pianificata di una volta ogni due minuti.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_add_log_shipping_alert_job  
[, [ @alert_job_id = ] alert_job_id OUTPUT ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@alert_job_id =** ] *alert_job_id* OUTPUT  
 Il [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ID processo dell'agente del log shipping processo Gestione avvisi.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="remarks"></a>Osservazioni  
 **sp_add_log_shipping_alert_job** deve essere eseguita la **master** database nel server di monitoraggio.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server possono eseguire questa procedura.  
  
## <a name="examples"></a>Esempi  
 In questo esempio viene illustrata l'esecuzione di **sp_add_log_shipping_alert_job** per creare un ID di processo di avviso.  
  
```  
USE master  
GO  
EXEC sp_add_log_shipping_alert_job;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sul Log Shipping & #40; SQL Server & #41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

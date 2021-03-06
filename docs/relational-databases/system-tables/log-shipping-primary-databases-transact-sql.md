---
title: log_shipping_primary_databases (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- log_shipping_primary_databases
- log_shipping_primary_databases_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- log_shipping_primary_databases system table
ms.assetid: 56888756-a798-42be-9b5e-0f9aa05a2cc6
caps.latest.revision: 30
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 233f883e4c714fb7c8eead62e885dabfb5f0167c
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33262455"
---
# <a name="logshippingprimarydatabases-transact-sql"></a>log_shipping_primary_databases (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Archivia un record per il database primario in una configurazione per il log shipping. Questa tabella è archiviata nel **msdb** database.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**primary_id**|**uniqueidentifier**|ID del database primario nella configurazione per il log shipping.|  
|**primary_database**|**sysname**|Nome del database primario nella configurazione di log shipping.|  
|**backup_directory**|**nvarchar(500)**|Directory in cui vengono archiviati i file di backup del log delle transazioni dal server primario.|  
|**backup_share**|**nvarchar(500)**|Percorso di rete o UNC della directory di backup.|  
|**backup_retention_period**|**int**|Intervallo di tempo, espresso in minuti, di conservazione del file di backup dei log nella directory di backup trascorso il quale il file viene eliminato.|  
|**backup_job_id**|**uniqueidentifier**|Il [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ID processo dell'agente associato il processo di backup nel server primario.|  
|**monitor_server**|**sysname**|Il nome dell'istanza del [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] viene utilizzata come server di monitoraggio nella configurazione di log shipping.|  
|**monitor_server_security_mode**|**bit**|Modalità di sicurezza utilizzata per connettersi al server di monitoraggio.<br /><br /> 1 = Autenticazione di Windows.<br /><br /> 0 = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l'autenticazione.|  
|**last_backup_file**|**nvarchar(500)**|Percorso assoluto del backup del log delle transazioni più recente.|  
|**last_backup_date**|**datetime**|Data e ora dell'ultima operazione di backup dei log.|  
|**user_specified_monitor**|**bit**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]<br /><br /> **sp_help_log_shipping_primary_database** e **sp_help_log_shipping_secondary_primary** consente di controllare la visualizzazione delle impostazioni di monitoraggio in questa colonna [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].<br /><br /> 0 = richiamando una di queste due stored procedure, l'utente non ha specificato un valore esplicito per il **@monitor_server** parametro.<br /><br /> 1 = È stato specificato un valore esplicito.|  
|**backup_compression**|**tinyint**|Indica se la configurazione per il log shipping esegue l'override del comportamento della compressione dei backup a livello del server.<br /><br /> 0 = disabilitati. I backup del log non vengono mai compressi, indipendentemente dalle impostazioni di compressione dei backup configurate dal server.<br /><br /> 1 = abilitati. I backup del log vengono sempre compressi, indipendentemente dalle impostazioni di compressione dei backup configurate dal server.<br /><br /> 2 = viene utilizzata la configurazione del server per il [consente di visualizzare o configurare l'opzione di configurazione del Server di backup compression default](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md) opzione di configurazione di server. Si tratta del valore predefinito.<br /><br /> La compressione dei backup è supportata solo in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise Edition.|  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sul Log Shipping & #40; SQL Server & #41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [sp_add_log_shipping_primary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-log-shipping-primary-database-transact-sql.md)   
 [sp_delete_log_shipping_primary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-primary-database-transact-sql.md)   
 [sp_help_log_shipping_primary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-log-shipping-primary-database-transact-sql.md)   
 [Tabelle di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  

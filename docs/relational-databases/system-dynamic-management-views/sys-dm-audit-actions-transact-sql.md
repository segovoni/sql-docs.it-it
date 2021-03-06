---
title: sys.dm_audit_actions (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_audit_actions_TSQL
- sys.dm_audit_actions
- dm_audit_actions_TSQL
- dm_audit_actions
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_audit_actions dynamic management view
ms.assetid: b987c2b9-998a-4a5f-a82d-280dc6963cbe
caps.latest.revision: 19
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 864072a00f2db088b03ce280bf0ad137627b6a7c
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "37987273"
---
# <a name="sysdmauditactions-transact-sql"></a>sys.dm_audit_actions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-xxx-md.md)]

  Restituisce una riga per ogni azione di controllo che può essere segnalata nel log di controllo e per ogni gruppo di azioni di controllo che possono essere configurate come parte di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Audit. Per altre informazioni sulle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Audit, vedere [SQL Server Audit &#40;motore di Database&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md).  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**action_id**|**varchar(4)**|ID dell'azione di controllo. Correlato per il **action_id** valore scritto in ogni record di controllo. Ammette i valori Null. Per i gruppi di controllo, il valore è Null.|  
|**action_in_log**|**bit**|Indica se un'azione può essere scritta in un log di controllo. Sono disponibili i valori seguenti:<br /><br /> 1 = Sì<br /><br /> 0 = No|  
|**name**|**sysname**|Nome dell'azione di controllo o del gruppo di azioni. Non ammette i valori Null.|  
|**class_desc**|**nvarchar(120)**|Nome della classe dell'oggetto al quale si applica l'azione di controllo. Tale oggetto può appartenere all'ambito del server, del database o dello schema, ma non un oggetto dello schema. Non ammette i valori Null.|  
|**parent_class_desc**|**nvarchar(120)**|Nome della classe padre per l'oggetto descritto da class_desc. Se class_desc è un oggetto server, il valore è Null.|  
|**covering_parent_action_name**|**nvarchar(120)**|Nome dell'azione di controllo o del gruppo di controllo che contiene l'azione di controllo descritta in questa riga. Viene utilizzato per creare una gerarchia di azioni e azioni di copertura. Ammette i valori Null.|  
|**configuration_level**|**nvarchar(10)**|Indica che l'azione o il gruppo di azioni specificato in questa riga è configurabile a livello di gruppo o di azione. Se l'azione non è configurabile, il valore è Null.|  
|**containing_group_name**|**nvarchar(120)**|Nome del gruppo di controllo contenente l'azione specificata. Se il valore in name è un gruppo, questo nome è Null.|  
  
## <a name="permissions"></a>Autorizzazioni  
 Le entità devono disporre **seleziona** l'autorizzazione. Per impostazione predefinita, tale autorizzazione è concessa al ruolo public.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)](Indici per tabelle con ottimizzazione per la memoria). Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE SERVER AUDIT &#40;Transact-SQL&#41;](../../t-sql/statements/create-server-audit-transact-sql.md)   
 [ALTER SERVER AUDIT &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-audit-transact-sql.md)   
 [DROP SERVER AUDIT &#40;Transact-SQL&#41;](../../t-sql/statements/drop-server-audit-transact-sql.md)   
 [CREATE SERVER AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../../t-sql/statements/create-server-audit-specification-transact-sql.md)   
 [ALTER SERVER AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-audit-specification-transact-sql.md)   
 [DROP SERVER AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../../t-sql/statements/drop-server-audit-specification-transact-sql.md)   
 [CREATE DATABASE AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../../t-sql/statements/create-database-audit-specification-transact-sql.md)   
 [ALTER DATABASE AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-audit-specification-transact-sql.md)   
 [DROP DATABASE AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-audit-specification-transact-sql.md)   
 [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [sys.fn_get_audit_file &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md)   
 [sys.server_audits &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-audits-transact-sql.md)   
 [sys.server_file_audits &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-file-audits-transact-sql.md)   
 [sys.server_audit_specifications &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-audit-specifications-transact-sql.md)   
 [sys.server_audit_specification_details &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-audit-specification-details-transact-sql.md)   
 [sys.database_audit_specifications &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql.md)   
 [sys.database_audit_specification_details &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-audit-specification-details-transact-sql.md)   
 [sys.dm_server_audit_status &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql.md)   
 [sys.dm_audit_class_type_map &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-class-type-map-transact-sql.md)   
 [Creazione di un controllo del server e di una specifica del controllo del server](../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md)  
  
  

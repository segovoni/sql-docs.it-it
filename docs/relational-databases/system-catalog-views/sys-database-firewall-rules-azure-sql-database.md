---
title: Sys. database_firewall_rules (Database SQL di Azure) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.component: system-catalog-views
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.database_firewall_rules_TSQL
- database_firewall_rules_TSQL
- sys.database_firewall_rules
- database_firewall_rules
dev_langs:
- TSQL
helpviewer_keywords:
- database_firewall_rules
- sys.database_firewall_rules
ms.assetid: 2e821593-3b9f-43d6-a99b-1ceffe177faf
caps.latest.revision: 10
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: ea5b9d5cb50740e349aa6d3cf58bd20f620a8ab6
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38038329"
---
# <a name="sysdatabasefirewallrules-azure-sql-database"></a>sys.database_firewall_rules (Database di SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Restituisce informazioni sulle impostazioni del firewall a livello di database associati con il [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. Le impostazioni del firewall a livello di database sono particolarmente utili quando si usano utenti del database indipendente. Per altre informazioni, vedere [Utenti di database indipendente: rendere portabile un database](../../relational-databases/security/contained-database-users-making-your-database-portable.md).  
  
 La vista `sys.database_firewall_rules` contiene le colonne seguenti:  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|id|**INTEGER**|Identificatore dell'impostazione del firewall a livello di database.|  
|NAME|**NVARCHAR (128)**|Il nome scelto per descrivere e distinguere l'impostazione del firewall a livello di database.|  
|start_ip_address|**VARCHAR (50)**|L'indirizzo IP più basso nell'intervallo dell'impostazione del firewall a livello di database. Gli indirizzi IP uguali o maggiori di questo possono tentare la connessione all'istanza del [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. L'indirizzo IP più basso possibile è `0.0.0.0`.|  
|end_ip_address|**VARCHAR (50)**|L'indirizzo IP più alto nell'intervallo dell'impostazione del firewall. Gli indirizzi IP uguali o minori di questo possono tentare la connessione all'istanza del [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. L'indirizzo IP più alto possibile è `255.255.255.255`.<br /><br /> Nota: Tentativi di connessione di Azure di Windows sono consentiti quando sia questo campo e il **start_ip_address** campo equals `0.0.0.0`.|  
|create_date|**DATA/ORA**|Data e ora UTC in cui è stata creata l'impostazione del firewall a livello di database.|  
|modify_date|**DATA/ORA**|Data e ora UTC in cui è stata modificata per l'ultima volta l'impostazione del firewall a livello di database.|  
  
## <a name="remarks"></a>Note  
 Per rimuovere una regola del firewall del database, usare [sp_delete_database_firewall_rule &#40;Database SQL di Azure&#41;](../../relational-databases/system-stored-procedures/sp-delete-database-firewall-rule-azure-sql-database.md). Per impostare una regola del firewall per tutti [!INCLUDE[ssSDS](../../includes/sssds-md.md)], vedere [sp_set_firewall_rule &#40;Database SQL di Azure&#41;](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md). Per restituire informazioni sui database esistente di regole del firewall, eseguire una query [Sys. database_firewall_rules (Database SQL di Azure)](../../relational-databases/system-catalog-views/sys-database-firewall-rules-azure-sql-database.md).  
  
## <a name="permissions"></a>Autorizzazioni  
 Questa vista è disponibile nel **master** database e in ogni database utente. L'accesso di sola lettura a questa vista è disponibile per tutti gli utenti che dispongono dell'autorizzazione per connettersi al database.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_set_firewall_rule &#40;Database SQL di Azure&#41;](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)   
 [Sys. database_firewall_rules (Database SQL di Azure)](../../relational-databases/system-catalog-views/sys-database-firewall-rules-azure-sql-database.md)   
 [sp_delete_database_firewall_rule &#40;Database SQL di Azure&#41;](../../relational-databases/system-stored-procedures/sp-delete-database-firewall-rule-azure-sql-database.md)   
 [Configurare un Firewall di Windows per l'accesso al motore di Database](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)   
 [Configurare un Firewall per l'accesso FILESTREAM](../../relational-databases/blob/configure-a-firewall-for-filestream-access.md)   
 [Configurare un firewall per l'accesso al server di report](../../reporting-services/report-server/configure-a-firewall-for-report-server-access.md)  
  
  

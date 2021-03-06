---
title: Sys. tcp_endpoints (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.tcp_endpoints
- sys.tcp_endpoints_TSQL
- tcp_endpoints
- tcp_endpoints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.tcp_endpoints catalog view
ms.assetid: 43cc3afa-cced-4463-8e97-fbfdaf2e4fa8
caps.latest.revision: 28
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 1c04be5f76337422601486d08ff41316c7c98192
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "33221292"
---
# <a name="systcpendpoints-transact-sql"></a>sys.tcp_endpoints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene una riga per ogni endpoint TCP nel sistema. Gli endpoint che sono descritti **Sys. tcp_endpoints** forniscono un oggetto per concedere e revocare il privilegio di connessione. Le informazioni visualizzate relative alle porte e agli indirizzi IP non vengono utilizzate per configurare i protocolli e potrebbero non corrispondere alla configurazione effettiva del protocollo. Per visualizzare e configurare i protocolli, utilizzare Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**< colonne ereditate >**||Eredita le colonne da [Endpoints](../../relational-databases/system-catalog-views/sys-endpoints-transact-sql.md).|  
|**port**|INT|Numero della porta su cui è in attesa l'endpoint. Non ammette i valori Null.|  
|**is_dynamic_port**|bit|1 = Il numero della porta è stato assegnato dinamicamente.<br /><br /> Non ammette i valori Null.|  
|**ip_address**|**nvarchar(45)**|Indirizzo IP del listener specificato dalla clausola LISTENER_IP. Ammette i valori Null.|  
  
## <a name="remarks"></a>Remarks  
 Eseguire la query seguente per raccogliere informazioni sugli endpoint e sulle connessioni. Gli endpoint senza connessioni correnti o TCP verranno visualizzati con valori NULL. Aggiungere il **in** clausola `WHERE des.session_id = @@SPID` per restituire informazioni sulla connessione corrente.  
  
```  
SELECT des.login_name, des.host_name, program_name,  dec.net_transport, des.login_time,   
e.name AS endpoint_name, e.protocol_desc, e.state_desc, e.is_admin_endpoint,   
t.port, t.is_dynamic_port, dec.local_net_address, dec.local_tcp_port   
FROM sys.endpoints AS e  
LEFT JOIN sys.tcp_endpoints AS t  
   ON e.endpoint_id = t.endpoint_id  
LEFT JOIN sys.dm_exec_sessions AS des  
   ON e.endpoint_id = des.endpoint_id  
LEFT JOIN sys.dm_exec_connections AS dec  
   ON des.session_id = dec.session_id;  
```  
  
## <a name="permissions"></a>Autorizzazioni  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Viste del catalogo degli endpoint &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql.md)  
  
  

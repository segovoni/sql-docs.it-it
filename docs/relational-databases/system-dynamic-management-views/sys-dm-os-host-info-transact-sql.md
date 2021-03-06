---
title: sys.dm_os_host_info (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 02/10/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sys.dm_os_host_info
- sys.dm_os_host_info_TSQL
- dm_os_host_info
- dm_os_host_info_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_host_info dynamic management view
ms.assetid: 9bb6ef86-957b-4ca1-ad20-ca2f8460a86d
caps.latest.revision: 9
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 0aa5f28f52c9d0df4e942809612e1ca59a1cb3c5
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38044237"
---
# <a name="sysdmoshostinfo-transact-sql"></a>sys.dm_os_host_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Restituisce una riga che visualizza le informazioni sulla versione del sistema operativo.  
  
|Nome colonna |Tipo di dati |Description |  
|-----------------|---------------|-----------------|  
|**host_platform** |**nvarchar(256)** |Il tipo del sistema operativo: Windows o Linux |
|**host_distribution** |**nvarchar(256)** |Descrizione del sistema operativo. |
|**host_release**|**nvarchar(256)**|Versione del sistema operativo [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows (numero di versione). Per un elenco di valori e descrizioni, vedere [versione del sistema operativo (Windows)](http://msdn.microsoft.com/library/ms724832\(VS.85\).aspx). <br> Per Linux, restituisce una stringa vuota. |  
|**host_service_pack_level**|**nvarchar(256)**|Livello Service Pack del sistema operativo Windows <br> Per Linux, restituisce una stringa vuota. |  
|**host_sku**|**int**|ID Windows del codice di riferimento del prodotto (SKU). Per un elenco degli ID SKU e descrizioni, vedere [funzione GetProductInfo](http://msdn.microsoft.com/library/ms724358.aspx). Ammette i valori Null. <br> Per Linux, viene restituito NULL. |  
|**os_language_version**|**int**|Identificatore delle impostazioni locali (LCID) Windows del sistema operativo. Per un elenco dei valori LCID e delle descrizioni, vedere [Locale IDs Assigned by Microsoft](http://go.microsoft.com/fwlink/?LinkId=208080). Non può essere null.|  

## <a name="remarks"></a>Note  
Questa visualizzazione è simile a [sys.dm_os_windows_info](../../relational-databases/system-dynamic-management-views/sys-dm-os-windows-info-transact-sql.md), aggiunta di colonne per differenziare Windows e Linux.
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>Autorizzazioni  
Il `SELECT` autorizzazione `sys.dm_os_host_info` viene concesso al `public` ruolo per impostazione predefinita. Se è stato revocato, è necessario `VIEW SERVER STATE` autorizzazione nel server.   
 
>  [!CAUTION]
>  Partire dalla versione [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.3, [!INCLUDE[ssManStudioFull_md](../../includes/ssmanstudiofull-md.md)] richiede la versione 17 `SELECT` autorizzazione `sys.dm_os_host_info` per connettersi a [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Se `SELECT` autorizzazione viene revocata `public`, solo gli account di accesso con `VIEW SERVER STATE` autorizzazione può connettersi con la versione più recente di SSMS. (Altri strumenti, ad esempio `sqlcmd.exe` possono connettersi senza `SELECT` autorizzazione `sys.dm_os_host_info`.)

  
## <a name="examples"></a>Esempi  
 L'esempio seguente restituisce tutte le colonne dai **DM os_host_info** visualizzazione.  
  
```  
SELECT host_platform, host_distribution, host_release, 
    host_service_pack_level, host_sku, os_language_version  
FROM sys.dm_os_host_info;  
```  

Ecco un esempio set di risultati su Windows:
 
 |host_platform |host_distribution |host_release |host_service_pack_level |host_sku |os_language_version |
 |----- |----- |----- |----- |----- |----- |
 |Windows   |Windows Server 2012 R2 Standard    |6.3    |   |7  |1033 |  

Ecco un esempio di risultato impostato in Linux:
 
 |host_platform |host_distribution |host_release |host_service_pack_level |host_sku |os_language_version |
 |----- |----- |----- |----- |----- |----- |
 |Linux |Ubuntu |16.04  |   |NULL   |1033 |  

  
## <a name="see-also"></a>Vedere anche  
 [sys.dm_os_sys_info &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)   
 [sys.dm_os_windows_info (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-os-windows-info-transact-sql.md)  
 


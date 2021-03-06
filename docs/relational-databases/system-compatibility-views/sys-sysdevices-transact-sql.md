---
title: Sys.sysdevices (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-compatibility-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sysdevices
- sysdevices_TSQL
- sys.sysdevices
- sys.sysdevices_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysdevices compatibility view
- sysdevices system table
ms.assetid: ac5bcaf4-8fb6-4855-8856-d7643f469361
caps.latest.revision: 24
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: bf1a22fae1c4c8f69edf843c1a126844abdd1190
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33219982"
---
# <a name="syssysdevices-transact-sql"></a>sys.sysdevices (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene una riga per ogni file di backup su disco, di backup su nastro e di database.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Nome logico del file di backup o di database.|  
|**size**|**int**|Dimensioni del file in pagine da 2 KB.|  
|**Bassa**|**int**|Supportata per compatibilità con le versioni precedenti.|  
|**Elevata**|**int**|Supportata per compatibilità con le versioni precedenti.|  
|**status**|**smallint**|Mappa di bit che indica il tipo di dispositivo:<br /><br /> 1 = disco predefinito<br /><br /> 2 = disco fisico<br /><br /> 4 = disco logico<br /><br /> 8 = ignora intestazione<br /><br /> 16 = file di backup<br /><br /> 32 = scritture in serie<br /><br /> 4096= sola lettura|  
|**cntrltype**|**smallint**|Tipo di controller:<br /><br /> 0 = file di database non CD-ROM<br /><br /> 2 = file di backup su disco<br /><br /> 3 - 4 = file di backup su dischetto<br /><br /> 5 = file di backup su nastro<br /><br /> 6 = file named pipe|  
|**phyname**|**nvarchar(260)**|Nome del file fisico.|  
  
## <a name="see-also"></a>Vedere anche  
 [Mapping di tabelle di sistema a viste di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Viste della compatibilità &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  

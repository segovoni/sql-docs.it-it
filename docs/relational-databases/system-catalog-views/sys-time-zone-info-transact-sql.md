---
title: sys.time_zone_info (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/27/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- Azure SQL Database
- SQL Data Warehouse
- SQL Server (starting with 2016)
f1_keywords:
- sys.time_zone_info
- sys.time_zone_info_TSQL
- time_zone_info
- time_zone_info_TSQL
helpviewer_keywords:
- sys.time_zone_info system table
ms.assetid: 3f51a9a4-75f8-4a11-9552-8bf6118b68da
caps.latest.revision: 7
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 252def1ce861b926a6c8a990a3cbf10b22eb83f6
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "37984923"
---
# <a name="systimezoneinfo-transact-sql"></a>sys.time_zone_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  Restituisce informazioni sui fusi orari supportati. Tutti i fusi orari installati nel computer sono archiviati nell'hive del Registro di sistema seguente:  
`KEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time Zones`(Indici per tabelle con ottimizzazione per la memoria).  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Nome del fuso orario in formato standard di Windows. Ad esempio, **CEN. Ora solare Europa occidentale** oppure **ora solare Europa centrale**.|  
|**current_utc_offset**|**nvarchar(12)**|Offset all'ora UTC corrente. Ad esempio, **+ 01:00** oppure **-07:00**.|  
|**is_currently_dst**|**bit**|True se attualmente osservando l'ora legale.|  
  
## <a name="see-also"></a>Vedere anche  
 [GETUTCDATE &#40;Transact-SQL&#41;](../../t-sql/functions/getutcdate-transact-sql.md)   
 [AT TIME ZONE &#40;Transact-SQL&#41;](../../t-sql/queries/at-time-zone-transact-sql.md)   
 [Funzioni e tipi di dati di data e ora &#40;Transact-SQL&#41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md)   
 [Viste del catalogo a livello di server di configurazione &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/server-wide-configuration-catalog-views-transact-sql.md)  

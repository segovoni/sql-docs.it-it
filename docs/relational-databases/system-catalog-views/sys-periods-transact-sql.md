---
title: Sys.Periods (Transact-SQL) | Documenti Microsoft
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
dev_langs:
- TSQL
ms.assetid: 25e66ed3-2270-4c5c-9f5a-2c0f165a57ca
caps.latest.revision: 6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ca6eea06d877ec9a6a92c35d0bd01401300f3974
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33180107"
---
# <a name="sysperiods-transact-sql"></a>Sys.Periods (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Restituisce una riga per ogni tabella per cui sono stati definiti i periodi.  
  
|Intestazione della colonna|Tipo di dati|Description|  
|-------------------|---------------|-----------------|  
|period_type|**sysname**|Nome del periodo|  
|period_type_desc|**tinyint**|Il valore numerico che rappresenta il tipo di periodo:<br /><br /> 1 = periodo con ora di sistema|  
|object_id|**nvarchar(60)**|La descrizione del tipo di colonna:<br /><br /> SYSTEM_TIME_PERIOD|  
|object_id|**int**|L'id della tabella contenente la colonna period_type|  
|start_column_id|**int**|L'id della colonna che definisce il limite inferiore di periodo|  
|end_column_id|**int**|L'id della colonna che definisce il limite massimo di periodo|  
  
## <a name="permissions"></a>Autorizzazioni  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste di sistema &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [Viste del catalogo dell'oggetto &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys.all_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [sys.system_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-system-columns-transact-sql.md)   
 [L'esecuzione di query il catalogo di sistema SQL Server domande frequenti](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [Tabelle temporali](../../relational-databases/tables/temporal-tables.md)  
  
  

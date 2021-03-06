---
title: Sys. security_predicates (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- Azure SQL Database
- SQL Server 2016 Preview
f1_keywords:
- SYS.SECURITY_PREDICATES
- SECURITY_PREDICATES
- SECURITY_PREDICATES_TSQL
- SYS.SECURITY_PREDICATES_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.security_predicates catalog view
- security_predicates catalog view
ms.assetid: c7a2f28c-98da-463d-8b8a-8e5619e2c6a6
caps.latest.revision: 9
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 539ca48e5c55485a5a4b3fdecb3044c1feae6826
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "37993853"
---
# <a name="syssecuritypredicates-transact-sql"></a>Sys. security_predicates (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Restituisce una riga per ogni predicato di sicurezza nel database.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|object_id|**int**|ID del criterio di sicurezza che contiene il predicato.|  
|security_predicate_id|**int**|ID predicato all'interno del criterio di sicurezza.|  
|target_object_id|**int**|ID dell'oggetto a cui è associato il predicato di sicurezza.|  
|predicate_definition|**nvarchar(max)**|Nome completo della funzione che verrà usata come predicato di sicurezza, inclusi gli argomenti. Si noti che il `schema.function` nome può essere normalizzato (vale a dire con caratteri di escape) come qualsiasi altro elemento nel testo per la coerenza. Esempio:<br /><br /> `[dbo].[fn_securitypredicate]([wing], [startTime], [endTime])`|  
|predicate_type|**int**|Tipo di predicato usato dai criteri di sicurezza:<br /><br /> 0 = PREDICATO DEL FILTRO<br /><br /> 1 = PREDICATO DI BLOCCO|  
|predicate_type_desc|**nvarchar(60)**|Tipo di predicato usato dai criteri di sicurezza:<br /><br /> FILTER<br /><br /> BLOCCO|  
|operazione|**int**|Il tipo di operazione specificato per il predicato:<br /><br /> NULL = tutte le operazioni applicabili<br /><br /> 1 = AFTER INSERT<br /><br /> 2 = DOPO L'AGGIORNAMENTO<br /><br /> 3 = PRIMA DELL'AGGIORNAMENTO<br /><br /> 4 = PRIMA DELL'ELIMINAZIONE|  
|operation_desc|**nvarchar(60)**|Il tipo di operazione specificato per il predicato:<br /><br /> NULL<br /><br /> DOPO L'INSERIMENTO<br /><br /> AFTER UPDATE<br /><br /> PRIMA DELL'AGGIORNAMENTO<br /><br /> PRIMA DELL'ELIMINAZIONE|  
  
## <a name="permissions"></a>Autorizzazioni  
 Le entità con la **ALTER ANY SECURITY POLICY** autorizzazione ha accesso a tutti gli oggetti in questa vista del catalogo, nonché tutti gli utenti con **VIEW DEFINITION** sull'oggetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza a livello di riga](../../relational-databases/security/row-level-security.md)   
 [sys.security_policies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-security-policies-transact-sql.md)   
 [CREATE SECURITY POLICY &#40;Transact-SQL&#41;](../../t-sql/statements/create-security-policy-transact-sql.md)   
 [Viste del catalogo relative alla sicurezza &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Entità &#40;motore di database&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  

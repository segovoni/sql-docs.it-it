---
title: sp_fulltext_database (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_fulltext_database_TSQL
- sp_fulltext_database
dev_langs:
- TSQL
helpviewer_keywords:
- sp_fulltext_database
ms.assetid: eeb1e151-eb00-484c-8fd1-5641e621ffc6
caps.latest.revision: 45
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 8f4904de1142052a8286aabb4a69bf439871b84e
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33241463"
---
# <a name="spfulltextdatabase-transact-sql"></a>sp_fulltext_database (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Non ha alcun effetto sui cataloghi full-text in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] e versioni successive ed è supportata solo per la compatibilità con le versioni precedenti. **sp_fulltext_database** non disabilita il motore Full-Text per un determinato database. Tutti i database creati dall'utente in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] sono sempre abilitati per l'indicizzazione full-text.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]Utilizzare [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] invece.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_fulltext_database [@action=] 'action'  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@action=**] **'***azione***'**  
 Azione da eseguire. **azione** viene **varchar (20)**, e può essere uno dei valori seguenti.  
  
|Value|Description|  
|-----------|-----------------|  
|**Abilitare**|Supportata unicamente per compatibilità con le versioni precedenti. Non produce alcun effetto sui cataloghi full-text in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] e versioni successive.|  
|**disable**|Supportata unicamente per compatibilità con le versioni precedenti. Non produce alcun effetto sui cataloghi full-text in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] e versioni successive.|  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="remarks"></a>Osservazioni  
 In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] e versioni successive, non è possibile disabilitare l'indicizzazione full-text. Disabilitare l'indicizzazione full-text non rimuove le righe da **sysfulltextcatalogs** e indicare che le tabelle abilitate full-text non sono più contrassegnate per l'indicizzazione full-text. Tutte le definizioni di metadati full-text vengono conservate nelle tabelle di sistema.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server e **db_owner** ruolo predefinito del database possono eseguire **sp_fulltext_database**.  
  
## <a name="see-also"></a>Vedere anche  
 [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](../../t-sql/functions/databasepropertyex-transact-sql.md)   
 [FULLTEXTSERVICEPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/fulltextserviceproperty-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

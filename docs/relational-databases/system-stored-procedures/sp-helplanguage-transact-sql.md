---
title: sp_helplanguage (Transact-SQL) | Documenti Microsoft
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
- sp_helplanguage
- sp_helplanguage_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helplanguage
- default languages
ms.assetid: 8c4651a5-7dbc-49c5-8691-dc72103c2dfa
caps.latest.revision: 19
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: fdea1704b8942191bf79cb9074715f61eb9a9e81
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33260434"
---
# <a name="sphelplanguage-transact-sql"></a>sp_helplanguage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce informazioni su una lingua alternativa specifica o su tutte le lingue in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_helplanguage [ [ @language = ] 'language' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@language=** ] **'***language***'**  
 Nome della lingua alternativa per la quale visualizzare le informazioni. *linguaggio* viene **sysname**, con un valore predefinito è NULL. Se *language* è specificato, vengono restituite informazioni sulla lingua specifica. Se non viene specificato alcun linguaggio, informazioni su tutte le lingue nel **Sys. syslanguages** vista di compatibilità viene restituito.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**langid**|**smallint**|Numero di identificazione della lingua.|  
|**dateformat**|**nchar(3)**|Formato della data.|  
|**DATEFIRST**|**tinyint**|Primo giorno della settimana: 1 per lunedì, 2 per martedì e così via fino a 7 per domenica.|  
|**Aggiornamento**|**int**|Versione dell'ultimo aggiornamento di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per la lingua specificata.|  
|**name**|**sysname**|Nome della lingua.|  
|**alias**|**sysname**|Nome alternativo per la lingua.|  
|**Mesi**|**nvarchar(372)**|Nomi dei mesi.|  
|**shortmonths**|**nvarchar(132)**|Nomi brevi dei mesi.|  
|**Giorni**|**nvarchar(217)**|Nomi dei giorni.|  
|**lcid**|**int**|ID delle impostazioni locali di Windows relative alla lingua.|  
|**msglangid**|**smallint**|ID del gruppo di messaggi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza al ruolo **public** .  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-returning-information-about-a-single-language"></a>A. Restituzione di informazioni su una sola lingua  
 Nell'esempio seguente vengono visualizzate informazioni sulla lingua alternativa `French`.  
  
```  
sp_helplanguage French;  
```  
  
### <a name="b-returning-information-about-all-languages"></a>B. Restituzione di informazioni su tutte le lingue  
 Nell'esempio seguente vengono visualizzate informazioni su tutte le lingue alternative installate.  
  
```  
sp_helplanguage;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure del motore di database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [@@LANGUAGE &#40;Transact-SQL&#41;](../../t-sql/functions/language-transact-sql.md)   
 [SET LANGUAGE &#40;Transact-SQL&#41;](../../t-sql/statements/set-language-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

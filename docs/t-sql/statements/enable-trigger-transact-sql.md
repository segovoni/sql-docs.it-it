---
title: ENABLE TRIGGER (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 05/12/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ENABLE TRIGGER
- ENABLE_TSQL
- ENABLE_TRIGGER_TSQL
- ENABLE
dev_langs:
- TSQL
helpviewer_keywords:
- DDL triggers, enabling
- triggers [SQL Server], enabling
- DML triggers, enabling
- ENABLE TRIGGER statement
ms.assetid: 6e21f0ad-68d0-432f-9c7c-a119dd2d3fc9
caps.latest.revision: 39
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 6d1f7ab7c0f0cb9f6fb5195be1409bb5109c13b4
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/04/2018
ms.locfileid: "37785022"
---
# <a name="enable-trigger-transact-sql"></a>ENABLE TRIGGER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Abilita un trigger DML, DDL o LOGON.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
ENABLE TRIGGER { [ schema_name . ] trigger_name [ ,...n ] | ALL }  
ON { object_name | DATABASE | ALL SERVER } [ ; ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *schema_name*  
 Nome dello schema a cui appartiene il trigger. *schema_name* non può essere specificato per i trigger DDL o LOGON.  
  
 *trigger_name*  
 Nome del trigger da abilitare.  
  
 ALL  
 Indica che vengono abilitati tutti i trigger definiti nell'ambito della clausola ON.  
  
 *object_name*  
 Nome della tabella o della vista su cui deve essere eseguito il trigger DML *trigger_name*.  
  
 DATABASE  
 Per un trigger DDL, indica che *trigger_name* è stato creato o modificato per essere eseguito con ambito database.  
  
 ALL SERVER  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Per un trigger DDL, indica che *trigger_name* è stato creato o modificato per essere eseguito con ambito server. ALL SERVER si applica anche ai trigger LOGON.  
  
> [!NOTE]  
>  Questa opzione non è disponibile in un database indipendente.  
  
## <a name="remarks"></a>Remarks  
 L'abilitazione di un trigger non comporta la sua creazione ex-novo. Un trigger disabilitato continua a esistere come oggetto nel database corrente, ma non verrà mai attivato. Se si abilita un trigger, questo verrà attivato ogni volta che vengono eseguite istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] per le quali è stato programmato in origine. I trigger vengono disabilitati tramite [DISABLE TRIGGER](../../t-sql/statements/disable-trigger-transact-sql.md). I trigger DML definiti su tabelle possono essere disabilitati o abilitati anche tramite [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md).  
  
## <a name="permissions"></a>Autorizzazioni  
 Per abilitare un trigger DML, un utente deve disporre almeno dell'autorizzazione ALTER per la tabella o vista in base alla quale il trigger è stato creato.  
  
 Per abilitare un trigger DDL con ambito server (ON ALLA SERVER) o un trigger LOGON, è necessario disporre dell'autorizzazione CONTROL SERVER per il server. Per abilitare un trigger DDL nell'ambito del database (ON DATABASE), un utente deve disporre almeno dell'autorizzazione ALTER ANY DATABASE DDL TRIGGER nel database corrente.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-enabling-a-dml-trigger-on-a-table"></a>A. Abilitazione di un trigger DML in una tabella  
 Nell'esempio seguente il trigger `uAddress` creato nella tabella `Address` del database AdventureWorks viene disabilitato e quindi abilitato.  
  
```  
DISABLE TRIGGER Person.uAddress ON Person.Address;  
GO  
ENABLE Trigger Person.uAddress ON Person.Address;  
GO  
```  
  
### <a name="b-enabling-a-ddl-trigger"></a>B. Abilitazione di un trigger DDL  
 Nell'esempio seguente viene creato un trigger DDL `safety` con ambito database, che viene quindi disabilitato e poi abilitato.  
  
```  
CREATE TRIGGER safety   
ON DATABASE   
FOR DROP_TABLE, ALTER_TABLE   
AS   
   PRINT 'You must disable Trigger "safety" to drop or alter tables!'   
   ROLLBACK;  
GO  
DISABLE TRIGGER safety ON DATABASE;  
GO  
ENABLE TRIGGER safety ON DATABASE;  
GO  
```  
  
### <a name="c-enabling-all-triggers-that-were-defined-with-the-same-scope"></a>C. Abilitazione di tutti i trigger definiti nello stesso ambito  
 Nell'esempio seguente vengono abilitati tutti i trigger DDL creati nell'ambito del server.  
  
**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```  
ENABLE Trigger ALL ON ALL SERVER;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [DISABLE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/disable-trigger-transact-sql.md)   
 [ALTER TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/alter-trigger-transact-sql.md)   
 [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)   
 [DROP TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/drop-trigger-transact-sql.md)   
 [sys.triggers &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-triggers-transact-sql.md)  
  
  

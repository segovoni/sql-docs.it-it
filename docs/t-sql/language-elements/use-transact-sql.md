---
title: UTILIZZARE (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 11/28/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- USE_TSQL
- USE
dev_langs:
- TSQL
helpviewer_keywords:
- USE statement
- database context [SQL Server]
- context changes [SQL Server]
- modifying database context
ms.assetid: c05acac8-c063-4770-8e36-d7f71d500b10
caps.latest.revision: 40
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d6274293bd4caedc9cad00ad4532952e63e3e989
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="use-transact-sql"></a>USE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  Sostituisce il contesto di database con il database o lo snapshot del database specificato in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
USE { database_name }   
[;]  
```  
  
## <a name="arguments"></a>Argomenti  
 *database_name*  
 Nome del database o dello snapshot del database su cui viene impostato il contesto utente. Database e i nomi degli snapshot di database devono essere conformi alle regole per [identificatori](../../relational-databases/databases/database-identifiers.md).  
  
 In [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] il parametro del database può fare riferimento solo al database corrente. Se viene fornito un database diverso da quello corrente, il `USE` istruzione non consente il passaggio tra database e viene restituito il codice di errore 40508. Per cambiare database, è necessario connettersi direttamente al database. L'istruzione USE è contrassegnato come non applicabile al Database SQL nella parte superiore della pagina, perché anche se è possibile avere il `USE` istruzione in un batch, non esegue alcuna operazione.
  
## <a name="remarks"></a>Osservazioni  
 Quando un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] si connette a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], tale account viene connesso automaticamente al relativo database predefinito e acquisisce il contesto di sicurezza di un utente del database. Se per l'account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non è stato creato alcun utente di database, l'account si connette come guest. Se l'utente del database non dispone dell'autorizzazione CONNECT per il database, l'istruzione USE avrà esito negativo. Se all'account di accesso non è stato assegnato un database predefinito, verrà impostato il database master.  
  
 L'istruzione USE viene eseguita sia in fase di compilazione che in fase di esecuzione e ha effetto immediato. Pertanto, le istruzioni presenti in un batch dopo l'istruzione USE vengono eseguite nel database specificato.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione CONNECT per il database di destinazione.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente il contesto di database viene impostato sul database `AdventureWorks2012`.  
  
```  
USE AdventureWorks2012;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Nell'esempio seguente il contesto di database viene impostato sul database `AccountingDB`.  
  
```  
USE AccountingDB;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [CREATE USER &#40;Transact-SQL&#41;](../../t-sql/statements/create-user-transact-sql.md)   
 [Entità &#40;motore di database&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [DROP DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-transact-sql.md)   
 [EXECUTE &#40;Transact-SQL&#41;](../../t-sql/language-elements/execute-transact-sql.md)  
  
  



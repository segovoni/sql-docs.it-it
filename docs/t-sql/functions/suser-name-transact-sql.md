---
title: SUSER_NAME (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-data-warehouse, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- SUSER_NAME
- SUSER_NAME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- security identification names [SQL Server]
- logins [SQL Server], users
- identification names for logins [SQL Server]
- users [SQL Server], logins
- SUSER_NAME function
- logins [SQL Server], names
- names [SQL Server], logins
ms.assetid: ae598d9f-9baa-49b8-b1c1-042854206de4
caps.latest.revision: 29
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: b5dce9250bdb473d5ab8dbd727d27d83a77c7161
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/04/2018
ms.locfileid: "37790882"
---
# <a name="susername-transact-sql"></a>SUSER_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-xxx-md.md)]

  Restituisce il nome di identificazione dell'account di accesso dell'utente.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SUSER_NAME ( [ server_user_id ] )   
```  
  
## <a name="arguments"></a>Argomenti  
 *server_user_id*  
 Numero di identificazione dell'account di accesso dell'utente. *server_user_id* è facoltativo ed è di tipo **int**. *server_user_id* può essere il numero di identificazione di qualsiasi account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oppure di qualsiasi utente o gruppo di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows autorizzato a connettersi a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Se *server_user_id* viene omesso, viene restituito il nome di identificazione dell'account di accesso dell'utente corrente. Se nel parametro è inclusa la parola NULL, verrà restituito NULL.  
  
## <a name="return-types"></a>Tipi restituiti  
 **nvarchar(128)**  
  
## <a name="remarks"></a>Remarks  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versione 7.0 l'ID dell'utente del server (SUID) è stato sostituito con l'ID di sicurezza (SID).  
  
 SUSER_NAME restituisce un nome di account di accesso solo per gli account a cui corrisponde una voce nella tabella di sistema **syslogins**.  
  
 È possibile utilizzare SUSER_NAME in un elenco di selezione, in una clausola WHERE e in qualsiasi posizione in cui è consentita un'espressione. La funzione SUSER_NAME deve essere sempre seguita dalle parentesi, anche se non si specifica alcun parametro.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene restituito il nome di identificazione dell'account di accesso dell'utente il cui numero di identificazione dell'account di accesso è `1`.  
  
```  
SELECT SUSER_NAME(1);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [SUSER_ID &#40;Transact-SQL&#41;](../../t-sql/functions/suser-id-transact-sql.md)   
 [Entità &#40;motore di database&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  

---
title: DROP COLUMN MASTER KEY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 04/20/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DROP COLUMN MASTER KEY
- DROP_COLUMN_MASTER_KEY_TSQL
- DROP COLUMN MASTER
- DROP_COLUMN_MASTER_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.column_master_keys catalog view
ms.assetid: fd5e77c8-a3ae-4795-bb46-b322c0500041
caps.latest.revision: 14
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 0d296c7bdb9c5923a49454c10e23f87a8156aff7
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/04/2018
ms.locfileid: "37784102"
---
# <a name="drop-column-master-key-transact-sql"></a>DROP COLUMN MASTER KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Elimina la chiave master di una colonna da un database. Si tratta di un'operazione sui metadati.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DROP COLUMN MASTER KEY key_name;  
```  
  
## <a name="arguments"></a>Argomenti  
 *key_name*  
 Nome della chiave master della colonna.  
  
## <a name="remarks"></a>Remarks  
 La chiave master della colonna può essere eliminata solo se non sono presenti valori della chiave di crittografia della colonna crittografati con tale chiave. Per eliminare i valori della chiave di crittografia della colonna, usare l'istruzione [DROP COLUMN ENCRYPTION KEY](../../t-sql/statements/drop-column-encryption-key-transact-sql.md).  
  
## <a name="permissions"></a>Autorizzazioni  
 È necessaria l'autorizzazione **ALTER ANY COLUMN MASTER KEY** per il database.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-dropping-a-column-master-key"></a>A. Eliminazione di una chiave master della colonna  
 Nell'esempio seguente viene eliminata una chiave master della colonna denominata `MyCMK`.  
  
```  
DROP COLUMN MASTER KEY MyCMK;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE COLUMN MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-column-master-key-transact-sql.md)   
 [CREATE COLUMN ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-column-encryption-key-transact-sql.md)   
 [DROP COLUMN ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-column-encryption-key-transact-sql.md)   
 [Always Encrypted &#40;Motore di database&#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
 [sys.column_master_keys &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-master-keys-transact-sql.md)  
  
  

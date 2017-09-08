---
title: DROP ASYMMETRIC KEY (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP ASYMMETRIC KEY
- DROP_ASYMMETRIC_KEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- asymmetric keys [SQL Server], removing
- removing asymmetric keys
- encryption [SQL Server], asymmetric keys
- DROP ASYMMETRIC KEY statement
- dropping asymmetric keys
- deleting asymmetric keys
- cryptography [SQL Server], asymmetric keys
ms.assetid: bf94ac07-9b62-4318-b55b-1eed8f3a1ac6
caps.latest.revision: 32
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f3737521ee178f9b7287f8d86e269973841d74c6
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="drop-asymmetric-key-transact-sql"></a>DROP ASYMMETRIC KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Rimuove una chiave asimmetrica dal database.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DROP ASYMMETRIC KEY key_name [ REMOVE PROVIDER KEY ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *key_name*  
 Nome della chiave asimmetrica da rimuovere dal database.  
  
 REMOVE PROVIDER KEY  
 Rimuove una chiave EKM (Extensible Key Management ) da un dispositivo EKM. Per ulteriori informazioni su Extensible Key Management, vedere [Extensible Key Management &#40; EKM &#41; ](../../relational-databases/security/encryption/extensible-key-management-ekm.md).  
  
## <a name="remarks"></a>Osservazioni  
 Non è possibile rimuovere una chiave asimmetrica con cui è stata crittografata una chiave simmetrica nel database o a cui è stato eseguito il mapping di un utente o un account di accesso. Prima di rimuovere questo tipo di chiave, è necessario rimuovere qualsiasi utente o account di accesso di cui è eseguito il mapping alla chiave, nonché rimuovere o modificare qualsiasi chiave simmetrica crittografata con la chiave asimmetrica. È possibile utilizzare l'opzione DROP ENCRYPTION di [ALTER SYMMETRIC KEY](../../t-sql/statements/alter-symmetric-key-transact-sql.md) per rimuovere la crittografia mediante una chiave asimmetrica.  
  
 I metadati delle chiavi asimmetriche sono accessibili tramite il [asymmetric_keys](../../relational-databases/system-catalog-views/sys-asymmetric-keys-transact-sql.md) vista del catalogo. Le chiavi non possono essere visualizzate direttamente dall'interno del database.  
  
 Se sulla chiave asimmetrica viene eseguito il mapping a una chiave EKM (Extensible Key Management) in un dispositivo EKM e l'opzione REMOVE PROVIDER KEY non è specificata, la chiave verrà rimossa dal database ma non dal dispositivo e verrà generato un avviso.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione CONTROL per la chiave asimmetrica.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene rimossa la chiave asimmetrica `MirandaXAsymKey6` dal database `AdventureWorks2012`.  
  
```  
USE AdventureWorks2012;  
DROP ASYMMETRIC KEY MirandaXAsymKey6;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [ALTER ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-asymmetric-key-transact-sql.md)   
 [Gerarchia di crittografia](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [ALTER SYMMETRIC KEY &#40; Transact-SQL &#41;](../../t-sql/statements/alter-symmetric-key-transact-sql.md)  
  
  
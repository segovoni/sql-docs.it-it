---
title: DECRYPTBYPASSPHRASE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DECRYPTBYPASSPHRASE
- DECRYPTBYPASSPHRASE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- decryption [SQL Server], symmetric keys
- symmetric keys [SQL Server], DECRYPTBYPASSPHRASE function
- DECRYPTBYPASSPHRASE function
ms.assetid: ca34b5cd-07b3-4dca-b66a-ed8c6a826c95
caps.latest.revision: 28
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ee0265d9974883cd0d61ac1b8f0514f97d1b3a04
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/04/2018
ms.locfileid: "37787752"
---
# <a name="decryptbypassphrase-transact-sql"></a>DECRYPTBYPASSPHRASE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Questa funzione decrittografa i dati originariamente crittografati con una passphrase.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DecryptByPassPhrase ( { 'passphrase' | @passphrase }   
    , { 'ciphertext' | @ciphertext }  
  [ , { add_authenticator | @add_authenticator }  
    , { authenticator | @authenticator } ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *passphrase*  
Passphrase usata per generare la chiave di decrittografia.  
  
 @passphrase  
Variabile di tipo

+ **char**
+ **nchar**
+ **nvarchar**

o Gestione configurazione

+ **varchar**

contenente la passphrase usata per generare la chiave di decrittografia.  
  
'*ciphertext*'  
Stringa di dati crittografata con la chiave. *ciphertext* ha un tipo dati **varbinary**.  
 
@ciphertext  
Variabile di tipo **varbinary** contenente dati crittografati con la chiave. La variabile *@ciphertext* ha una dimensione massima di 8.000 byte.  
  
*add_authenticator*  
Indica se il processo di crittografia originale includeva e crittografava un autenticatore insieme al testo non crittografato. *add_authenticator* ha un valore pari a 1 se il processo di crittografia ha usato un autenticatore. *add_authenticator* ha un tipo di dati **int**.  
  
@add_authenticator  
Variabile che indica se il processo di crittografia originale includeva e crittografava un autenticatore insieme al testo non crittografato. *@add_authenticator* ha un valore pari a 1 se il processo di crittografia ha usato un autenticatore. *@add_authenticator* ha un tipo di dati **int**.  

*authenticator*  
Dati usati come base per la generazione dell'autenticatore. *authenticator* ha un tipo di dati **sysname**.  
  
@authenticator  
Variabile contenente i dati usati come base per la generazione degli autenticatori. *@authenticator* ha un tipo di dati **sysname**.  
  
## <a name="return-types"></a>Tipi restituiti  
**varbinary** con un valore massimo di 8.000 byte.  
  
## <a name="remarks"></a>Remarks  
`DECRYPTBYPASSPHRASE` non richiede autorizzazioni per l'esecuzione. `DECRYPTBYPASSPHRASE` restituisce NULL se riceve la passphrase non corretta o informazioni errate sull'autenticatore.  
  
`DECRYPTBYPASSPHRASE` usa la passphrase per generare la chiave di decrittografia. Questa chiave di decrittografia non sarà persistente.  
  
Se è stato incluso un autenticatore durante la crittografia del testo, `DECRYPTBYPASSPHRASE` deve ricevere lo stesso autenticatore per il processo di decrittografia. Se il valore dell'autenticatore fornito per il processo di decrittografia non corrisponde al valore dell'autenticatore usato originariamente per crittografare i dati, non sarà possibile completare l'operazione `DECRYPTBYPASSPHRASE`.  
  
## <a name="examples"></a>Esempi  
Questo esempio decrittografa il record aggiornato in [EncryptByPassPhrase](../../t-sql/functions/encryptbypassphrase-transact-sql.md).  
  
```  
USE AdventureWorks2012;  
-- Get the pass phrase from the user.  
DECLARE @PassphraseEnteredByUser nvarchar(128);  
SET @PassphraseEnteredByUser   
= 'A little learning is a dangerous thing!';  
  
-- Decrypt the encrypted record.  
SELECT CardNumber, CardNumber_EncryptedbyPassphrase   
    AS 'Encrypted card number', CONVERT(nvarchar,  
    DecryptByPassphrase(@PassphraseEnteredByUser, CardNumber_EncryptedbyPassphrase, 1   
    , CONVERT(varbinary, CreditCardID)))  
    AS 'Decrypted card number' FROM Sales.CreditCard   
    WHERE CreditCardID = '3681';  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Scelta di un algoritmo di crittografia](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)   
 [ENCRYPTBYPASSPHRASE &#40;Transact-SQL&#41;](../../t-sql/functions/encryptbypassphrase-transact-sql.md)  
  
  

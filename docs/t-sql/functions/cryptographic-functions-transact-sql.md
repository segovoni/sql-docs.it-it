---
title: Funzioni di crittografia (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- functions [SQL Server], cryptographic
- crypto functions
- cryptography [SQL Server], functions
- decryption [SQL Server], functions
- security functions
- encryption [SQL Server], functions
ms.assetid: 0be5626b-5a25-4d8c-9f44-7abbfccf816c
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3952669bb2d378338fc31aebe7e6e539f4dbf173
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/04/2018
ms.locfileid: "37788742"
---
# <a name="cryptographic-functions-transact-sql"></a>Funzioni di crittografia (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Queste funzioni supportano la firma digitale, la convalida della firma digitale, la crittografia e la decrittografia.
  
## <a name="symmetric-encryption-and-decryption"></a>Crittografia e decrittografia simmetrica
  
|||  
|-|-|  
|[ENCRYPTBYKEY](../../t-sql/functions/encryptbykey-transact-sql.md)|[DECRYPTBYKEY](../../t-sql/functions/decryptbykey-transact-sql.md)|  
|[ENCRYPTBYPASSPHRASE](../../t-sql/functions/encryptbypassphrase-transact-sql.md)|[DECRYPTBYPASSPHRASE](../../t-sql/functions/decryptbypassphrase-transact-sql.md)|  
|[KEY_ID](../../t-sql/functions/key-id-transact-sql.md)|[KEY_GUID](../../t-sql/functions/key-guid-transact-sql.md)|  
|[DECRYPTBYKEYAUTOASYMKEY](../../t-sql/functions/decryptbykeyautoasymkey-transact-sql.md)|[KEY_NAME](../../t-sql/functions/key-name-transact-sql.md)|  
|[SYMKEYPROPERTY](../../t-sql/functions/symkeyproperty-transact-sql.md)||  
  
## <a name="asymmetric-encryption-and-decryption"></a>Crittografia e decrittografia asimmetrica
  
|||  
|-|-|  
|[ENCRYPTBYASYMKEY](../../t-sql/functions/encryptbyasymkey-transact-sql.md)|[DECRYPTBYASYMKEY](../../t-sql/functions/decryptbyasymkey-transact-sql.md)|  
|[ENCRYPTBYCert](../../t-sql/functions/encryptbycert-transact-sql.md)|[DECRYPTBYCERT](../../t-sql/functions/decryptbycert-transact-sql.md)|  
|[ASYMKEYPROPERTY](../../t-sql/functions/asymkeyproperty-transact-sql.md)|[ASYMKEY_ID](../../t-sql/functions/asymkey-id-transact-sql.md)|  
  
## <a name="signing-and-signature-verification"></a>Firma e verifica delle firme
  
|||  
|-|-|  
|[SIGNBYASYMKEY](../../t-sql/functions/signbyasymkey-transact-sql.md)|[VERIFYSIGNEDBYASMKEY](../../t-sql/functions/verifysignedbyasymkey-transact-sql.md)|  
|[SIGNBYCERT](../../t-sql/functions/signbycert-transact-sql.md)|[VERIGYSIGNEDBYCERT](../../t-sql/functions/verifysignedbycert-transact-sql.md)|  
|[IS_OBJECTSIGNED](../../t-sql/functions/is-objectsigned-transact-sql.md)||  
  
## <a name="symmetric-decryption-with-automatic-key-handling"></a>Decrittografia simmetrica, con gestione automatica delle chiavi
  
|||  
|-|-|  
|[DecryptByKeyAutoCert](../../t-sql/functions/decryptbykeyautocert-transact-sql.md)||  
  
## <a name="encryption-hashing"></a>Hashing di crittografia
  
|||  
|-|-|  
|[HASHBYTES](../../t-sql/functions/hashbytes-transact-sql.md)||  
  
## <a name="certificate-copying"></a>Copia del certificato
  
|||  
|-|-|  
|[CERTENCODED &#40;Transact-SQL&#41;](../../t-sql/functions/certencoded-transact-sql.md)||  
|[CERTPRIVATEKEY &#40;Transact-SQL&#41;](../../t-sql/functions/certprivatekey-transact-sql.md)||  
  
## <a name="see-also"></a>Vedere anche
[Funzioni](../../t-sql/functions/functions.md)  
[Gerarchia di crittografia](../../relational-databases/security/encryption/encryption-hierarchy.md)  
[Gerarchia delle autorizzazioni &#40;motore di database&#41;](../../relational-databases/security/permissions-hierarchy-database-engine.md)  
[CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)  
[CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)  
[CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)  
[Viste del catalogo relative alla sicurezza &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)
  
  

---
title: cryptographic_provider_properties (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_cryptographic_provider_properties_TSQL
- sys.dm_cryptographic_provider_properties
- sys.dm_cryptographic_provider_properties_TSQL
- dm_cryptographic_provider_properties
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_cryptographic_provider_properties dynamic management view
ms.assetid: 024b0095-6766-4189-a39a-d316c5ec2874
caps.latest.revision: 15
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: af1e68502ad7be83a8cfa8f3477420d7336e5f43
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/23/2018
---
# <a name="sysdmcryptographicproviderproperties-transact-sql"></a>sys.dm_cryptographic_provider_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce informazioni sui provider di crittografia registrati.  
  
 
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|provider_id|**int**|Numero di identificazione del provider di crittografia.|  
|guid|**uniqueidentifier**|GUID univoco del provider.|  
|provider_version|**nvarchar(256)**|Versione del provider nel formato '*aa.bb.cccc.dd*'.|  
|sqlcrypt_version|**nvarchar(256)**|Versione principale del [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dell'API di crittografia nel formato '*aa.bb.cccc.dd*'.|  
|friendly_name|**nvarchar(2048)**|Nome fornito dal provider.|  
|authentication_type|**nvarchar(256)**|WINDOWS, BASIC o OTHER.|  
|symmetric_key_support|**tinyint**|0 (non supportato)<br /><br /> 1 (supportato)|  
|symmetric_key_export|**tinyint**|0 (non supportato)<br /><br /> 1 (supportato)|  
|symmetric_key_import|**tinyint**|0 (non supportato)<br /><br /> 1 (supportato)|  
|symmetric_key_persistance|**tinyint**|0 (non supportato)<br /><br /> 1 (supportato)|  
|asymmetric_key_support|**tinyint**|0 (non supportato)<br /><br /> 1 (supportato)|  
|asymmetric_key_export|**tinyint**|0 (non supportato)<br /><br /> 1 (supportato)|  
|symmetric_key_import|**tinyint**|0 (non supportato)<br /><br /> 1 (supportato)|  
|symmetric_key_persistance|**tinyint**|0 (non supportato)<br /><br /> 1 (supportato)|  
  
## <a name="remarks"></a>Osservazioni  
 La vista sys.dm_cryptographic_provider_properties è visibile a tutti.  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo relative alla sicurezza &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Gerarchia di crittografia](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [Extensible Key Management &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)   
 [CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](../../t-sql/statements/create-cryptographic-provider-transact-sql.md)   
 [Funzioni e viste a gestione dinamica relative alla sicurezza &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/security-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  

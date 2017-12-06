---
title: Sys. sp_rda_reauthorize_db (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-stretch
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_rda_reauthorize_db
- sp_rda_reauthorize_db_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.sp_rda_reauthorize_db stored procedure
ms.assetid: f6f3e4b2-8c72-4d23-a5de-fe671ca5c5cd
caps.latest.revision: "20"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b6e9f73c96cc07bfe442ac3104c4b1f4824596ed
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="syssprdareauthorizedb-transact-sql"></a>Sys. sp_rda_reauthorize_db (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Ripristina la connessione autenticata tra un database locale abilitato per l'estensione e il database remoto.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_rda_reauthorize_db @credential = @credential, @with_copy = @with_copy [ , @azure_servername = @azure_servername, @azure_databasename = @azure_databasename ]  
```  
  
## <a name="arguments"></a>Argomenti  
 @credential = *@credential*  
 Sia le credenziali con ambito database associate al database locale abilitata per l'estensione.  
  
 @with_copy = *@with_copy*  
 Specifica se eseguire una copia dei dati remoti e connettersi alla copia (scelta consigliata). *@with_copy*è di tipo bit.  
  
 @azure_servername = *@azure_servername*  
 Specifica il nome del server Azure che contiene i dati remoti. *@azure_servername*è di tipo sysname.  
  
 @azure_databasename = *@azure_databasename*  
 Specifica il nome del database di Azure che contiene i dati remoti. *@azure_databasename*è di tipo sysname.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o >0 (esito negativo)  
  
## <a name="permissions"></a>Permissions  
 Richiede autorizzazioni db_owner.  
  
## <a name="remarks"></a>Osservazioni  
 Quando si esegue [sp_rda_reauthorize_db (Transact-SQL)](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md) per riconnettersi al database Azure remoto, questa operazione reimposta automaticamente la modalità query LOCAL_AND_REMOTE, ovvero il comportamento predefinito per l'estensione Database. Ovvero, le query restituiscono risultati dai dati locali e remoti.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente consente di ripristinare la connessione autenticata tra un database locale abilitato per l'estensione e il database remoto. Effettua una copia dei dati remoti (scelta consigliati) e si connette alla nuova copia.  
  
```tsql  
DECLARE @credentialName nvarchar(128);   
SET @credentialName = N'<existing_database_scoped_credential_name>';   
EXEC sp_rda_reauthorize_db @credential = @credentialName, @with_copy = 1;  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Sys. sp_rda_deauthorize_db &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-deauthorize-db-transact-sql.md)   
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
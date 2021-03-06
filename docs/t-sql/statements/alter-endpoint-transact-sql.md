---
title: ALTER ENDPOINT (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ALTER ENDPOINT
- ALTER_ENDPOINT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER ENDPOINT statement
- modifying endpoints
- endpoints [SQL Server], modifying
ms.assetid: 70f35566-30cf-47c6-8394-dfe5d71629d3
caps.latest.revision: 56
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 972788ef2369c8b885e9c736b2b2e71ebc89470c
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/04/2018
ms.locfileid: "37787732"
---
# <a name="alter-endpoint-transact-sql"></a>ALTER ENDPOINT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  Consente di modificare un endpoint esistente tramite:  
  
-   L'aggiunta di un nuovo metodo a un endpoint esistente.  
  
-   La modifica o l'eliminazione di un metodo esistente dall'endpoint.  
  
-   La modifica delle proprietà di un endpoint.  
  
> [!NOTE]  
>  In questo argomento vengono descritti la sintassi e gli argomenti specifici dell'istruzione ALTER ENDPOINT. Per le descrizioni degli argomenti comuni sia a CREATE ENDPOINT che a ALTER ENDPOINT, vedere [CREATE ENDPOINT &#40;Transact-SQL&#41;](../../t-sql/statements/create-endpoint-transact-sql.md).  
  
 I servizi Web XML nativi (endpoint SOAP/HTTP) verranno eliminati a partire da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
ALTER ENDPOINT endPointName [ AUTHORIZATION login ]  
[ STATE = { STARTED | STOPPED | DISABLED } ]  
[ AS { TCP } ( <protocol_specific_items> ) ]  
[ FOR { TSQL | SERVICE_BROKER | DATABASE_MIRRORING } (  
   <language_specific_items>  
        ) ]  
  
<AS TCP_protocol_specific_arguments> ::=  
AS TCP (  
  LISTENER_PORT = listenerPort  
  [ [ , ] LISTENER_IP = ALL | ( 4-part-ip ) | ( "ip_address_v6" ) ]  
)  
<FOR SERVICE_BROKER_language_specific_arguments> ::=  
FOR SERVICE_BROKER (  
   [ AUTHENTICATION = {   
      WINDOWS [ { NTLM | KERBEROS | NEGOTIATE } ]  
      | CERTIFICATE certificate_name   
      | WINDOWS [ { NTLM | KERBEROS | NEGOTIATE } ] CERTIFICATE certificate_name   
      | CERTIFICATE certificate_name WINDOWS [ { NTLM | KERBEROS | NEGOTIATE } ]   
    } ]  
   [ , ENCRYPTION = { DISABLED   
       |   
         {{SUPPORTED | REQUIRED }   
       [ ALGORITHM { RC4 | AES | AES RC4 | RC4 AES } ] }   
   ]  
  
  [ , MESSAGE_FORWARDING = {ENABLED | DISABLED} ]  
  [ , MESSAGE_FORWARD_SIZE = forwardSize  
)  
  
<FOR DATABASE_MIRRORING_language_specific_arguments> ::=  
FOR DATABASE_MIRRORING (  
   [ AUTHENTICATION = {   
      WINDOWS [ { NTLM | KERBEROS | NEGOTIATE } ]  
      | CERTIFICATE certificate_name   
      | WINDOWS [ { NTLM | KERBEROS | NEGOTIATE } ] CERTIFICATE certificate_name   
      | CERTIFICATE certificate_name WINDOWS [ { NTLM | KERBEROS | NEGOTIATE } ]   
    } ]  
   [ , ENCRYPTION = { DISABLED   
       |   
         {{SUPPORTED | REQUIRED }   
       [ ALGORITHM { RC4 | AES | AES RC4 | RC4 AES } ] }   
    ]   
   [ , ] ROLE = { WITNESS | PARTNER | ALL }  
)  
  
```  
  
## <a name="arguments"></a>Argomenti  
  
> [!NOTE]  
>  Gli argomenti seguenti sono specifici dell'istruzione ALTER ENDPOINT. Per una descrizione degli altri argomenti, vedere [CREATE ENDPOINT &#40;Transact-SQL&#41;](../../t-sql/statements/create-endpoint-transact-sql.md).  
  
 **AS** { **TCP** }  
 Non è possibile modificare il protocollo di trasporto con **ALTER ENDPOINT**.  
  
 **AUTHORIZATION** *login*  
 L'opzione **AUTHORIZATION** non è disponibile in **ALTER ENDPOINT**. La proprietà può essere assegnata solo quando l'endpoint viene creato.  
  
 **FOR** { **TSQL** | **SERVICE_BROKER** | **DATABASE_MIRRORING** }  
 Non è possibile modificare il tipo di payload con **ALTER ENDPOINT**.  
  
## <a name="remarks"></a>Remarks  
 Se si utilizza ALTER ENDPOINT, specificare solo i parametri che si desidera aggiornare. Tutte le proprietà di un endpoint esistente rimangono invariate a meno che non vengano modificate in modo esplicito.  
  
 Non è possibile eseguire le istruzioni ENDPOINT DDL all'interno di una transazione utente.  
  
 Per informazioni sulla scelta di un algoritmo di crittografia da usare con un endpoint, vedere [Scelta di un algoritmo di crittografia](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md).  
  
> [!NOTE]  
>  L'algoritmo RC4 è supportato solo per motivi di compatibilità con le versioni precedenti. È possibile crittografare il nuovo materiale usando RC4 o RC4_128 solo quando il livello di compatibilità del database è 90 o 100. (Non consigliato.) Usare un algoritmo più recente, ad esempio uno degli algoritmi AES. In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] e versioni successive il materiale crittografato utilizzando RC4 o RC4_128 può essere decrittografato in qualsiasi livello di compatibilità.  
>   
>  RC4 è un algoritmo relativamente vulnerabile, mentre AES costituisce un algoritmo relativamente avanzato ma notevolmente più lento rispetto a RC4. Se la sicurezza ha una priorità superiore rispetto alla velocità, è consigliabile utilizzare AES.  
  
## <a name="permissions"></a>Autorizzazioni  
 L'utente deve essere membro del ruolo predefinito del server **sysadmin**, proprietario dell'endpoint oppure disporre dell'autorizzazione ALTER ANY ENDPOINT.  
  
 Per modificare la proprietà di un endpoint esistente, è necessario utilizzare l'autorizzazione ALTER AUTHORIZATION. Per altre informazioni, vedere [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-authorization-transact-sql.md).  
  
 Per altre informazioni, vedere [GRANT - autorizzazioni per endpoint &#40;Transact-SQL&#41;](../../t-sql/statements/grant-endpoint-permissions-transact-sql.md).  
  
## <a name="see-also"></a>Vedere anche  
 [DROP ENDPOINT &#40;Transact-SQL&#41;](../../t-sql/statements/drop-endpoint-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  

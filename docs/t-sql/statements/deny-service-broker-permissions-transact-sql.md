---
title: DENY - autorizzazioni per Service Broker (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/09/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- denying permissions [Service Broker]
- routes [Service Broker], permissions
- Service Broker, permissions
- DENY statement, Service Broker
- remote service bindings [Service Broker], permissions
- permissions [Service Broker]
- message types [Service Broker], permissions
- denying permissions [SQL Server], Service Broker
- contracts [Service Broker], permissions
- services [Service Broker], permissions
ms.assetid: 7c6de71b-865c-41db-9413-ad9b3562e579
caps.latest.revision: 22
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: c5553d6a7ea1f1dc7f241c8e2361e80a601dd706
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/04/2018
ms.locfileid: "37785662"
---
# <a name="deny-service-broker-permissions-transact-sql"></a>DENY (autorizzazioni di Service Broker) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Nega le autorizzazioni per un contratto, un tipo di messaggio, un'associazione al servizio remoto, una route o un servizio di [!INCLUDE[ssSB](../../includes/sssb-md.md)].  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
DENY permission  [ ,...n ] ON  
    {    
       [ CONTRACT :: contract_name ]   
       | [ MESSAGE TYPE :: message_type_name ]    
       | [ REMOTE SERVICE BINDING :: remote_binding_name ]    
       | [ ROUTE :: route_name ]   
       | [ SERVICE :: service_name ]      
        }  
    TO database_principal [ ,...n ]   
    [ CASCADE ]  
        [ AS denying_principal ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *permission*  
 Specifica un'autorizzazione che può essere negata per un'entità a sicurezza diretta di [!INCLUDE[ssSB](../../includes/sssb-md.md)]. Per un elenco delle autorizzazioni, vedere la sezione Osservazioni di seguito in questo argomento.  
  
 CONTRACT **::***contract_name*  
 Specifica il contratto per il quale viene negata l'autorizzazione. Il qualificatore di ambito **::** è obbligatorio.  
  
 MESSAGE TYPE **::***message_type_name*  
 Specifica il tipo di messaggio per il quale viene negata l'autorizzazione. Il qualificatore di ambito **::** è obbligatorio.  
  
 REMOTE SERVICE BINDING **::***remote_binding_name*  
 Specifica l'associazione al servizio remoto per la quale viene negata l'autorizzazione. Il qualificatore di ambito **::** è obbligatorio.  
  
 ROUTE **::***route_name*  
 Specifica la route per la quale viene negata l'autorizzazione. Il qualificatore di ambito **::** è obbligatorio.  
  
 SERVICE **::***message_type_name*  
 Specifica il servizio per il quale viene negata l'autorizzazione. Il qualificatore di ambito **::** è obbligatorio.  
  
 *database_principal*  
 Specifica l'entità a cui viene negata l'autorizzazione. I tipi validi sono:  
  
-   Utente del database  
-   Ruolo del database  
-   Ruolo applicazione  
-   Utente del database di cui è stato eseguito il mapping a un account di accesso di Windows  
-   Utente del database di cui è stato eseguito il mapping a un gruppo di Windows  
-   Utente del database di cui è stato eseguito il mapping a un certificato  
-   Utente del database di cui è stato eseguito il mapping a una chiave asimmetrica  
-   Utente del database sul quale non viene eseguito il mapping ad alcuna entità server  
  
CASCADE  
 Indica che l'autorizzazione negata viene negata anche ad altre entità alle quali è stata concessa da questa entità.  
  
*denying_principal*  
 Specifica un'entità dalla quale l'entità che esegue la query ottiene il diritto di negare l'autorizzazione. I tipi validi sono:  
  
-   Utente del database  
-   Ruolo del database  
-   Ruolo applicazione  
-   Utente del database di cui è stato eseguito il mapping a un account di accesso di Windows  
-   Utente del database di cui è stato eseguito il mapping a un gruppo di Windows  
-   Utente del database di cui è stato eseguito il mapping a un certificato  
-   Utente del database di cui è stato eseguito il mapping a una chiave asimmetrica  
-   Utente del database sul quale non viene eseguito il mapping ad alcuna entità server  
  
## <a name="remarks"></a>Remarks  
  
## <a name="service-broker-contracts"></a>Contratti di Service Broker  
 Un contratto di [!INCLUDE[ssSB](../../includes/sssb-md.md)] è un'entità a sicurezza diretta a livello di database contenuta nel database padre nella gerarchia di autorizzazioni. Nella tabella seguente sono elencate le autorizzazioni più specifiche e limitate che possono essere negate per un contratto di [!INCLUDE[ssSB](../../includes/sssb-md.md)] assieme alle autorizzazioni più generali incluse in modo implicito.  
  
|Autorizzazione del contratto di Service Broker|Autorizzazione del contratto di Service Broker in cui è inclusa|Autorizzazione del database in cui è inclusa|  
|----------------------------------------|---------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY CONTRACT|  
|REFERENCES|CONTROL|REFERENCES|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="service-broker-message-types"></a>Tipi di messaggio di Service Broker  
 Un tipo di messaggio di [!INCLUDE[ssSB](../../includes/sssb-md.md)] è un'entità a sicurezza diretta a livello di database contenuta nel database padre nella gerarchia di autorizzazioni. Nella tabella seguente sono elencate le autorizzazioni più specifiche e limitate che possono essere negate per un tipo di messaggio di [!INCLUDE[ssSB](../../includes/sssb-md.md)] assieme alle autorizzazioni più generali incluse in modo implicito.  
  
|Autorizzazione del tipo di messaggio di Service Broker|Autorizzazione del tipo di messaggio di Service Broker in cui è inclusa|Autorizzazione del database in cui è inclusa|  
|--------------------------------------------|-------------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY MESSAGE TYPE|  
|REFERENCES|CONTROL|REFERENCES|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="service-broker-remote-service-bindings"></a>Associazioni ai servizi remoti di Service Broker  
 Un'associazione al servizio remoto di [!INCLUDE[ssSB](../../includes/sssb-md.md)] è un'entità a sicurezza diretta a livello di database contenuta nel database padre nella gerarchia di autorizzazioni. Nella tabella seguente sono elencate le autorizzazioni più specifiche e limitate che possono essere negate per un'associazione al servizio remoto di [!INCLUDE[ssSB](../../includes/sssb-md.md)] assieme alle autorizzazioni più generali incluse in modo implicito.  
  
|Autorizzazione dell'associazione al servizio remoto di Service Broker|Autorizzazione dell'associazione al servizio remoto di Service Broker in cui è inclusa|Autorizzazione del database in cui è inclusa|  
|------------------------------------------------------|-----------------------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY REMOTE SERVICE BINDING|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="service-broker-routes"></a>Route di Service Broker  
 Una route di [!INCLUDE[ssSB](../../includes/sssb-md.md)] è un'entità a sicurezza diretta a livello di database contenuta nel database padre nella gerarchia di autorizzazioni. Nella tabella seguente sono elencate le autorizzazioni più specifiche e limitate che possono essere negate per una route di [!INCLUDE[ssSB](../../includes/sssb-md.md)] assieme alle autorizzazioni più generali incluse in modo implicito.  
  
|Autorizzazione della route di Service Broker|Autorizzazione della route di Service Broker in cui è inclusa|Autorizzazione del database in cui è inclusa|  
|-------------------------------------|------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY ROUTE|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
### <a name="service-broker-services"></a>Servizi di Service Broker  
 Un servizio di [!INCLUDE[ssSB](../../includes/sssb-md.md)] è un'entità a sicurezza diretta a livello di database contenuta nel database padre nella gerarchia di autorizzazioni. Nella tabella seguente sono elencate le autorizzazioni più specifiche e limitate che possono essere negate per un servizio di [!INCLUDE[ssSB](../../includes/sssb-md.md)] assieme alle autorizzazioni più generali incluse in modo implicito.  
  
|Autorizzazione del servizio di Service Broker|Autorizzazione del servizio di Service Broker in cui è inclusa|Autorizzazione del database in cui è inclusa|  
|---------------------------------------|--------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|SEND|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY SERVICE|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione CONTROL per il contratto, il tipo di messaggio, l'associazione al servizio remoto, la route o il servizio di [!INCLUDE[ssSB](../../includes/sssb-md.md)]. Se si utilizza la clausola AS, l'entità specificata deve essere proprietaria dell'entità a protezione diretta per cui vengono negate le autorizzazioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Entità &#40;motore di database&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [REVOKE - autorizzazioni per Service Broker &#40;Transact-SQL&#41;](../../t-sql/statements/revoke-service-broker-permissions-transact-sql.md)   
 [DENY &#40;Transact-SQL&#41;](../../t-sql/statements/deny-transact-sql.md)   
 [Autorizzazioni &#40;motore di database&#41;](../../relational-databases/security/permissions-database-engine.md)  
  
  

---
title: sp_enumcustomresolvers (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_enumcustomresolvers
- sp_enumcustomresolvers_TSQL
helpviewer_keywords:
- sp_enumcustomresolvers
ms.assetid: 81bd0d3a-48dc-42b1-b662-c630f61fc630
caps.latest.revision: 22
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: eb49ae55f4bde2304713f4fd336076585a987904
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32993158"
---
# <a name="spenumcustomresolvers-transact-sql"></a>sp_enumcustomresolvers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce l'elenco di tutti i gestori della logica di business e i sistemi di risoluzione personalizzati disponibili registrati nel server di distribuzione. Questa stored procedure viene eseguita in qualsiasi database del server di pubblicazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_enumcustomresolvers [ [ @distributor =] 'distributor']  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@distributor =**] **'***distributore***'**  
 Nome del server di distribuzione che include il sistema di risoluzione personalizzato. *server di distribuzione* viene **sysname**, con un valore predefinito è NULL. *Questo parametro è deprecato e verrà rimossa in una versione futura.*  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**article_resolver**|**nvarchar(255)**|Nome descrittivo del gestore della logica di business o del sistema di risoluzione dei conflitti.|  
|**resolver_clsid**|**nvarchar(50)**|ID classe (CLSID) del sistema di risoluzione basato su COM. Per un gestore della logica di business, questa colonna restituisce un valore di CLSID pari a zero.|  
|**is_dotnet_assembly**|**bit**|Indica se la registrazione viene eseguita per un gestore della logica di business.<br /><br /> **0** = sistema di risoluzione dei conflitti basato su COM<br /><br /> **1** = gestore della logica di business|  
|**dotnet_assembly_name**|**nvarchar(255)**|Nome dell'assembly [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework che implementa il gestore della logica di business.|  
|**dotnet_class_name**|**nvarchar(255)**|Nome della classe che sostituisce <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> per implementare il gestore della logica di business.|  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_enumcustomresolvers** viene utilizzata nella replica di tipo merge.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server e **db_owner** ruolo predefinito del database possono eseguire **sp_enumcustomresolvers**.  
  
## <a name="see-also"></a>Vedere anche  
 [Implementare un gestore della logica di business per un articolo di merge](../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md)   
 [Implementare un sistema di risoluzione dei conflitti personalizzato per un articolo di tipo merge](../../relational-databases/replication/implement-a-custom-conflict-resolver-for-a-merge-article.md)   
 [sp_lookupcustomresolver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-lookupcustomresolver-transact-sql.md)   
 [sp_unregistercustomresolver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-unregistercustomresolver-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

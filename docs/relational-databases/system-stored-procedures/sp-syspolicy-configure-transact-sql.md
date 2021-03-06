---
title: sp_syspolicy_configure (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_syspolicy_configure
- sp_syspolicy_configure_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syspolicy_configure
ms.assetid: 70c10922-9345-4190-ba69-808a43f760da
caps.latest.revision: 8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c51d30c8453cd5a9c2a92a3eb2ad22016c461b8f
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33255935"
---
# <a name="spsyspolicyconfigure-transact-sql"></a>sp_syspolicy_configure (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Configura le impostazioni della gestione basata su criteri, ad esempio se la stessa è abilitata.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_syspolicy_configure [ @name = ] 'name'  
    , [ @value = ] value  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@name =** ] **'***nome***'**  
 Nome dell'impostazione che si desidera configurare. *nome* viene **sysname**, è necessario e non può essere NULL o una stringa vuota.  
  
 *nome* può essere uno dei valori seguenti:  
  
-   'Enabled' - Determina se la gestione basata su criteri è abilitata.  
  
-   'HistoryRetentionInDays' - Specifica il numero di giorni di conservazione della cronologia di valutazione dei criteri. Se il valore è pari a 0, la cronologia non verrà rimossa automaticamente.  
  
-   'LogOnSuccess' - Specifica se vengono registrate le valutazioni di criteri riuscite nella gestione basata su criteri.  
  
 [  **@value =** ] *valore*  
 È il valore è associato il valore specificato per *nome*. *valore* viene **sql_variant**ed è obbligatorio.  
  
-   Se si specifica 'Enabled' per *nome*, è possibile utilizzare uno dei valori seguenti:  
  
    -   0 = Disabilita la gestione basata su criteri.  
  
    -   1 = Abilita la gestione basata su criteri.  
  
-   Se viene specificato 'HistoryRententionInDays' per *nome*, specificare il numero di giorni come valore intero.  
  
-   Se si specifica 'LogOnSuccess' per *nome*, è possibile utilizzare uno dei valori seguenti:  
  
    -   0 = Registra solo le valutazioni di criteri non riuscite.  
  
    -   1 = Registra sia le valutazioni di criteri riuscite che quelle fallite.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 È necessario eseguire sp_syspolicy_configure nel contesto del database di sistema msdb.  
  
 Per visualizzare i valori impostati attualmente, eseguire una query sulla vista di sistema msdb.dbo.syspolicy_configuration.  
  
## <a name="permissions"></a>Autorizzazioni  
 È necessaria l'appartenenza al ruolo predefinito del database PolicyAdministratorRole.  
  
> [!IMPORTANT]  
>  Possibile elevazione di credenziali: gli utenti nel ruolo PolicyAdministratorRole possono creare trigger server e pianificare le esecuzioni di criteri che influiscono sul funzionamento dell'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Gli utenti con il ruolo PolicyAdministratorRole possono ad esempio creare criteri che impediscono la creazione della maggior parte degli oggetti nel [!INCLUDE[ssDE](../../includes/ssde-md.md)]. A causa di questa possibile elevazione di credenziali, il ruolo PolicyAdministratorRole deve essere concesso solo a utenti ritenuti attendibili per il controllo della configurazione del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene abilitata la gestione basata su criteri.  
  
```  
EXEC msdb.dbo.sp_syspolicy_configure @name = N'Enabled'  
, @value = 1;  
  
GO  
```  
  
 Nell'esempio seguente viene impostato un periodo di memorizzazione cronologia criteri di 14 giorni.  
  
```  
EXEC msdb.dbo.sp_syspolicy_configure @name = N'HistoryRetentionInDays'  
, @value = 14;  
  
GO  
```  
  
 Nell'esempio seguente viene configurata la registrazione sia delle valutazioni di criteri riuscite che di quelle non riuscite nella gestione basata su criteri.  
  
```  
EXEC msdb.dbo.sp_syspolicy_configure @name = N'LogOnSuccess'  
, @value = 1;  
  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure della gestione basata su criteri &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)   
 [sp_syspolicy_set_config_enabled &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-set-config-enabled-transact-sql.md)   
 [sp_syspolicy_set_config_history_retention &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-set-config-history-retention-transact-sql.md)   
 [sp_syspolicy_set_log_on_success &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-set-log-on-success-transact-sql.md)  
  
  

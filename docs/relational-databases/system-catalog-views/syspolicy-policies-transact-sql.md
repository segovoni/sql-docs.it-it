---
title: syspolicy_policies (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- syspolicy_policies_TSQL
- syspolicy_policies
dev_langs:
- TSQL
helpviewer_keywords:
- syspolicy_policies view
ms.assetid: aecf35bb-187e-4f80-870f-48081b88974e
caps.latest.revision: 25
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5c05a24d94ba5b65eff8c3aec2791c9993b99589
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33221502"
---
# <a name="syspolicypolicies-transact-sql"></a>syspolicy_policies (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Visualizza una riga per ogni criterio della gestione basata su criteri nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. syspolicy_policies è lo schema dbo nel database msdb. Nella tabella seguente vengono descritte le colonne contenute nella vista syspolicy_policies.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|policy_id|**int**|Identificatore dei criteri.|  
|name|**sysname**|Nome dei criteri.|  
|condition_id|**int**|ID della condizione applicata o testata da questi criteri.|  
|root_condition_id|**int**|Solo per uso interno.|  
|date_created|**datetime**|Data e ora di creazione dei criteri.|  
|execution_mode|**int**|Modalità di valutazione per i criteri. Sono disponibili i valori seguenti:<br /><br /> 0 = Su richiesta<br /><br /> Questa modalità consente di valutare i criteri quando questi vengono specificati direttamente dall'utente.<br /><br /> 1 = Su modifica: impedisci esecuzione<br /><br /> Questa modalità automatica utilizza trigger DDL per impedire violazioni dei criteri.<br /><br /> 2 = Su modifica: solo log<br /><br /> Questa modalità automatica utilizza la notifica degli eventi per valutare i criteri quando viene apportata una modifica rilevante e consente di registrare le violazioni dei criteri.<br /><br /> 4 = Su pianificazione<br /><br /> Questa modalità automatica utilizza un processo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent per valutare periodicamente i criteri e consente di registrare le violazioni dei criteri.<br /><br /> Nota: Il valore 3 non è un valore possibile.|  
|policy_category|**int**|ID della categoria di criteri della gestione basata su criteri cui appartengono i criteri. Se il valore è NULL; viene utilizzato il gruppo di criteri predefinito.|  
|schedule_uid|**uniqueidentifier**|Quando il valore di execution_mode è Su pianificazione, contiene l'ID della pianificazione; in caso contrario, il valore è NULL.|  
|description|**nvarchar(max)**|Descrizione dei criteri. La colonna della descrizione è facoltativa e il valore può essere NULL.|  
|help_text|**nvarchar(4000)**|Testo del collegamento ipertestuale di proprietà di help_link.|  
|help_link|**nvarchar(2083)**|Collegamento ipertestuale aggiuntivo della guida assegnato ai criteri dall'autore dei criteri.|  
|object_set_id|**int**|ID del set di oggetti valutato dai criteri.|  
|is_enabled|**bit**|Indica se i criteri sono attualmente abilitati (1) o disabilitati (0).|  
|job_id|**uniqueidentifier**|Quando il valore di execution_mode è Su pianificazione, contiene l'ID del processo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent che esegue i criteri.|  
|created_by|**sysname**|Account di accesso che ha creato i criteri.|  
|modified_by|**sysname**|Account di accesso che ha modificato i criteri per ultimo. NULL se non sono state apportate modifiche.|  
|date_modified|**datetime**|Data e ora di creazione dei criteri. NULL se non sono state apportate modifiche.|  
  
## <a name="remarks"></a>Osservazioni  
 Durante la risoluzione di gestione basata su criteri, eseguire una query di [syspolicy_conditions](../../relational-databases/system-catalog-views/syspolicy-conditions-transact-sql.md) vista per determinare se il criterio è abilitato. In questa vista viene inoltre visualizzato l'utente che ha creato o modificato per ultimo i criteri.  
  
## <a name="permissions"></a>Autorizzazioni  
 È necessaria l'appartenenza al ruolo PolicyAdministratorRole nel database msdb.  
  
## <a name="see-also"></a>Vedere anche  
 [Amministrazione di server tramite la gestione basata su criteri](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [Viste di Gestione basata su criteri &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  

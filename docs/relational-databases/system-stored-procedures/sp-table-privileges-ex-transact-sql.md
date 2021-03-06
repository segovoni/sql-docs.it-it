---
title: sp_table_privileges_ex (Transact-SQL) | Documenti Microsoft
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
- sp_table_privileges_ex
- sp_table_privileges_ex_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_table_privileges_ex
ms.assetid: b58d4a07-5c40-4f17-b66e-6d6b17188dda
caps.latest.revision: 33
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: fc97335ccb0e014e130a2f47c70f480dd7c23554
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33259997"
---
# <a name="sptableprivilegesex-transact-sql"></a>sp_table_privileges_ex (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce informazioni sui privilegi per la tabella specificata nel server collegato specificato.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_table_privileges_ex [ @table_server = ] 'table_server'   
     [ , [ @table_name = ] 'table_name' ]   
     [ , [ @table_schema = ] 'table_schema' ]   
     [ , [ @table_catalog = ] 'table_catalog' ]  
     [ , [@fUsePattern =] 'fUsePattern']  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@table_server =** ] **'***table_server***'**  
 Nome del server collegato per cui si desidera restituire le informazioni. *table_server* viene **sysname**, non prevede alcun valore predefinito.  
  
 [  **@table_name =** ] **'***table_name***'**]  
 Nome della tabella per cui si desidera ottenere informazioni sui privilegi assegnati. *TABLE_NAME* viene **sysname**, con un valore predefinito è NULL.  
  
 [  **@table_schema =** ] **'***table_schema***'**  
 Schema della tabella. In alcuni ambienti DBMS corrisponde al proprietario della tabella. *TABLE_SCHEMA* viene **sysname**, con un valore predefinito è NULL.  
  
 [  **@table_catalog =** ] **'***table_catalog***'**  
 Il nome del database in cui è specificato *table_name* risiede. *TABLE_CATALOG* viene **sysname**, con un valore predefinito è NULL.  
  
 [  **@fUsePattern =**] **'***fUsePattern***'**  
 Determina se i caratteri '_', '%', '[', e ']' vengono interpretati come caratteri jolly. I valori validi sono 0 (utilizzo dei criteri di ricerca disattivato) e 1 (utilizzo dei criteri di ricerca attivato). *fUsePattern* viene **bit**, con un valore predefinito è 1.  
  
## <a name="return-code-values"></a>Valori restituiti  
 Nessuno  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**TABLE_CAT**|**sysname**|Nome del qualificatore della tabella. Vari prodotti DBMS supportano nomi in tre parti per le tabelle (*qualificatore ***.*** proprietario ***.*** nome*). In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] questa colonna rappresenta il nome del database. In altri prodotti rappresenta il nome del server dell'ambiente di database della tabella. Questo campo può essere NULL.|  
|**TABLE_SCHEM**|**sysname**|Nome del proprietario della tabella. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] questa colonna rappresenta il nome dell'utente del database che ha creato la tabella. Questo campo restituisce sempre un valore.|  
|**TABLE_NAME**|**sysname**|Nome della tabella. Questo campo restituisce sempre un valore.|  
|**GRANTOR**|**sysname**|Nome utente di database che ha concesso autorizzazioni al **TABLE_NAME** per la tabella **utente autorizzato**. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], questa colonna è sempre lo stesso come il **TABLE_OWNER**. Questo campo restituisce sempre un valore. Inoltre, la colonna GRANTOR può rappresentare il proprietario del database (**TABLE_OWNER**) o un utente a cui il proprietario del database concesso autorizzazioni tramite la clausola WITH GRANT OPTION dell'istruzione GRANT.|  
|**UTENTE AUTORIZZATO**|**sysname**|Nome utente di database che ha concesso autorizzazioni al **TABLE_NAME** da elencato **GRANTOR**. Questo campo restituisce sempre un valore.|  
|**CON PRIVILEGI**|**varchar (** 32 **)**|Una delle autorizzazioni di tabella disponibili. I possibili valori delle autorizzazioni di tabella sono i seguenti. È inoltre possibile utilizzare altri valori supportati dall'origine dei dati al momento della definizione dell'implementazione.<br /><br /> Selezionare = **utente autorizzato** può recuperare dati per uno o più colonne.<br /><br /> INSERT = **utente autorizzato** può fornire dati per le nuove righe per uno o più colonne.<br /><br /> UPDATE = **utente autorizzato** può modificare i dati per uno o più colonne.<br /><br /> ELIMINARE = **utente autorizzato** può rimuovere righe dalla tabella.<br /><br /> RIFERIMENTI = **utente autorizzato** possono fare riferimento a una colonna in una tabella esterna in una relazione chiave primaria/esterna chiave. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le relazioni tra chiave primaria e chiave esterna vengono definite tramite l'utilizzo di vincoli di tabella.<br /><br /> L'ambito di azione ottenuto il **utente autorizzato** da una tabella specifica privilegio è dipendente dall'origine dati. Ad esempio, l'autorizzazione UPDATE è stato possibile abilitare il **utente autorizzato** per aggiornare tutte le colonne di una tabella in un'origine dati e solo le colonne per cui il **GRANTOR** dispone di autorizzazioni per un'altra origine dati.|  
|**IS_GRANTABLE**|**varchar (** 3 **)**|Indica se il **utente autorizzato** può concedere autorizzazioni ad altri utenti. Questa autorizzazione spesso viene denominata "autorizzazione per la concessione di autorizzazioni". I possibili valori sono YES, NO e NULL. Il valore sconosciuto, o NULL, indica un'origine dei dati per la quale l'autorizzazione per la concessione di autorizzazioni non è applicabile.|  
  
## <a name="remarks"></a>Osservazioni  
 I risultati restituiti vengono ordinati in base **TABLE_QUALIFIER**, **TABLE_OWNER**, **TABLE_NAME**, e **PRIVILEGIO**.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione SELECT per lo schema.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono restituite informazioni sui privilegi per le tabelle il cui nome inizia con `Product` incluse nel database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] disponibile nel server collegato `Seattle1`. In questo esempio si presuppone che il server collegato esegua [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
EXEC sp_table_privileges_ex @table_server = 'Seattle1',   
   @table_name = 'Product%',   
   @table_schema = 'Production',  
   @table_catalog ='AdventureWorks2012';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_column_privileges_ex &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-column-privileges-ex-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Distributed query Stored procedure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/distributed-queries-stored-procedures-transact-sql.md)  
  
  

---
title: sp_help_downloadlist (Transact-SQL) | Documenti Microsoft
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
- sp_help_downloadlist_TSQL
- sp_help_downloadlist
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_downloadlist
ms.assetid: 745b265b-86e8-4399-b928-c6969ca1a2c8
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e48423bc91413518abe3002a3c3d8da2cef330c2
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33260334"
---
# <a name="sphelpdownloadlist-transact-sql"></a>sp_help_downloadlist (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Elenca tutte le righe di **sysdownloadlist** tabella di sistema per il processo specificato oppure tutte le righe se viene specificato alcun processo.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_help_downloadlist { [ @job_id = ] job_id | [ @job_name = ] 'job_name' }   
     [ , [ @operation = ] 'operation' ]   
     [ , [ @object_type = ] 'object_type' ]   
     [ , [ @object_name = ] 'object_name' ]   
     [ , [ @target_server = ] 'target_server' ]   
     [ , [ @has_error = ] has_error ]   
     [ , [ @status = ] status ]   
     [ , [ @date_posted = ] date_posted ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@job_id=** ] *job_id*  
 ID del processo per il quale devono essere restituite informazioni. *job_id* viene **uniqueidentifier**, con un valore predefinito è NULL.  
  
 [ **@job_name=** ] **'***job_name***'**  
 Nome del processo. *job_name* viene **sysname**, con un valore predefinito è NULL.  
  
> [!NOTE]  
>  Entrambi *job_id* o *job_name* devono essere specificati, ma non è possibile specificarli entrambi.  
  
 [  **@operation=** ] **'***operazione***'**  
 Operazione valida per il processo specificato. *operazione* viene **varchar(64)**, con un valore predefinito è NULL, e può essere uno dei valori seguenti.  
  
|Value|Description|  
|-----------|-----------------|  
|**ERRORE**|Operazione server che richiede l'esclusione del server di destinazione dal Master **SQLServerAgent** servizio.|  
|**DELETE**|Operazione del processo che rimuove un intero processo.|  
|**INSERT**|Operazione del processo che inserisce un intero processo o ne aggiorna uno esistente. Include tutti i passaggi e le pianificazioni del processo, se applicabile.|  
|**REINTEGRARE**|Operazione del server con cui viene attivato il rinvio delle informazioni di integrazione del server di destinazione, tra cui l'intervallo di polling e il fuso orario per il dominio multiserver. Il server di destinazione redownloads anche il **MSXOperator** dettagli.|  
|**SET-POLL**|Operazione del server con cui viene impostato l'intervallo di tempo in secondi per il polling del dominio multiserver eseguito dai server di destinazione. Se specificato, *valore* viene interpretato come valore di intervallo obbligatorio e può essere un valore da **10** a **28.800**.|  
|**INIZIO**|Operazione del processo con cui viene richiesto l'avvio dell'esecuzione del processo.|  
|**ARRESTA**|Operazione del processo con cui viene richiesto l'arresto dell'esecuzione del processo.|  
|**ORA DI SINCRONIZZAZIONE**|Operazione del server con cui viene attivata la sincronizzazione del clock di sistema dei server di destinazione con il clock di sistema del dominio multiserver. Si tratta di un'operazione onerosa ed è pertanto consigliabile non eseguirla di frequente.|  
|**UPDATE**|Operazione di aggiornamento solo del processo di **sysjobs** informazioni per un processo, non i passaggi di processo o pianificazioni. Viene chiamato automaticamente da **sp_update_job**.|  
  
 [  **@object_type=** ] **'***object_type***'**  
 Tipo di oggetto per il processo specificato. *object_type* viene **varchar(64)**, con un valore predefinito è NULL. *object_type* può essere JOB o SERVER. Per ulteriori informazioni su valido *object_type*valori, vedere [sp_add_category &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-category-transact-sql.md).  
  
 [  **@object_name=** ] **'***object_name***'**  
 Nome dell'oggetto . *object_name* viene **sysname**, con un valore predefinito è NULL. Se *object_type* è JOB, *object_name*è il nome del processo. Se *object_type*è SERVER, *object_name*è il nome del server.  
  
 [ **@target_server=** ] **'***target_server***'**  
 Nome del server di destinazione. *target_server* viene **nvarchar (128)**, con un valore predefinito è NULL.  
  
 [  **@has_error=** ] *has_error*  
 Specifica se il processo deve segnalare o meno gli errori. *has_error* viene **tinyint**, con un valore predefinito è NULL, che indica gli errori non devono essere segnalati. **1** indica che tutti gli errori devono essere segnalati.  
  
 [  **@status=** ] *stato*  
 Stato per il processo. *lo stato* viene **tinyint**, con valore predefinito è NULL.  
  
 [  **@date_posted=** ] *partire*  
 Valore di data e ora. Nel set di risultati verranno incluse tutte le voci create a partire dalla data e ora specificate. *partire* viene **datetime**, con un valore predefinito è NULL.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**instance_id**|**int**|Numero di identificazione univoco integer dell'istruzione.|  
|**source_server**|**nvarchar(30)**|Nome di computer del server da cui viene inviata l'istruzione. In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versione 7.0, è sempre il nome del computer del server master (MSX).|  
|**operation_code**|**nvarchar(4000)**|Codice di operazione dell'istruzione.|  
|**object_name**|**sysname**|Oggetto su cui viene eseguita l'istruzione.|  
|**object_id**|**uniqueidentifier**|Numero di identificazione dell'oggetto interessato dall'istruzione (**job_id** per un oggetto processo o 0x00 per un oggetto server) o un valore di dati specifico di **operation_code**.|  
|**target_server**|**nvarchar(30)**|Server di destinazione in cui deve essere eseguito il download dell'istruzione.|  
|**error_message**|**nvarchar(1024)**|Eventuale messaggio di errore inviato dal server di destinazione se si verifica un problema durante l'elaborazione dell'istruzione.<br /><br /> Nota: I blocchi di messaggio di errore tutte le ulteriori operazioni di download dal server di destinazione.|  
|**date_posted**|**datetime**|Data di inserimento dell'istruzione nella tabella.|  
|**date_downloaded**|**datetime**|Data di download dell'istruzione nel server di destinazione.|  
|**status**|**tinyint**|Stato del processo:<br /><br /> **0** = non ancora scaricato<br /><br /> **1** = scaricato correttamente.|  
  
## <a name="permissions"></a>Autorizzazioni  
 Le autorizzazioni di esecuzione per questa procedura vengono assegnate per impostazione predefinita ai membri del ruolo predefinito del server **sysadmin** .  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene visualizzato un elenco di righe in `sysdownloadlist` per il processo `NightlyBackups`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_downloadlist  
    @job_name = N'NightlyBackups',  
    @operation = N'UPDATE',   
    @object_type = N'JOB',   
    @object_name = N'NightlyBackups',  
    @target_server = N'SEATTLE2',   
    @has_error = 1,   
    @status = NULL,   
    @date_posted = NULL ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

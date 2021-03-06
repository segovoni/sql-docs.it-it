---
title: sp_addmergesubscription (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/16/2017
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
- sp_addmergesubscription_TSQL
- sp_addmergesubscription
helpviewer_keywords:
- sp_addmergesubscription
ms.assetid: a191d817-0132-49ff-93ca-76f13e609b38
caps.latest.revision: 42
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 8d5b8cf744909969166b2d391604735c1a2a7db4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32993668"
---
# <a name="spaddmergesubscription-transact-sql"></a>sp_addmergesubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crea una sottoscrizione push o pull di tipo merge. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_addmergesubscription [ @publication= ] 'publication'  
    [ , [ @subscriber = ] 'subscriber' ]  
    [ , [ @subscriber_db= ] 'subscriber_db' ]  
    [ , [ @subscription_type= ] 'subscription_type' ]  
    [ , [ @subscriber_type= ] 'subscriber_type' ]  
    [ , [ @subscription_priority= ] subscription_priority ]  
    [ , [ @sync_type= ] 'sync_type' ]  
    [ , [ @frequency_type= ] frequency_type ]  
    [ , [ @frequency_interval= ] frequency_interval ]  
    [ , [ @frequency_relative_interval= ] frequency_relative_interval ]  
    [ , [ @frequency_recurrence_factor= ] frequency_recurrence_factor ]  
    [ , [ @frequency_subday= ] frequency_subday ]  
    [ , [ @frequency_subday_interval= ] frequency_subday_interval ]  
    [ , [ @active_start_time_of_day= ] active_start_time_of_day ]  
    [ , [ @active_end_time_of_day= ] active_end_time_of_day ]  
    [ , [ @active_start_date= ] active_start_date ]  
    [ , [ @active_end_date= ] active_end_date ]  
    [ , [ @optional_command_line= ] 'optional_command_line' ]  
    [ , [ @description= ] 'description' ]  
    [ , [ @enabled_for_syncmgr= ] 'enabled_for_syncmgr' ]  
    [ , [ @offloadagent= ] remote_agent_activation]  
    [ , [ @offloadserver= ] 'remote_agent_server_name' ]  
    [ , [ @use_interactive_resolver= ] 'use_interactive_resolver' ]  
    [ , [ @merge_job_name= ] 'merge_job_name' ]  
    [ , [ @hostname = ] 'hostname'  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publication=**] **'***pubblicazione***'**  
 Nome della pubblicazione. *pubblicazione* viene **sysname**, non prevede alcun valore predefinito. È necessario che la pubblicazione esista già.  
  
 [  **@subscriber =**] **'***sottoscrittore***'**  
 Nome del Sottoscrittore. *Sottoscrittore* viene **sysname**, con un valore predefinito è NULL.  
  
 [  **@subscriber_db=**] **'***subscriber_db***'**  
 Nome del database di sottoscrizione. *subscriber_db*viene **sysname**, con un valore predefinito è NULL.  
  
 [  **@subscription_type=**] **'***subscription_type***'**  
 Tipo di sottoscrizione. *subscription_type*viene **nvarchar(15)**, con un valore predefinito è PUSH. Se **push**, viene aggiunta una sottoscrizione push e viene aggiunto l'agente di Merge nel server di distribuzione. Se **pull**, viene aggiunta una sottoscrizione pull senza aggiunta di un agente di Merge nel server di distribuzione.  
  
> [!NOTE]  
>  Con le sottoscrizioni anonime non è necessario utilizzare questa stored procedure.  
  
 [  **@subscriber_type=**] **'***subscriber_type***'**  
 Tipo di Sottoscrittore. *subscriber_type*viene **nvarchar(15)**, e può essere uno dei valori seguenti.  
  
|Value|Description|  
|-----------|-----------------|  
|**locale** (impostazione predefinita)|Sottoscrittore noto solo al server di pubblicazione.|  
|**Globale**|Sottoscrittore noto a tutti i server.|  
  
 In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive le sottoscrizioni locali vengono dette sottoscrizioni client e le sottoscrizioni globali vengono dette sottoscrizioni server.  
  
 [  **@subscription_priority=**] *subscription_priority*  
 Numero che indica il livello di priorità della sottoscrizione. *subscription_priority*viene **reale**, con un valore predefinito è NULL. Per le sottoscrizioni locali e anonime, il livello di priorità è 0.0. Per le sottoscrizioni globali, la priorità deve essere inferiore a 100.0.  
  
 [  **@sync_type=**] **'***sync_type***'**  
 Tipo di sincronizzazione per la sottoscrizione. *sync_type*viene **nvarchar(15)**, il valore predefinito è **automatico**. Può essere **automatica** o **Nessuno**. Se **automatico**, lo schema e i dati iniziali per le tabelle pubblicate vengono trasferiti nel Sottoscrittore prima. Se **Nessuno**, si presuppone il sottoscrittore includa già lo schema e i dati iniziali per le tabelle pubblicate. Le tabelle e i dati di sistema vengono sempre trasferiti.  
  
> [!NOTE]  
>  Si consiglia di non specificare un valore di **Nessuno**.  
  
 [  **@frequency_type=**] *frequency_type*  
 Valore che indica la frequenza con cui viene eseguito l'agente di merge. *frequency_type* viene **int**, e può essere uno dei valori seguenti.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|**1**|Una volta|  
|**4**|Ogni giorno|  
|**8**|Settimanale|  
|**10**|Mensile|  
|**20**|Mensile, in base all'intervallo di frequenza|  
|**40**|All'avvio di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent|  
|NULL (predefinito)||  
  
 [  **@frequency_interval=**] *frequency_interval*  
 Giorno o giorni in cui viene eseguito l'agente di merge. *frequency_interval* viene **int**, e può essere uno dei valori seguenti.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|**1**|Domenica|  
|**2**|Lunedì|  
|**3**|Martedì|  
|**4**|Mercoledì|  
|**5**|Giovedì|  
|**6**|Venerdì|  
|**7**|Sabato|  
|**8**|Day|  
|**9**|Giorni feriali|  
|**10**|Giorni festivi|  
|NULL (predefinito)||  
  
 [  **@frequency_relative_interval=**] *frequency_relative_interval*  
 Occorrenza di merge pianificata dell'intervallo di frequenza per ogni mese. *frequency_relative_interval* viene **int**, e può essere uno dei valori seguenti.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|**1**|Primo|  
|**2**|Secondo|  
|**4**|Terzo|  
|**8**|Quarto|  
|**16**|Ultimo|  
|NULL (predefinito)||  
  
 [  **@frequency_recurrence_factor=**] *frequency_recurrence_factor*  
 Fattore di occorrenza utilizzato da *frequency_type*. *frequency_recurrence_factor*viene **int**, con un valore predefinito è NULL.  
  
 [  **@frequency_subday=**] *frequency_subday*  
 Unità di *frequency_subday_interval*. *frequency_subday* viene **int**, e può essere uno dei valori seguenti.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|**1**|Una volta|  
|**2**|Secondo|  
|**4**|Minuto|  
|**8**|Ora|  
|NULL (predefinito)||  
  
 [  **@frequency_subday_interval=**] *frequency_subday_interval*  
 Frequenza di *frequency_subday* devono intercorrere tra ogni operazione di unione. *frequency_subday_interval* viene **int**, con un valore predefinito è NULL.  
  
 [  **@active_start_time_of_day=**] *active_start_time_of_day*  
 Ora del giorno della prima esecuzione pianificata dell'agente di merge, nel formato HHMMSS. *active_start_time_of_day* viene **int**, con un valore predefinito è NULL.  
  
 [  **@active_end_time_of_day=**] *active_end_time_of_day*  
 Ora del giorno dell'ultima esecuzione pianificata dell'agente di merge, nel formato HHMMSS. *active_end_time_of_day* viene **int**, con un valore predefinito è NULL.  
  
 [  **@active_start_date=**] *active_start_date*  
 Data della prima esecuzione pianificata dell'agente di merge, nel formato AAAAMMGG. *active_start_date* viene **int**, con un valore predefinito è NULL.  
  
 [  **@active_end_date=**] *active_end_date*  
 Data dell'ultima esecuzione pianificata dell'agente di merge, nel formato AAAAMMGG. *active_end_date* viene **int**, con un valore predefinito è NULL.  
  
 [  **@optional_command_line=**] **'***optional_command_line***'**  
 Prompt dei comandi facoltativo da eseguire. *optional_command_line*viene **nvarchar(4000**, con un valore predefinito è NULL. Questo parametro viene utilizzato per aggiungere un comando per l'acquisizione e il salvataggio dell'output in un file o per specificare un file o un attributo di configurazione.  
  
 [  **@description=**] **'***descrizione***'**  
 Breve descrizione della sottoscrizione di tipo merge. *Descrizione*viene **nvarchar(255**, con un valore predefinito è NULL. Questo valore viene visualizzato da Monitoraggio replica nel **nome descrittivo** colonna, che può essere utilizzato per ordinare le sottoscrizioni per una pubblicazione monitorata.  
  
 [  **@enabled_for_syncmgr=**] **'***enabled_for_syncmgr***'**  
 Specifica se la sottoscrizione può essere sincronizzata tramite Gestione sincronizzazione [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. *enabled_for_syncmgr* viene **nvarchar(5**, con un valore predefinito è FALSE. Se **false**, la sottoscrizione non è registrata con Gestione sincronizzazione. Se **true**, la sottoscrizione viene registrata con Gestione sincronizzazione e può essere sincronizzata senza avviare [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 [  **@offloadagent=** ] *remote_agent_activation*  
 Specifica se è possibile o meno attivare l'agente in remoto. *remote_agent_activation* viene **bit** con valore predefinito è **0**.  
  
> [!NOTE]  
>  Questo parametro è deprecato ed è ancora disponibile per compatibilità con gli script di versioni precedenti.  
  
 [  **@offloadserver=** ] **'***remote_agent_server_name***'**  
 Nome di rete del server da utilizzare per l'attivazione remota dell'agente. *remote_agent_server_name*viene **sysname**, con un valore predefinito è NULL.  
  
 [  **@use_interactive_resolver=** ] **'***use_interactive_resolver***'**  
 Consente la risoluzione interattiva dei conflitti per tutti gli articoli che la prevedono. *use_interactive_resolver* viene **nvarchar(5**, con un valore predefinito è FALSE.  
  
 [  **@merge_job_name=** ] **'***merge_job_name***'**  
 Il *@merge_job_name* parametro è deprecato e non può essere impostata. *merge_job_name* viene **sysname**, con un valore predefinito è NULL.  
  
 [ **@hostname**=] **'***hostname***'**  
 Sostituisce il valore restituito da [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) quando questa funzione viene utilizzata nella clausola WHERE di un filtro con parametri. *Hostname* viene **sysname**, con un valore predefinito è NULL.  
  
> [!IMPORTANT]  
>  Per motivi relativi alle prestazioni è consigliabile evitare di applicare funzioni ai nomi di colonna nelle clausole per filtri di riga con parametri, come `LEFT([MyColumn]) = SUSER_SNAME()`. Se si utilizza [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) in una clausola di filtro e si sostituisce il valore di HOST_NAME, potrebbe essere necessario convertire i tipi di dati tramite [CONVERTIRE](../../t-sql/functions/cast-and-convert-transact-sql.md). Per altre informazioni sulle procedure consigliate in questo caso, vedere la sezione relativa alla sostituzione del valore HOST_NAME() nell'argomento [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_addmergesubscription** viene utilizzata nella replica di tipo merge.  
  
 Quando **sp_addmergesubscription** viene eseguita da un membro del **sysadmin** ruolo predefinito del server per creare una sottoscrizione push, il processo di agente di Merge viene creato in modo implicito e viene eseguito il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] agente account del servizio. È consigliabile eseguire [sp_addmergepushsubscription_agent](../../relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql.md) e specificare le credenziali di un account Windows diverso specifico dell'agente per **@job_login** e **@job_password**. Per altre informazioni, vedere [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
## <a name="example"></a>Esempio  
 [!code-sql[HowTo#sp_addmergepushsubscriptionagent](../../relational-databases/replication/codesnippet/tsql/sp-addmergesubscription-_1.sql)]  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server o **db_owner** ruolo predefinito del database possono eseguire **sp_addmergesubscription**.  
  
## <a name="see-also"></a>Vedere anche  
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Creare una sottoscrizione pull](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Risoluzione interattiva dei conflitti](../../relational-databases/replication/merge/advanced-merge-replication-conflict-interactive-resolution.md)   
 [Sottoscrivere le pubblicazioni](../../relational-databases/replication/subscribe-to-publications.md)   
 [sp_changemergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql.md)   
 [sp_dropmergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql.md)   
 [sp_helpmergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql.md)  
  
  

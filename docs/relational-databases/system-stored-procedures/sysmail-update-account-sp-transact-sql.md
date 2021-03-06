---
title: sysmail_update_account_sp (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 11/17/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sysmail_update_account_sp
- sysmail_update_account_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_update_account_sp
ms.assetid: ba2fdccc-5ed4-40ef-a479-79497b4d61aa
caps.latest.revision: 51
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ad64d1d455a4419c66949ba0196f9a9557a8ae52
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33262183"
---
# <a name="sysmailupdateaccountsp-transact-sql"></a>sysmail_update_account_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifica le informazioni di un account di Posta elettronica database esistente.  
 
 
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sysmail_update_account_sp [ [ @account_id = ] account_id ] [ , ] [ [ @account_name = ] 'account_name' ] ,  
    [ @email_address = ] 'email_address' ,   
    [ @display_name = ] 'display_name' ,   
    [ @replyto_address = ] 'replyto_address' ,  
    [ @description = ] 'description' ,   
    [ @mailserver_name = ] 'server_name' ,   
    [ @mailserver_type = ] 'server_type' ,   
    [ @port = ] port_number ,   
    [ @timeout = ] 'timeout' ,  
    [ @username = ] 'username' ,  
    [ @password = ] 'password' ,  
    [ @use_default_credentials = ] use_default_credentials ,  
    [ @enable_ssl = ] enable_ssl   
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@account_id** = ] *account_id*  
 ID dell'account da aggiornare. *account_id* viene **int**, con un valore predefinito è NULL. Almeno uno dei *account_id* o *account_name* deve essere specificato. Se si specificano entrambi, la stored procedure modifica il nome dell'account.  
  
 [ **@account_name** =] **'***account_name***'**  
 Nome dell'account da aggiornare. *account_name* viene **sysname**, con un valore predefinito è NULL. Almeno uno dei *account_id* o *account_name* deve essere specificato. Se si specificano entrambi, la stored procedure modifica il nome dell'account.  
  
 [ **@email_address** =] **'***email_address***'**  
 Nuovo indirizzo di posta elettronica da cui inviare il messaggio. Deve essere un indirizzo di posta elettronica Internet. Il nome del server nell'indirizzo è il server utilizzato da Posta elettronica database per l'invio di posta da questo account. *email_address* viene **nvarchar (128)**, con un valore predefinito è NULL.  
  
 [ **@display_name** =] **'***display_name***'**  
 Nuovo nome visualizzato da utilizzare nei messaggi di posta elettronica provenienti da questo account. *DISPLAY_NAME* viene **nvarchar (128)**, non prevede alcun valore predefinito.  
  
 [ **@replyto_address** =] **'***replyto_address***'**  
 Nuovo indirizzo da utilizzare nel campo Risposta dei messaggi di posta elettronica inviati da questo account. *replyto_address* viene **nvarchar (128)**, non prevede alcun valore predefinito.  
  
 [ **@description** =] **'***descrizione***'**  
 Nuova descrizione dell'account. *Descrizione* viene **nvarchar(256)**, con un valore predefinito è NULL.  
  
 [ **@mailserver_name** =] **'***nome_server***'**  
 Nome del nuovo server di posta elettronica SMTP da utilizzare per l'account. Il computer che esegue [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deve essere in grado di risolvere il *nome_server* in un indirizzo IP. *nome_server* viene **sysname**, non prevede alcun valore predefinito.  
  
 [ **@mailserver_type** =] **'***server_type***'**  
 Nuovo tipo del server di posta elettronica. *server_type* viene **sysname**, non prevede alcun valore predefinito. Solo un valore di **'SMTP'** è supportato.  
  
 [ **@port** =] *numero_porta*  
 Nuovo numero di porta del server di posta elettronica. *numero_porta* viene **int**, non prevede alcun valore predefinito.  
  
 [ **@timeout** =] **'***timeout***'**  
 Parametro di timeout per SmtpClient.Send di un singolo messaggio di posta elettronica. *Timeout* viene **int** espresso in secondi, non prevede alcun valore predefinito.  
  
 [ **@username** =] **'***username***'**  
 Nuovo nome utente da utilizzare per l'accesso al server di posta elettronica. *Nome utente* viene **sysname**, non prevede alcun valore predefinito.  
  
 [ **@password** =] **'***password***'**  
 Nuova password da utilizzare per l'accesso al server di posta elettronica. *password* viene **sysname**, non prevede alcun valore predefinito.  
  
 [ **@use_default_credentials** =] use_default_credentials  
 Specifica se inviare la posta elettronica al server SMTP utilizzando le credenziali del servizio [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. **use_default_credentials** è di tipo bit e non prevede alcun valore predefinito. Se questo parametro è 1, Posta elettronica database utilizza le credenziali di [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Quando questo parametro è 0, posta elettronica Database utilizza il **@username** e **@password** per l'autenticazione sul server SMTP. Se **@username** e **@password** sono NULL, utilizzata l'autenticazione anonima. Prima di specificare questo parametro consultare l'amministratore del server SMTP.  
  
 [ **@enable_ssl** =] enable_ssl  
 Specifica l'utilizzo della crittografia mediante SSL (Secure Sockets Layer) da parte di Posta elettronica database. Utilizzare questa opzione se SSL è obbligatorio per il server SMTP. **enable_ssl** è di tipo bit e non prevede alcun valore predefinito.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 Se si specificano sia il nome dell'account che l'ID dell'account, la stored procedure modifica il nome dell'account, oltre ad aggiornare le informazioni relative all'account. Questo può essere utile se è necessario correggere un errore nel nome dell'account.  
  
 La stored procedure **sysmail_update_account_sp** nel **msdb** database ed è di proprietà di **dbo** dello schema. La procedura deve essere eseguita con un nome in tre parti se il database corrente non è **msdb**.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza al ruolo predefinito del server **sysadmin** .  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-changing-the-information-for-an-account"></a>A. Modifica delle informazioni di un account  
 L'esempio seguente aggiorna l'account `AdventureWorks Administrator` nel **msdb** database. Le informazioni dell'account vengono impostate in base ai valori specificati.  
  
```  
EXECUTE msdb.dbo.sysmail_update_account_sp  
     @account_name = 'AdventureWorks Administrator'  
    ,@description = 'Mail account for administrative e-mail.'  
    ,@email_address = 'dba@Adventure-Works.com'  
    ,@display_name = 'AdventureWorks Automated Mailer'  
    ,@replyto_address = NULL  
    ,@mailserver_name = 'smtp.Adventure-Works.com'  
    ,@mailserver_type = 'SMTP'  
    ,@port = 25  
    ,@timeout = 60  
    ,@username = NULL  
    ,@password = NULL  
    ,@use_default_credentials = 0  
    ,@enable_ssl = 0;  
```  
  
### <a name="b-changing-the-name-of-an-account-and-the-information-for-an-account"></a>B. Modifica del nome e delle informazioni di un account  
 Nell'esempio seguente vengono modificati il nome e le informazioni dell'account con ID `125`. Il nuovo nome dell'account è `Backup Mail Server`.  
  
```  
EXECUTE msdb.dbo.sysmail_update_account_sp  
     @account_id = 125  
    ,@account_name = 'Backup Mail Server'  
    ,@description = 'Mail account for administrative e-mail.'  
    ,@email_address = 'dba@Adventure-Works.com'  
    ,@display_name = 'AdventureWorks Automated Mailer'  
    ,@replyto_address = NULL  
    ,@mailserver_name = 'smtp-backup.Adventure-Works.com'  
    ,@mailserver_type = 'SMTP'  
    ,@port = 25  
    ,@timeout = 60  
    ,@username = NULL  
    ,@password = NULL  
    ,@use_default_credentials = 0  
    ,@enable_ssl = 0;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Posta elettronica database](../../relational-databases/database-mail/database-mail.md)   
 [Creare un Account di posta elettronica Database](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [Stored procedure di posta elettronica database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  

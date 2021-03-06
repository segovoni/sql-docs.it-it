---
title: sp_adddistpublisher (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/15/2018
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
- sp_adddistpublisher
- sp_adddistpublisher_TSQL
helpviewer_keywords:
- sp_adddistpublisher
ms.assetid: 04e15011-a902-4074-b38c-3ec2fc73b838
caps.latest.revision: 35
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 75db58f4711b946eeceeb74dcbb3a34538ea97e1
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39084293"
---
# <a name="spadddistpublisher-transact-sql"></a>sp_adddistpublisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Configura un server di pubblicazione per l'utilizzo del database di distribuzione specificato. Questa stored procedure viene eseguita in qualsiasi database del server di distribuzione. Si noti che le stored procedure [sp_adddistributor &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-adddistributor-transact-sql.md) e [sp_adddistributiondb &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-adddistributiondb-transact-sql.md) necessario eseguire prima di utilizzare questa stored procedura.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_adddistpublisher [ @publisher= ] 'publisher'   
        , [ @distribution_db= ] 'distribution_db'   
    [ , [ @security_mode= ] security_mode ]   
    [ , [ @login= ] 'login' ]   
    [ , [ @password= ] 'password' ]   
    [ , [ @working_directory= ] 'working_directory' ]   
    [ , [ @storage_connection_string= ] 'storage_connection_string']
    [ , [ @trusted= ] 'trusted' ]   
    [ , [ @encrypted_password= ] encrypted_password ]   
    [ , [ @thirdparty_flag = ] thirdparty_flag ]  
    [ , [ @publisher_type = ] 'publisher_type' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publisher=**] **'***publisher***'**  
 Nome del server di pubblicazione. *server di pubblicazione* viene **sysname**, non prevede alcun valore predefinito.  
  
 [  **@distribution_db=**] **'***distribution_db***'**  
 Nome del database di distribuzione. *distributor_db* viene **sysname**, non prevede alcun valore predefinito. Questo parametro viene utilizzato dagli agenti di replica per la connessione al server di pubblicazione.  
  
 [  **@security_mode=**] *security_mode*  
 Modalità di sicurezza implementata. Questo parametro viene utilizzato solo dagli agenti di replica per connettersi al server di pubblicazione per sottoscrizioni ad aggiornamento in coda o con un server di pubblicazione non [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *security_mode* viene **int**, i possibili valori sono i seguenti.  
  
|valore|Description|  
|-----------|-----------------|  
|**0**|Gli agenti di replica nel server di distribuzione si connettono al server di pubblicazione tramite l'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**1** (impostazione predefinita)|Gli agenti di replica nel server di distribuzione si connettono al server di pubblicazione tramite l'autenticazione di Windows.|  
  
 [  **@login=**] **'***account di accesso***'**  
 Account di accesso. Questo parametro è obbligatorio se *security_mode* viene **0**. *login* è di tipo **sysname** e il valore predefinito è NULL. Questo parametro viene utilizzato dagli agenti di replica per la connessione al server di pubblicazione.  
  
 [  **@password=**] **'***password***'**]  
 Password. *la password* viene **sysname**, con un valore predefinito è NULL. Questo parametro viene utilizzato dagli agenti di replica per la connessione al server di pubblicazione.  
  
> [!IMPORTANT]  
>  Non usare una password vuota. Usare una password complessa.  
  
 [  **@working_directory=**] **'***working_directory***'**  
 Nome della directory di lavoro utilizzata per archiviare i file dei dati e di schema per la pubblicazione *working_directory* viene **nvarchar(255**e il valore predefinito è la cartella ReplData per questa istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ad esempio `C:\Program Files\Microsoft SQL Server\MSSQL\MSSQ.1\ReplData`. Il nome deve essere specificato in formato UNC.  

 Per il Database SQL di Azure, usare `\\<storage_account>.file.core.windows.net\<share>`.

 [  **@storage_connection_string =**] **'***storage_connection_string***'**  
 È necessario per il Database SQL. Usare la chiave di accesso dal portale di Azure in archiviazione > Impostazioni.

 > [!INCLUDE[Azure SQL Database link](../../includes/azure-sql-db-repl-for-more-information.md)]

 [  **@trusted=**] **'***attendibile***'**  
 Questo parametro è deprecato ed è disponibile solo per compatibilità con le versioni precedenti. *attendibile* viene **nvarchar(5**e impostandola su qualsiasi valore diverso **false** comporterà un errore.  
  
 [  **@encrypted_password=**] *encrypted_password*  
 L'impostazione *encrypted_password* non è più supportata. Tentativo di impostare questo **bit** parametro per **1** comporterà un errore.  
  
 [  **@thirdparty_flag =**] *thirdparty_flag*  
 Indica se il server di pubblicazione è un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *thirdparty_flag* viene **bit**, e può essere uno dei valori seguenti.  
  
|valore|Description|  
|-----------|-----------------|  
|**0** (predefinito)|Database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**1**|Database non di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
 [ **@publisher_type**=] **'***publisher_type***'**  
 Specifica il tipo di server di pubblicazione quando è diverso da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *publisher_type* è di tipo sysname e può essere uno dei valori seguenti.  
  
|valore|Description|  
|-----------|-----------------|  
|**MSSQLSERVER**<br /><br /> (predefinito)|Specifica un server di pubblicazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**ORACLE**|Specifica un server di pubblicazione Oracle standard.|  
|**ORACLE GATEWAY**|Specifica un server di pubblicazione Oracle Gateway.|  
  
 Per altre informazioni sulle differenze tra un server di pubblicazione Oracle e un server di pubblicazione Oracle Gateway, vedere [configurare un server di pubblicazione Oracle](../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md).  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="remarks"></a>Note  
 **sp_adddistpublisher** viene utilizzato dalla replica snapshot, la replica transazionale e di tipo merge.  
  
## <a name="example"></a>Esempio  
 [!code-sql[HowTo#AddDistPub](../../relational-databases/replication/codesnippet/tsql/sp-adddistpublisher-tran_1.sql)]  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server possono eseguire **sp_adddistpublisher**.  
  
## <a name="see-also"></a>Vedere anche  
 [Configurare la pubblicazione e la distribuzione](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [sp_changedistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql.md)   
 [sp_dropdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md)   
 [sp_helpdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdistpublisher-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Configurare la distribuzione](../../relational-databases/replication/configure-distribution.md)  
  
  

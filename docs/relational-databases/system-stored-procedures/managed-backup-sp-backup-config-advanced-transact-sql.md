---
title: managed_backup.sp_backup_config_advanced (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_backup_config_optional
- sp_backup_config_optional_TSQL
- managed_backup.sp_backup_config_optional_TSQL
- managed_backup.sp_backup_config_optional
dev_langs:
- TSQL
helpviewer_keywords:
- sp_backup_config_optional
- managed_backup.sp_backup_config_optional
ms.assetid: 4fae8193-1f88-48fd-a94a-4786efe8d6af
caps.latest.revision: 15
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 08c79b906a95c41013f28a559acdc7f98809c186
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "37970483"
---
# <a name="managedbackupspbackupconfigadvanced-transact-sql"></a>managed_backup.sp_backup_config_advanced (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Consente di configurare le impostazioni avanzate per [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
EXEC managed_backup.sp_backup_config_advanced   
    [@database_name = ] 'database_name'  
    ,[@encryption_algorithm = ] 'name of the encryption algorithm'  
    ,[@encryptor_type = ] {'CERTIFICATE' | 'ASYMMETRIC_KEY'}  
    ,[@encryptor_name = ] 'name of the certificate or asymmetric key'  
    ,[@local_cache_path = ] 'NOT AVAILABLE'  
```  
  
##  <a name="Arguments"></a> Argomenti  
 @database_name  
 Il nome del database per l'abilitazione del backup gestito in un database specifico. Se è NULL o *, il backup gestito verrà applicata a tutti i database nel server.  
  
 @encryption_algorithm  
 Nome dell'algoritmo di crittografia utilizzato durante il backup per crittografare il file di backup. Il @encryption_algorithm viene **SYSNAME**. È un parametro obbligatorio quando si configura il [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] per la prima volta per il database. Specificare **NO_ENCRYPTION** se non si desidera crittografare il file di backup. Quando si modificano le impostazioni di configurazione del [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)], questo parametro è facoltativo. Se il parametro non viene specificato, vengono mantenuti i valori di configurazione esistenti. I valori consentiti per questo parametro sono:  
  
-   AES_128  
  
-   AES_192  
  
-   AES_256  
  
-   TRIPLE_DES_3KEY  
  
-   NO_ENCRYPTION  
  
 Per altre informazioni sugli algoritmi di crittografia, vedere [Choose an Encryption Algorithm](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md).  
  
 @encryptor_type  
 Tipo di componente, che può essere uno dei certificati' ' o ' ASYMMETRIC_KEY ". Il @encryptor_type viene **nvarchar(32)**. Questo parametro è facoltativo se si specifica NO_ENCRYPTION per il @encryption_algorithm parametro.  
  
 @encryptor_name  
 Nome di un certificato o una chiave asimmetrica esistente da utilizzare per crittografare il backup. Il @encryptor_name viene **SYSNAME**. Se si utilizza una chiave asimmetrica, deve essere configurata con Extensible Key Management (EKM). Questo parametro è facoltativo se si specifica NO_ENCRYPTION per il @encryption_algorithm parametro.  
  
 Per altre informazioni, vedere [Extensible Key Management &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md).  
  
 @local_cache_path  
 Questo parametro non è ancora supportato.  
  
## <a name="return-code-value"></a>Valore del codice restituito  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>Autorizzazioni  
 Richiede l'appartenenza al **db_backupoperator** ruolo del database con **ALTER ANY CREDENTIAL** autorizzazioni, e **EXECUTE** autorizzazioni sul **sp_delete BackupHistory** stored procedure.  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente imposta le opzioni di configurazione avanzata per [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] per l'istanza di SQL Server.  
  
```  
Use msdb;  
Go  
   EXEC managed_backup.sp_backup_config_advanced  
                @encryption_algorithm ='AES_128'  
                ,@encryptor_type = 'CERTIFICATE'  
                ,@encryptor_name = 'MyTestDBBackupEncryptCert'  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [managed_backup.sp_backup_config_basic (Transact-SQL)](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-basic-transact-sql.md)   
 [managed_backup.sp_backup_config_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-schedule-transact-sql.md)  
  
  

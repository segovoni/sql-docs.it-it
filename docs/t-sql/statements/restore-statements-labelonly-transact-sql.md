---
title: RESTORE LABELONLY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2018
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- LABELONLY
- RESTORE_LABELONLY_TSQL
- LABELONLY_TSQL
- RESTORE LABELONLY
dev_langs:
- TSQL
helpviewer_keywords:
- RESTORE LABELONLY statement
- backup media [SQL Server], content information
ms.assetid: 7cf0641e-0d55-4ffb-9500-ecd6ede85ae5
caps.latest.revision: 46
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 31f99d63631ee03435aa83fa870c88f68dd45ea8
ms.sourcegitcommit: 00ffbc085c5a4b792646ec8657495c83e6b851b5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/26/2018
ms.locfileid: "36941647"
---
# <a name="restore-statements---labelonly-transact-sql"></a>Istruzioni RESTORE - LABELONLY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md )]
  Restituisce un set di risultati che include informazioni sul supporto di backup identificato dal dispositivo di backup specificato.  

[!INCLUDE[ssMIlimitation](../../includes/sql-db-mi-limitation.md)]
  
> [!NOTE]  
>  Per le descrizioni degli argomenti, vedere [Argomenti RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-arguments-transact-sql.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
RESTORE LABELONLY   
FROM <backup_device>   
[ WITH   
 {  
--Media Set Options  
   MEDIANAME = { media_name | @media_name_variable }   
 | MEDIAPASSWORD = { mediapassword | @mediapassword_variable }  
  
--Error Management Options  
 | { CHECKSUM | NO_CHECKSUM }   
 | { STOP_ON_ERROR | CONTINUE_AFTER_ERROR }  
  
--Tape Options  
 | { REWIND | NOREWIND }   
 | { UNLOAD | NOUNLOAD }    
 } [ ,...n ]  
]  
[;]  
  
<backup_device> ::=  
{   
   { logical_backup_device_name |  
      @logical_backup_device_name_var }  
   | { DISK | TAPE } = { 'physical_backup_device_name' |  
       @physical_backup_device_name_var }   
}  
  
```  
  
## <a name="arguments"></a>Argomenti  
 Per le descrizioni degli argomenti RESTORE LABELONLY, vedere [Argomenti RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-arguments-transact-sql.md).  
  
## <a name="result-sets"></a>Set di risultati  
 Il set di risultati dall'istruzione RESTORE LABELONLY consiste in una riga singola che include le informazioni seguenti.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**MediaName**|**nvarchar(128)**|Nome del supporto.|  
|**MediaSetId**|**uniqueidentifier**|Numero di identificazione univoco del set di supporti.|  
|**FamilyCount**|**int**|Numero di gruppi di supporti nel set di supporti.|  
|**FamilySequenceNumber**|**int**|Numero di sequenza del gruppo.|  
|**MediaFamilyId**|**uniqueidentifier**|Numero di identificazione univoco del gruppo di supporti.|  
|**MediaSequenceNumber**|**int**|Numero di sequenza del supporto nel gruppo di supporti.|  
|**MediaLabelPresent**|**tinyint**|Specifica se la descrizione del supporto include:<br /><br /> **1** =  etichetta di supporto [!INCLUDE[msCoName](../../includes/msconame-md.md)] Tape Format<br /><br /> **0** = descrizione dei supporti|  
|**MediaDescription**|**nvarchar(255)**|Descrizione del supporto come testo in formato libero o etichetta del supporto Microsoft Tape Format|  
|**SoftwareName**|**nvarchar(128)**|Nome del software di backup con cui è stata scritta l'etichetta.|  
|**SoftwareVendorId**|**int**|Numero di identificazione univoco del produttore del software che ha scritto il backup.|  
|**MediaDate**|**datetime**|Data e ora in cui è stata scritta l'etichetta.|  
|**Mirror_Count**|**int**|Numero di mirror nel set (1-4).<br /><br /> Nota: le etichette scritte per mirror diversi in un set sono identiche.|  
|**IsCompressed**|**bit**|Specifica se il backup è compresso:<br /><br /> 0 = non compresso<br /><br /> 1 = compresso|  
  
> [!NOTE]  
>  Se per il set di supporti sono state definite password, l'istruzione RESTORE LABELONLY restituisce informazioni solo se nell'opzione MEDIAPASSWORD del comando si specifica la password di supporto corretta.  
  
## <a name="general-remarks"></a>Osservazioni generali  
 L'esecuzione di RESTORE LABELONLY consente di individuare rapidamente il contenuto del supporto di backup. Poiché viene letta solo l'intestazione supporto, l'esecuzione dell'istruzione risulta veloce anche con dispositivi nastro ad alta capacità.  
  
## <a name="security"></a>Security  
 Per un'operazione di backup è possibile specificare facoltativamente una password per un set di supporti. Se è stata impostata una password per un set di supporti, la password corretta deve essere specificata nell'istruzione RESTORE. La password impedisce operazioni di ripristino non autorizzate e l'aggiunta non autorizzata di set di backup ai supporti tramite gli strumenti di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Tuttavia, la password non impedisce la sovrascrittura dei supporti tramite l'opzione FORMAT dell'istruzione BACKUP.  
  
> [!IMPORTANT]  
>  Il livello di protezione garantito da questa password è ridotto. Lo scopo è impedire un ripristino non corretto da parte di utenti autorizzati o non autorizzati mediante gli strumenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Non impedisce la lettura dei dati di backup eseguita con altri mezzi o la sostituzione della password. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Per ottenere un livello di protezione adeguato dei backup è consigliabile archiviare i nastri di backup in un luogo sicuro oppure eseguire il backup in file su disco protetti da elenchi di controllo di accesso (ACL) appropriati. Gli elenchi di controllo di accesso devono essere impostati a livello della directory radice in cui vengono creati i backup.  
  
### <a name="permissions"></a>Autorizzazioni  
 In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] e versioni successive, per ottenere informazioni su un set o un dispositivo di backup è necessario disporre dell'autorizzazione CREATE DATABASE. Per altre informazioni, vedere [GRANT - autorizzazioni per database &#40;Transact-SQL&#41;](../../t-sql/statements/grant-database-permissions-transact-sql.md).  
  
## <a name="see-also"></a>Vedere anche  
 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)   
 [Set di supporti, gruppi di supporti e set di backup &#40;SQL Server&#41;](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md)   
 [RESTORE REWINDONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-rewindonly-transact-sql.md)   
 [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-verifyonly-transact-sql.md)   
 [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)   
 [Informazioni sulla cronologia e sull'intestazione del backup &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-history-and-header-information-sql-server.md)  
  
  

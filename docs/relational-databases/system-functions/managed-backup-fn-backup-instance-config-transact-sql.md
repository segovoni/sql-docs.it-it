---
title: managed_backup.fn_backup_instance_config (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- fn_backup_instance_config
- smart_admin.fn_backup_instance_config_TSQL
- fn_backup_instance_config_TSQL
- smart_admin.fn_backup_instance_config
dev_langs:
- TSQL
helpviewer_keywords:
- smart_admin.fn_backup_instance_config
- fn_backup_instance_config
ms.assetid: 2382a547-c0c9-4e1d-87c9-d8526192eb5a
caps.latest.revision: 16
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 4dae80911e6508a1a398cf208300bf4145faeecc
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "37970503"
---
# <a name="managedbackupfnbackupinstanceconfig-transact-sql"></a>managed_backup.fn_backup_instance_config (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Restituisce una riga con le impostazioni di configurazione predefinite del [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] per l'istanza di SQL Server.  
  
 Utilizzare questa stored procedure per controllare o determinare le impostazioni di configurazione correnti del [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] per un'istanza di SQL Server.  
  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```sql  
managed_backup.fn_backup_db_config ()  
```  
  
##  <a name="Arguments"></a> Argomenti  
 None  
  
## <a name="table-returned"></a>Tabella restituita  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|is_smart_backup_enabled|INT|Visualizza 1 quando il [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] è abilitato e 0 quando il [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] è disabilitato.|  
|credential_name|SYSNAME|Credenziali SQL predefinite utilizzate per l'autenticazione per l'archiviazione.|  
|retention_days|INT|Periodo di memorizzazione predefinito impostato a livello di istanza.|  
|storage_url|NVARCHAR(1024)|URL dell'account di archiviazione predefinito impostato a livello di istanza.|  
|encryption_algorithm|SYSNAME|Nome dell'algoritmo di crittografia. Se la crittografia non è specificata, è impostato su NULL.|  
|encryptor_type|NVARCHAR(32)|Tipo di componente di crittografia: certificato o chiave asimmetrica. Se nessun componente di crittografia è specificato, è impostato su NULL.|  
|encryptor_name|SYSNAME|Nome del certificato o della chiave asimmetrica. Se nessun nome è specificato, è impostato su NULL.|  
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>Autorizzazioni  
 Richiede l'appartenenza al **db_backupoperator** ruolo del database con **ALTER ANY CREDENTIAL** autorizzazioni. L'utente non deve essere negata **VIEW ANY DEFINITION** autorizzazioni.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono restituite le impostazioni di configurazione predefinite del [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] per l'istanza in cui viene eseguito.  
  
```  
Use msdb;  
GO  
SELECT * FROM managed_backup.fn_backup_instance_config ();  
  
```  
  
  

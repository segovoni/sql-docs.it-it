---
title: sp_pdw_database_encryption (SQL Data Warehouse) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.service: sql-data-warehouse
ms.component: system-objects
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: f5ccb424-7a95-4557-b774-c69de33c1545
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 6508d150df663a6e95437d0b6b3bfd0c8f65906f
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38052229"
---
# <a name="sppdwdatabaseencryption-sql-data-warehouse"></a>sp_pdw_database_encryption (SQL Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Uso **sp_pdw_database_encryption** per abilitare transparent data encryption in per un [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] appliance. Quando **sp_pdw_database_encryption** impostato su 1, utilizzare il **ALTER DATABASE** istruzione per crittografare un database tramite Transparent Data Encryption.  
  
## <a name="syntax"></a>Sintassi  
  
```sql  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_pdw_database_encryption [ [ @enabled = ] enabled ] ;  
```  
  
#### <a name="parameters"></a>Parametri  
 [  **@enabled=** ] *abilitata*  
 Determina se transparent data encryption è abilitato. *abilitata* viene **int**, e può essere uno dei valori seguenti:  
  
-   0 = Disabilitato  
  
-   1 = Attivato  
  
 L'esecuzione **sp_pdw_database_encryption** senza parametri, viene restituito lo stato corrente della funzionalità TDE nell'appliance come set di risultati scalari: 0 per disabilitato o 1 per abilitata.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Note  
 Quando TDE è abilitata tramite **sp_pdw_database_encryption**, il database tempdb è eliminato, ricreato e crittografato. Per questo motivo, non è possibile abilitare TDE in un'appliance mentre sono presenti altre sessioni attive usando tempdb. Abilitazione o disabilitazione di TDE in un'appliance è un'azione che modifica lo stato dell'appliance, nella maggior parte dei casi si dovrà essere eseguita una sola volta nel ciclo di vita di appliance e deve essere eseguita quando non viene rilevato traffico nell'appliance.  
  
## <a name="permissions"></a>Autorizzazioni  
 Richiede l'appartenenza al **sysadmin** ruolo predefinito del database, o **CONTROL SERVER** l'autorizzazione.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente Abilita TDE nell'appliance.  
  
```sql  
EXEC sys.sp_pdw_database_encryption 1;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_pdw_database_encryption_regenerate_system_keys &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-database-encryption-regenerate-system-keys-sql-data-warehouse.md)   
 [sp_pdw_log_user_data_masking &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-log-user-data-masking-sql-data-warehouse.md)  
  
  

---
title: sp_pdw_log_user_data_masking (SQL Data Warehouse) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-objects
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 43c63b42-03cb-4fb5-8362-ec3b7e22a590
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 16de9489583cce2e696a94c75c7e5fd3ac1c0fe1
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "37993713"
---
# <a name="sppdwloguserdatamasking-sql-data-warehouse"></a>sp_pdw_log_user_data_masking (SQL Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Uso **sp_pdw_log_user_data_masking** per abilitare i dati utente, maschera [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] i log attività. Mascheramento dei dati utente interessa le istruzioni in tutti i database nell'appliance.  
  
> [!IMPORTANT]  
>  Il [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] log attività interessate da **sp_pdw_log_user_data_masking** certezze [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] i log attività. **sp_pdw_log_user_data_masking** influisce sui registri delle transazioni del database o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] i log degli errori.  
  
 **Sfondo:** nella configurazione predefinita [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] log attività contengono completi [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzioni ed è possibile in alcuni casi includono i dati utente contenuti nelle operazioni, ad esempio **Inserisci**,  **UPDATE**, e **selezionare** istruzioni. In caso di un problema nell'appliance, in questo modo, l'analisi delle condizioni che ha causato il problema senza la necessità di riprodurre il problema. Allo scopo di impedire che i dati utente su cui scrivere [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] i log attività, i clienti possono scegliere di abilitare il mascheramento dei dati utente tramite questa stored procedure. Le istruzioni verranno ancora scritti [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] i log attività, ma tutti i valori letterali nelle istruzioni che possono contenere i dati dell'utente verranno applicata la maschera; sostituiti con alcuni valori costanti predefinite.  
  
 Quando transparent data encryption è abilitato nell'appliance, mascheramento dei dati utente in [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] i log attività vengono attivati automaticamente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_pdw_log_user_data_masking [ [ @masking_mode = ] value ] ;  
```  
  
#### <a name="parameters"></a>Parametri  
 [  **@masking_mode=** ] *masking_mode*  
 Determina se sono abilitati transparent data encryption log utente maschera dati. *masking_mode* viene **int**, e può essere uno dei valori seguenti:  
  
-   0 = disabilitato, utente i dati vengono visualizzati nei [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] i log attività.  
  
-   1 = Enabled, utente vengono visualizzate le istruzioni di dati nel [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] i log attività, ma i dati dell'utente viene mascherato.  
  
-   2 = istruzioni contenente i dati utente non vengono scritte le [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] i log attività.  
  
 L'esecuzione **sp_pdw_ log_user_data_masking** senza parametri, viene restituito lo stato corrente della maschera dati utente di log TDE nell'appliance come set di risultati scalari.  
  
## <a name="remarks"></a>Note  
 Maschera dati utente [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] abilita la sostituzione di valori letterali con valori costanti predefiniti in i log attività **selezionare** e istruzioni DML, poiché possono contenere i dati dell'utente. L'impostazione *masking_mode* a 1 non maschera quella dei metadati, ad esempio i nomi di colonna o nomi di tabella. L'impostazione *masking_mode* 2 Rimuove le istruzioni con i metadati, ad esempio i nomi di colonna o nomi di tabella.  
  
 Maschera di dati utente [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] i log attività viene implementata nel modo seguente:  
  
-   Transparent Data Encryption e i dati utente maschera [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] i log attività sono stati disabilitate per impostazione predefinita. Le istruzioni non saranno automaticamente nascosta se la crittografia del database non è abilitata nell'appliance.  
  
-   L'abilitazione di TDE nell'appliance automaticamente consente di attivare il mascheramento dei dati utente in [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] i log attività.  
  
-   Disabilitazione di TDE non incide sulla maschera dati utente [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] i log attività.  
  
-   È possibile abilitare in modo esplicito i dati utente, maschera nel [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] log attività usando il **sp_pdw_log_user_data_masking** procedure.  
  
## <a name="permissions"></a>Autorizzazioni  
 Richiede l'appartenenza al **sysadmin** ruolo predefinito del database, o **CONTROL SERVER** l'autorizzazione.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente Abilita i dati utente di log TDE nell'appliance di mascheramento.  
  
```  
EXEC sp_pdw_log_user_data_masking 1;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_pdw_database_encryption &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-database-encryption-sql-data-warehouse.md)   
 [sp_pdw_database_encryption_regenerate_system_keys &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-database-encryption-regenerate-system-keys-sql-data-warehouse.md)  
  
  

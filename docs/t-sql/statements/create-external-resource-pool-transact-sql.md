---
title: CREATE EXTERNAL RESOURCE POOL (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/13/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CREATE EXTERNAL RESOURCE POOL
- CREATE EXTERNAL_RESOURCE_POOL_TSQL
- EXTERNAL RESOURCE POOL
- EXTERNAL_RESOURCE_POOL_TSQL
- EXTERNAL RESOURCE
- EXTERNAL_RESOURCE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CREATE EXTERNAL RESOURCE POOL statement
ms.assetid: 8cc798ad-c395-461c-b7ff-8c561c098808
author: HeidiSteen
ms.author: heidist
manager: cgronlund
ms.openlocfilehash: 7e4ae3239332c004ad6ceda624b641b7bf7603be
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37415380"
---
# <a name="create-external-resource-pool-transact-sql"></a>CREATE EXTERNAL RESOURCE POOL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]
**Si applica a:**  [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)] e [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)] [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]

Crea un pool esterno usato per definire le risorse per i processi esterni. Un pool di risorse rappresenta un subset delle risorse fisiche (memoria e CPU) di un'istanza del motore di database. Resource Governor consente a un amministratore di database di distribuire le risorse del server tra pool di risorse, fino a un massimo di 64 pool.

+ Per [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)] in [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] il pool esterno gestisce `rterm.exe`, `BxlServer.exe` e altri processi derivati.

+ Per [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)] in [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)], il pool esterno gestisce i processi R elencati per SQL Server 2016, oltre a `python.exe`, `BxlServer.exe` e altri processi derivati.

  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
CREATE EXTERNAL RESOURCE POOL pool_name  
[ WITH (  
    [ MAX_CPU_PERCENT = value ]  
    [ [ , ] AFFINITY CPU =    
            {  
                AUTO   
              | ( <cpu_range_spec> )   
              | NUMANODE = ( <NUMA_node_id> )   
            } ]   
    [ [ , ] MAX_MEMORY_PERCENT = value ]  
    [ [ , ] MAX_PROCESSES = value ]   
    )   
]  
[ ; ]  
  
<CPU_range_spec> ::=    
{ CPU_ID | CPU_ID  TO CPU_ID } [ ,...n ]  
```  
  
## <a name="arguments"></a>Argomenti

*pool_name*  
Nome definito dall'utente per il pool di risorse esterne. *pool_name* è un valore alfanumerico, può essere composto da un massimo di 128 caratteri, deve essere univoco all'interno di un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e deve essere conforme alle regole relative agli [identificatori](../../relational-databases/databases/database-identifiers.md).  

MAX_CPU_PERCENT =*value*  
Specifica la larghezza di banda media massima della CPU ricevibile da tutte le richieste nel pool di risorse esterne in caso di contesa di CPU. *value* è un intero con impostazione predefinita 100. L'intervallo consentito per *value* è compreso tra 1 e 100.

AFFINITY {CPU = AUTO | ( \<CPU_range_spec> ) | NUMANODE = (\<NUMA_node_range_spec>)} Associa il pool di risorse esterne a CPU specifiche. Il valore predefinito è AUTO.

AFFINITY CPU = **(** \<CPU_range_spec> **)** esegue il mapping del pool di risorse esterne alle CPU [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] identificate dai valori CPU_ID dati.

Quando si usa AFFINITY NUMANODE = **(** \<NUMA_node_range_spec> **)** viene creata un'affinità tra il pool di risorse e le CPU fisiche [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] corrispondenti al nodo o all'intervallo di nodi NUMA specificato. 

MAX_MEMORY_PERCENT =*value*  
Specifica la memoria totale del server usabile dalle richieste in questo pool di risorse esterne. *value* è un intero con impostazione predefinita 100. L'intervallo consentito per *value* è compreso tra 1 e 100.

MAX_PROCESSES =*value*  
Specifica il numero massimo di processi consentiti per il pool di risorse esterne. Specificare 0 per impostare una soglia illimitata per il pool, che di conseguenza sarà limitato solo dalle risorse di computer. Il valore predefinito è 0.

## <a name="remarks"></a>Remarks

[!INCLUDE[ssDE](../../includes/ssde-md.md)] implementa il pool di risorse quando si esegue l'istruzione [ALTER RESOURCE GOVERNOR RECONFIGURE](../../t-sql/statements/alter-resource-governor-transact-sql.md).

 Per informazioni generali sui pool di risorse, vedere [Resource Governor Resource Pool](../../relational-databases/resource-governor/resource-governor-resource-pool.md) (Pool di risorse Resource Governor), [sys.resource_governor_external_resource_pools &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md) e [sys.dm_resource_governor_external_resource_pool_affinity &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md).

Per informazioni specifiche per la gestione di pool di risorse esterne usati per il machine learning, vedere [Resource governance for machine learning in SQL Server](../../advanced-analytics/r/resource-governance-for-r-services.md) (Gestione delle risorse per il machine learning in SQL Server). 

## <a name="permissions"></a>Autorizzazioni

È richiesta l'autorizzazione `CONTROL SERVER`.

## <a name="examples"></a>Esempi

L'istruzione seguente definisce un pool esterno che limita l'uso della CPU al 75% e la memoria massima al 30% della memoria disponibile nel computer.

```sql
CREATE EXTERNAL RESOURCE POOL ep_1
WITH (  
    MAX_CPU_PERCENT = 75
    , AFFINITY CPU = AUTO
    , MAX_MEMORY_PERCENT = 30
);
GO
ALTER RESOURCE GOVERNOR RECONFIGURE;
GO
```
  
## <a name="see-also"></a>Vedere anche

 [Opzione di configurazione del server external scripts enabled](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)   
 [sp_execute_external_script &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)   
 [ALTER EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-external-resource-pool-transact-sql.md)   
 [DROP EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/drop-external-resource-pool-transact-sql.md)   
 [CREATE RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-resource-pool-transact-sql.md)   
 [CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/create-workload-group-transact-sql.md)   
 [Pool di risorse di Resource Governor](../../relational-databases/resource-governor/resource-governor-resource-pool.md)   
 [sys.resource_governor_external_resource_pools &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md)   
 [sys.dm_resource_governor_external_resource_pool_affinity &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md) 

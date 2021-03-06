---
title: sp_check_dynamic_filters (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
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
- dynamic_filters_TSQL
- sp_check_TSQL
- check
- sp_check_dynamic filter
- check_TSQL
- filters_TSQL
- check_dynamic_filters_TSQL
- dynamic filters
- filters
- check dynamic filters
- sp_check_dynamic filter_TSQL
- sp_check_for_sync_trigger_TSQL
- sp_check
helpviewer_keywords:
- sp_check_dynamic_filters
ms.assetid: dd7760db-a3a5-460f-bd97-b8d436015e19
caps.latest.revision: 23
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 248a5234a0620ce18122723db7bce88c61201758
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32990046"
---
# <a name="spcheckdynamicfilters-transact-sql"></a>sp_check_dynamic_filters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Visualizza informazioni sulle proprietà dei filtri di riga con parametri per una pubblicazione, specificando in particolare le funzioni utilizzate per generare una partizione di dati filtrati per una pubblicazione e se la pubblicazione consente l'utilizzo di partizioni pre-calcolate. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_check_dynamic_filters [ @publication = ] 'publication'  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@publication**=] **'***pubblicazione***'**  
 Nome della pubblicazione. *pubblicazione* viene **sysname**, non prevede alcun valore predefinito.  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**can_use_partition_groups**|**bit**|Specifica se la pubblicazione consente l'utilizzo di partizioni pre-calcolate; dove **1** significa che le partizioni calcolate possono essere utilizzate, e **0** significa che non possono essere utilizzate.|  
|**has_dynamic_filters**|**bit**|È se è stato definito il filtro di almeno una riga con parametri della pubblicazione; dove **1** significa che esistono uno o più filtri di riga con parametri, e **0** significa che non esistono filtri dinamici.|  
|**dynamic_filters_function_list**|**nvarchar(500)**|Elenco delle funzioni utilizzate per filtrare gli articoli di una pubblicazione, separate con un punto e virgola.|  
|**validate_subscriber_info**|**nvarchar(500)**|Elenco delle funzioni utilizzate per filtrare gli articoli di una pubblicazione, separate con un segno più (+).|  
|**uses_host_name**|**bit**|Se il [HOST_NAME ()](../../t-sql/functions/host-name-transact-sql.md) funzione viene utilizzata nei filtri di riga con parametri, in cui **1** indica che questa funzione viene utilizzata per i filtri dinamici.|  
|**uses_suser_sname**|**bit**|Se il [SUSER_SNAME ()](../../t-sql/functions/suser-sname-transact-sql.md) funzione viene utilizzata nei filtri di riga con parametri, in cui **1** indica che questa funzione viene utilizzata per i filtri dinamici.|  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_check_dynamic_filters** viene utilizzata nella replica di tipo merge.  
  
 Se una pubblicazione è stata definita per l'utilizzo di partizioni pre-calcolate, **sp_check_dynamic_filters** verifica la presenza di eventuali violazioni delle restrizioni di partizioni pre-calcolate. Se viene rilevata una qualsiasi violazione, viene restituito un errore. Per altre informazioni, vedere [Ottimizzare le prestazioni dei filtri con parametri con le partizioni pre-calcolate](../../relational-databases/replication/merge/parameterized-filters-optimize-for-precomputed-partitions.md).  
  
 Se una pubblicazione è stata definita in modo da includere filtri di riga con parametri ma non viene rilevato alcun filtro, viene restituito un errore.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server o **db_owner** ruolo predefinito del database possono eseguire **sp_check_dynamic_filters**.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione delle partizioni di una pubblicazione di tipo Merge con filtri con parametri](../../relational-databases/replication/publish/manage-partitions-for-a-merge-publication-with-parameterized-filters.md)   
 [sp_check_join_filter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-check-join-filter-transact-sql.md)   
 [sp_check_subset_filter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-check-subset-filter-transact-sql.md)  
  
  

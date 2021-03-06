---
title: sys.dm_xe_session_targets (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_xe_session_targets
- dm_xe_session_targets_TSQL
- dm_xe_session_targets
- sys.dm_xe_session_targets_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_xe_session_targets dynamic management view
- extended events [SQL Server], views
ms.assetid: 76fbc3e1-ad88-4a47-8bf1-471c3bee5ad8
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 95adcb1dfaaf5fb25a78703936608bfed75f4c39
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/23/2018
---
# <a name="sysdmxesessiontargets-transact-sql"></a>sys.dm_xe_session_targets (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce informazioni sulle destinazioni della sessione.  
  
  |Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|event_session_address|**varbinary(8)**|Indirizzo di memoria della sessione dell'evento. Ha una relazione molti-a-uno con sys.dm_xe_sessions.address. Non ammette i valori Null.|  
|target_name|**nvarchar(60)**|Nome della destinazione in una sessione. Non ammette i valori Null.|  
|target_package_guid|**uniqueidentifier**|GUID del pacchetto che contiene la destinazione. Non ammette i valori Null.|  
|execution_count|**bigint**|Numero di volte in cui la destinazione è stata eseguita per la sessione. Non ammette i valori Null.|  
|execution_duration_ms|**bigint**|Tempo totale di esecuzione della destinazione, espresso in millisecondi. Non ammette i valori Null.|  
|target_data|**nvarchar(max)**|Dati che la destinazione gestisce, ad esempio informazioni di aggregazione di evento. Ammette i valori Null.|  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione VIEW SERVER STATE per il server.  
  
### <a name="relationship-cardinalities"></a>Cardinalità delle relazioni  
  
|From|Per|Relazione|  
|----------|--------|------------------|  
|sys.dm_xe_session_targets.event_session_address|sys.dm_xe_sessions.address|Molti-a-uno|  
  
## <a name="change-history"></a>Cronologia modifiche  
  
|Contenuto aggiornato|  
|---------------------|  
|Correzione relativa al tipo di dati della colonna target_data.|  
|Correzione della descrizione della colonna target_data per indicare che sono ammessi valori Null.|  
|Correzione della tabella "Cardinalità delle relazioni".|  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
  
  


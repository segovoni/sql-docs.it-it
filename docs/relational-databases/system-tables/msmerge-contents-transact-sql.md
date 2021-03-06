---
title: MSmerge_contents (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSmerge_contents
- MSmerge_contents_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_contents system table
ms.assetid: 8d68a61a-683f-4b20-92f9-c0a8d9ba0ad1
caps.latest.revision: 19
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4643b0ba6bdfd9eea4405be02ca481133f0db096
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39101559"
---
# <a name="msmergecontents-transact-sql"></a>MSmerge_contents (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **MSmerge_contents** tabella contiene una riga per ogni riga modificata nel database corrente dopo la pubblicazione. Questa tabella viene utilizzata durante il processo di unione per determinare le righe modificate. Questa tabella è archiviata nei database di pubblicazione e di sottoscrizione.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**tablenick**|**int**|Nome alternativo della tabella pubblicata.|  
|**rowguid**|**uniqueidentifier**|Identificatore della riga specificata.|  
|**generazione**|**bigint**|La generazione della riga identificata per il **tablenick** e **rowguid**.|  
|**partchangegen**|**bigint**|Generazione associata all'ultima modifica dei dati che potrebbe aver modificato l'appartenenza della riga a una pubblicazione filtrata.|  
|**derivazione**|**varbinary(501)**|Coppie di nome alternativo del Sottoscrittore e numero di versione utilizzate per memorizzare una cronologia delle modifiche apportate alla riga.|  
|**colvl**|**varbinary(7489)**|Informazioni sulla versione della colonna.|  
|**marcatore**|**uniqueidentifier**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**logical_record_parent_rowguid**|**uniqueidentifier**|Identifica la riga padre di livello principale nel **MSmerge_contents** (dal **rowguid**) per ogni riga figlio corrispondente in un record logico.|  
|**logical_record_lineage**|**varbinary(501)**|Coppie di nome alternativo del Sottoscrittore e numero di versione utilizzate per memorizzare una cronologia delle modifiche apportate alla riga padre di livello principale in un record logico. Per tutte le righe figlio in un record logico, questo valore è NULL.|  
|**logical_relation_change_gen**|**bigint**|Valore di generazione associato all'ultima modifica che ha comportato il riallineamento nel record logico, in cui una riga esistente è stata inserita o eliminata.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  

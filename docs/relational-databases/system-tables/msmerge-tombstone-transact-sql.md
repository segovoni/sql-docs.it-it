---
title: MSmerge_tombstone (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- MSmerge_tombstone_TSQL
- MSmerge_tombstone
dev_langs: TSQL
helpviewer_keywords: MSmerge_tombstone system table
ms.assetid: 8b3fc7bf-729b-40f2-8a26-e7dfbe8ddb38
caps.latest.revision: "13"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 55644aa0543de70ca4ec11ee65a446d073ce3556
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="msmergetombstone-transact-sql"></a>MSmerge_tombstone (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **MSmerge_tombstone** tabella contiene informazioni sulle righe eliminate e consentono le eliminazioni vengano propagate ad altri sottoscrittori. Questa tabella è archiviata nei database di pubblicazione e di sottoscrizione.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**ROWGUID**|**uniqueidentifier**|Identificatore di riga.|  
|**tablenick**|**int**|Nome alternativo della tabella.|  
|**tipo**|**tinyint**|Tipo di eliminazione:<br /><br /> 1 = Eliminazione eseguita dall'utente.<br /><br /> 5 = La riga non appartiene più alla partizione filtrata.<br /><br /> 6 = Eliminazione del sistema.|  
|**derivazione**|**varbinary(249)**|Indica la versione del record eliminato e gli aggiornamenti noti al momento dell'eliminazione. Consente di utilizzare le regole per la risoluzione coerente di un conflitto quando un Sottoscrittore esegue l'aggiornamento di una riga mentre questa viene eliminata in un altro Sottoscrittore.|  
|**generazione**|**int**|Viene assegnato quando si elimina una riga. Se per un Sottoscrittore è necessaria una generazione N, vengono inviate solo rimozioni definitive con generazione >= N.|  
|**logical_record_parent_rowguid**|**uniqueidentifier**|Identificatore del record logico al quale appartiene una riga eliminata.|  
|**logical_record_lineage**|**Varbinary(501)**|Coppie di nome alternativo del Sottoscrittore e numero di versione utilizzate per memorizzare la cronologia delle eliminazioni del record logico al quale appartiene la riga corrente.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
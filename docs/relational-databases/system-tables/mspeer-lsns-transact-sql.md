---
title: MSpeer_lsns (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
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
- MSpeer_lsns
- MSpeer_lsns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSpeer_lsns system table
ms.assetid: 0ba33907-601b-4c3d-8099-2663f680a161
caps.latest.revision: 33
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: de37f4de25bef419c67af1ff858251bec4b5e543
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39101999"
---
# <a name="mspeerlsns-transact-sql"></a>MSpeer_lsns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **Mspeer_lsns** tabella viene utilizzata per eseguire il mapping di ogni transazione a una sottoscrizione in una topologia di replica peer-to-peer. Questa tabella è archiviata in tutti i database di pubblicazione in una topologia di replica peer-to-peer e nel database di sottoscrizione di tutti i Sottoscrittori di una pubblicazione peer-to-peer. Per altre informazioni su questo tipo di topologia di replica transazionale, vedere [la replica transazionale Peer-to-Peer](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md). Questa tabella è archiviata nel database di pubblicazione.  
  
## <a name="definition"></a>Definizione  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**id**|**int**|Identifica un LSN peer-to-peer.|  
|**last_updated**|**datetime**|Il **datetime** in cui è stato effettuato l'ultimo aggiornamento di riga.|  
|**originator**|**sysname**|Nome del server di pubblicazione che ha avviato la transazione.|  
|**originator_db**|**sysname**|Nome del database in cui è stata avviata la transazione.|  
|**originator_publication**|**sysname**|Nome della pubblicazione in cui è stata avviata la transazione.|  
|**originator_publication_id**|**int**|ID della pubblicazione in cui è stata avviata la transazione.|  
|**originator_db_version**|**int**|Identifica il numero di versione del database di origine.|  
|**originator_lsn**|**int**|Identifica l'LSN nella pubblicazione di origine.|  
|**originator_version**|**int**|Identifica il numero di versione del server di pubblicazione.|  
|**originator_id**|**smallint**|Identifica ogni nodo nella topologia per consentire il rilevamento dei conflitti. Per altre informazioni, vedere [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md).|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  

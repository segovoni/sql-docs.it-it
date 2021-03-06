---
title: MSpeer_conflictdetectionconfigresponse (Transact-SQL) | Microsoft Docs
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
- MSpeer_conflictdetectionconfigresponse
- MSpeer_conflictdetectionconfigresponse_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSpeer_conflictdetectionconfigureresponse
ms.assetid: 2685fb66-731d-40f7-af4b-596b9222c5d4
caps.latest.revision: 11
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 65d192cbf84ab41c0ffe9ee6dee47f7a9468e45d
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39103549"
---
# <a name="mspeerconflictdetectionconfigresponse-transact-sql"></a>MSpeer_conflictdetectionconfigresponse (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Utilizzata nella replica peer-to-peer per archiviare la risposta di ogni nodo a una richiesta di configurazione a livello di topologia. Questa tabella è archiviata nel database di pubblicazione.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|request_id|**int**|Identifica una voce di richiesta di configurazione dei conflitti nella [MSpeer_conflictdetectionconfigrequest](../../relational-databases/system-tables/mspeer-conflictdetectionconfigrequest-transact-sql.md) tabella.|  
|peer_node|**sysname**|Nome dell'istanza del server che ha generato la risposta.|  
|peer_db|**sysname**|Database di sottoscrizione del peer che ha generato la risposta.|  
|peer_version|**sysname**|Identifica il numero di versione del server di pubblicazione.|  
|peer_db_version|**sysname**|Identifica il numero di versione del database peer.|  
|is_peer|**bit**|Indica se un nodo è un Sottoscrittore di sola lettura. Un valore pari **0** indicato un sottoscrittore di sola lettura.|  
|conflict_detection_enabled|**bit**|Indica se il rilevamento dei conflitti è abilitato per la topologia.|  
|originator_id|**varbinary(16)**|Identifica ogni nodo nella topologia per consentire il rilevamento dei conflitti. Per altre informazioni, vedere [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md).|  
|peer_conflict_retention|**int**|Periodo di tempo, espresso in giorni, in cui i metadati vengono archiviati nelle tabelle dei conflitti.|  
|peer_subscriptions|**XML**|Informazioni sul nodo che ha risposto alla richiesta.|  
|progress_phase|**nvarchar(32)**|Identifica la fase di elaborazione corrente utilizzando uno dei valori seguenti:<br /><br /> Started<br /><br /> Versione peer raccolta<br /><br /> Stato raccolto|  
|modified_date|**datetime**|Data e ora del completamento di una fase.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  

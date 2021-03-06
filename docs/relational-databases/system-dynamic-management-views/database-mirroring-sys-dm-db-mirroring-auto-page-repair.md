---
title: sys.dm_db_mirroring_auto_page_repair (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_db_mirroring_auto_page_repair_TSQL
- sys.dm_db_mirroring_auto_page_repair_TSQL
- sys.dm_db_mirroring_auto_page_repair
- dm_db_mirroring_auto_page_repair
dev_langs:
- TSQL
helpviewer_keywords:
- automatic page repair
- database mirroring [SQL Server], automatic page repair
- sys.dm_db_mirroring_auto_page_repair dynamic management view
ms.assetid: 49f0fc2a-e25e-47e1-a135-563adb509af1
caps.latest.revision: 17
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: fb08f5eb710a2a258a462767382c1b6b609bec76
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/23/2018
---
# <a name="database-mirroring---sysdmdbmirroringautopagerepair"></a>Database Mirroring - Sys.dm db_mirroring_auto_page_repair
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Viene restituita una riga per ogni tentativo di correzione automatica della pagina in qualsiasi database con mirroring nell'istanza del server. Questa vista contiene le righe degli ultimi tentativi automatici di ripristino della pagina in un determinato database con mirroring, con un massimo di 100 righe per database. Non appena un database raggiunge il limite massimo, la riga per il tentativo successivo di correzione automatica della pagina sostituisce una delle voci esistenti. Nella tabella seguente viene definito il significato delle varie colonne.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|ID del database al quale corrisponde questa riga.|  
|**file_id**|**int**|ID del file in cui si trova la pagina.|  
|**page_id**|**bigint**|ID della pagina nel file.|  
|**error_type**|**int**|Tipo di errore. I valori possibili sono i seguenti.<br /><br /> **-** 1 = tutti gli errori hardware 823<br /><br /> 1 = 824 errori diversi da un errore nel checksum o di una pagina incompleta (ad esempio un ID pagina errato)<br /><br /> 2 = Errore nel checksum<br /><br /> 3 = Pagina incompleta|  
|**page_status**|**int**|La stato del tentativo di ripristino della pagina:<br /><br /> 2 = in coda per la richiesta dal partner.<br /><br /> 3 = richiesta inviata al partner.<br /><br /> 4 = in coda per il ripristino automatico della pagina (risposta ricevuta dal partner).<br /><br /> 5 = il ripristino automatico della pagina è stato completato e la pagina può essere utilizzata.<br /><br /> 6 = irreparabile. Indica che si è verificato un errore durante il tentativo di ripristino della pagina, ad esempio perché la pagina è danneggiata anche per il partner, il partner è disconnesso o si è verificato un problema di rete. Questo stato non è finale; se il danno si verifica nuovamente nella pagina, questa verrà nuovamente richiesta dal partner.|  
|**modification_time**|**datetime**|Ora dell'ultima modifica dello stato della pagina.|  
  
## <a name="security"></a>Sicurezza  
  
### <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione VIEW SERVER STATE per il server.  
  
## <a name="see-also"></a>Vedere anche  
 [Correzione automatica della pagina &#40;Gruppi di disponibilità/Mirroring del database&#41;](../../sql-server/failover-clusters/automatic-page-repair-availability-groups-database-mirroring.md)   
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [suspect_pages & #40; Transact-SQL & #41;](../../relational-databases/system-tables/suspect-pages-transact-sql.md)   
 [Gestione della tabella suspect_pages &#40;SQL Server&#41;](../../relational-databases/backup-restore/manage-the-suspect-pages-table-sql-server.md)  
  
  



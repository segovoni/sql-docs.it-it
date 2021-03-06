---
title: Sys. syscacheobjects (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-compatibility-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.syscacheobjects_TSQL
- sys.syscacheobjects
- syscacheobjects
- syscacheobjects_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- syscacheobjects system table
- sys.syscacheobjects compatibility view
ms.assetid: 9b14f37c-b7f5-4f71-b070-cce89a83f69e
caps.latest.revision: 37
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: de76f70e43c7b8d4cc043be069c2b412bb03f69b
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33221982"
---
# <a name="syssyscacheobjects-transact-sql"></a>sys.syscacheobjects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene informazioni sull'utilizzo della cache.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**bucketid**|**int**|ID bucket. I valori sono compresi tra 0 e le dimensioni della directory -1. Le dimensioni della directory corrispondono a quelle della tabella hash.|  
|**cacheobjtype**|**nvarchar(17)**|Tipo di oggetto nella cache:<br /><br /> Piano compilato<br /><br /> Piano eseguibile<br /><br /> Albero di analisi<br /><br /> Cursore<br /><br /> Stored procedure estesa|  
|**objtype**|**nvarchar(8)**|Tipo di oggetto:<br /><br /> Stored procedure<br /><br /> Istruzione preparata<br /><br /> Query ad hoc ([!INCLUDE[tsql](../../includes/tsql-md.md)] inviate come eventi del linguaggio dal **sqlcmd** o **osql** utilità, invece di chiamate di procedura remota)<br /><br /> ReplProc (procedura della replica)<br /><br /> Trigger<br /><br /> Visualizza<br /><br /> Valore predefinito<br /><br /> Tabella utente<br /><br /> Tabella di sistema<br /><br /> Controlla<br /><br /> Rule|  
|**objid**|**int**|Una delle chiavi principali utilizzate per la ricerca di un oggetto nella cache. Questo è l'ID di oggetto archiviato in **sysobjects** per gli oggetti di database (procedure, viste, trigger e così via). Per gli oggetti della cache, ad esempio SQL ad hoc o preparati, **objid** è un valore generato internamente.|  
|**dbid**|**smallint**|ID del database in cui è stato compilato l'oggetto della cache.|  
|**dbidexec**|**smallint**|ID del database da cui viene eseguita la query.<br /><br /> Per la maggior parte degli oggetti, **dbidexec** ha lo stesso valore di **dbid**.<br /><br /> Per le viste di sistema, **dbidexec** è l'ID di database da cui viene eseguita la query.<br /><br /> Per le query ad hoc, **dbidexec** è 0. Ciò significa **dbidexec** ha lo stesso valore di **dbid**.|  
|**uid**|**smallint**|Indica il creatore dei piani per le query ad hoc e dei piani preparati.<br /><br /> -2 = Il batch inviato non dipende dalla risoluzione implicita del nome e può essere condiviso da diversi utenti. Questo è il metodo consigliato. Qualsiasi altro valore rappresenta l'ID dell'utente che invia la query al database.<br /><br /> Causa un errore di overflow o restituisce NULL se il numero di utenti e ruoli è maggiore di 32.767.|  
|**refCounts**|**int**|Numero degli altri oggetti della cache che fanno riferimento a questo oggetto della cache. Il valore di base è 1.|  
|**usecounts**|**int**|Numero di utilizzi dell'oggetto della cache dall'inizio.|  
|**pagesused**|**int**|Numero di pagine utilizzate dall'oggetto della cache.|  
|**setopts**|**int**|Impostazioni delle opzioni SET che hanno effetto su un piano compilato. Queste impostazioni fanno parte della chiave della cache. Eventuali modifiche dei valori di questa colonna indicano che gli utenti hanno modificato le opzioni SET. Di seguito vengono descritte alcune di queste opzioni:<br /><br /> **ANSI_PADDING**<br /><br /> **FORCEPLAN**<br /><br /> **CONCAT_NULL_YIELDS_NULL**<br /><br /> **ANSI_WARNINGS**<br /><br /> **ANSI_NULLS**<br /><br /> **QUOTED_IDENTIFIER**<br /><br /> **ANSI_NULL_DFLT_ON**<br /><br /> **ANSI_NULL_DFLT_OFF**|  
|**langid**|**smallint**|ID della lingua. ID della lingua della connessione in cui è stato creato l'oggetto della cache.|  
|**dateformat**|**smallint**|Formato della data della connessione in cui è stato creato l'oggetto della cache.|  
|**status**|**int**|Indica se l'oggetto della cache è un piano di cursore. Attualmente viene utilizzato solo il bit meno significativo.|  
|**lasttime**|**bigint**|Disponibile solo per compatibilità con le versioni precedenti. Restituisce sempre 0.|  
|**maxexectime**|**bigint**|Disponibile solo per compatibilità con le versioni precedenti. Restituisce sempre 0.|  
|**avgexectime**|**bigint**|Disponibile solo per compatibilità con le versioni precedenti. Restituisce sempre 0.|  
|**lastreads**|**bigint**|Disponibile solo per compatibilità con le versioni precedenti. Restituisce sempre 0.|  
|**lastwrites**|**bigint**|Disponibile solo per compatibilità con le versioni precedenti. Restituisce sempre 0.|  
|**sqlbytes**|**int**|Lunghezza in byte della definizione della procedura o del batch inviato.|  
|**sql**|**nvarchar(3900)**|Definizione del modulo o primi 3900 caratteri del batch inviato.|  
  
## <a name="see-also"></a>Vedere anche  
 [Viste della compatibilità &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  


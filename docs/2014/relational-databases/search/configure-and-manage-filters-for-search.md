---
title: Configurare e gestire filtri per la ricerca | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: search
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- full-text search [SQL Server], filters
- filters [full-text search]
ms.assetid: 7ccf2ee0-9854-4253-8cca-1faed43b7095
caps.latest.revision: 68
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 7b19f9141df65be952551dbb899b6cb30544e9a3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37278927"
---
# <a name="configure-and-manage-filters-for-search"></a>Configurazione e gestione di filtri per la ricerca
  Indicizzazione di documenti in un `varbinary`, `varbinary(max)`, `image`, o `xml` colonna tipo di dati necessaria un'elaborazione aggiuntiva. che devono essere eseguite mediante un filtro. Il filtro estrae le informazioni testuali dal documento rimuovendo la formattazione, quindi invia il testo al word breaker per la lingua associata alla colonna della tabella.  
  
 Un determinato filtro è specifico di un determinato tipo di documento (file con estensione doc, pdf, xls, xml e così via). Questi filtri implementano l'interfaccia IFilter. Per altre informazioni su questi tipi di documento, eseguire una query nella vista del catalogo [sys.fulltext_document_types](/sql/relational-databases/system-catalog-views/sys-fulltext-document-types-transact-sql) .  
  
 I documenti binari possono essere archiviati in una singola colonna `varbinary(max)` o `image`. Per ogni documento, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sceglie il filtro corretto da utilizzare in base all'estensione file. Poiché l'estensione non è visibile quando il file viene archiviato in una colonna `varbinary(max)` o `image`, l'estensione file (doc, docx, xls, xlsx, pdf e così via) deve essere archiviata in una colonna distinta della tabella, denominata colonna del tipo. Questa colonna può includere qualsiasi tipo di dati basato su caratteri e contiene l'estensione file del documento, ad esempio l'estensione doc per un documento di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Word. Nel **documento** nella tabella [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)], il **documento** sloupec JE typu `varbinary(max)`e la colonna con tipo **FileExtension**, JE typu `nvarchar(8)`.  
  
> [!NOTE]  
>  Un filtro potrebbe essere in grado di gestire gli oggetti incorporati nell'oggetto padre, a seconda della relativa implementazione. In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , tuttavia, i filtri non vengono configurati per seguire collegamenti ad altri oggetti.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installa i propri filtri XML e HTML. Inoltre, anche gli eventuali filtri per i formati proprietari [!INCLUDE[msCoName](../../../includes/msconame-md.md)] (con estensione DOC, XDOX, PPT e così via) già installati nel sistema operativo vengono caricati da  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Per identificare i filtri attualmente caricati in un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], usare la stored procedure [sp_help_fulltext_system_components](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql) nel modo seguente:  
  
```  
EXEC sp_help_fulltext_system_components 'filter';   
```  
  
 Per poter usare i filtri per formati non [!INCLUDE[msCoName](../../../includes/msconame-md.md)] , è tuttavia necessario caricarli manualmente nell'istanza del server. Per informazioni sull'installazione di filtri aggiuntivi, vedere [Visualizzare o modificare word breaker e filtri registrati](view-or-change-registered-filters-and-word-breakers.md).  
  
 **Per visualizzare la colonna del tipo in un indice full-text esistente**  
  
-   [sys.fulltext_index_columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql)  
  
## <a name="see-also"></a>Vedere anche  
 [sys.fulltext_index_columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql)   
 [Compatibilità FILESTREAM con altre funzionalità di SQL Server](../blob/filestream-compatibility-with-other-sql-server-features.md)  
  
  

---
title: Proprietà personalizzate della destinazione SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b736aa6d-c154-44a0-be08-f25733fca1d9
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ef78bf43e09f277873303336630da37bc01f3fd5
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2018
ms.locfileid: "35405293"
---
# <a name="sql-server-destination-custom-properties"></a>Proprietà personalizzate della destinazione SQL Server
  La destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] include sia proprietà personalizzate sia le proprietà comuni a tutti i componenti del flusso di dati.  
  
 La tabella seguente descrive le proprietà personalizzate della destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Tutte le proprietà sono di lettura/scrittura.  
  
|Nome proprietà|Tipo di dati|Descrizione|  
|-------------------|---------------|-----------------|  
|AlwaysUseDefaultCodePage|Boolean|Forza l'uso del valore della proprietà DefaultCodePage. Il valore predefinito di questa proprietà è **False**.|  
|BulkInsertCheckConstraints|Boolean|Valore che specifica se l'inserimento bulk verifica i vincoli. Il valore predefinito di questa proprietà è **True**.|  
|BulkInsertFireTriggers|Boolean|Valore che specifica se l'inserimento bulk attiva trigger nelle tabelle. Il valore predefinito di questa proprietà è **False**.|  
|BulkInsertFirstRow|Valore intero|Valore che specifica la prima riga da inserire. Il valore predefinito di questa proprietà è **-1**, che indica che non è stato assegnato alcun valore.|  
|BulkInsertKeepIdentity|Boolean|Valore che specifica se i valori possono essere inseriti in colonne Identity. Il valore predefinito di questa proprietà è **False**.|  
|BulkInsertKeepNulls|Boolean|Valore che specifica se l'inserimento bulk mantiene i valori Null. Il valore predefinito di questa proprietà è **False**.|  
|BulkInsertLastRow|Valore intero|Valore che specifica l'ultima riga da inserire. Il valore predefinito di questa proprietà è **-1**, che indica che non è stato assegnato alcun valore.|  
|BulkInsertMaxErrors|Valore intero|Valore che specifica il numero massimo di errori che possono verificarsi prima dell'arresto dell'inserimento bulk. Il valore predefinito di questa proprietà è **–1**, che indica che non è stato assegnato alcun valore.|  
|BulkInsertOrder|String|Nomi delle colonne di ordinamento. È possibile ordinare ogni colonna in ordine crescente o decrescente. Se si utilizzano più colonne di ordinamento, i nomi delle colonne saranno separati da virgole.|  
|BulkInsertTableName|String|Tabella o vista [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nel database in cui vengono copiati i dati.|  
|BulkInsertTablock|Boolean|Valore che specifica se la tabella è bloccata durante l'inserimento bulk. Il valore predefinito di questa proprietà è **True**.|  
|DefaultCodePage|Valore intero|Tabella codici da utilizzare quando le informazioni sulla tabella codici non sono disponibili dall'origine dati.|  
|MaxInsertCommitSize|Valore intero|Valore che specifica il numero massimo di righe da inserire in un batch. Quando il valore è zero, tutte le righe vengono inserite in un singolo batch.|  
|Timeout|Valore intero|Valore che specifica il numero di secondi di attesa della destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prima della chiusura se non vi sono dati disponibili per l'inserimento. Il valore 0 indica l'assenza di timeout per la destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Il valore predefinito di questa proprietà è 30.|  
  
 L'input e le colonne di input della destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non includono proprietà personalizzate.  
  
 Per altre informazioni, vedere [Destinazione SQL Server](../../integration-services/data-flow/sql-server-destination.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà comuni](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
  

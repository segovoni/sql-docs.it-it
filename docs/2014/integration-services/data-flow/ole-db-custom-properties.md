---
title: Proprietà personalizzate OLE DB | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 13a82d41-dd7a-4708-bc84-4407a536c877
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5d1f203a7c80d08de14857ea08a4fe14ecbaf3bc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37215981"
---
# <a name="ole-db-custom-properties"></a>Proprietà personalizzate OLE DB
  **Proprietà personalizzate delle origini**  
  
 L'origine OLE DB include sia proprietà personalizzate che le proprietà comuni a tutti i componenti del flusso di dati.  
  
 Nella tabella seguente vengono descritte le proprietà personalizzate dell'origine OLE DB. Tutte le proprietà sono di lettura/scrittura.  
  
|Nome proprietà|Tipo di dati|Description|  
|-------------------|---------------|-----------------|  
|AccessMode|Valore intero|Modalità utilizzata per accedere al database. I valori possibili sono **set di righe aperto**, **OPENROWSET da variabile**, `SQL Command`, e **comando SQL da variabile**. Il valore predefinito è **OpenRowset**.|  
|AlwaysUseDefaultCodePage|Boolean|Un valore che indica se utilizzare il valore della `DefaultCodePage` proprietà per ogni colonna, o per tentare di dedurre la tabella codici dalle impostazioni locali di ogni colonna. Il valore predefinito di questa proprietà è `False`.|  
|CommandTimeout|Valore intero|Numero di secondi prima del timeout del comando. Il valore 0 indica un timeout infinito.<br /><br /> Nota: questa proprietà non è disponibile in **Editor origine OLE DB**, ma può essere impostata usando **Editor avanzato**.|  
|DefaultCodePage|Valore intero|Tabella codici da utilizzare quando le informazioni sulla tabella codici non sono disponibili dall'origine dati.|  
|OpenRowset|String|Nome dell'oggetto di database utilizzato per aprire un set di righe.|  
|OpenRowsetVariable|String|Variabile che contiene il nome dell'oggetto di database utilizzato per aprire un set di righe.|  
|ParameterMapping|String|Mapping tra i parametri nel comando SQL e le variabili.|  
|SqlCommand|String|Comando SQL da eseguire.|  
|SqlCommandVariable|String|Variabile che contiene il comando SQL da eseguire.|  
  
 L'output e le colonne di output dell'origine OLE DB non includono proprietà personalizzate.  
  
 Per altre informazioni, vedere [OLE DB Source](ole-db-source.md).  
  
 **Proprietà personalizzate delle destinazioni**  
  
 La destinazione OLE DB include sia proprietà personalizzate che le proprietà comuni a tutti i componenti del flusso di dati.  
  
 Nella tabella seguente vengono descritte le proprietà personalizzate della destinazione OLE DB. Tutte le proprietà sono di lettura/scrittura.  
  
> [!NOTE]  
>  Le opzioni FastLoad elencate di seguito (FastLoadKeepIdentity, FastLoadKeepNulls e FastLoadOptions) corrispondono alle proprietà di nome simile esposte dalla `IRowsetFastLoad` interfaccia implementata dal Provider Microsoft OLE DB per SQL Server (SQLOLEDB). Per ulteriori informazioni, eseguire una ricerca di IRowsetFastLoad nel sito Web MSDN Library.  
  
|Nome proprietà|Tipo di dati|Description|  
|-------------------|---------------|-----------------|  
|AccessMode|Integer (enumerazione)|Valore che specifica la modalità di accesso della destinazione al relativo database di destinazione.<br /><br /> Di seguito vengono indicati i possibili valori della proprietà.<br /><br /> `OpenRowset` (0): specificare il nome di una tabella o vista.<br />`OpenRowset from Variable` (1): è fornire il nome di una variabile che contiene il nome di una tabella o vista.<br />`OpenRowset Using Fastload` (3): specificare il nome di una tabella o vista.<br />`OpenRowset Using Fastload from Variable` (4): è fornire il nome di una variabile che contiene il nome di una tabella o vista.<br />`SQL Command` (2): specificare un'istruzione SQL.|  
|AlwaysUseDefaultCodePage|Boolean|Un valore che indica se utilizzare il valore della `DefaultCodePage` proprietà per ogni colonna, o per tentare di dedurre la tabella codici dalle impostazioni locali di ogni colonna. Il valore predefinito di questa proprietà è `False`.|  
|CommandTimeout|Valore intero|Numero massimo di secondi durante i quali è possibile eseguire il comando SQL prima del timeout. Il valore 0 corrisponde a un intervallo infinito. Il valore predefinito di questa proprietà è 0.<br /><br /> Nota: questa proprietà non è disponibile in **Editor destinazione OLE DB**, ma può essere impostata usando **Editor avanzato**.|  
|DefaultCodePage|Valore intero|Tabella codici predefinita associata alla destinazione OLE DB.|  
|FastLoadKeepIdentity|Boolean|Valore che specifica se copiare i valori Identity durante il caricamento dei dati. Questa proprietà è disponibile solo con una delle opzioni di caricamento rapido. Il valore predefinito di questa proprietà è `False`. Questa proprietà corrisponde alla proprietà OLE DB [IRowsetFastLoad &#40;OLE DB&#41; ](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-ole-db.md) proprietà `SSPROP_FASTLOADKEEPIDENTITY`.|  
|FastLoadKeepNulls|Boolean|Valore che specifica se copiare i valori Null durante il caricamento dei dati. Questa proprietà è disponibile solo con una delle opzioni di caricamento rapido. Il valore predefinito di questa proprietà è `False`. Questa proprietà corrisponde alla proprietà OLE DB [IRowsetFastLoad &#40;OLE DB&#41; ](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-ole-db.md) proprietà `SSPROP_FASTLOADKEEPNULLS`.|  
|FastLoadMaxInsertCommitSize|Valore intero|Valore che specifica le dimensioni del batch di cui la destinazione OLE DB tenta di eseguire il commit durante le operazioni di caricamento rapido. Il valore predefinito **0**indica una singola operazione di commit in seguito all'elaborazione di tutte le righe.|  
|FastLoadOptions|String|Raccolta di opzioni di caricamento rapido. Tra le opzioni di caricamento rapido sono inclusi il blocco delle tabelle e la verifica dei vincoli. È possibile specificare una, nessuna o entrambe le opzioni. Questa proprietà corrisponde alla proprietà OLE DB IRowsetFastLoad `SSPROP_FASTLOADOPTIONS` e accetta opzioni stringa, ad esempio `CHECK_CONSTRAINTS` e `TABLOCK`.<br /><br /> Nota: alcune opzioni per questa proprietà non sono disponibili in **Editor destinazione Excel**, ma possono essere impostate usando **Editor avanzato**.|  
|OpenRowset|String|Quando AccessMode è `OpenRowset`, il nome della tabella o della vista a cui accede la destinazione OLE DB.|  
|OpenRowsetVariable|String|Quando AccessMode è `OpenRowset from Variable`, il nome della variabile che contiene il nome della tabella o della vista a cui accede la destinazione OLE DB.|  
|SqlCommand|String|Quando AccessMode è `SQL Command`, l'istruzione Transact-SQL utilizzata dalla destinazione OLE DB per specificare le colonne di destinazione per i dati.|  
  
 L'input e le colonne di input della destinazione OLE DB non includono proprietà personalizzate.  
  
 Per altre informazioni, vedere [OLE DB Destination](ole-db-destination.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà comuni](../common-properties.md)  
  
  

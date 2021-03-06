---
title: Utilizzo di segnalibri | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- bookmarks [ADO]
- Recordset object [ADO]
ms.assetid: cca244e6-84f8-4394-bca9-f7a819b8f4df
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 643d07d49e2e2ec0e31f9a677796f309fedd0d1d
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35273220"
---
# <a name="using-bookmarks"></a>Utilizzo di segnalibri
È spesso utile tornare direttamente a un record specifico dopo vari spostamenti **Recordset** senza dover scorrere ogni record e confrontare i valori. Ad esempio, se si tenta di eseguire la ricerca di un record utilizzando il **trovare** metodo ma la ricerca non restituisce alcun record, si viene automaticamente posizionati in delle estremità del **Recordset**. Se il provider supporta questa funzionalità, è possono utilizzare i segnalibri per contrassegnare la posizione prima di utilizzare il **trovare** metodo in modo da poter ritornare alla posizione dell'utente. Un segnalibro è un **Variant** tipo di valore che identifica in modo univoco un record in un **Recordset** oggetto.  
  
 È inoltre possibile utilizzare una matrice di tipo variant di segnalibri con il **filtro Recordset** metodo per filtrare un set di record selezionato. Per ulteriori informazioni su questa tecnica, vedere filtrando i risultati nell'argomento [utilizzo degli oggetti recordset](../../../ado/guide/data/working-with-recordsets.md), più avanti in questa sezione.  
  
 È possibile utilizzare il **segnalibro** proprietà per ottenere un segnalibro a un record, oppure impostare il record corrente in un **Recordset** oggetto sul record identificato da un segnalibro valido. Il codice seguente usa il **segnalibro** proprietà per impostare un segnalibro e quindi tornare al record di segnalibro dopo lo spostamento ad altri record. Per determinare se il **Recordset** supporta segnalibri, utilizzare il **supporta** metodo.  
  
```  
'BeginBookmarkEg  
Dim varBookmark As Variant  
Dim blnCanBkmrk As Boolean  
  
objRs.Open strSQL, strConnStr, adOpenStatic, adLockOptimistic, adCmdText  
  
If objRs.RecordCount > 4 Then  
    objRs.Move 4                       ' move to the fifth record  
    blnCanBkmrk = objRs.Supports(adBookmark)  
    If blnCanBkmrk = True Then  
        varBookmark = objRs.Bookmark   ' record the bookmark  
        objRs.MoveLast                 ' move to a different record  
        objRs.Bookmark = varBookmark   ' return to the bookmarked (sixth) record  
    End If  
End If  
'EndBookmarkEg  
```  
  
 Il [supporta](../../../ado/reference/ado-api/supports-method.md) metodo illustrato più dettagliatamente in seguito.  
  
 Ad eccezione del caso di clonato **recordset**, i segnalibri sono univoci per il **Recordset** in cui sono stati creati, anche se viene utilizzato lo stesso comando. Ciò significa che non è possibile utilizzare un **segnalibro** ottenuto da uno **Recordset** per spostare lo stesso record in un secondo **Recordset** aperto con lo stesso comando.

---
title: Ricerca incrementale in un documento attivo | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- searches [SQL Server Management Studio], incremental
- Query Editor [SQL Server Management Studio], incremental search
- incremental searches [SQL Server Management Studio]
ms.assetid: 490bb36c-dd43-4219-9e2a-ff27046b9395
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 15d053e71b2c2ac156bbd32e548ecd926384eefe
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37213051"
---
# <a name="search-an-active-document-incrementally"></a>Ricerca incrementale in un documento attivo
  È possibile eseguire una ricerca incrementale in un singolo documento o in una singola finestra immettendo il testo. Verrà evidenziato il primo set di caratteri che corrisponde ai caratteri immessi durante la ricerca incrementale nel documento o nella finestra. La ricerca viene estesa automaticamente a tutto il testo all'interno di un documento o di una finestra, fatta eccezione per il testo nascosto.  
  
 Se viene scelta l'opzione **Maiuscole/minuscole** , per la ricerca incrementale verranno usati i criteri della ricerca precedente. Se, ad esempio, in precedenza è stata eseguita una ricerca su più file tramite la finestra di dialogo **Cerca nei file** , viene selezionata l'opzione **Maiuscole/minuscole**e quindi viene eseguita una ricerca incrementale. Nella ricerca verrà fatta distinzione tra maiuscole e minuscole.  
  
### <a name="to-search-incrementally"></a>Per eseguire una ricerca incrementale  
  
1.  Aprire il file o la finestra in cui si desidera eseguire la ricerca.  
  
2.  Scegliere **Avanzate** dal menu **Modifica**e quindi fare clic su **Ricerca incrementale**.  
  
     L'icona del cursore si trasforma in un binocolo con una freccia, che indica la direzione della ricerca, mentre sulla barra di stato viene visualizzato "Ricerca incrementale".  
  
3.  Iniziare a digitare la stringa di testo.  
  
     Sulla barra di stato viene visualizzato il testo immesso mentre l'editor evidenzia la prima occorrenza corrispondente. Mentre la digitazione continua, l'editor si sposta sulla corrispondenza successiva e la evidenzia. Se non viene trovata nessuna corrispondenza, sulla barra di stato viene visualizzato quanto segue.  
  
    ```  
    Incremental Search: <text> (not found)  
    ```  
  
 Le ricerche incrementali vengono eseguite procedendo verso il basso e da sinistra a destra a partire dalla posizione corrente nel documento. È possibile utilizzare i tasti di scelta rapida.  
  
> [!NOTE]  
>  Per un elenco completo dei tasti di scelta rapida, vedere [Tasti di scelta rapida di SQL Server Management Studio](../../ssms/sql-server-management-studio-keyboard-shortcuts.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Ricerca e sostituzione](search-and-replace.md)   
 [Ricerca interattiva all'interno di documenti](search-documents-interactively.md)   
 [Ricerca nei documenti utilizzando gli elenchi dei risultati](search-documents-using-results-lists.md)   
 [Testo di ricerca con caratteri jolly](search-text-with-wildcards.md)   
 [Eseguire ricerche di testo con espressioni regolari](search-text-with-regular-expressions.md)  
  
  
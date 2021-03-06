---
title: Controllo della concorrenza | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- transactions [ODBC], concurrency control
- concurrency control [ODBC]
ms.assetid: 75e4adb3-3d43-49c5-8c5e-8df96310d912
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2fd05a84e70b601180ce67a94cbdc4caabf7e37e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32910316"
---
# <a name="concurrency-control"></a>Controllo della concorrenza
*Concorrenza* è la possibilità di due transazioni utilizzano gli stessi dati nello stesso momento e delle transazioni isolamento in genere comporta una riduzione. In questo modo l'isolamento delle transazioni viene in genere implementata da blocco di righe e come vengono bloccate altre righe, numero di transazioni può essere completato senza almeno temporaneamente bloccate da una riga bloccata. Mentre una riduzione della concorrenza è generalmente considerato come un compromesso per i livelli di isolamento delle transazioni superiore necessari a mantenere l'integrità del database, può diventare un problema di applicazioni interattive con attività di lettura/scrittura elevata che utilizzano i cursori.  
  
 Ad esempio, si supponga che un'applicazione viene eseguita l'istruzione SQL **selezionare \* FROM Orders**. Chiama **SQLFetchScroll** per scorrere il risultato impostato e consente all'utente di aggiornare, eliminare o inserire gli ordini. Dopo che l'utente aggiorna, Elimina o inserisce un ordine, l'applicazione esegue il commit della transazione.  
  
 Se il livello di isolamento Repeatable Read, la transazione potrebbe, a seconda di come viene implementato, ogni riga restituita da bloccare **SQLFetchScroll**. Se il livello di isolamento è Serializable, la transazione potrebbe bloccare l'intera tabella Orders. In entrambi i casi, la transazione rilascia i blocchi solo quando è stato eseguito il commit o rollback. Pertanto, se l'utente impiega molto tempo lettura ordini e un tempo molto breve l'aggiornamento, eliminazione o inserendoli, la transazione è stato possibile facilmente bloccare un numero elevato di righe, rendendoli disponibili ad altri utenti.  
  
 Si tratta di un problema anche se il cursore è di sola lettura e l'applicazione consente all'utente di leggere solo gli ordini esistenti. In questo caso, il commit della transazione, l'applicazione e rilascia i blocchi, quando viene chiamata **SQLCloseCursor** (in modalità di commit automatico) o **SQLEndTran** (in modalità di commit manuale).  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Tipi di concorrenza](../../../odbc/reference/develop-app/concurrency-types.md)  
  
-   [Concorrenza ottimistica](../../../odbc/reference/develop-app/optimistic-concurrency.md)

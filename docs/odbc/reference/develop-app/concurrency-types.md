---
title: Tipi di concorrenza | Documenti Microsoft
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
- locking concurrency control [ODBC]
- optimistic concurrency [ODBC]
- read-only concurrency control [ODBC]
ms.assetid: 46762ae5-17dd-4777-968e-58156f470fe1
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6b5970995d3b8f881b62556b0f12eac96d302760
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32911856"
---
# <a name="concurrency-types"></a>Tipi di concorrenza
Per risolvere il problema di riduzione della concorrenza nei cursori, ODBC espone quattro diversi tipi di concorrenza dei cursori:  
  
-   **Sola lettura** il cursore può leggere i dati, ma non è possibile aggiornare o eliminare dati. Questo è il tipo di concorrenza predefinita. Anche se il sistema DBMS potrebbe bloccare le righe per imporre la lettura ripetibile e livelli di isolamento serializzabile, è possibile utilizzare blocchi in lettura anziché blocchi di scrittura. Questo comporta una concorrenza più elevata poiché almeno possono leggere i dati.  
  
-   **Blocco** il cursore utilizza il livello più basso di blocco necessario per assicurarsi che può aggiornare o eliminare righe nel set di risultati. Ciò comporta in genere i livelli di concorrenza molto bassa, soprattutto a livelli di isolamento Repeatable Read e Serializable.  
  
-   **La concorrenza ottimistica con le versioni di riga e la concorrenza ottimistica con valori** il cursore utilizza la concorrenza ottimistica: aggiorna o Elimina righe solo se poiché sono stati ultima lettura non sono stati modificati. Per rilevare le modifiche, confronta le versioni delle righe o valori. Non c'è garanzia che il cursore sarà in grado di aggiornare o eliminare una riga, ma la concorrenza è superiore rispetto a quando il blocco viene utilizzato. Per ulteriori informazioni, vedere la sezione seguente, [la concorrenza ottimistica](../../../odbc/reference/develop-app/optimistic-concurrency.md).  
  
 Un'applicazione specifica il tipo di concorrenza è richiesto il cursore da utilizzare con l'attributo di istruzione SQL_ATTR_CONCURRENCY. Per determinare i tipi supportati, chiama **SQLGetInfo** con l'opzione SQL_SCROLL_CONCURRENCY.

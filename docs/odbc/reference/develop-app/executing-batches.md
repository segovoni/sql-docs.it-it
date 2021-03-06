---
title: L'esecuzione batch | Documenti Microsoft
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
- batches [ODBC], executing
- SQL statements [ODBC], batches
ms.assetid: f082c717-4f82-4820-a2fa-ba607d8fd872
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 22c034d4be28ca8c3212fad4ee1493cb0a22d915
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32909896"
---
# <a name="executing-batches"></a>L'esecuzione di batch
Prima di un'applicazione esegue un batch di istruzioni, deve verificare se sono supportate. A tale scopo, l'applicazione chiama **SQLGetInfo** con le opzioni SQL_BATCH_SUPPORT SQL_PARAM_ARRAY_ROW_COUNTS e SQL_PARAM_ARRAY_SELECTS. La prima opzione restituisce se conteggio: generazione di riga e di creazione di set di istruzioni sono supportate in batch esplicita e procedure, mentre le due opzioni quest'ultime restituiscono informazioni sulla disponibilità del conteggio delle righe e risultato imposta nel risultato con parametri esecuzione.  
  
 Batch di istruzioni vengono eseguite tramite **SQLExecute** o **SQLExecDirect**. Ad esempio, la chiamata seguente esegue un batch di istruzioni per aprire un nuovo ordine vendita esplicito.  
  
```  
SQLCHAR *BatchStmt =  
   "INSERT INTO Orders (OrderID, CustID, OpenDate, SalesPerson, Status)"  
      "VALUES (2002, 1001, {fn CURDATE()}, 'Garcia', 'OPEN');"  
   "INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (2002, 1, 1234, 10);"  
   "INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (2002, 2, 987, 8);"  
   "INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (2002, 3, 566, 17);"  
   "INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (2002, 4, 412, 500)";  
  
SQLExecDirect(hstmt, BatchStmt, SQL_NTS);  
```  
  
 Quando un batch di generazione di risultati istruzioni viene eseguita, restituisce uno o più i conteggi delle righe o risultato imposta. Per informazioni su come recuperare questi, vedere [più risultati](../../../odbc/reference/develop-app/multiple-results.md).  
  
 Se un batch di istruzioni include marcatori di parametro, queste sono numerate in ordine crescente l'ordine dei parametri come se fossero in qualsiasi altra istruzione. Ad esempio, il batch di istruzioni seguente ha parametri numerati da 1 a 21; quelli nel primo **inserire** istruzione sono numerate 1 a 5 e quelli nelle ultime **inserire** istruzione vengono numerati 18 a 21.  
  
```  
INSERT INTO Orders (OrderID, CustID, OpenDate, SalesPerson, Status)  
   VALUES (?, ?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
```  
  
 Per ulteriori informazioni sui parametri, vedere [parametri dell'istruzione](../../../odbc/reference/develop-app/statement-parameters.md), più avanti in questa sezione.

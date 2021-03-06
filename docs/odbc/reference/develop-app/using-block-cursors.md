---
title: Utilizzo di cursori a blocchi | Documenti Microsoft
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
- cursors [ODBC], block
- block cursors [ODBC]
- result sets [ODBC], block cursors
ms.assetid: 2aad7d6b-216e-47e7-b3cb-f95ad096f21a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1bca1bc96ac1c2582bab592a80d65639944e0766
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32915237"
---
# <a name="using-block-cursors"></a>Utilizzo di cursori a blocchi
Supporto per cursori a blocchi viene compilato in ODBC 3. *x*. **SQLFetch** può essere usato solo per operazioni di recupero più righe quando viene chiamato in ODBC 3. *x*; se un database ODBC 2. *x* applicazione chiama **SQLFetch**, il report verrà aperto solo un singola riga-cursore forward only. Quando un'applicazione ODBC 3. *x* applicazione chiama **SQLFetch** in un'API ODBC 2. *x* driver, restituisce una singola riga, a meno che il driver supporta **SQLExtendedFetch**. Per ulteriori informazioni, vedere [cursori a blocchi, i cursori scorrevoli e compatibilità con le versioni precedenti](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) nell'appendice g: Driver le linee guida per la compatibilità con le versioni precedenti.  
  
 Per utilizzare cursori a blocchi, l'applicazione imposta le dimensioni del set di righe, associa i buffer di set di righe (come descritto nella sezione precedente), facoltativamente imposta gli attributi di istruzione SQL_ATTR_ROWS_FETCHED_PTR e vengono impostati SQL_ATTR_ROW_STATUS_PTR e chiamate **SQLFetch**  o **SQLFetchScroll** per recuperare un blocco di righe. L'applicazione può modificare le dimensioni del set di righe e associare nuovi buffer di set di righe (chiamando **SQLBindCol** o specificando un offset di associazione) anche dopo le righe recuperate.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Dimensione del set di righe](../../../odbc/reference/develop-app/rowset-size.md)  
  
-   [Numero di righe recuperate e stato](../../../odbc/reference/develop-app/number-of-rows-fetched-and-status.md)  
  
-   [SQLGetData e cursori a blocchi; bloccare un cursore](../../../odbc/reference/develop-app/sqlgetdata-and-block-cursors.md)

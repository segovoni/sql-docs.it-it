---
title: Modalità asincrona e SQLCancel | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client  - "database-engine" - "docset-sql-devref"
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- asynchronous operations [SQL Server Native Client]
- SQLCancel function
- SQLSetConnectAttr function
- SQL Server Native Client, asynchronous operations
- ODBC functions
- ODBC applications, asynchronous operations
- SQL Server Native Client ODBC driver, asynchronous mode
ms.assetid: f31702a2-df76-4589-ac3b-da5412c03dc2
caps.latest.revision: 29
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4465e572aaa0068e5a5c9f84c1a6525438e75c17
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37431570"
---
# <a name="asynchronous-mode-and-sqlcancel"></a>Modalità asincrona e SQLCancel
  Alcune funzioni ODBC possono essere utilizzate in modo sincrono o in modo asincrono. Le operazioni asincrone possono essere abilitate per un handle di istruzione o per un handle di connessione. Se l'opzione viene impostata per un handle di connessione, sarà valida per tutti gli handle di istruzione nell'handle di connessione. Per abilitare o disabilitare le operazioni asincrone vengono utilizzate le istruzioni seguenti:  
  
```  
SQLSetConnectAttr(hdbc, SQL_ATTR_ASYNC_ENABLE,  
                        SQL_ASYNC_ENABLE_ON, SQL_IS_INTEGER);  
SQLSetConnectAttr(hdbc, SQL_ATTR_ASYNC_ENABLE,  
                        SQL_ASYNC_ENABLE_OFF, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ASYNC_ENABLE,  
                        SQL_ASYNC_ENABLE_ON, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ASYNC_ENABLE,  
                        SQL_ASYNC_ENABLE_OFF, SQL_IS_INTEGER);  
```  
  
 Quando una funzione ODBC viene chiamata in modalità sincrona, il driver restituisce il controllo all'applicazione solo dopo la notifica del completamento del comando da parte del server.  
  
 In modalità asincrona, il driver restituisce immediatamente il controllo all'applicazione, anche prima dell'invio del comando al server. Il driver imposta il codice restituito su SQL_STILL_EXECUTING. È quindi possibile eseguire altre operazioni.  
  
 Durante il controllo del completamento del comando, viene effettuata la stessa chiamata di funzione con gli stessi parametri al driver. Se il driver non riceve una risposta dal server, restituirà nuovamente SQL_STILL_EXECUTING. È necessario controllare periodicamente il comando finché il codice restituito non sia diverso da SQL_STILL_EXECUTING. Quando si ottiene un codice restituito diverso, anche SQL_ERROR, è possibile determinare che il comando è stato completato.  
  
 A volte un comando rimane in attesa per molto tempo. Se l'applicazione deve annullare il comando senza attendere una risposta, è possibile farlo tramite una chiamata **SQLCancel** con la stessa istruzione handle del comando in attesa. Questa è l'unica volta **SQLCancel** deve essere utilizzato. Alcuni programmatori utilizzano **SQLCancel** durante l'elaborazione a metà tra il risultato impostato e si vuole annullare il resto del set di risultati. [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) oppure [SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md) deve essere usato per annullare il resto di un set di risultati in attesa, non **SQLCancel**.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un'applicazione driver ODBC di SQL Server Native Client](creating-a-driver-application.md)  
  
  

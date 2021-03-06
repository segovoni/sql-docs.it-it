---
title: Esempio di diagnostica di Driver basati su DBMS | Documenti Microsoft
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
- DBMS-based driver diagnostic [ODBC]
- diagnostic information [ODBC], examples
- error messages [ODBC], diagnostic messages
ms.assetid: a80d54b0-43ff-4dfd-b6cb-f4694a5ed765
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2d2f26421a71edad627dcc4d89c854dbafa78766
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32910846"
---
# <a name="dbms-based-driver-diagnostic-example"></a>Esempio di diagnostica di Driver basati su DBMS
Un driver basati su DBMS invia le richieste a un sistema DBMS e restituisce informazioni per l'applicazione tramite Gestione Driver. Poiché il driver è il componente che si interfaccia con gestione Driver, viene formattato e restituisce gli argomenti per **SQLGetDiagRec**.  
  
 Ad esempio, se l'utilizzo di SQL e servizi, un driver Microsoft per Oracle Rdb ha rilevato un nome di cursore non valido, potrebbe restituire i valori seguenti **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "34000"  
Native Error:      0  
Diagnostic Msg:   "[Microsoft][ODBC Rdb Driver]Invalid cursor name: EMPLOYEE_CURSOR."  
```  
  
 Perché si è verificato l'errore nel driver, aggiungere i prefissi degli spazi per il messaggio di diagnostica per il fornitore ([Microsoft]) e il driver ([Driver ODBC Rdb]).  
  
 Se nel sistema DBMS non ha trovato la tabella dipendente, il driver potrebbe formattare e restituire i valori seguenti dal **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "42S02"  
Native Error:      -1  
Diagnostic Msg:   "[Microsoft][ODBC Rdb Driver][Rdb] %SQL-F-RELNOTDEF, Table EMPLOYEE "  
                  "is not defined in schema."  
```  
  
 Si è verificato l'errore nell'origine dati, il driver aggiunto un prefisso per l'identificatore dell'origine dati ([Rdb]) per il messaggio di diagnostica. Poiché il driver è stato componente collegato con l'origine dati, aggiungerlo prefissi per il fornitore ([Microsoft]) e l'identificatore ([Driver ODBC Rdb]) per il messaggio di diagnostica.

---
title: Mapping SQLGetConnectOption | Documenti Microsoft
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
- mapping deprecated functions [ODBC], SQLGetConnectOption
- SQLGetConnectOption function [ODBC], mapping
ms.assetid: e3792fe4-a955-473a-a297-c1b2403660c4
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9ec36a536732299337efde3cf58cc98fbf4c46e0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32906736"
---
# <a name="sqlgetconnectoption-mapping"></a>Mapping di SQLGetConnectOption
Quando un'applicazione chiama **SQLGetConnectOption** tramite un'applicazione ODBC 3*x* driver, la chiamata a  
  
```  
SQLGetConnectOption(hdbc, fOption, pvParam)   
```  
  
 è stato eseguito il mapping come indicato di seguito:  
  
-   Se *fOption* indica un'opzione di connessione definite da ODBC che restituisce una stringa, le chiamate di gestione Driver  
  
    ```  
    SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
-   Se *fOption* indica un'opzione di connessione definite da ODBC che restituisce un valore integer a 32 bit, le chiamate di gestione Driver  
  
    ```  
    SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, 0, NULL)  
    ```  
  
-   Se *fOption* indica un'opzione di istruzione definito dal driver, le chiamate di gestione Driver  
  
    ```  
    SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
 Nei tre casi precedenti, il *ConnectionHandle* argomento è impostato sul valore *hdbc*, *attributo* argomento è impostato sul valore *fOption* e *ValuePtr* argomento è impostato sullo stesso valore di *il parametro pvParam*.  
  
 Per le opzioni di connessione di stringa definite da ODBC Driver Manager imposta la *BufferLength* argomento nella chiamata a **SQLGetConnectAttr** per la lunghezza massima predefinita (SQL_MAX_OPTION_STRING_LENGTH); per un'opzione di connessione non di tipo stringa, *BufferLength* è impostato su 0.  
  
 Per un'applicazione ODBC 3*x* driver, gestione Driver non controlla se *opzione* è tra SQL_CONN_OPT_MIN e SQL_CONN_OPT_MAX, oppure è maggiore di SQL_CONNECT_OPT_DRVR_START. Il driver deve verificare la validità dei valori di opzione.

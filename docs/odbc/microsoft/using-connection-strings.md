---
title: Utilizzo delle stringhe di connessione | Documenti Microsoft
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
- connection strings [ODBC]
- connecting to data source [ODBC], Visual FoxPro
- Visual FoxPro data source [ODBC], connecting
ms.assetid: 57634960-47e9-49bf-95c1-6e3702ac8166
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 014c3cf66d18ab0b859c98e96584e73e160a6e63
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32905687"
---
# <a name="using-connection-strings"></a>Utilizzo delle stringhe di connessione
È possibile utilizzare una stringa di connessione per connettersi a un'origine dati di Visual FoxPro.  
  
 Ad esempio, per connettersi all'origine dati TasTrade e l'impostazione corrente di esclusivo associata con l'origine dati di sostituzione, utilizzare la stringa:  
  
```  
DSN=TasTrade;Exclusive=Yes  
```  
  
 Per un elenco delle parole chiave di attributo e dei valori è possibile includere nella stringa di connessione, vedere [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md).  
  
 Per una spiegazione completa della sintassi della stringa di connessione, vedere [SQLBrowseConnect](../../odbc/reference/syntax/sqlbrowseconnect-function.md) nel *riferimento per programmatori ODBC*.

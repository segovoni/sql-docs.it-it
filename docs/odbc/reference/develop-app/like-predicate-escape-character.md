---
title: COME carattere di Escape predicato | Documenti Microsoft
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
- LIKE predicate [ODBC]
- escape sequences [ODBC], LIKE predicate
ms.assetid: 185d6109-48cf-4981-bc40-ec2a4a90cafc
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 38fa73fb069f7b7a037a61af711474b277cfa0d7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32911866"
---
# <a name="like-predicate-escape-character"></a>COME carattere di Escape predicato
In un **come** predicato, il segno di percentuale (%) corrispondenze zero o più di qualsiasi carattere e il carattere di sottolineatura (_) consente di ricercare qualsiasi carattere. In base a un segno di percentuale effettivo o un carattere di sottolineatura un **come** predicato, un carattere di escape deve precedere il segno di percentuale o un carattere di sottolineatura. La sequenza di escape che definisce il **come** carattere di escape del predicato è:  
  
 **{escape '** *carattere di escape* **'}**  
  
 dove *carattere di escape* è qualsiasi carattere supportato dall'origine dati.  
  
 Per altre informazioni simili sequenza di escape, vedere [come sequenza di Escape](../../../odbc/reference/appendixes/like-escape-sequence.md) nella grammatica SQL di appendice c:.  
  
 Le istruzioni SQL seguenti, ad esempio, creano lo stesso set di risultati di cliente nomi che iniziano con i caratteri "% AAA". La prima istruzione utilizza la sintassi della sequenza di escape. La seconda istruzione utilizza la sintassi nativa per Microsoft® Access e non è interoperativa. Si noti che la percentuale del secondo carattere in ogni **come** predicato è composto da un carattere jolly che corrisponde a zero o più di qualsiasi carattere.  
  
```  
SELECT Name FROM Customers WHERE Name LIKE '\%AAA%' {escape '\'}  
  
SELECT Name FROM Customers WHERE Name LIKE '[%]AAA%'  
```  
  
 Per determinare se il **come** carattere di escape del predicato è supportata da un'origine dati, un'applicazione chiama **SQLGetInfo** con l'opzione SQL_LIKE_ESCAPE_CLAUSE.

---
title: Livelli di conformità SQL | Documenti Microsoft
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
- conformance levels [ODBC], SQL
- SQL conformance levels [ODBC]
- data sources [ODBC], conformance levels
- ODBC drivers [ODBC], conformance levels
ms.assetid: 3529df2c-a09b-4c16-9c60-eae7a06d903a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dcdb0f98d7260985e418a6eaeb670c40409c518d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32913296"
---
# <a name="sql-conformance-levels"></a>Livelli di conformità SQL
Il livello di grammatica SQL-92 supportata da un driver è indicato dal valore restituito da una chiamata a **SQLGetInfo** con il tipo di informazioni SQL_SQL_CONFORMANCE. Indica se il driver conforme ai livelli di voce, FIPS transitorio, intermedio o Full definiti in SQL-92.  
  
 Tutti i driver ODBC devono supportare la grammatica SQL minima descritto in [la grammatica SQL minima](../../../odbc/reference/appendixes/sql-minimum-grammar.md) nella grammatica SQL di appendice c:. Questa sintassi sono un subset di Entry level di SQL-92. Driver può supportare SQL aggiuntive e sia conforme a livello di voce di SQL-92, intermedio o Full o per lo standard FIPS 127-2 livello di transizione. Driver conformi a un determinato livello di SQL-92 o FIPS 127-2 possibile supporta funzionalità aggiuntive in uno dei livelli più elevati ma non sia completamente conforme a tale livello. Per determinare se una funzionalità è supportata, un'applicazione deve chiamare **SQLGetInfo** con il tipo di informazioni appropriate. Il livello di conformità di una funzionalità SQL è descritto nel tipo di informazioni corrispondenti. (Vedere il [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) descrizione della funzione.)

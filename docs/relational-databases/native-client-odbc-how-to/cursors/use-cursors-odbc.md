---
title: Utilizzare cursori (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], how to topics
ms.assetid: c502736f-bca0-45c3-ae25-d2ad52d296bf
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: d9679dfb8cd4fecce07ff34aeb13d257381bee9a
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37409420"
---
# <a name="use-cursors-odbc"></a>Utilizzare cursori (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

    
### <a name="to-use-cursors"></a>Per utilizzare i cursori  
  
1.  Chiamare [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) per impostare gli attributi del cursore desiderati:  
  
     Impostare gli attributi SQL_ATTR_CURSOR_TYPE e SQL_ATTR_CONCURRENCY (opzione consigliata).  
  
     e  
  
     Impostare gli attributi SQL_CURSOR_SCROLLABLE e SQL_CURSOR_SENSITIVITY.  
  
2.  Chiamare [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) per impostare le dimensioni del set di righe usando l'attributo SQL_ATTR_ROW_ARRAY_SIZE.  
  
3.  Facoltativamente, è possibile chiamare [SQLSetCursorName](http://go.microsoft.com/fwlink/?LinkId=58406) per impostare un nome di cursore se gli aggiornamenti posizionati verranno eseguiti usando la clausola WHERE CURRENT OF.  
  
4.  Eseguire l'istruzione SQL.  
  
5.  Facoltativamente, è possibile chiamare [SQLGetCursorName](../../../relational-databases/native-client-odbc-api/sqlgetcursorname.md) per ottenere il nome del cursore se gli aggiornamenti posizionati verranno eseguiti usando la clausola WHERE CURRENT OF e se con [SQLSetCursorName](http://go.microsoft.com/fwlink/?LinkId=58406) non è stato fornito un nome di cursore al passaggio 3.  
  
6.  Chiamare [SQLNumResultCols](../../../relational-databases/native-client-odbc-api/sqlnumresultcols.md) per ottenere il numero di colonne (C) nel set di righe.  
  
     Utilizzare un'associazione per colonna.  
  
     \- - oppure -  
  
     Utilizzare un'associazione per riga.  
  
7.  Recuperare i set di righe dal cursore nel modo desiderato.  
  
8.  Chiamare [SQLMoreResults](../../../relational-databases/native-client-odbc-api/sqlmoreresults.md) per determinare se è disponibile un altro set di risultati.  
  
    -   Se viene restituito SQL_SUCCESS, è disponibile un altro set di risultati.  
  
    -   Se viene restituito SQL_NO_DATA, non è più disponibile alcun set di risultati.  
  
    -   Se viene restituito SQL_SUCCESS_WITH_INFO o SQL_ERROR, chiamare [SQLGetDiagRec](http://go.microsoft.com/fwlink/?LinkId=58402) per determinare se è disponibile l'output da un'istruzione PRINT o RAISERROR.  
  
     Se si utilizzano parametri di istruzione associati per i parametri di output o il valore restituito di una stored procedure, utilizzare i dati disponibili nei buffer dei parametri associati.  
  
     Quando si utilizzano parametri associati, ogni chiamata a [SQLExecute](http://go.microsoft.com/fwlink/?LinkId=58400) o [SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399) eseguirà l'istruzione SQL S volte, in cui S è il numero di elementi nella matrice dei parametri associati. Di conseguenza, vi saranno S set di risultati da elaborare, in cui ogni set di risultati comprende tutti i set di risultati, i parametri di output e i codici restituiti utilizzati normalmente da una singola esecuzione dell'istruzione SQL.  
  
     Si noti che quando un set di risultati contiene righe di calcolo, ogni riga di calcolo viene resa disponibile come set di risultati distinto. Tali set di risultati di calcolo vengono intercalati all'interno delle normali righe e le suddividono in più set di risultati.  
  
9. Facoltativamente, è possibile chiamare [SQLFreeStmt](../../../relational-databases/native-client-odbc-api/sqlfreestmt.md) con SQL_UNBIND per rilasciare qualsiasi buffer delle colonne associate.  
  
10. Se è disponibile un altro set di risultati, andare al passaggio 6.  
  
     Nel passaggio 9 la chiamata a [SQLMoreResults](../../../relational-databases/native-client-odbc-api/sqlmoreresults.md) in un set di risultati parzialmente elaborato cancella il resto del set di risultati. Un altro modo per cancellare un set di risultati parzialmente elaborato consiste nel chiamare [SQLCloseCursor](../../../relational-databases/native-client-odbc-api/sqlclosecursor.md).  
  
     È possibile controllare il tipo di cursore utilizzato impostando SQL_ATTR_CURSOR_TYPE e SQL_ATTR_CONCURRENCY oppure impostando SQL_ATTR_CURSOR_SENSITIVITY e SQL_ATTR_CURSOR_SCROLLABLE. È consigliabile non combinare i due metodi di definizione del comportamento del cursore.  
  
## <a name="see-also"></a>Vedere anche  
 [Usando procedure per cursori &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-how-to/cursors/using-cursors-how-to-topics-odbc.md)  
  
  

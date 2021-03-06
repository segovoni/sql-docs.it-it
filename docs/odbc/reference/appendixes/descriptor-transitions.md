---
title: Le transizioni descrittore | Documenti Microsoft
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
- state transitions [ODBC], descriptor
- transitioning states [ODBC], descriptor
- descriptor transitions [ODBC]
ms.assetid: 0cf24fe6-5e3c-45fa-81b8-4f52ddf8501d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 32799b8a7b78672e33da24bfac45aab1d764bb0b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32907696"
---
# <a name="descriptor-transitions"></a>Descrittore transizioni
Descrittori ODBC sono i seguenti tre stati.  
  
|State|Description|  
|-----------|-----------------|  
|D0|Descrittore non allocato|  
|D1i|Descrittore allocato in modo implicito|  
|D1e|Descrittore allocato in modo esplicito|  
  
 Le tabelle seguenti illustrano come ogni funzione ODBC influisce sullo stato del descrittore.  
  
## <a name="sqlallochandle"></a>SQLAllocHandle  
  
|D0<br /><br /> Non allocato|D1i<br /><br /> Implicito|D1e<br /><br /> Esplicito|  
|------------------------|----------------------|----------------------|  
|D1i [1]|--|--|  
|D1e [2]|--|--|  
  
 [1] questa riga vengono mostrate le transizioni quando *HandleType* è stato impostato su SQL_HANDLE_STMT.  
  
 [2] questa riga vengono mostrate le transizioni quando *HandleType* stato SQL_HANDLE_DESC.  
  
## <a name="sqlcopydesc"></a>SQLCopyDesc  
  
|D0<br /><br /> Non allocato|D1i<br /><br /> Implicito|D1e<br /><br /> Esplicito|  
|------------------------|----------------------|----------------------|  
|(IH)|--|--|  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
  
|D0<br /><br /> Non allocato|D1i<br /><br /> Implicito|D1e<br /><br /> Esplicito|  
|------------------------|----------------------|----------------------|  
|--[1]|D0|--|  
|(QUALI) [2]|(HY017)|D0|  
  
 [1] questa riga vengono mostrate le transizioni quando *HandleType* è stato impostato su SQL_HANDLE_STMT.  
  
 [2] questa riga vengono mostrate le transizioni quando *HandleType* stato SQL_HANDLE_DESC.  
  
## <a name="sqlgetdescfield-and-sqlgetdescrec"></a>SQLGetDescField e SQLGetDescRec  
  
|D0<br /><br /> Non allocato|D1i<br /><br /> Implicito|D1e<br /><br /> Esplicito|  
|------------------------|----------------------|----------------------|  
|(IH)|--|--|  
  
## <a name="sqlsetdescfield-and-sqlsetdescrec"></a>SQLSetDescField e SQLSetDescRec  
  
|D0<br /><br /> Non allocato|D1i<br /><br /> Implicito|D1e<br /><br /> Esplicito|  
|------------------------|----------------------|----------------------|  
|(QUALI) [1]|--|--|  
  
 [1] questa riga vengono mostrate le transizioni quando *DescriptorHandle* è l'handle di un ARD, APD o IPD, o (per **SQLSetDescField**) quando *DescriptorHandle* è l'handle di un IRD. e *FieldIdentifier* era SQL_DESC_ARRAY_STATUS_PTR o SQL_DESC_ROWS_PROCESSED_PTR.  
  
## <a name="all-other-odbc-functions"></a>Tutte le altre funzioni ODBC  
  
|D0<br /><br /> Non allocato|D1i<br /><br /> Implicito|D1e<br /><br /> Esplicito|  
|------------------------|----------------------|----------------------|  
|--|--|--|

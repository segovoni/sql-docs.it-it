---
title: Metodo Next (SQLServerResultSet) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerResultSet.next
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 60248447-6908-4036-a779-a501453cd553
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fa878b809af8dab927877f8af0db3d54a6a3eb30
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32840826"
---
# <a name="next-method-sqlserverresultset"></a>Metodo Next (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Sposta il cursore di una riga verso il basso dalla posizione corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean next()  
```  
  
## <a name="return-value"></a>Valore restituito  
 **true** se la nuova riga corrente è valida. **false** se non sono presenti altre righe da elaborare.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo successivo viene specificato dal metodo nell'interfaccia Java.SQL. ResultSet successivo.  
  
 Un cursore del set di risultati viene posizionato inizialmente prima della prima riga. La prima chiamata al metodo successivo rende la prima riga della riga corrente, la seconda chiamata rende la seconda riga quella corrente e così via.  
  
 Se un flusso di input è aperto per la riga corrente, una chiamata al metodo successivo in modo implicito chiuderà. Una catena di avviso per il [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto viene cancellato durante la lettura di una nuova riga.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  

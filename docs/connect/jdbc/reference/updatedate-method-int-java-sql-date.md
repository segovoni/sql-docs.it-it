---
title: Metodo updateDate (int, Java.SQL. date) | Documenti Microsoft
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
- SQLServerResultSet.updateDate (int, java.sql.Date)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c5fb1292-a5cf-4cdd-8c4a-d1679944a6d0
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cb9a9a7480d77101dd024d68e39a069577960233
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32851036"
---
# <a name="updatedate-method-int-javasqldate"></a>Metodo updateDate (int, java.sql.Date)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aggiorna la colonna designata con un valore di data in base all'indice di colonna.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void updateDate(int index,  
                       java.sql.Date x)  
```  
  
#### <a name="parameters"></a>Parametri  
 *index*  
  
 Un **int** che indica l'indice di colonna.  
  
 *x*  
  
 Valore di data.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo updateDate viene specificato dal metodo updateDate nell'interfaccia Java.SQL. ResultSet.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo updateDate &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatedate-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  

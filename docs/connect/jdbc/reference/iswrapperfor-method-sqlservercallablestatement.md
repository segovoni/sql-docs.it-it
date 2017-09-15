---
title: Metodo isWrapperFor (SQLServerCallableStatement) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 71156863-3588-453e-b5a5-0573b2c1bebf
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6f9dbbea767628235a468cb595b7e4a74068a41a
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="iswrapperfor-method-sqlservercallablestatement"></a>Metodo isWrapperFor (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Indica se questo oggetto istruzione è un wrapper per l'interfaccia specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean isWrapperFor(Class iface)  
```  
  
#### <a name="parameters"></a>Parametri  
 *iface*  
  
 Oggetto **classe** che definisce un'interfaccia.  
  
## <a name="return-value"></a>Valore restituito  
 **true** se l'oggetto implementa l'interfaccia o esegue il wrapping di un oggetto che implementa l'interfaccia. In caso contrario, **false**.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Il [isWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlservercallablestatement.md) (metodo) e [unwrap](../../../connect/jdbc/reference/unwrap-method-sqlservercallablestatement.md) metodo definiti dall'interfaccia Java.SQL, che è stata introdotta in JDBC 4.0.  
  
 Se questo metodo restituisce **true**, la chiamata [unwrap](../../../connect/jdbc/reference/unwrap-method-sqlservercallablestatement.md) con lo stesso argomento avrà esito positivo.  
  
 Per ulteriori informazioni, vedere [wrapper e interfacce](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Unwrap (metodo) &#40; SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/unwrap-method-sqlservercallablestatement.md)   
 [Membri di SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Classe SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
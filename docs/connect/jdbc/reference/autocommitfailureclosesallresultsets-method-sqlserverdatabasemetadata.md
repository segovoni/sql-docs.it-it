---
title: Driver JDBC chiusa set di risultati aperti | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 1739ecb5-e5cb-4807-b5a8-97c0299929d0
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 88db086e2620ae1548382133e0536542d91035fe
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32829186"
---
# <a name="autocommitfailureclosesallresultsets-method-sqlserverdatabasemetadata"></a>Metodo autoCommitFailureClosesAllResultSets (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Indica se tramite il driver JDBC vengono chiusi tutti i set di risultati aperti, inclusi quelli trattenibili, quando è abilitata una modalità di commit automatico e viene generata un'eccezione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean autoCommitFailureClosesAllResultSets()  
```  
  
## <a name="return-value"></a>Valore restituito  
 **true** se aperto il risultato set, inclusi quelli trattenibili, vengono chiusi quando è abilitato un commit automatico e viene generata un'eccezione. In caso contrario, **false**.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo autoCommitFailureClosesAllResultSets viene specificato dal metodo autoCommitFailureClosesAllResultSets nell'interfaccia DatabaseMetaData.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

---
title: Metodo insertsAreDetected (SQLServerDatabaseMetaData) | Documenti Microsoft
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
- SQLServerDatabaseMetaData.insertsAreDetected
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f296cc42-9d26-48c3-a360-bcf51c31f7fb
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a4883b1e6baece15e5ef01ddbefc6d4eb5143cb8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32840576"
---
# <a name="insertsaredetected-method-sqlserverdatabasemetadata"></a>Metodo insertsAreDetected (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera o meno in cui è possibile rilevare un inserimento riga visibile chiamando il metodo [rowInserted](../../../connect/jdbc/reference/rowinserted-method-sqlserverresultset.md) metodo il [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) classe.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean insertsAreDetected(int type)  
```  
  
#### <a name="parameters"></a>Parametri  
 *type*  
  
 Integer che indica il tipo di set di risultati che può essere uno dei valori seguenti, in base a quanto definito in java.sql.ResultSet o SQLServerResultSet:  
  
## <a name="javasqlresultset-types"></a>Tipi java.sql.ResultSet  
 TYPE_FORWARD_ONLY  
  
 TYPE_SCROLL_SENSITIVE  
  
 TYPE_SCROLL_INSENSITIVE  
  
## <a name="sqlserverresultset-types"></a>Tipi SQLServerResultSet  
 TYPE_SS_SCROLL_STATIC  
  
 TYPE_SS_SCROLL_KEYSET  
  
 TYPE_SS_DIRECT_FORWARD_ONLY  
  
 TYPE_SS_SERVER_CURSOR_FORWARD_ONLY  
  
 TYPE_SS_SCROLL_DYNAMIC  
  
## <a name="return-value"></a>Valore restituito  
 **true** se è possibile rilevare l'inserimento della riga. In caso contrario, **false**.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo insertsAreDetected viene specificato dal metodo insertsAreDetected nell'interfaccia DatabaseMetaData.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] non rileva le righe inserite per qualsiasi tipo di cursore.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

---
title: Metodo (lang) getClientInfo | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e8e632c4-d6cc-4c5e-b6ad-873579343b19
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d221477af9d39b65c359712682132e15a54fce25
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32833176"
---
# <a name="getclientinfo-method-javalangstring"></a>Metodo getClientInfo (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il valore di una proprietà delle informazioni client specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.lang.String getClientInfo (java.lang.String name)  
```  
  
#### <a name="parameters"></a>Parametri  
 *name*  
  
 Stringa che contiene il nome della proprietà delle informazioni client da recuperare.  
  
## <a name="return-value"></a>Valore restituito  
 Stringa che contiene il valore della proprietà delle informazioni client.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getClientInfo viene specificato dal metodo getClientInfo nell'interfaccia Java.SQL. Connection.  
  
 Il [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] non supporta alcuna proprietà delle informazioni client. Di conseguenza, questo metodo restituisce **null**.  
  
 Analogamente, le applicazioni possono utilizzare il [getClientInfoProperties](../../../connect/jdbc/reference/getclientinfoproperties-method-sqlserverdatabasemetadata.md) metodo il [SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md) classe per recuperare un elenco di proprietà delle informazioni client supportate dal driver. Il [getClientInfoProperties](../../../connect/jdbc/reference/getclientinfoproperties-method-sqlserverdatabasemetadata.md) metodo restituisce un set di risultati vuoto.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getClientInfo &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/getclientinfo-method-sqlserverconnection.md)   
 [Membri di SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  

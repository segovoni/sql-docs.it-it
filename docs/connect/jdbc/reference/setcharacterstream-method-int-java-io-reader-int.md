---
title: Metodo setCharacterStream (int, Java.IO. Reader, int) | Documenti Microsoft
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
- SQLServerPreparedStatement.setCharacterStream
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 139a5b74-8d7d-41cf-991a-a142349c58f6
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 06d5f6721efb91f3e92a9ba778bb4b43d8b08da4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32843166"
---
# <a name="setcharacterstream-method-int-javaioreader-int"></a>Metodo setCharacterStream (int, java.io.Reader, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta il parametro designato sull'oggetto Reader specificato, che contiene il numero specificato di caratteri.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public final void setCharacterStream(int n,  
                                     java.io.Reader reader,  
                                     int length)  
```  
  
#### <a name="parameters"></a>Parametri  
 *n*  
  
 Un **int** che indica il numero di parametro.  
  
 *Lettore*  
  
 Un oggetto del lettore.  
  
 *lunghezza*  
  
 Numero di caratteri.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo setCharacterStream viene specificato dal metodo setCharacterStream nell'interfaccia Java.SQL. PreparedStatement.  
  
 Se la lunghezza del flusso è diversa rispetto a quella specificata nel *lunghezza* parametro, il driver JDBC genera un'eccezione quando viene inserita o aggiornata la riga.  
  
 Se la lunghezza del flusso è sconosciuta, il *lunghezza* parametro può essere impostato su -1 per indicare che il driver deve accettare il flusso indipendentemente dalla lunghezza. Con sqljdbc4.jar, si consiglia di utilizzare il metodo di JDBC 4.0 [metodo setCharacterStream &#40;int, java.io.Reader&#41; ](../../../connect/jdbc/reference/setcharacterstream-method-int-java-io-reader.md) se l'applicazione è richiesto aggiornare la colonna da un flusso la cui lunghezza è sconosciuta.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [Classe SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  

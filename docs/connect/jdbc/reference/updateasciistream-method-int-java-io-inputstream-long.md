---
title: Metodo (Java.IO. InputStream, long) updateAsciiStream | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 143bff3e-2b5c-485d-9529-1c2387560094
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 324b8f6ce1bd335ee7f322ffd38a18304423492a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32850302"
---
# <a name="updateasciistream-method-int-javaioinputstream-long"></a>Metodo updateAsciiStream (int, java.io.InputStream, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aggiorna la colonna designata con un valore del flusso ASCII, che conterrà il numero specificato di byte.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void updateAsciiStream(int columnIndex,  
                              java.io.InputStream x,  
                              long length)  
```  
  
#### <a name="parameters"></a>Parametri  
 *columnIndex*  
  
 Un **int** che indica l'indice di colonna.  
  
 *x*  
  
 Un oggetto InputStream.  
  
 *lunghezza*  
  
 Lunghezza del flusso.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo updateAsciiStream viene specificato dal metodo updateAsciiStream nell'interfaccia Java.SQL. ResultSet.  
  
 Questo metodo passa caratteri ASCII (byte) da un oggetto InputStream alle colonne di tipo carattere convertibili, l'intervallo ASCII [0x00 – 0x7F] di Unicode e 874, 932, 936, 949, 950 e 1250 a 1258 tabelle codici. Esegue una conversione nella pagina delle regole di confronto di destinazione. Se si tenta di aggiornare una colonna di destinazione non convertibile, verrà generata un'eccezione. Per le colonne binarie, vengono passati byte non elaborati.  
  
 Se la lunghezza del flusso è diversa rispetto a quella specificata nel *lunghezza* parametro, il driver JDBC genera un'eccezione quando viene inserita o aggiornata la riga.  
  
 Se la lunghezza del flusso è sconosciuta, il *lunghezza* parametro può essere impostato su -1 per indicare che il driver deve accettare il flusso indipendentemente dalla lunghezza. Con sqljdbc4.jar, si consiglia di utilizzare il metodo di JDBC 4.0 [metodo updateAsciiStream &#40;int. InputStream&#41; ](../../../connect/jdbc/reference/updateasciistream-method-int-java-io-inputstream.md) se l'applicazione è richiesto aggiornare la colonna da un flusso la cui lunghezza è sconosciuta.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo updateAsciiStream &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updateasciistream-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  

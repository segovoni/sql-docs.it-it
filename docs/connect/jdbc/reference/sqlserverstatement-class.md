---
title: Classe SQLServerStatement | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ec24963c-8b51-4838-91e9-1fbfa2347451
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 14add0b451947092946129c9388366eb10186dce
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32846276"
---
# <a name="sqlserverstatement-class"></a>Classe SQLServerStatement
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Rappresenta l'implementazione di base della funzionalità dell'istruzione JDBC.  
  
 **Pacchetto:** com.microsoft.sqlserver.jdbc  
  
 **Implementa:** [ISQLServerStatement](../../../connect/jdbc/reference/isqlserverstatement-interface.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public class SQLServerStatement  
```  
  
## <a name="remarks"></a>Osservazioni  
 La classe SQLServerStatement fornisce anche un numero di metodi di implementazione della classe base per JDBC preparata l'istruzione e le istruzioni disponibili. Il ruolo di base della classe SQLServerStatement consiste nell'eseguire istruzioni SQL e quindi restituzione dei conteggi aggiornamenti e il risultato di imposta per l'applicazione dell'utente.  
  
 Questa classe supporta l'annullamento del wrapping nella classe SQLServerStatement, l'interfaccia ISQLServerStatement e l'interfaccia Java.SQL. Statement. Per ulteriori informazioni, vedere [wrapper e interfacce](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Riferimento all'API del Driver JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  

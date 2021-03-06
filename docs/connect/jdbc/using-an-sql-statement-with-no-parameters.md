---
title: Utilizzando un'istruzione SQL senza parametri | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 4b0728bd-059b-4b71-895c-999335bc7427
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bd6fbcc2813fbd1e19078e94e4ba23b002e2818c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32851126"
---
# <a name="using-an-sql-statement-with-no-parameters"></a>Utilizzo di un'istruzione SQL senza parametri
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Per utilizzare i dati in un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database utilizzando un'istruzione SQL che non contiene parametri, è possibile utilizzare il [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md) metodo il [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) classe per restituire un [ SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) che conterrà i dati richiesti. A tale scopo, è innanzitutto necessario creare un oggetto SQLServerStatement utilizzando il [createStatement](../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md) metodo il [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) classe.  
  
 Nell'esempio seguente, una connessione aperta per la [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] database di esempio viene passato alla funzione, un'istruzione SQL viene costruita ed eseguita e quindi i risultati vengono letti dal set di risultati.  
  
 [!code[JDBC#UsingSQLWithNoParams1](../../connect/jdbc/codesnippet/Java/using-an-sql-statement-w_0_1.java)]  
  
 Per ulteriori informazioni sull'utilizzo di set di risultati, vedere [gestione dei set di risultati con il Driver JDBC](../../connect/jdbc/managing-result-sets-with-the-jdbc-driver.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Uso di istruzioni con SQL](../../connect/jdbc/using-statements-with-sql.md)  
  
  

---
title: Utilizzo delle istruzioni e i set di risultati | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: cc917534-f5f8-4844-87c8-597c48b4e06d
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 14a6f86b503cf4c0f864a881479a37314c11d528
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32852276"
---
# <a name="working-with-statements-and-result-sets"></a>Utilizzo delle istruzioni e dei set di risultati
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Quando si utilizza il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] e l'istruzione e ResultSet oggetti forniti, sono disponibili diverse tecniche che è possibile utilizzare per migliorare le prestazioni e affidabilità delle applicazioni.  
  
## <a name="use-the-appropriate-statement-object"></a>Utilizzo dell'oggetto istruzione appropriato  
 Quando si utilizza un oggetto istruzione del driver JDBC, ad esempio il [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md), [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md), o [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) oggetto, Assicurarsi che si utilizza l'oggetto sia appropriato per il processo.  
  
-   Se non dispone di parametri OUT, non è necessario utilizzare l'oggetto SQLServerCallableStatement. Utilizzare invece SQLServerStatement oppure l'oggetto SQLServerPreparedStatement.  
  
-   Se non si intende eseguire l'istruzione più volte o non è IN o OUT, non è necessario utilizzare l'oggetto SQLServerPreparedStatement o SQLServerCallableStatement. In alternativa, utilizzare l'oggetto SQLServerStatement.  
  
## <a name="use-the-appropriate-concurrency-for-resultset-objects"></a>Utilizzo della concorrenza appropriata per gli oggetti ResultSet  
 Non richiedere la concorrenza aggiornabile quando si creano le istruzioni che producono i set di risultati, a meno che non si intenda aggiornare effettivamente i risultati. Il modello predefinito di cursore forward only di sola lettura è il più veloce per la lettura dei set di risultati di piccole dimensioni.  
  
## <a name="limit-the-size-of-your-result-sets"></a>Limitazione delle dimensioni dei set di risultati  
 È consigliabile utilizzare il [setMaxRows](../../connect/jdbc/reference/setmaxrows-method-sqlserverstatement.md) metodo (o sintassi SET ROWCOUNT o SELECT TOP N SQL) per limitare il numero di righe restituite da set di risultati potenzialmente di grandi dimensioni. Se si opera con set di risultati di grandi dimensioni, valutare l'opportunità di utilizzare un buffer adattivo per le risposte impostando la proprietà della stringa di connessione responseBuffering=adaptive, che corrisponde alla modalità predefinita. Questo approccio consente all'applicazione di elaborare set di risultati di grandi dimensioni senza richiedere i cursori sul lato server e di ridurre al minimo l'utilizzo della memoria dell'applicazione. Per ulteriori informazioni, vedere [utilizzando il buffer adattivo](../../connect/jdbc/using-adaptive-buffering.md).  
  
## <a name="use-the-appropriate-fetch-size"></a>Utilizzo della dimensione di recupero appropriata  
 Per i cursori server di sola lettura, il compromesso è un round trip al server rispetto alla quantità di memoria utilizzata nel driver. Per i cursori server aggiornabili, la dimensione del recupero influenza anche la sensibilità del set di risultati alle modifiche e alla concorrenza sul server. Gli aggiornamenti alle righe nel buffer di recupero corrente non sono visibili finché esplicita [refreshRow](../../connect/jdbc/reference/refreshrow-method-sqlserverresultset.md) metodo viene chiamato o fino a quando il cursore non lascia il buffer di recupero. I buffer di recupero di grandi dimensioni offriranno prestazioni migliori (meno round trip al server), ma sono meno sensibili alle modifiche e riducono la concorrenza sul server se si utilizza CONCUR_SS_SCROLL_LOCKS (1009). Per ottenere il livello massimo di sensibilità alle modifiche, utilizzare la dimensione di recupero 1. Si noti, tuttavia, che ciò comporterà un round trip al server per ogni riga recuperata.  
  
## <a name="use-streams-for-large-in-parameters"></a>Utilizzo dei flussi per parametri IN di grandi dimensioni  
 Utilizzare i flussi o i tipi di dati BLOB e CLOB che vengono materializzati in modo incrementale per gestire l'aggiornamento dei valori delle colonne di grandi dimensioni o l'invio di parametri IN di grandi dimensioni. Il driver JDBC li blocca al server in più round trip, consentendo di impostare e aggiornare i valori per i quali non è disponibile memoria sufficiente.  
  
## <a name="see-also"></a>Vedere anche  
 [Uso del driver JDBC per il miglioramento di prestazioni e affidabilità](../../connect/jdbc/improving-performance-and-reliability-with-the-jdbc-driver.md)  
  
  

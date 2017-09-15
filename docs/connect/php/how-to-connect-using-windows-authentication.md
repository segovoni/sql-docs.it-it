---
title: 'Procedura: connessione tramite l''autenticazione di Windows | Documenti Microsoft'
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connecting to the server, Windows Authentication
ms.assetid: f403a4e0-b0a8-4939-9dc1-e1209626367e
caps.latest.revision: 35
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 669ea9f70127c383f1390930a842cfee70366dd9
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="how-to-connect-using-windows-authentication"></a>Procedura: Connessione con l'autenticazione di Windows
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Per impostazione predefinita, [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] usa l'autenticazione di Windows per la connessione a SQL Server. È importante notare che nella maggior parte dei casi ciò significa che viene usata l'identità del processo del server Web o l'identità del thread (se il server Web usa l'impersonificazione) per connettersi al server e non l'identità dell'utente finale.  
  
Quando si usa l'autenticazione di Windows per la connessione a SQL Server è necessario considerare i seguenti punti:  
  
-   Le credenziali con cui viene eseguito il processo del server Web o il thread devono eseguire il mapping a un account di accesso di SQL Server valido per stabilire una connessione.  
  
-   Se SQL Server e il server Web si trovano in computer diversi, SQL Server deve essere configurato per l'abilitazione di connessioni remote.  
  
> [!NOTE]  
> Quando si stabilisce una connessione è possibile impostare attributi di connessione quali *Database* e *ConnectionPooling* . Per un elenco completo degli attributi di connessione supportati, vedere [Connection Options](../../connect/php/connection-options.md).  
  
L'autenticazione di Windows deve essere usata per connettersi a SQL Server ogni volta che è possibile per i motivi seguenti:  
  
-   Non vengono passate credenziali attraverso la rete durante l'autenticazione. I nomi utente e le password non sono incorporati nella stringa di connessione del database. In questo modo utenti non autorizzati o malintenzionati non possono ottenere le credenziali monitorando la rete o visualizzando le stringhe di connessione nei file di configurazione.  
  
-   Gli utenti sono soggetti a una gestione centralizzata degli account. Vengono applicati criteri di sicurezza, ad esempio i periodi di scadenza delle password, la lunghezza minima delle password e il blocco degli account dopo più richieste di accesso non valide.  
  
Se l'autenticazione di Windows non è un'opzione possibile, vedere [How to: Connect Using SQL Server Authentication](../../connect/php/how-to-connect-using-sql-server-authentication.md).  
  
## <a name="example"></a>Esempio  
Con il driver SQLSRV dei [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], l'esempio seguente usa l'autenticazione di Windows per connettersi a un'istanza locale di SQL Server. Dopo aver stabilito la connessione, viene richiesto al server l'account dell'utente che accede al database.  
  
Nell'esempio si presuppone che SQL Server e il database [AdventureWorks](http://go.microsoft.com/fwlink/?LinkID=67739) siano installati nel computer locale. Quando l'esempio viene eseguito dal browser, tutto l'output viene scritto nel browser.  
  
```  
<?php  
/* Specify the server and connection string attributes. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
  
/* Connect using Windows Authentication. */  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
     echo "Unable to connect.</br>";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Query SQL Server for the login of the user accessing the  
database. */  
$tsql = "SELECT CONVERT(varchar(32), SUSER_SNAME())";  
$stmt = sqlsrv_query( $conn, $tsql);  
if( $stmt === false )  
{  
     echo "Error in executing query.</br>";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Retrieve and display the results of the query. */  
$row = sqlsrv_fetch_array($stmt);  
echo "User login: ".$row[0]."</br>";  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="example"></a>Esempio  
L'esempio seguente usa il driver PDO_SQLSRV per eseguire la stessa attività dell'esempio precedente.  
  
```  
<?php  
try {  
   $conn = new PDO( "sqlsrv:Server=(local);Database=AdventureWorks", NULL, NULL);   
   $conn->setAttribute( PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION );  
}  
  
catch( PDOException $e ) {  
   die( "Error connecting to SQL Server" );   
}  
  
echo "Connected to SQL Server\n";  
  
$query = 'select * from Person.ContactType';   
$stmt = $conn->query( $query );   
while ( $row = $stmt->fetch( PDO::FETCH_ASSOC ) ){   
   print_r( $row );   
}  
?>  
```  
  
## <a name="see-also"></a>Vedere anche  
[How to: Connect Using SQL Server Authentication](../../connect/php/how-to-connect-using-sql-server-authentication.md)  
[Guida di programmazione per il driver SQL PHP](../../connect/php/programming-guide-for-php-sql-driver.md)
[Informazioni sugli esempi di codice nella documentazione](../../connect/php/about-code-examples-in-the-documentation.md)  
[Procedura: Creazione di un account di accesso di SQL Server](http://go.microsoft.com/fwlink/?LinkId=106325)  
[Procedura: Creazione di un utente del database](http://go.microsoft.com/fwlink/?LinkId=106327)  
[Gestione di utenti, ruoli e account di accesso](http://go.microsoft.com/fwlink/?LinkId=106329)  
[Separazione Schema-utente](http://go.microsoft.com/fwlink/?LinkId=106330)  
[Concedere autorizzazioni per oggetti (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=106332)  
  

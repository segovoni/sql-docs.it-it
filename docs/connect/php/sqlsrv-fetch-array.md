---
title: sqlsrv_fetch_array | Microsoft Docs
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- sqlsrv_fetch_array
apitype: NA
helpviewer_keywords:
- sqlsrv_fetch_array
- retrieving data, as an array
- API Reference, sqlsrv_fetch_array
ms.assetid: 69270b9e-0791-42f4-856d-412da39dea63
caps.latest.revision: 52
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: aab41821d2f4eb1eb3f92ce998fe440593567d0a
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35308970"
---
# <a name="sqlsrvfetcharray"></a>sqlsrv_fetch_array
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Recupera la riga successiva di dati come matrice indicizzata numericamente, matrice associativa o entrambe.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sqlsrv_fetch_array( resource $stmt[, int $fetchType [, row[, ]offset]])  
```  
  
#### <a name="parameters"></a>Parametri  
*$stmt*: risorsa di istruzione corrispondente a un'istruzione eseguita.  
  
*$fetchType* [facoltativo]: costante predefinita. Questo parametro può assumere uno dei valori elencati nella tabella seguente:  
  
|valore|Description|  
|---------|---------------|  
|SQLSRV_FETCH_NUMERIC|La riga successiva di dati viene restituita come matrice numerica.|  
|SQLSRV_FETCH_ASSOC|La riga successiva di dati viene restituita come matrice associativa. Le chiavi della matrice sono i nomi di colonna nel set di risultati.|  
|SQLSRV_FETCH_BOTH|La riga successiva di dati viene restituita come matrice numerica e matrice associativa. Si tratta del valore predefinito.|  
  
*riga* [facoltativo]: aggiunto nella versione 1.1. Uno dei valori seguenti che specifica la riga a cui accedere in un set di risultati che usa un cursore scorrevole. (Quando *riga* è specificato, *fetchtype* devono essere specificati esplicitamente, anche se si specifica il valore predefinito.)  
  
-   SQLSRV_SCROLL_NEXT  
-   SQLSRV_SCROLL_PRIOR  
-   SQLSRV_SCROLL_FIRST  
-   SQLSRV_SCROLL_LAST  
-   SQLSRV_SCROLL_ABSOLUTE  
-   SQLSRV_SCROLL_RELATIVE  
  
Per altre informazioni su questi valori, vedere [Specifica di un tipo di cursore e selezione di righe](../../connect/php/specifying-a-cursor-type-and-selecting-rows.md). Il supporto del cursore scorrevole è stato aggiunto nella versione 1.1 dei [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].  
  
*offset* [facoltativo]: usato con SQLSRV_SCROLL_ABSOLUTE e SQLSRV_SCROLL_RELATIVE per specificare la riga da recuperare. Il primo record nel set di risultati è 0.  
  
## <a name="return-value"></a>Valore restituito  
Se viene recuperata una riga di dati, viene restituita una **matrice** . Se non sono presenti altre righe da recuperare, viene restituito **null** . Se si verifica un errore, viene restituito **false** .  
  
In base al valore del parametro *$fetchType* , la **matrice** restituita può essere una **matrice**indicizzata numericamente, una **matrice**associativa o entrambe. Per impostazione predefinita, viene restituita una **matrice** con chiavi sia numeriche sia associative. Il tipo di dati di un valore nella matrice restituita corrisponderà al tipo di dati PHP predefinito. Per informazioni sui tipi di dati PHP predefiniti, vedere [Default PHP Data Types](../../connect/php/default-php-data-types.md).  
  
## <a name="remarks"></a>Remarks  
Se viene restituita una colonna senza nome, la chiave associativa per l'elemento della matrice sarà una stringa vuota (""). Ad esempio, si consideri l'istruzione Transact-SQL seguente che inserisce un valore in una tabella di database e recupera la chiave primaria generata dal server:  
  
```
INSERT INTO Production.ProductPhoto (LargePhoto) VALUES (?);  
SELECT SCOPE_IDENTITY()
```
  
Se il set di risultati restituito dal `SELECT SCOPE_IDENTITY()` parte di questa istruzione viene recuperato come matrice associativa, la chiave per il valore restituito sarà una stringa vuota ("") perché la colonna restituita non ha nome. Per evitare questa circostanza, è possibile recuperare il risultato come matrice numerica oppure specificare un nome per la colonna restituita nell'istruzione Transact-SQL. Di seguito è illustrato un modo per specificare un nome di colonna in Transact-SQL:  
  
```
SELECT SCOPE_IDENTITY() AS PictureID
```
  
Se un set di risultati contiene più colonne senza nome, alla chiave della stringa vuota ("") verrà assegnato il valore dell'ultima colonna senza nome.  
  
## <a name="example"></a>Esempio  
L'esempio seguente recupera ciascuna riga di un set di risultati in forma di **matrice**associativa. Nell'esempio si presuppone che SQL Server e il [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) database vengono installati nel computer locale. Quando si esegue l'esempio dalla riga di comando, tutto l'output viene scritto nel browser.  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Set up and execute the query. */  
$tsql = "SELECT FirstName, LastName  
         FROM Person.Contact  
         WHERE LastName='Alan'";  
$stmt = sqlsrv_query( $conn, $tsql);  
if( $stmt === false)  
{  
     echo "Error in query preparation/execution.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Retrieve each row as an associative array and display the results.*/  
while( $row = sqlsrv_fetch_array( $stmt, SQLSRV_FETCH_ASSOC))  
{  
      echo $row['LastName'].", ".$row['FirstName']."\n";  
}  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="example"></a>Esempio  
L'esempio seguente recupera ciascuna riga di un set di risultati in forma di matrice indicizzata numericamente.  
  
L'esempio recupera informazioni sui prodotti dal *Purchasing. PurchaseOrderDetail* tabella del database AdventureWorks per prodotti con una data specifica e scorte (*StockQty*) minore di un valore specificato.  
  
Nell'esempio si presuppone che SQL Server e il [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) database vengono installati nel computer locale. Quando si esegue l'esempio dalla riga di comando, tutto l'output viene scritto nel browser.  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Define the query. */  
$tsql = "SELECT ProductID,  
                UnitPrice,  
                StockedQty   
         FROM Purchasing.PurchaseOrderDetail  
         WHERE StockedQty < 3   
         AND DueDate='2002-01-29'";  
  
/* Execute the query. */  
$stmt = sqlsrv_query( $conn, $tsql);  
if ( $stmt )  
{  
     echo "Statement executed.\n";  
}   
else   
{  
     echo "Error in statement execution.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Iterate through the result set printing a row of data upon each  
iteration.*/  
while( $row = sqlsrv_fetch_array( $stmt, SQLSRV_FETCH_NUMERIC))  
{  
     echo "ProdID: ".$row[0]."\n";  
     echo "UnitPrice: ".$row[1]."\n";  
     echo "StockedQty: ".$row[2]."\n";  
     echo "-----------------\n";  
}  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
La funzione **sqlsrv_fetch_array** restituisce sempre i dati in base ai [Default PHP Data Types](../../connect/php/default-php-data-types.md). Per informazioni su come specificare il tipo di dati PHP, vedere [How to: Specify PHP Data Types](../../connect/php/how-to-specify-php-data-types.md).  
  
Se viene recuperato un campo senza nome, la chiave associativa per l'elemento della matrice sarà una stringa vuota (""). Per altre informazioni, vedere [sqlsrv_fetch_array](../../connect/php/sqlsrv-fetch-array.md).  
  
## <a name="see-also"></a>Vedere anche  
[Riferimento all'API del driver SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)

[Recupero di dati](../../connect/php/retrieving-data.md)

[Informazioni sugli esempi di codice nella documentazione](../../connect/php/about-code-examples-in-the-documentation.md)

[Guida di programmazione per i driver Microsoft per PHP per SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)
  

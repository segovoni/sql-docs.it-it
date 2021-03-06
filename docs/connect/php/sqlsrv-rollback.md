---
title: sqlsrv_rollback | Microsoft Docs
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
- sqlsrv_rollback
apitype: NA
helpviewer_keywords:
- transaction support
- API Reference, sqlsrv_rollback
- sqlsrv_rollback
ms.assetid: 6e6bac39-45af-428c-bc32-f773482562ee
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1c8be6ead0f7da39718ab77ec98af3bcfbcad041
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35309470"
---
# <a name="sqlsrvrollback"></a>sqlsrv_rollback
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Esegue il rollback della transazione corrente sulla connessione specificata e restituisce la connessione in modalità autocommit. La transazione corrente include tutte le istruzioni della connessione specificata eseguite dopo la chiamata a [sqlsrv_begin_transaction](../../connect/php/sqlsrv-begin-transaction.md) e prima delle chiamate a **sqlsrv_rollback** o [sqlsrv_commit](../../connect/php/sqlsrv-commit.md).  
  
> [!NOTE]  
> Il [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] è in modalità autocommit per impostazione predefinita. Ciò significa che viene eseguito automaticamente il commit di tutte le query al completamento dell'operazione a meno che non siano state programmate come parte di una transazione esplicita usando **sqlsrv_begin_transaction**.  
  
> [!NOTE]  
> Se **sqlsrv_rollback** viene chiamato in una connessione che non è presente in una transazione attiva e che è stata avviata con **sqlsrv_begin_transaction**, la chiamata restituisce **false** e un errore *Not in Transaction* viene aggiunto alla raccolta degli errori.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sqlsrv_rollback( resource $conn)  
```  
  
#### <a name="parameters"></a>Parametri  
*$conn*: connessione in cui la transazione è attiva.  
  
## <a name="return-value"></a>Valore restituito  
Valore booleano: **true** se è stato eseguito il rollback della transazione. In caso contrario, **false**.  
  
## <a name="example"></a>Esempio  
L'esempio seguente esegue due query come parte di una transazione. Se entrambe le query hanno esito positivo, viene eseguito il commit della transazione. Se una o entrambe le query hanno esito negativo, viene eseguito il rollback della transazione.  
  
La prima query dell'esempio inserisce un nuovo ordine di vendita nella tabella *Sales.SalesOrderDetail* del database AdventureWorks. L'ordine è per cinque unità del prodotto con ID 709. La seconda query riduce la quantità di inventario del prodotto con ID 709 di 5 unità. Queste query vengono incluse in una transazione perché entrambe le query devono essere completate correttamente per riflettere accuratamente lo stato degli ordini e la disponibilità del prodotto.  
  
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
     die( print_r( sqlsrv_errors(), true ));  
}  
  
/* Initiate transaction. */  
/* Exit script if transaction cannot be initiated. */  
if ( sqlsrv_begin_transaction( $conn) === false )  
{  
     echo "Could not begin transaction.\n";  
     die( print_r( sqlsrv_errors(), true ));  
}  
  
/* Initialize parameter values. */  
$orderId = 43659; $qty = 5; $productId = 709;  
$offerId = 1; $price = 5.70;  
  
/* Set up and execute the first query. */  
$tsql1 = "INSERT INTO Sales.SalesOrderDetail   
                     (SalesOrderID,   
                      OrderQty,   
                      ProductID,   
                      SpecialOfferID,   
                      UnitPrice)  
          VALUES (?, ?, ?, ?, ?)";  
$params1 = array( $orderId, $qty, $productId, $offerId, $price);  
$stmt1 = sqlsrv_query( $conn, $tsql1, $params1 );  
  
/* Set up and executee the second query. */  
$tsql2 = "UPDATE Production.ProductInventory   
          SET Quantity = (Quantity - ?)   
          WHERE ProductID = ?";  
$params2 = array($qty, $productId);  
$stmt2 = sqlsrv_query( $conn, $tsql2, $params2 );  
  
/* If both queries were successful, commit the transaction. */  
/* Otherwise, rollback the transaction. */  
if( $stmt1 && $stmt2 )  
{  
     sqlsrv_commit( $conn );  
     echo "Transaction was committed.\n";  
}  
else  
{  
     sqlsrv_rollback( $conn );  
     echo "Transaction was rolled back.\n";  
}  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt1);  
sqlsrv_free_stmt( $stmt2);  
sqlsrv_close( $conn);  
?>  
```  
  
Per porre l'attenzione sul comportamento delle transazioni, una parte della gestione degli errori consigliata non è inclusa nell'esempio. Nel caso di un'applicazione di produzione è consigliabile ricercare eventuali errori in tutte le chiamate a una funzione **sqlsrv** e gestirli di conseguenza.  
  
> [!NOTE]  
> Non usare Transact-SQL incorporato per l'esecuzione delle transazioni. Ad esempio, non eseguire un'istruzione con "BEGIN TRANSACTION" come query Transact-SQL per iniziare una transazione. Il comportamento transazionale previsto non può essere garantito quando si usa Transact-SQL incorporato per l'esecuzione delle transazioni.  
  
## <a name="see-also"></a>Vedere anche  
[Riferimento all'API del driver SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)

[Procedura: Eseguire le transazioni](../../connect/php/how-to-perform-transactions.md)

[Panoramica dei driver Microsoft per PHP per SQL Server](../../connect/php/overview-of-the-php-sql-driver.md) 
  

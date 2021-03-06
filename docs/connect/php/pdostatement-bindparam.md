---
title: 'Pdostatement:: Bindparam | Documenti Microsoft'
ms.custom: ''
ms.date: 05/22/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 65212058-2632-47a4-ba7d-2206883abf09
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 683ee4dcfd797f49ccd297f0a88f8fc607ea7aae
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35308314"
---
# <a name="pdostatementbindparam"></a>PDOStatement::bindParam
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Associa un parametro a un segnaposto denominato o punto interrogativo nell'istruzione SQL.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
bool PDOStatement::bindParam($parameter, &$variable[, $data_type[, $length[, $driver_options]]]);  
```  
  
#### <a name="parameters"></a>Parametri  
$*parametro*: un identificatore del parametro (misto). Per un'istruzione che usa segnaposti denominati, utilizzare un nome di parametro (: nome). Per un'istruzione preparata utilizzando la sintassi punto interrogativo, si tratta dell'indice in base 1 del parametro.  
  
&$*variabile*: il nome (misto) della variabile PHP da associare al parametro dell'istruzione SQL.  
  
$*data_type*: (intero) facoltativo PDO::PARAM_ * costante. Il valore predefinito è PDO::PARAM_STR.  
  
$*lunghezza*: lunghezza (intero) facoltativa del tipo di dati. È possibile specificare PDO:: sqlsrv_param_out_default_size per indicare la dimensione predefinita quando si usa PDO:: param_int o PDO:: param_bool in $*data_type*.  
  
$*driver_options*: le opzioni specifiche del driver (miste) facoltative. Ad esempio, è possibile specificare PDO::SQLSRV_ENCODING_UTF8 per associare la colonna a una variabile come stringa codificata in UTF-8.  
  
## <a name="return-value"></a>Valore restituito  
TRUE in caso di esito positivo; in caso contrario, FALSE.  
  
## <a name="remarks"></a>Remarks  
Quando si associano dati null alle colonne del server di tipo varbinary, binary o varbinary (max) è necessario specificare la codifica binaria (PDO:: sqlsrv_encoding_binary) usando $*driver_options*. Per ulteriori informazioni sulle costanti di codifica, vedere [costanti](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md).  
  
Nella versione 2.0 dei [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]è stato aggiunto il supporto per PDO.  

## <a name="example"></a>Esempio  
In questo esempio viene illustrato che dopo l'associazione di $contact al parametro, la modifica del valore non modifica il valore passato nella query.  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO("sqlsrv:server=$server ; Database = $database", "", "");  
  
$contact = "Sales Agent";  
$stmt = $conn->prepare("select * from Person.ContactType where name = ?");  
$stmt->bindParam(1, $contact);  
$contact = "Owner";  
$stmt->execute();  
  
while ($row = $stmt->fetch(PDO::FETCH_ASSOC)) {  
   print "$row[Name]\n\n";  
}  
  
$stmt = null;  
$contact = "Sales Agent";  
$stmt = $conn->prepare("select * from Person.ContactType where name = :contact");  
$stmt->bindParam(':contact', $contact);  
$contact = "Owner";  
$stmt->execute();  
  
while ($row = $stmt->fetch(PDO::FETCH_ASSOC)) {  
   print "$row[Name]\n\n";  
}  
?>  
```  
  
## <a name="example"></a>Esempio  
In questo esempio di codice viene illustrato come accedere a un parametro di output.  
  
```  
<?php  
$database = "Test";  
$server = "(local)";  
$conn = new PDO("sqlsrv:server=$server ; Database = $database", "", "");  
  
$input1 = 'bb';  
  
$stmt = $conn->prepare("select ? = count(*) from Sys.tables");  
$stmt->bindParam(1, $input1, PDO::PARAM_STR, 10);  
$stmt->execute();  
echo $input1;  
?>  
```  
  
> [!NOTE]
> Quando si associa un parametro di output a un tipo bigint, se il valore può finire di fuori dell'intervallo di un [integer](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md), l'utilizzo di PDO:: param_int con PDO:: sqlsrv_param_out_default_size potrebbe generare un'eccezione di "valore non compreso nell'intervallo". Pertanto, in alternativa, usare il valore predefinito PDO:: param_str e indicano le dimensioni della stringa risulta, che è al massimo 21. È il numero massimo di cifre, incluso il segno negativo, di qualsiasi valore bigint. 

## <a name="example"></a>Esempio  
In questo esempio di codice viene illustrato come usare un parametro di input/output.  
  
```  
<?php  
   $database = "AdventureWorks";  
   $server = "(local)";  
   $dbh = new PDO("sqlsrv:server=$server ; Database = $database", "", "");  
  
   $dbh->query("IF OBJECT_ID('dbo.sp_ReverseString', 'P') IS NOT NULL DROP PROCEDURE dbo.sp_ReverseString");  
   $dbh->query("CREATE PROCEDURE dbo.sp_ReverseString @String as VARCHAR(2048) OUTPUT as SELECT @String = REVERSE(@String)");  
   $stmt = $dbh->prepare("EXEC dbo.sp_ReverseString ?");  
   $string = "123456789";  
   $stmt->bindParam(1, $string, PDO::PARAM_STR | PDO::PARAM_INPUT_OUTPUT, 2048);  
   $stmt->execute();  
   print $string;   // Expect 987654321  
?>  
```  

> [!NOTE]
> È consigliabile utilizzare le stringhe come input durante l'associazione di valori da un [colonna decimal o numeric](../../t-sql/data-types/decimal-and-numeric-transact-sql.md) per garantire la precisione e l'accuratezza PHP limitate precisione per [numeri a virgola mobile](http://php.net/manual/en/language.types.float.php). Lo stesso vale per le colonne di tipo bigint, soprattutto quando i valori sono di fuori dell'intervallo di un [integer](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md).

## <a name="example"></a>Esempio  
In questo esempio di codice viene illustrato come associare un valore decimale come parametro di input.  

```
<?php  
$database = "Test";  
$server = "(local)";  
$conn = new PDO("sqlsrv:server=$server ; Database = $database", "", "");  

// Assume TestTable exists with a decimal field 
$input = 9223372036854.80000;
$stmt = $conn->prepare("INSERT INTO TestTable (DecimalCol) VALUES (?)");
// by default it is PDO::PARAM_STR, rounding of a large input value may
// occur if PDO::PARAM_INT is specified
$stmt->bindParam(1, $input, PDO::PARAM_STR);
$stmt->execute();
```


## <a name="see-also"></a>Vedere anche  
[Classe PDOStatement](../../connect/php/pdostatement-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  

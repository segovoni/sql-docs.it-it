---
title: Tipi di dati PHP predefinito | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- default data types
- converting data types
ms.assetid: b66c301d-3d20-45b8-a112-225d8f01c0bd
caps.latest.revision: 40
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 432b09a03f9f0d7704ed50de92db64417b624ba8
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35307700"
---
# <a name="default-php-data-types"></a>Tipi di dati PHP predefiniti
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Quando si recuperano dati dal server, i [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] convertono i dati in un tipo di dati PHP predefinito se non è stato specificato alcun tipo di dati PHP dall'utente.  
  
Quando vengono restituiti dati mediante il driver PDO_SQLSRV, il tipo di dati sarà int o string.  
  
Nella parte restante di questo argomento sono descritti i tipi di dati predefiniti del driver SQLSRV.  
  
Nella tabella seguente sono elencati i tipi di dati di SQL Server (recuperati dal server), i tipi di dati PHP predefiniti (nei quali vengono convertiti i dati), nonché la codifica predefinita per i flussi e le stringhe. Per informazioni dettagliate su come specificare i tipi di dati durante il recupero di dati dal server, vedere [How to: Specify PHP Data Types](../../connect/php/how-to-specify-php-data-types.md).  
  
|Tipo di SQL Server|Tipo PHP predefinito|Codifica predefinita|  
|-------------------|--------------------|--------------------|  
|BIGINT|String|caratteri a 8 bit<sup>1</sup>|  
|BINARY|Stream<sup>2</sup>|Binario<sup>3</sup>|  
|bit|Valore intero|caratteri a 8 bit<sup>1</sup>|  
|char|String|caratteri a 8 bit<sup>1</sup>|  
|date<sup>4</sup>|DATETIME|Non applicabile|  
|Data/ora<sup>4</sup>|DATETIME|Non applicabile|  
|datetime2<sup>4</sup>|DATETIME|Non applicabile|  
|datetimeoffset<sup>4</sup>|DATETIME|Non applicabile|  
|Decimal|String|caratteri a 8 bit<sup>1</sup>|  
|FLOAT|float|caratteri a 8 bit<sup>1</sup>|  
|geography|Stream|Binario<sup>3</sup>|  
|geometry|Stream|Binario<sup>3</sup>|  
|immagine<sup>5</sup>|Stream<sup>2</sup>|Binario<sup>3</sup>|  
|INT|Valore intero|caratteri a 8 bit<sup>1</sup>|  
|money|String|caratteri a 8 bit<sup>1</sup>|  
|NCHAR|String|caratteri a 8 bit<sup>1</sup>|  
|NUMERIC|String|caratteri a 8 bit<sup>1</sup>|  
|NVARCHAR|String|caratteri a 8 bit<sup>1</sup>|  
|nvarchar(MAX)|Stream<sup>2</sup>|caratteri a 8 bit<sup>1</sup>|  
|ntext<sup>6</sup>|Stream<sup>2</sup>|caratteri a 8 bit<sup>1</sup>|  
|REAL|float|caratteri a 8 bit<sup>1</sup>|  
|smalldatetime|DATETIME|caratteri a 8 bit<sup>1</sup>|  
|SMALLINT|Valore intero|caratteri a 8 bit<sup>1</sup>|  
|SMALLMONEY|String|caratteri a 8 bit<sup>1</sup>|  
|sql_variant<sup>7</sup>|String|caratteri a 8 bit<sup>1</sup>|  
|testo<sup>8</sup>|Stream<sup>2</sup>|caratteri a 8 bit<sup>1</sup>|  
|time<sup>4</sup>|DATETIME|Non applicabile|  
|TIMESTAMP|String|caratteri a 8 bit<sup>1</sup>|  
|TINYINT|Valore intero|caratteri a 8 bit<sup>1</sup>|  
|UDT (tipo definito dall'utente)|Stream<sup>2</sup>|Binario<sup>3</sup>|  
|UNIQUEIDENTIFIER|Stringa<sup>9</sup>|caratteri a 8 bit<sup>1</sup>|  
|varbinary|Stream<sup>2</sup>|Binario<sup>3</sup>|  
|varbinary(MAX)|Stream<sup>2</sup>|Binario<sup>3</sup>|  
|varchar|String|caratteri a 8 bit<sup>1</sup>|  
|varchar(MAX)|Stream<sup>2</sup>|caratteri a 8 bit<sup>1</sup>|
|xml|Stream<sup>2</sup>|caratteri a 8 bit<sup>1</sup>|  
  

1.  I dati vengono restituiti come caratteri a 8 bit come specificato nella tabella codici delle impostazioni locali di Windows impostate nel sistema. Eventuali caratteri multibyte o che non eseguano il mapping in questa tabella codici vengono sostituiti con un carattere a byte singolo punto interrogativo (?).  
  
2.  Se [sqlsrv_fetch_array](../../connect/php/sqlsrv-fetch-array.md) oppure [sqlsrv_fetch_object](../../connect/php/sqlsrv-fetch-object.md) viene utilizzato per recuperare dati con un tipo PHP predefinito Stream, i dati viene restituiti sotto forma di stringa con la stessa codifica del flusso. Ad esempio, se un Server SQL binario tipo viene recuperato utilizzando **sqlsrv_fetch_array**, il tipo restituito predefinito è una stringa binaria.  
  
3.  I dati vengono restituiti come flusso di byte non elaborati proveniente dal server senza alcuna codifica o conversione.  

4.  I tipi date e time possono essere recuperati come stringhe. Per altre informazioni, vedere [Procedura: Recuperare il tipo data e ora come stringhe usando il driver SQLSRV](../../connect/php/how-to-retrieve-date-and-time-type-as-strings-using-the-sqlsrv-driver.md).  

5.  Si tratta di un tipo legacy che esegue il mapping al tipo varbinary(max).

6. Si tratta di un tipo legacy che esegue il mapping al tipo nvarchar(max).

7.  sql_variant non è supportato nei parametri di output o bidirezionale.

8.  Si tratta di un tipo legacy che esegue il mapping al tipo varchar(max).  
  
9.  UNIQUEIDENTIFIER sono GUID rappresentati dall'espressione regolare seguente:  
  
    [0-9-fA-F] {8}-[0-9-fA-F]{4}-[0-9-fA-f]{4}-[0-9-fA-f]{4}-[0-9-fA-F]{12}  
 
 
## <a name="other-new-sql-server-2008-data-types-and-features"></a>Nuovi tipi di dati e funzionalità di SQL Server 2008  
Tipi di dati che sono nuovi in SQL Server 2008 e presenti all'esterno delle colonne (ad esempio i parametri con valori di tabella) non sono supportati nel [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]. Nella tabella seguente viene riepilogato il supporto PHP per le nuove funzionalità di SQL Server 2008.  
  
|Funzionalità|Supporto PHP|  
|-----------|---------------|  
|Parametro con valori di tabella|no|  
|Colonne di tipo sparse|Partial|  
|Compressione bit Null|Sì|  
|Tipi CLR definiti dall'utente di grandi dimensioni (UDT)|Sì|  
|Nome dell'entità servizio|no|  
|MERGE|Sì|  
|FILESTREAM|Partial|  
  
Il supporto dei tipi parziale indica che non è possibile eseguire una query a livello di programmazione per il tipo della colonna.  
  
## <a name="see-also"></a>Vedere anche  
[Costanti &#40;driver Microsoft per PHP per SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)

[Converting Data Types](../../connect/php/converting-data-types.md)

[Tipi PHP](http://php.net/manual/en/language.types.php)

[Tipi di dati (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)

[sqlsrv_field_metadata](../../connect/php/sqlsrv-field-metadata.md)  
  

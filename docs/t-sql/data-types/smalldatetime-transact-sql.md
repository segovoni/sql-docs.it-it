---
title: smalldatetime (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 7/22/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- smalldatetime_TSQL
- smalldatetime
dev_langs:
- TSQL
helpviewer_keywords:
- time [SQL Server], data types
- smalldatetime data type [SQL Server]
- dates [SQL Server], data types
- date and time [SQL Server], smalldatetime
- data types [SQL Server], date and time
ms.assetid: 68b74610-d54c-4c8e-b4b2-7e3747546ee0
caps.latest.revision: 50
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 8b77039bf95967038bc2dd1df9efbd3bb6faba16
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37415990"
---
# <a name="smalldatetime-transact-sql"></a>smalldatetime (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Definisce una data combinata con un'ora del giorno. L'ora si basa su un formato di 24 ore, con secondi sempre a zero (: 00) e senza secondi frazionari.
  
> [!NOTE]  
>  Usare i tipi di dati **time**, **date**, **datetime2** e **datetimeoffset** per la creazione di nuovo codice. Questi tipi sono conformi allo standard SQL. e offrono una migliore portabilità. **time**, **datetime2** e **datetimeoffset** offrono una maggiore precisione dei secondi. **datetimeoffset** offre il supporto del fuso orario per le applicazioni distribuite globalmente.  
  
## <a name="smalldatetime-description"></a>Descrizione di smalldatetime
  
|||  
|-|-|  
|Sintassi|**smalldatetime**|  
|Utilizzo|DECLARE @MySmalldatetime **smalldatetime**<br /><br /> CREATE TABLE Table1 ( Column1 **smalldatetime** )|  
|Formati predefiniti dei valori letterali stringa<br /><br /> (utilizzato per client legacy)|Non applicabile|  
|Intervallo di date|da 01-01-1900 a 06-06-2079<br /><br /> Da 1 gennaio 1900 a 6 giugno 2079|  
|Intervallo di ore|Da 00:00:00 a 23:59:59<br /><br /> 2007-05-09 23:59:59 verrà arrotondato a<br /><br /> 2007-05-10 00:00:00|  
|Intervalli di elementi|AAAA rappresenta un numero di quattro cifre, compreso tra 1900 e 2079, indicante l'anno.<br /><br /> MM rappresenta un numero di due cifre compreso tra 01 e 12 indicante un mese dell'anno specificato.<br /><br /> GG rappresenta un numero di due cifre compreso tra 01 e 31, a seconda del mese, indicante il giorno del mese specificato.<br /><br /> hh rappresenta un numero di due cifre compreso tra 00 e 23 indicante l'ora.<br /><br /> mm rappresenta un numero di due cifre compreso tra 00 e 59 indicante i minuti.<br /><br /> ss rappresenta un numero di due cifre compreso tra 00 e 59 indicante i secondi. I valori minori o uguali a 29,998 secondi vengono arrotondati al minuto per difetto. I valori maggiori o uguali a 29,999 secondi vengono arrotondati al minuto per eccesso.|  
|Lunghezza in caratteri|Massimo 19 posizioni|  
|Dimensioni dello spazio di archiviazione|4 byte, fissa.|  
|Accuratezza|Un minuto|  
|Valore predefinito|1900-01-01 00:00:00|  
|Calendario|Gregoriano<br /><br /> Non è incluso l'intervallo completo di anni.|  
|Precisione in secondi frazionari definita dall'utente|no|  
|Considerazione e conservazione delle differenze di fuso orario|no|  
|Considerazione dell'ora legale|no|  
  
## <a name="ansi-and-iso-8601-compliance"></a>Conformità agli standard ANSI e ISO 8601  
**smalldatetime** non è conforme agli standard ANSI o ISO 8601.
  
## <a name="converting-date-and-time-data"></a>Conversione dei dati relativi a data e ora
Nella conversione di tipi di dati relativi alla data e all'ora, in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono rifiutati tutti i valori non riconosciuti come date o orari. Per informazioni sull'uso delle funzioni CAST e CONVERT con i dati relativi a data e ora, vedere [CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md).
  
### <a name="converting-smalldatetime-to-other-date-and-time-types"></a>Conversione del tipo di dati smalldatetime in altri tipi di dati relativi a data e ora
Nella sezione seguente viene descritto il risultato della conversione di un tipo di dati **smalldatetime** in altri tipi di dati relativi a data e ora.
  
Nel caso della conversione a **date** vengono copiati l'anno, il mese e il giorno. Nel codice seguente vengono illustrati i risultati della conversione di un valore `smalldatetime` in un valore `date`.
  
```sql
DECLARE @smalldatetime smalldatetime = '1955-12-13 12:43:10';  
DECLARE @date date = @smalldatetime  
  
SELECT @smalldatetime AS '@smalldatetime', @date AS 'date';  
  
--Result  
--@smalldatetime          date  
------------------------- ----------  
--1955-12-13 12:43:00     1955-12-13  
--  
--(1 row(s) affected)  
```  
  
Nel caso della conversione a **time(n)** vengono copiate le ore, i minuti e i secondi. I secondi frazionari sono impostati su 0. Nel codice seguente vengono illustrati i risultati della conversione di un valore `smalldatetime` in un valore `time(4)`.
  
```sql
DECLARE @smalldatetime smalldatetime = '1955-12-13 12:43:10';  
DECLARE @time time(4) = @smalldatetime;  
  
SELECT @smalldatetime AS '@smalldatetime', @time AS 'time';  
  
--Result  
--@smalldatetime          time  
------------------------- -------------  
--1955-12-13 12:43:00     12:43:00.0000  
--  
--(1 row(s) affected)  
```  
  
Nel caso della conversione a **datetime** il valore **smalldatetime** viene copiato nel valore **datetime**. I secondi frazionari sono impostati su 0. Nel codice seguente vengono illustrati i risultati della conversione di un valore `smalldatetime` in un valore `datetime`.
  
```sql
DECLARE @smalldatetime smalldatetime = '1955-12-13 12:43:10';  
DECLARE @datetime datetime = @smalldatetime;  
  
SELECT @smalldatetime AS '@smalldatetime', @datetime AS 'datetime';  
  
--Result  
--@smalldatetime          datetime  
------------------------- -----------------------  
--1955-12-13 12:43:00     1955-12-13 12:43:00.000  
--  
--(1 row(s) affected)  
```  
  
Nel caso della conversione a **datetimeoffset(n)** il valore **smalldatetime** viene copiato nel valore **datetimeoffset(n)**. I secondi frazionari vengono impostati su 0, mentre la differenza di fuso orario viene impostata su +00:0. Nel codice seguente vengono illustrati i risultati della conversione di un valore `smalldatetime` in un valore `datetimeoffset(4)`.
  
```sql
DECLARE @smalldatetime smalldatetime = '1955-12-13 12:43:10';  
DECLARE @datetimeoffset datetimeoffset(4) = @smalldatetime;  
  
SELECT @smalldatetime AS '@smalldatetime', @datetimeoffset AS 'datetimeoffset(4)';  
  
--Result  
--@smalldatetime          datetimeoffset(4)  
------------------------- ------------------------------  
--1955-12-13 12:43:00     1955-12-13 12:43:00.0000 +00:0  
--  
--(1 row(s) affected)  
```  
  
Nel caso della conversione a **datetime2(n)** il valore **smalldatetime** viene copiato nel valore **datetime2(n)**. I secondi frazionari sono impostati su 0. Nel codice seguente vengono illustrati i risultati della conversione di un valore `smalldatetime` in un valore `datetime2(4)`.
  
```sql
DECLARE @smalldatetime smalldatetime = '1955-12-13 12:43:10';  
DECLARE @datetime2 datetime2(4) = @smalldatetime;  
  
SELECT @smalldatetime AS '@smalldatetime', @datetime2 AS ' datetime2(4)';  
  
--Result  
--@smalldatetime           datetime2(4)  
------------------------- ------------------------  
--1955-12-13 12:43:00     1955-12-13 12:43:00.0000  
--  
--(1 row(s) affected)  
```  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-casting-string-literals-with-seconds-to-smalldatetime"></a>A. Cast di valori letterali stringa con secondi a smalldatetime  
Nell'esempio seguente viene confrontata la conversione dei secondi nei valori letterali stringa in `smalldatetime`.
  
```sql
SELECT   
     CAST('2007-05-08 12:35:29'     AS smalldatetime)  
    ,CAST('2007-05-08 12:35:30'     AS smalldatetime)  
    ,CAST('2007-05-08 12:59:59.998' AS smalldatetime);  
```  
  
|Input|Output|  
|---|---|
|2007-05-08 12:35:29|2007-05-08 12:35:00|  
|2007-05-08 12:35:30|2007-05-08 12:36:00|  
|2007-05-08 12:59:59.998|2007-05-08 13:00:00|  
  
### <a name="b-comparing-date-and-time-data-types"></a>B. Confronto dei tipi di dati di data e ora  
Nell'esempio seguente vengono confrontati i risultati dell'esecuzione del cast di una stringa ai tipi di dati relativi a data e ora.
  
```sql
SELECT   
     CAST('2007-05-08 12:35:29. 1234567 +12:15' AS time(7)) AS 'time'   
    ,CAST('2007-05-08 12:35:29. 1234567 +12:15' AS date) AS 'date'   
    ,CAST('2007-05-08 12:35:29.123' AS smalldatetime) AS   
        'smalldatetime'   
    ,CAST('2007-05-08 12:35:29.123' AS datetime) AS 'datetime'   
    ,CAST('2007-05-08 12:35:29. 1234567 +12:15' AS datetime2(7)) AS   
        'datetime2'  
    ,CAST('2007-05-08 12:35:29.1234567 +12:15' AS datetimeoffset(7)) AS   
        'datetimeoffset';  
```  
  
|Tipo di dati|Output|  
|---|---|
|**time**|12:35:29. 1234567|  
|**data**|2007-05-08|  
|**smalldatetime**|2007-05-08 12:35:00|  
|**datetime**|2007-05-08 12:35:29.123|  
|**datetime2**|2007-05-08 12:35:29. 1234567|  
|**datetimeoffset**|2007-05-08 12:35:29.1234567 +12:15|  
  
## <a name="see-also"></a>Vedere anche
[CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
  

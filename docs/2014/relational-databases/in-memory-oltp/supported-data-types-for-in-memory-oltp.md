---
title: Tipi di dati supportati | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a7380ef0-c9d7-49e4-b6de-fad34752b9f3
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3f967b7cf4c20492f7e7d46ad9b8f9a2556042e7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37195311"
---
# <a name="supported-data-types"></a>Tipi di dati supportati
  I seguenti tipi di dati sono **supportato** nelle tabelle ottimizzate per la memoria e stored procedure compilate in modo nativo:  
  
 **Tipi di dati numerici**  
  
|Tipo di dati|Per ulteriori informazioni|  
|---------------|--------------------------|  
|INT|[int, bigint, smallint e tinyint &#40;Transact-SQL&#41;](/sql/t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql)|  
|BIGINT|[int, bigint, smallint e tinyint &#40;Transact-SQL&#41;](/sql/t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql)|  
|SMALLINT|[int, bigint, smallint e tinyint &#40;Transact-SQL&#41;](/sql/t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql)|  
|TINYINT|[int, bigint, smallint e tinyint &#40;Transact-SQL&#41;](/sql/t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql)|  
|Decimal|[decimal e numeric &#40;Transact-SQL&#41;](/sql/t-sql/data-types/decimal-and-numeric-transact-sql)|  
|NUMERIC|[decimal e numeric &#40;Transact-SQL&#41;](/sql/t-sql/data-types/decimal-and-numeric-transact-sql)|  
|FLOAT|[float e real &#40;Transact-SQL&#41;](/sql/t-sql/data-types/float-and-real-transact-sql)|  
|REAL|[float e real &#40;Transact-SQL&#41;](/sql/t-sql/data-types/float-and-real-transact-sql)|  
|money|[money e smallmoney &#40;Transact-SQL&#41;](/sql/t-sql/data-types/money-and-smallmoney-transact-sql)|  
|SMALLMONEY|[money e smallmoney &#40;Transact-SQL&#41;](/sql/t-sql/data-types/money-and-smallmoney-transact-sql)|  
  
 **Tipi di dati stringa**  
  
|Tipo di dati|Per ulteriori informazioni|  
|---------------|--------------------------|  
|char(n)|[char e varchar &#40;Transact-SQL&#41;](/sql/t-sql/data-types/char-and-varchar-transact-sql)|  
|varchar (n) <sup>1</sup>|[char e varchar &#40;Transact-SQL&#41;](/sql/t-sql/data-types/char-and-varchar-transact-sql)|  
|nchar(n)|[nchar e nvarchar &#40;Transact-SQL&#41;](/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql)|  
|nvarchar (n) <sup>1</sup>|[nchar e nvarchar &#40;Transact-SQL&#41;](/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql)|  
|sysname|[nchar e nvarchar &#40;Transact-SQL&#41;](/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql)|  
  
 <sup>1</sup> limitazione è 8060 byte per totale di riga, conteggiando (n) in tipi a lunghezza variabile.  
  
 Per informazioni sulle regole di confronto supportate, vedere [Collations and Code Pages](../../database-engine/collations-and-code-pages.md).  
  
 **Tipi di dati di data e ora**  
  
|Tipo di dati|Per ulteriori informazioni|  
|---------------|--------------------------|  
|Data|[Data &#40;Transact-SQL&#41;](/sql/t-sql/data-types/date-transact-sql)|  
|time|[time &#40;Transact-SQL&#41;](/sql/t-sql/data-types/time-transact-sql)|  
|DATETIME|[datetime &#40;Transact-SQL&#41;](/sql/t-sql/data-types/datetime-transact-sql)|  
|datetime2|[datetime2 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/datetime2-transact-sql)|  
|smalldatetime|[smalldatetime &#40;Transact-SQL&#41;](/sql/t-sql/data-types/smalldatetime-transact-sql)|  
  
 **Tipi di dati binari**  
  
|Tipo di dati|Per ulteriori informazioni|  
|---------------|--------------------------|  
|bit|[bit &#40;Transact-SQL&#41;](/sql/t-sql/data-types/bit-transact-sql)|  
|binary(n)|[binary e varbinary &#40;Transact-SQL&#41;](/sql/t-sql/data-types/binary-and-varbinary-transact-sql)|  
|varbinary (n) <sup>1</sup>|[binary e varbinary &#40;Transact-SQL&#41;](/sql/t-sql/data-types/binary-and-varbinary-transact-sql)|  
  
 <sup>1</sup> limitazione è 8060 byte per totale di riga, conteggiando (n) in tipi a lunghezza variabile.  
  
 **Altri tipi di dati**  
  
|Tipo di dati|Per ulteriori informazioni|  
|---------------|--------------------------|  
|UNIQUEIDENTIFIER|[uniqueidentifier &#40;Transact-SQL&#41;](/sql/t-sql/data-types/uniqueidentifier-transact-sql)|  
  
 **Tipi di dati non supportato**  
  
 I tipi di dati indicati di seguito non sono supportati:  
  
||||  
|-|-|-|  
|DATETIMEOFFSET|GEOGRAPHY|GEOMETRY|  
|HIERARCHYID|Oggetti di grandi dimensioni. Ad esempio, varchar(max), nvarchar(max), varbinary(max), image, xml, text e ntext.|ROWVERSION|  
|sql_variant|Funzioni CLR|Tipi definiti dall'utente (UDT)|  
  
## <a name="see-also"></a>Vedere anche  
 [Supporto di Transact-SQL per OLTP in memoria](transact-sql-support-for-in-memory-oltp.md)   
 [Implementazione di colonne LOB in una tabella con ottimizzazione per la memoria](../../database-engine/implementing-lob-columns-in-a-memory-optimized-table.md)   
 [Implementazione di SQL_VARIANT in una tabella con ottimizzazione per la memoria](implementing-sql-variant-in-a-memory-optimized-table.md)  
  
  

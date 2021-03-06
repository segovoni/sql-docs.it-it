---
title: DATETIMEOFFSETFROMPARTS (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DATETIMEOFFSETFROMPARTS_TSQL
- DATETIMEOFFSETFROMPARTS
dev_langs:
- TSQL
helpviewer_keywords:
- DATETIMEOFFSETFROMPARTS function
ms.assetid: 463da1f4-b4b6-45a3-9a95-ea1f99575542
caps.latest.revision: 19
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 09e705fd426963018eadae7351df1046d3d1ef0c
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2018
ms.locfileid: "35698272"
---
# <a name="datetimeoffsetfromparts-transact-sql"></a>DATETIMEOFFSETFROMPARTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

Questa funzione restituisce un valore di tipo **datetimeoffset** per gli argomenti date e time. Il valore restituito ha una precisione specificata dall'argomento precision e differenze determinate dagli argomenti di offset relativi a ora e minuto.
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
DATETIMEOFFSETFROMPARTS ( year, month, day, hour, minute, seconds, fractions, hour_offset, minute_offset, precision )  
```  
  
## <a name="arguments"></a>Argomenti  
*year*  
Espressione Integer che specifica un anno.
  
*month*  
Espressione Integer che specifica un mese.
  
*day*  
Espressione Integer che specifica un giorno.
  
*hour*  
Espressione Integer che specifica le ore.
  
*minute*  
Espressione Integer che specifica i minuti.
  
*secondi*  
Espressione Integer che specifica i secondi.
  
*fractions*  
Espressione Integer che specifica un valore frazionario.
  
*hour_offset*  
Espressione Integer che specifica la parte di ora della differenza di fuso orario.
  
*minute_offset*  
Espressione Integer che specifica la parte di minuto della differenza di fuso orario.
  
*precisione*  
Valore letterale Integer che specifica la precisione del valore **datetimeoffset** che verrà restituito da `DATETIMEOFFSETFROMPARTS`.
  
## <a name="return-types"></a>Tipi restituiti
**datetimeoffset(** *precision* **)**
  
## <a name="remarks"></a>Remarks  
`DATETIMEOFFSETFROMPARTS` restituisce un tipo di dati **datetimeoffset** completamente inizializzato. `DATETIMEOFFSETFROMPARTS` usa gli argomenti di offset per rappresentare la differenza di fuso orario. Se gli argomenti di offset vengono omessi, `DATETIMEOFFSETFROMPARTS` presuppone una differenza di fuso orario pari a 00:00, ovvero nessuna differenza di fuso orario. Per gli argomenti di offset specificati, `DATETIMEOFFSETFROMPARTS` prevede per entrambi gli argomenti valori entrambi positivi o entrambi negativi. Per un'espressione *minute_offset* specificata senza un valore *hour_offset* specificato, `DATETIMEOFFSETFROMPARTS` genererà un errore. Se gli altri argomenti hanno valori non validi, `DATETIMEOFFSETFROMPARTS` genererà un errore. `DATETIMEOFFSETFROMPARTS` restituisce null se almeno un argomento obbligatorio ha un valore null. Se tuttavia l'argomento *precision* ha un valore null, `DATETIMEOFFSETFROMPARTS` genererà un errore.
  
L'argomento *fractions* dipende dall'argomento *precision*. Ad esempio, per un valore di *precision* pari a 7, ogni frazione rappresenta 100 nanosecondi, mentre per *precision* pari a 3, ogni frazione rappresenta un millisecondo. Per un valore di *precision* pari a zero, anche il valore di *fractions* deve essere zero. In caso contrario, `DATETIMEOFFSETFROMPARTS` genererà un errore.

Questa funzione supporta la comunicazione remota con i server [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e versioni successive. Non supporterà la comunicazione remota con i server con versioni precedenti a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].
  
## <a name="examples"></a>Esempi  
  
### <a name="a-an-example-without-fractions-of-a-second"></a>A. Esempio senza frazioni di un secondo  
  
```sql
SELECT DATETIMEOFFSETFROMPARTS ( 2010, 12, 31, 14, 23, 23, 0, 12, 0, 7 ) AS Result;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Result  
-------------------------------------------  
2010-12-07 00:00:00.0000000 +00:00  
  
(1 row(s) affected)  
```  
  
### <a name="b-example-with-fractions-of-a-second"></a>B. Esempio con frazioni di un secondo  
Questo esempio illustra l'uso dei parametri *fractions* e *precision*:
1.   Se *fractions* ha valore 5 e *precision* ha valore 1, il valore di *fractions* corrisponde a 5/10 di secondo.  
1.   Se *fractions* ha valore 50 e *precision* ha valore 2, il valore di *fractions* corrisponde a 50/100 di secondo.  
1.   Se *fractions* ha valore 500 e *precision* ha valore 3, il valore di *fractions* corrisponde a 500/1000 di secondo.  
  
```sql
SELECT DATETIMEOFFSETFROMPARTS ( 2011, 8, 15, 14, 30, 00, 5, 12, 30, 1 );  
SELECT DATETIMEOFFSETFROMPARTS ( 2011, 8, 15, 14, 30, 00, 50, 12, 30, 2 );  
SELECT DATETIMEOFFSETFROMPARTS ( 2011, 8, 15, 14, 30, 00, 500, 12, 30, 3 );  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
----------------------------------  
2011-08-15 14:30:00.5 +12:30  
  
(1 row(s) affected)  
  
----------------------------------  
2011-08-15 14:30:00.50 +12:30  
  
(1 row(s) affected)  
  
----------------------------------  
2011-08-15 14:30:00.500 +12:30  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Vedere anche
[datetimeoffset &#40;Transact-SQL&#41;](../../t-sql/data-types/datetimeoffset-transact-sql.md)  
[AT TIME ZONE &#40;Transact-SQL&#41;](../../t-sql/queries/at-time-zone-transact-sql.md)
  
  



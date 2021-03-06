---
title: sql_variant (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 9/12/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sql_variant
- sql_variant_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sql_variant comparisons
- storing data [SQL Server], sql_variant
- sql_variant data type
- storage [SQL Server], sql_variant
ms.assetid: 01229779-8bc1-4c7d-890a-8246d4899250
caps.latest.revision: 43
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 812e9e2e27434605f4339dd62edc93caad923ee7
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37420410"
---
# <a name="sqlvariant-transact-sql"></a>sql_variant (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Tipo di dati per l'archiviazione di valori per vari tipi di dati supportati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
sql_variant  
```  
  
## <a name="remarks"></a>Remarks  
**sql_variant** può essere usato in colonne, parametri, variabili e in valori restituiti di funzioni definite dall'utente. **sql_variant** consente a questi oggetti di database di supportare valori di altri tipi di dati.
  
Una colonna di tipo **sql_variant** può includere righe con tipi di dati diversi. Ad esempio, una colonna definita come **sql_variant** può archiviare valori **int**, **binary**, e **char**.
  
La lunghezza massima supportata da **sql_variant** è pari a 8016 byte. La lunghezza include sia le informazioni sul tipo di base che il valore del tipo di base. La lunghezza massima del valore effettivo del tipo di base è di 8.000 byte.
  
Per poter usare il tipo di dati **sql_variant** in operazioni quali l'addizione e la sottrazione, è prima necessario eseguirne il casting al valore del tipo di dati di base corrispondente.
  
È possibile assegnare un valore predefinito a **sql_variant**. A questo tipo di dati è inoltre possibile assegnare NULL come valore sottostante, ma in questo caso ai valori NULL non verrà associato alcun tipo di base. **sql_variant** non può avere un altro valore **sql_variant** come tipo di base.
  
Una chiave univoca, primaria o esterna può includere colonne di tipo **sql_variant**, ma la lunghezza totale dei valori di dati che compongono la chiave di una riga specifica non deve superare la lunghezza massima di un indice, ovvero 900 byte.
  
Una tabella può contenere un numero qualsiasi di colonne di tipo **sql_variant**.
  
Non è possibile usare il tipo di dati **sql_variant** in CONTAINSTABLE e FREETEXTTABLE.
  
ODBC non offre il supporto completo di **sql_variant**. Quando si usa il provider Microsoft OLE DB per ODBC (MSDASQL), pertanto, le query eseguite su colonne di tipo **sql_variant** restituiscono dati binari. Ad esempio, la stringa di caratteri "PS2091" di una colonna di tipo **sql_variant** viene restituita come 0x505332303931.
  
## <a name="comparing-sqlvariant-values"></a>Confronto di valori sql_variant  
Il tipo di dati **sql_variant** è incluso nella parte iniziale dell'elenco della gerarchia dei tipi di dati per la conversione. Per l'esecuzione di confronti di valori **sql_variant**, la gerarchia dei tipi di dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene suddivisa in gruppi di tipi di dati.
  
|Gerarchia dei tipi di dati|Gruppo di tipi di dati|  
|---|---|
|**sql_variant**|sql_variant |  
|**datetime2**|Date e Time|  
|**datetimeoffset**|Date e Time|  
|**datetime**|Date e Time|  
|**smalldatetime**|Date e Time|  
|**data**|Date e Time|  
|**time**|Date e Time|  
|**float**|Valori numerici approssimati|  
|**real**|Valori numerici approssimati|  
|**decimal**|Valori numerici esatti|  
|**money**|Valori numerici esatti|  
|**smallmoney**|Valori numerici esatti|  
|**bigint**|Valori numerici esatti|  
|**int**|Valori numerici esatti|  
|**smallint**|Valori numerici esatti|  
|**tinyint**|Valori numerici esatti|  
|**bit**|Valori numerici esatti|  
|**nvarchar**|Unicode|  
|**nchar**|Unicode|  
|**varchar**|Unicode|  
|**char**|Unicode|  
|**varbinary**|Binario|  
|**binary**|Binario|  
|**uniqueidentifier**|Uniqueidentifier |  
  
Per i confronti **sql_variant** vengono applicate le regole seguenti:
-   Nei confronti tra valori **sql_variant** con tipi di dati di base diversi appartenenti a gruppi di tipi di dati diversi, il valore appartenente al gruppo di tipi di dati che occupa un livello più alto nella gerarchia viene considerato il valore maggiore.  
-   Nei confronti di valori **sql_variant** con tipi di dati di base diversi appartenenti allo stesso gruppo, il valore del tipo di dati di base che appartiene a un gruppo di livello inferiore nella gerarchia viene convertito in modo implicito nell'altro tipo di dati, dopodiché viene eseguito il confronto.  
-   Quando vengono confrontati i valori **sql_variant** dei tipi di dati **char**, **varchar**, **nchar** o **nvarchar**, vengono messe a confronto per prime le regole di confronto in base ai criteri seguenti: LCID, versione LCID, flag di confronto e ID di ordinamento. Per ognuno di questi criteri il confronto viene eseguito con valori interi e nell'ordine elencato. Se tutti questi criteri sono uguali, i valori effettivi della stringa vengono confrontati in base alle regole di confronto.  
  
## <a name="converting-sqlvariant-data"></a>Conversione di dati sql_variant  
Nel caso del tipo di dati **sql_variant**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supporta la conversione implicita in **sql_variant** degli oggetti con tipi di dati diversi. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non supporta tuttavia le conversioni implicite dal tipo di dati **sql_variant** in oggetti con un tipo di dati diverso.
  
## <a name="restrictions"></a>Restrictions  
Nella tabella seguente sono elencati i tipi di valori che non è possibile archiviare con **sql_variant**:
  
|||  
|-|-|  
|**ntext**|**varbinary(max)**|  
|**nvarchar(max)**|**xml**|  
|**text**|**ntext**|  
|**image**|**rowversion** (**timestamp**)|  
|**sql_variant**|**geography**|  
|**hierarchyid**|**geometry**|  
|Tipi definiti dall'utente|**datetimeoffset**|  

## <a name="examples"></a>Esempi  

### <a name="a-using-a-sqlvariant-in-a-table"></a>A. Uso di un tipo sql_variant in una tabella  
 Nell'esempio seguente viene creata una tabella con tipi di dati sql_variant. In seguito vengono recuperate le informazioni di `SQL_VARIANT_PROPERTY` relative al valore `colA` `46279.1`, dove `colB` =`1689`, partendo dal presupposto che `tableA` include `colA` di tipo `sql_variant` e `colB`.  
  
```sql    
CREATE   TABLE tableA(colA sql_variant, colB int)  
INSERT INTO tableA values ( cast (46279.1 as decimal(8,2)), 1689)  
SELECT   SQL_VARIANT_PROPERTY(colA,'BaseType') AS 'Base Type',  
         SQL_VARIANT_PROPERTY(colA,'Precision') AS 'Precision',  
         SQL_VARIANT_PROPERTY(colA,'Scale') AS 'Scale'  
FROM      tableA  
WHERE      colB = 1689  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)] Si noti che tutti e tre i valori sono di tipo **sql_variant**.  
  
```  
Base Type    Precision    Scale  
---------    ---------    -----  
decimal      8           2  
  
(1 row(s) affected)  
```  
  
### <a name="b-using-a-sqlvariant-as-a-variable"></a>B. Uso di un tipo sql_variant come variabile   
 Nell'esempio seguente viene creata una variabile con il tipo di dati sql_variant e in seguito vengono recuperate le informazioni di `SQL_VARIANT_PROPERTY` su una variabile denominata @v1.  
  
```sql    
DECLARE @v1 sql_variant;  
SET @v1 = 'ABC';  
SELECT @v1;  
SELECT SQL_VARIANT_PROPERTY(@v1, 'BaseType');  
SELECT SQL_VARIANT_PROPERTY(@v1, 'MaxLength');  
```    


## <a name="see-also"></a>Vedere anche
[CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[SQL_VARIANT_PROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/sql-variant-property-transact-sql.md)
  
  

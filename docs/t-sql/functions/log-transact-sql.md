---
title: LOG (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- LOG
- LOG_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- float expressions
- logarithm of expression
- LOG function
ms.assetid: f7c39511-cd84-4362-93ba-0d93655217ee
caps.latest.revision: 42
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: e9dcba7a5006d88b9378e9ce7f04957873ec3846
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/04/2018
ms.locfileid: "37785302"
---
# <a name="log-transact-sql"></a>LOG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce il logaritmo naturale dell'espressione **float** specificata in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server  
  
LOG ( float_expression [, base ] )  
```  
  
```  
-- Syntax for Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
LOG ( float_expression )  
```  
  
## <a name="arguments"></a>Argomenti  
 *float_expression*  
 [Espressione](../../t-sql/language-elements/expressions-transact-sql.md) di tipo **float** oppure di un tipo che può essere convertito in modo implicito in **float**.  
  
 *base*  
 Argomento di tipo Integer facoltativo che imposta la base per il logaritmo.  
  
**Si applica a**: da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
## <a name="return-types"></a>Tipi restituiti  
 **float**  
  
## <a name="remarks"></a>Remarks  
 Per impostazione predefinita, **LOG()** restituisce il logaritmo naturale. A partire da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] è possibile impostare la base del logaritmo su un altro valore usando il parametro *base* facoltativo.  
  
 Il logaritmo naturale è il logaritmo in base **e**, dove **e** è una costante non razionale approssimativamente uguale a 2,718281828.  
  
 Il logaritmo naturale del valore esponenziale di un numero è il numero stesso: LOG( EXP( *n* ) ) = *n*. Il valore esponenziale del logaritmo naturale di un numero è il numero stesso: EXP( LOG( *n* ) ) = *n*.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-calculating-the-logarithm-for-a-number"></a>A. Calcolo del logaritmo di un numero.  
 Nell'esempio seguente viene calcolato il valore `LOG` per l'espressione **float** specificata.  
  
```  
DECLARE @var float = 10;  
SELECT 'The LOG of the variable is: ' + CONVERT(varchar, LOG(@var));  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
-------------------------------------  
The LOG of the variable is: 2.30259  
  
(1 row(s) affected)  
```  
  
### <a name="b-calculating-the-logarithm-of-the-exponent-of-a-number"></a>B. Calcolo del logaritmo dell'esponente di un numero.  
 Nell'esempio seguente viene calcolato il valore `LOG` per l'esponente di un numero.  
  
```  
SELECT LOG (EXP (10));  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
----------------------------------  
10  
(1 row(s) affected)  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-calculating-the-logarithm-for-a-number"></a>C. Calcolo del logaritmo di un numero  
 Nell'esempio seguente viene calcolato il valore `LOG` per l'espressione **float** specificata.  
  
```  
SELECT LOG(10);  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 ----------------`  
  
 2.30
 ```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni matematiche &#40;Transact-SQL&#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)   
 [EXP &#40;Transact-SQL&#41;](../../t-sql/functions/exp-transact-sql.md)   
 [LOG10 &#40;Transact-SQL&#41;](../../t-sql/functions/log10-transact-sql.md)  
  
  


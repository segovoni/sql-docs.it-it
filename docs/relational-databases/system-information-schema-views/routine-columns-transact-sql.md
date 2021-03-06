---
title: ROUTINE_COLUMNS (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ROUTINE_COLUMNS_TSQL
- ROUTINE_COLUMNS
dev_langs:
- TSQL
helpviewer_keywords:
- ROUTINE_COLUMNS view
- INFORMATION_SCHEMA.ROUTINE_COLUMNS view
ms.assetid: 91dbc61b-e4c0-4826-976c-b2fce88b7793
caps.latest.revision: 37
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: fc7e43784d336fcd5358b00ad5fc82b5c89e0c3b
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33239281"
---
# <a name="routinecolumns-transact-sql"></a>ROUTINE_COLUMNS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce una riga per ogni colonna restituita dalle funzioni con valori di tabella a cui può accedere l'utente corrente del database corrente.  
  
 Per recuperare informazioni da questa vista, specificare il nome completo di **INFORMATION_SCHEMA. * * * view_name*.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**TABLE_CATALOG**|**nvarchar (** 128 **)**|Nome del catalogo o del database della funzione con valori di tabella.|  
|**TABLE_SCHEMA**|**nvarchar (** 128 **)**|Nome dello schema che contiene la funzione con valori di tabella.<br /><br /> **\*\* Importante \* \***  non utilizzare viste INFORMATION_SCHEMA per determinare lo schema di un oggetto. L'unica modalità affidabile per cercare lo schema di un oggetto consiste nell'eseguire una query sulla vista del catalogo sys.objects.|  
|**TABLE_NAME**|**nvarchar (** 128 **)**|Nome della funzione con valori di tabella.|  
|**COLUMN_NAME**|**nvarchar (** 128 **)**|Nome colonna.|  
|**ORDINAL_POSITION**|**int**|Numero di identificazione della colonna.|  
|**COLUMN_DEFAULT**|**nvarchar (** 4000 **)**|Valore predefinito della colonna.|  
|**IS_NULLABLE**|**varchar (** 3 **)**|Se la colonna ammette valori NULL, restituisce YES. In caso contrario restituisce NO.|  
|**DATA_TYPE**|**nvarchar (** 128 **)**|Tipo di dati di sistema.|  
|**CHARACTER_MAXIMUM_LENGTH**|**int**|Lunghezza massima espressa in caratteri per i dati di tipo binario, carattere, text o image.<br /><br /> -1 per **xml** e i dati del tipo di valori di grandi dimensioni. In caso contrario, viene restituito NULL. Per altre informazioni, vedere [Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md).|  
|**CHARACTER_OCTET_LENGTH**|**int**|Lunghezza massima espressa in byte per i dati di tipo binario, carattere, text o image.<br /><br /> -1 per **xml** e i dati del tipo di valori di grandi dimensioni. In caso contrario, viene restituito NULL.|  
|**NUMERIC_PRECISION**|**tinyint**|Precisione dei dati numerici approssimati, dei dati numerici esatti, dei dati integer o dei dati in valuta. In caso contrario, viene restituito NULL.|  
|**NUMERIC_PRECISION_RADIX**|**smallint**|Base di precisione dei dati numerici approssimati, dei dati numerici esatti, dei dati integer o dei dati in valuta. In caso contrario, viene restituito NULL.|  
|**NUMERIC_SCALE**|**tinyint**|Scala dei dati numerici approssimati, dei dati numerici esatti, dei dati integer o dei dati in valuta. In caso contrario, viene restituito NULL.|  
|**DATETIME_PRECISION**|**smallint**|Codice di sottotipo per **datetime** e ISO**intero** tipi di dati. Per gli altri tipi di dati restituisce NULL.|  
|**CHARACTER_SET_CATALOG**|**varchar (** 6 **)**|Restituisce **master**. Indica il database in cui si trova il set di caratteri se la colonna è di tipo carattere o **testo** tipo di dati. In caso contrario, viene restituito NULL.|  
|**CHARACTER_SET_SCHEMA**|**varchar (** 3 **)**|Viene restituito sempre NULL.|  
|**CHARACTER_SET_NAME**|**nvarchar (** 128 **)**|Restituisce il nome univoco per il carattere impostato se questa colonna è di tipo carattere o **testo** tipo di dati. In caso contrario, viene restituito NULL.|  
|**COLLATION_CATALOG**|**varchar (** 6 **)**|Viene restituito sempre NULL.|  
|**COLLATION_SCHEMA**|**varchar (** 3 **)**|Viene restituito sempre NULL.|  
|**COLLATION_NAME**|**nvarchar (** 128 **)**|Restituisce il nome univoco per l'ordinamento, se la colonna è di tipo carattere o **testo** tipo di dati. In caso contrario, viene restituito NULL.|  
|**DOMAIN_CATALOG**|**nvarchar (** 128 **)**|Restituisce il nome del database in cui è stato creato il tipo di dati definito dall'utente se la colonna contiene un tipo di dati alias. In caso contrario, viene restituito NULL.|  
|**DOMAIN_SCHEMA**|**nvarchar (** 128 **)**|Se il tipo di dati della colonna è un tipo definito dall'utente, restituisce il nome dello schema contenente il tipo di dati definito dall'utente. In caso contrario, viene restituito NULL.<br /><br /> **\*\* Importante \* \***  non utilizzare viste INFORMATION_SCHEMA per determinare lo schema di un oggetto. L'unica modalità affidabile per cercare lo schema di un oggetto consiste nell'eseguire una query sulla vista del catalogo sys.objects.|  
|**NOME_DOMINIO**|**nvarchar (** 128 **)**|Restituisce il nome del tipo di dati definito dall'utente se la colonna contiene un tipo di dati definito dall'utente. In caso contrario, viene restituito NULL.|  
  
## <a name="see-also"></a>Vedere anche  
 [Viste di sistema &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [Viste degli schemi delle informazioni &#40;Transact-SQL&#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)  
  
  

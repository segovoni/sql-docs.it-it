---
title: sp_columns_ex (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_columns_ex
- sp_columns_ex_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_columns_ex
ms.assetid: c12ef6df-58c6-4391-bbbf-683ea874bd81
caps.latest.revision: 38
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: a7f075de05288823c1ed290527de4005b1160c20
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33240071"
---
# <a name="spcolumnsex-transact-sql"></a>sp_columns_ex (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce le informazioni sulle colonne, utilizzando una riga per ogni colonna, per le tabelle del server collegato specificato. **sp_columns_ex** restituisce informazioni sulle colonne per la specifica colonna se *colonna* è specificato.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_columns_ex [ @table_server = ] 'table_server'   
     [ , [ @table_name = ] 'table_name' ]   
     [ , [ @table_schema = ] 'table_schema' ]   
     [ , [ @table_catalog = ] 'table_catalog' ]   
     [ , [ @column_name = ] 'column' ]   
     [ , [ @ODBCVer = ] 'ODBCVer' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@table_server =** ] **'***table_server***'**  
 Nome del server collegato per cui si desidera restituire le informazioni sulle colonne. *table_server* viene **sysname**, non prevede alcun valore predefinito.  
  
 [  **@table_name =** ] **'***table_name***'**  
 Nome della tabella per cui si desidera restituire le informazioni sulle colonne. *TABLE_NAME* viene **sysname**, con un valore predefinito è NULL.  
  
 [  **@table_schema =** ] **'***table_schema***'**  
 Nome dello schema per cui si desidera restituire le informazioni sulle colonne. *TABLE_SCHEMA* viene **sysname**, con un valore predefinito è NULL.  
  
 [  **@table_catalog =** ] **'***table_catalog***'**  
 Nome del catalogo per cui si desidera restituire le informazioni sulle colonne. *TABLE_CATALOG* viene **sysname**, con un valore predefinito è NULL.  
  
 [  **@column_name =** ] **'***colonna***'**  
 Nome della colonna del database per cui si desidera ottenere informazioni. *colonna* viene **sysname**, con un valore predefinito è NULL.  
  
 [  **@ODBCVer =** ] **'***ODBCVer***'**  
 Versione di ODBC utilizzata. *ODBCVer* viene **int**, con un valore predefinito è 2. che indica ODBC versione 2. I valori validi sono 2 e 3. Per informazioni sulle differenze di comportamento tra le versioni 2 e 3, vedere la specifica relativa a SQLColumns di ODBC.  
  
## <a name="return-code-values"></a>Valori restituiti  
 Nessuno  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**TABLE_CAT**|**sysname**|Nome del qualificatore della tabella o della vista. Vari prodotti DBMS supportano nomi in tre parti per le tabelle (*qualificatore ***.*** proprietario ***.*** nome*). In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], questa colonna rappresenta il nome del database. In altri prodotti rappresenta il nome del server dell'ambiente di database della tabella. Questo campo può essere NULL.|  
|**TABLE_SCHEM**|**sysname**|Nome del proprietario della tabella o della vista. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] questa colonna rappresenta il nome dell'utente del database che ha creato la tabella. Questo campo restituisce sempre un valore.|  
|**TABLE_NAME**|**sysname**|Nome della tabella o della vista. Questo campo restituisce sempre un valore.|  
|**COLUMN_NAME**|**sysname**|Nome della colonna, per ogni colonna del **TABLE_NAME** restituito. Questo campo restituisce sempre un valore.|  
|**DATA_TYPE**|**smallint**|Valore intero corrispondente agli indicatori del tipo di dati ODBC. Se si tratta di un tipo di dati di cui non è possibile eseguire il mapping a un tipo ODBC, il valore è NULL. Cui viene restituito il nome del tipo di dati nativi di **TYPE_NAME** colonna.|  
|**TYPE_NAME**|**varchar (** 13 **)**|Stringa che rappresenta un tipo di dati. Il DBMS sottostante utilizza questo nome del tipo di dati.|  
|**COLUMN_SIZE**|**int**|Numero di cifre significative. Il valore restituito per il **precisione** colonna è in base 10.|  
|**BUFFER_LENGTH**|**int**|Dimensioni di trasferimento dei dati.1|  
|**DECIMAL_DIGITS**|**smallint**|Numero di cifre a destra del separatore decimale.|  
|**NUM_PREC_RADIX**|**smallint**|Base per i tipi di dati numerici.|  
|**AMMETTE VALORI NULL**|**smallint**|Specifica se i valori Null sono supportati.<br /><br /> 1 = I valori Null sono supportati.<br /><br /> 0 = I valori Null non sono supportati (NOT NULL).|  
|**SEZIONE OSSERVAZIONI**|**varchar (** 254 **)**|In questo campo viene sempre restituito NULL.|  
|**COLUMN_DEF**|**varchar (** 254 **)**|Valore predefinito della colonna.|  
|**SQL_DATA_TYPE**|**smallint**|Valore del tipo di dati SQL visualizzato nel campo TYPE del descrittore. Questa colonna corrisponde alla **DATA_TYPE** colonna, tranne che per il **datetime** e SQL-92 **intervallo** tipi di dati. In questa colonna viene sempre restituito un valore.|  
|**SQL_DATETIME_SUB**|**smallint**|Codice di sottotipo per **datetime** e SQL-92 **intervallo** tipi di dati. Per gli altri tipi di dati in questa colonna viene restituito NULL.|  
|**CHAR_OCTET_LENGTH**|**int**|Lunghezza massima, espressa in byte, di una colonna di tipo carattere o integer. Per tutti gli altri tipi di dati in questa colonna viene restituito NULL.|  
|**ORDINAL_POSITION**|**int**|Posizione ordinale della colonna nella tabella. La prima colonna nella tabella è 1. In questa colonna viene sempre restituito un valore.|  
|**IS_NULLABLE**|**varchar (** 254 **)**|Impostazione relativa al supporto di valori Null nella colonna della tabella. Per determinare il supporto di valori Null vengono seguite le regole ISO. In un sistema DBMS conforme a ISO SQL non vengono restituite stringhe vuote.<br /><br /> YES = La colonna ammette valori Null.<br /><br /> NO = La colonna non ammette valori Null.<br /><br /> Quando non è noto se i valori Null sono supportati, in questa colonna viene restituita una stringa di lunghezza zero.<br /><br /> Il valore restituito per questa colonna è diverso dal valore restituito per il **NULLABLE** colonna.|  
|**SS_DATA_TYPE**|**tinyint**|Tipo di dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizzato in stored procedure estese.|  
  
 Per ulteriori informazioni, vedere la documentazione di Microsoft ODBC.  
  
## <a name="remarks"></a>Osservazioni  
 **sp_columns_ex** viene eseguita tramite una query di set di righe COLUMNS il **IDBSchemaRowset** interfaccia del provider OLE DB corrispondente a *table_server*. Il *table_name*, *table_schema*, *table_catalog*, e *colonna* i parametri vengono passati a questa interfaccia per limitare le righe restituito.  
  
 **sp_columns_ex** restituisce un risultato vuoto se il provider OLE DB del server collegato specificato non supporta il set di righe COLUMNS di impostare il **IDBSchemaRowset** interfaccia.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione SELECT per lo schema.  
  
## <a name="remarks"></a>Osservazioni  
 **sp_columns_ex** soddisfa i requisiti per gli identificatori delimitati. Per altre informazioni, vedere [Identificatori del database](../../relational-databases/databases/database-identifiers.md).  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene restituito il tipo di dati della colonna `JobTitle` della tabella `HumanResources.Employee` inclusa nel database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] disponibile nel server collegato `Seattle1`.  
  
```  
EXEC sp_columns_ex 'Seattle1',   
   'Employee',   
   'HumanResources',   
   'AdventureWorks2012',   
   'JobTitle';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_catalogs &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-catalogs-transact-sql.md)   
 [sp_foreignkeys &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-foreignkeys-transact-sql.md)   
 [sp_indexes &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-indexes-transact-sql.md)   
 [sp_linkedservers & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-linkedservers-transact-sql.md)   
 [sp_primarykeys &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-primarykeys-transact-sql.md)   
 [sp_tables_ex &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-tables-ex-transact-sql.md)   
 [sp_table_privileges &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-table-privileges-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

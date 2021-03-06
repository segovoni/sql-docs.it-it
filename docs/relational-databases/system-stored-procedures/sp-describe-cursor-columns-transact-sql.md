---
title: sp_describe_cursor_columns (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_describe_cursor_columns
- sp_describe_cursor_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_describe_cursor_columns
ms.assetid: 6eaa54af-7ba4-4fce-bf6c-6ac67cc1ac94
caps.latest.revision: 31
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: d1a39ab87291a51f272966bb60e407d89b4f2cb2
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33260274"
---
# <a name="spdescribecursorcolumns-transact-sql"></a>sp_describe_cursor_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crea un report degli attributi associati alle colonne del set di risultati in un cursore del server.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_describe_cursor_columns   
   [ @cursor_return = ] output_cursor_variable OUTPUT   
    { [ , [ @cursor_source = ] N'local' ,   
          [ @cursor_identity = ] N'local_cursor_name' ]   
    | [ , [ @cursor_source = ] N'global' ,   
          [ @cursor_identity = ] N'global_cursor_name' ]   
    | [ , [ @cursor_source = ] N'variable' ,   
          [ @cursor_identity = ] N'input_cursor_variable' ]   
   }  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @cursor_return=] *output_cursor_variable* OUTPUT  
 Nome di una variabile di cursore dichiarata per ricevere l'output del cursore. *output_cursor_variable* viene **cursore**e non prevede alcun valore predefinito, non essere associata ad alcun cursore al momento della chiamata di stored procedure sp_describe_cursor_columns. Il cursore restituito è di tipo scorrevole, dinamico e di sola lettura.  
  
 [ @cursor_source=] {N'local' | N'global' | N'variable'}  
 Specifica se il cursore di cui viene generato il report viene specificato utilizzando il nome di un cursore locale, di un cursore globale o di una variabile di cursore. Il parametro è **nvarchar (30)**.  
  
 [ @cursor_identity=] N'*local_cursor_name*'  
 Nome di un cursore creato da un'istruzione DECLARE CURSOR con la parola chiave LOCAL o impostato sul valore predefinito LOCAL. *local_cursor_name* viene **nvarchar (128)**.  
  
 [ @cursor_identity=] N'*global_cursor_name*'  
 Nome di un cursore creato da un'istruzione DECLARE CURSOR con la parola chiave GLOBAL o impostato sul valore predefinito GLOBAL. *global_cursor_name* viene **nvarchar (128)**.  
  
 *global_cursor_name* può anche essere il nome di un cursore API del server aperto da un'applicazione ODBC e quindi denominato tramite SQLSetCursorName.  
  
 [ @cursor_identity=] N'*input_cursor_variable*'  
 Nome di una variabile di cursore associata a un cursore aperto. *input_cursor_variable* viene **nvarchar (128)**.  
  
## <a name="return-code-values"></a>Valori restituiti  
 Nessuno  
  
## <a name="cursors-returned"></a>Cursori restituiti  
 sp_describe_cursor_columns incapsula il report in un [!INCLUDE[tsql](../../includes/tsql-md.md)] **cursore** parametro di output. In questo modo i batch, le stored procedure e i trigger [!INCLUDE[tsql](../../includes/tsql-md.md)] possono elaborare l'output una riga alla volta. Questo significa inoltre che non è possibile richiamare direttamente la procedura da funzioni API del database. Il **cursore** parametro di output deve essere associato a una variabile di programma, ma le API di database non supportano l'associazione **cursore** parametri o variabili.  
  
 Nella seguente tabella viene descritto il formato del cursore restituito da sp_describe_cursor_columns.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|column_name|**sysname** (ammette valori null)|Nome assegnato alla colonna del set di risultati. La colonna è NULL se è stata specificata senza la clausola AS.|  
|ordinal_position|**int**|Posizione relativa della colonna a partire dalla prima colonna a sinistra del set di risultati. La prima colonna si trova nella posizione 0.|  
|column_characteristics_flags|**int**|Maschera di bit che indica le informazioni archiviate in DBCOLUMNFLAGS in OLE DB. I possibili valori sono i seguenti:<br /><br /> 1 = Segnalibro<br /><br /> 2 = Lunghezza fissa<br /><br /> 4 = Ammette valori Null<br /><br /> 8 = Controllo delle versioni delle righe<br /><br /> 16 = Colonna aggiornabile (viene impostata per le eventuali colonne di cursore prive della clausola FOR UPDATE; un cursore può includere una sola colonna di questo tipo)<br /><br /> Quando i valori bit vengono combinati, vengono applicate le caratteristiche dei valori bit combinati. Se, ad esempio, il valore bit è 6, la colonna è a lunghezza fissa (2) e ammette valori Null (4).|  
|column_size|**int**|Dimensioni massime consentite per un valore della colonna.|  
|data_type_sql|**smallint**|Numero che indica il tipo di dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] della colonna.|  
|column_precision|**tinyint**|Precisione massima della colonna in base il *bPrecision* valore in OLE DB.|  
|column_scale|**tinyint**|Numero di cifre a destra del separatore decimale per il **numerico** o **decimale** tipi di dati in base il *bScale* valore in OLE DB.|  
|order_position|**int**|Se la colonna partecipa all'ordinamento del set di risultati, posizione della colonna nella chiave di ordinamento relativa alla prima colonna a sinistra.|  
|order_direction|**varchar(1)**(ammette valori null)|A = La colonna è inclusa nella chiave di ordinamento e l'ordine è crescente.<br /><br /> D = La colonna è inclusa nella chiave di ordinamento e l'ordine è decrescente.<br /><br /> NULL = La colonna non partecipa all'ordinamento.|  
|hidden_column|**smallint**|0 = La colonna è inclusa nell'elenco di selezione.<br /><br /> 1 = Riservato per utilizzi futuri.|  
|columnid|**int**|ID della colonna di base. Se la colonna del set di risultati è stata creata in base a un'espressione, columnid è -1.|  
|objectid|**int**|ID dell'oggetto o della tabella di base che include la colonna. Se la colonna del set di risultati è stata creata in base a un'espressione, objectid è -1.|  
|dbid|**int**|ID del database contenente la tabella di base che include la colonna. Se la colonna del set di risultati è stata creata in base a un'espressione, dbid è -1.|  
|dbname|**sysname**<br /><br /> (ammette valori Null)|Nome del database contenente la tabella di base che include la colonna. Se la colonna del set di risultati è stata creata in base a un'espressione, dbname è NULL.|  
  
## <a name="remarks"></a>Osservazioni  
 La stored procedure sp_describe_cursor_columns descrive gli attributi delle colonne di un set di risultati di un cursore del server, quali il nome e il tipo di dati di ogni colonna. Utilizzare sp_describe_cursor per ottenere una descrizione degli attributi globali del cursore del server. Utilizzare sp_describe_cursor_tables per ottenere un report delle tabelle di base a cui fa riferimento il cursore. Per ottenere un report relativo ai cursori del server [!INCLUDE[tsql](../../includes/tsql-md.md)] visibili nella connessione, utilizzare la stored procedure sp_cursor_list.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza al ruolo public.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene aperto un cursore globale e viene utilizzata la stored procedure `sp_describe_cursor_columns` per creare un report delle colonne utilizzate nel cursore.  
  
```  
USE AdventureWorks2012;  
GO  
-- Declare and open a global cursor.  
DECLARE abc CURSOR KEYSET FOR  
SELECT LastName  
FROM Person.Person;  
GO  
OPEN abc;  
  
-- Declare a cursor variable to hold the cursor output variable  
-- from sp_describe_cursor_columns.  
DECLARE @Report CURSOR;  
  
-- Execute sp_describe_cursor_columns into the cursor variable.  
EXEC master.dbo.sp_describe_cursor_columns  
    @cursor_return = @Report OUTPUT  
    ,@cursor_source = N'global'   
    ,@cursor_identity = N'abc';  
  
-- Fetch all the rows from the sp_describe_cursor_columns output cursor.  
FETCH NEXT from @Report;  
WHILE (@@FETCH_STATUS <> -1)  
BEGIN  
   FETCH NEXT from @Report;  
END  
  
-- Close and deallocate the cursor from sp_describe_cursor_columns.  
CLOSE @Report;  
DEALLOCATE @Report;  
GO  
-- Close and deallocate the original cursor.  
CLOSE abc;  
DEALLOCATE abc;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Cursori](../../relational-databases/cursors.md)   
 [CURSOR_STATUS &#40;Transact-SQL&#41;](../../t-sql/functions/cursor-status-transact-sql.md)   
 [DECLARE CURSOR &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-cursor-transact-sql.md)   
 [stored procedure sp_describe_cursor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-describe-cursor-transact-sql.md)   
 [sp_cursor_list &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursor-list-transact-sql.md)   
 [sp_describe_cursor_tables &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-describe-cursor-tables-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

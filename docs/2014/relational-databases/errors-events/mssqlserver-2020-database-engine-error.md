---
title: MSSQLSERVER_2020 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 2020 (Database Engine error)
ms.assetid: 4a8bf90f-a083-4c53-84f0-d23c711c8081
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0397a78a8679199968f6324ef2a7a9133fbf1476
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37427510"
---
# <a name="mssqlserver2020"></a>MSSQLSERVER_2020
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|2020|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico||  
|Testo del messaggio|Le dipendenze segnalate per l'entità "%.*ls" non includono riferimenti a colonne. L'entità fa riferimento a un oggetto che non esiste oppure si è verificato un errore in una o più istruzioni dell'entità.  Prima di provare a eseguire nuovamente la query, accertarsi che non siano presenti errori nell'entità e che tutti gli oggetti a cui l'entità fa riferimento esistano.|  
  
## <a name="explanation"></a>Spiegazione  
 La funzione di sistema **sys.dm_sql_referenced_entities** segnalerà tutte le dipendenze a livello di colonna per i riferimenti associati a schema. La funzione restituirà ad esempio tutte le dipendenze a livello di colonna per una vista indicizzata poiché una vista indicizzata richiede l'associazione allo schema. Tuttavia, quando l'entità a cui si fa riferimento non è associata a schema, le dipendenze della colonna vengono restituite solo quando è possibile associare tutte le istruzioni in cui si fa riferimento alle colonne. Le istruzioni possono essere associate correttamente solo se tutti gli oggetti esistono al momento dell'analisi delle istruzioni. Se un'istruzione definita nell'entità non viene associata, le dipendenze della colonna non verranno segnalate e la colonna **referenced_minor_id** restituirà 0. Quando le dipendenze della colonna non possono essere risolte, viene generato l'errore 2020. Questo errore non impedisce alla query di restituire dipendenze a livello di oggetto.  
  
## <a name="user-action"></a>Azione dell'utente  
 Correggere tutti gli errori identificati nel messaggio prima dell'errore 2020. Nell'esempio di codice seguente viene definita la vista `Production.ApprovedDocuments` nelle colonne `Title`, `ChangeNumber` e `Status` della tabella `Production.Document`. Viene eseguita una query sulla funzione di sistema **sys.dm_sql_referenced_entities** per gli oggetti e le colonne da cui dipende la vista `ApprovedDocuments`. Poiché la vista non viene creata utilizzando la clausola WITH SCHEMA_BINDING, è possibile modificare le colonne con riferimenti nella vista della tabella a cui si fa riferimento. Nell'esempio viene modificata la colonna `ChangeNumber` della tabella `Production.Document` rinominandola con `TrackingNumber`. Viene eseguita di nuovo una query sulla vista del catalogo per la vista `ApprovedDocuments`. Non è però possibile eseguire l'associazione a tutte le colonne definite nella vista. Vengono restituiti gli errori 207 e 2020 identificando il problema. Per risolvere il problema, è necessario modificare la vista in modo da riflettere il nuovo nome della colonna.  
  
 `USE AdventureWorks2012;`  
  
 `GO`  
  
 `CREATE VIEW Production.ApprovedDocuments`  
  
 `AS`  
  
 `SELECT Title, ChangeNumber, Status`  
  
 `FROM Production.Document`  
  
 `WHERE Status = 2;`  
  
 `GO`  
  
 `SELECT referenced_schema_name AS schema_name`  
  
 `,referenced_entity_name AS table_name`  
  
 `,referenced_minor_name AS referenced_column`  
  
 `FROM sys.dm_sql_referenced_entities ('Production.ApprovedDocuments', 'OBJECT');`  
  
 `GO`  
  
 `EXEC sp_rename 'Production.Document.ChangeNumber', 'TrackingNumber', 'COLUMN';`  
  
 `GO`  
  
 `SELECT referenced_schema_name AS schema_name`  
  
 `,referenced_entity_name AS table_name`  
  
 `,referenced_minor_name AS referenced_column`  
  
 `FROM sys.dm_sql_referenced_entities ('Production.ApprovedDocuments', 'OBJECT');`  
  
 `GO`  
  
 La query restituisce i messaggi di errore seguenti:  
  
 `Msg 207, Level 16, State 1, Procedure ApprovedDocuments, Line 3`  
  
 `Invalid column name 'ChangeNumber'.`  
  
 `Msg 2020, Level 16, State 1, Line 1`  
  
 `The dependencies reported for entity`  
  
 `"Production.ApprovedDocuments" do not include references to`  
  
 `columns. This is either because the entity references an`  
  
 `object that does not exist or because of an error in one or`  
  
 `more statements in the entity. Before rerunning the query,`  
  
 `ensure that there are no errors in the entity and that all`  
  
 `objects referenced by the entity exist.`  
  
 Nell'esempio seguente viene corretto il nome della colonna nella vista.  
  
 `USE AdventureWorks2012;`  
  
 `GO`  
  
 `ALTER VIEW Production.ApprovedDocuments`  
  
 `AS`  
  
 `SELECT Title,TrackingNumber, Status`  
  
 `FROM Production.Document`  
  
 `WHERE Status = 2;`  
  
 `GO`  
  
## <a name="see-also"></a>Vedere anche  
 [sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql)  
  
  

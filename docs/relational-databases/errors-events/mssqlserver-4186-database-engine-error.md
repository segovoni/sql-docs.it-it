---
title: MSSQLSERVER_4186 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 4186 (Database Engine error)
ms.assetid: 1ae88554-f291-45bc-a186-6f41d9cd0fca
caps.latest.revision: 14
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8192d47221f0d220b114636a7749e040c63ff9f6
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2018
ms.locfileid: "34323412"
---
# <a name="mssqlserver4186"></a>MSSQLSERVER_4186
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|4186|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico||  
|Testo del messaggio|Colonna '%ls.%. Impossibile fare riferimento a *ls' nella clausola OUTPUT perché la definizione di colonna contiene una sottoquery o fa riferimento a una funzione che accede a dati utente o di sistema. Si presuppone che le funzioni non associate a schema eseguano per impostazione predefinita l'accesso ai dati. Rimuovere la sottoquery o la funzione dalla definizione di colonna o rimuovere la colonna dalla clausola OUTPUT.|  
  
## <a name="explanation"></a>Spiegazione  
Per impedire un comportamento non deterministico, la clausola OUTPUT non può fare riferimento a una colonna di una vista o di una funzione inline con valori di tabella se la colonna in questione viene definita mediante uno dei metodi seguenti:  
  
-   Sottoquery.  
  
-   Funzione definita dall'utente che esegue, o si presume esegua, l'accesso ai dati dell'utente o di sistema.  
  
-   Colonna calcolata che contiene una funzione definita dall'utente che esegue l'accesso ai dati dell'utente o di sistema nella relativa definizione.  
  
### <a name="examples"></a>Esempi  
**Visualizzare una colonna definita da una sottoquery**  
  
Nell'esempio seguente viene creata una vista che utilizza una sottoquery dell'elenco di selezione per definire la colonna `State`. Un'istruzione UPDATE fa quindi riferimento alla colonna `State` nella clausola OUTPUT e ha esito negativo a causa della sottoquery nell'elenco di selezione.  
  
```  
USE AdventureWorks2012;  
GO  
CREATE VIEW dbo.V1  
AS  
    SELECT City,  
-- subquery to return the State name  
           (SELECT Name FROM Person.StateProvince AS sp   
            WHERE sp.StateProvinceID = a.StateProvinceID) AS State  
    FROM Person.Address AS a;  
GO  
--Reference the State column in the OUTPUT clause of an UPDATE statement  
UPDATE dbo.V1   
SET City = City + 'Test'   
OUTPUT deleted.City, deleted.State, inserted.City, inserted.State  
WHERE State = 'Texas';  
GO  
```  
  
**Visualizzare una colonna definita da una funzione**  
  
Nell'esempio seguente viene creata una vista che usa la funzione scalare di accesso ai dati `dbo.ufnGetStock`dell'elenco di selezione per definire la colonna `CurrentInventory`. Un'istruzione UPDATE fa quindi riferimento alla colonna `CurrentInventory` nella clausola OUTPUT.  
  
```  
USE AdventureWorks2012;  
GO  
CREATE VIEW Production.ReorderLevels  
AS  
    SELECT ProductID, ProductModelID, ReorderPoint,  
           dbo.ufnGetStock(ProductID) AS CurrentInventory  
    FROM Production.Product;  
GO  
  
UPDATE Production.ReorderLevels  
SET ReorderPoint += CurrentInventory  
OUTPUT deleted.ReorderPoint, deleted.CurrentInventory,  
       inserted.ReorderPoint, inserted.CurrentInventory  
WHERE ProductModelID BETWEEN 75 and 80;  
```  
  
## <a name="user-action"></a>Azione dell'utente  
È possibile correggere l'errore 4186 in uno dei modi seguenti:  
  
-   Utilizzare i join anziché le sottoquery per definire la colonna nella vista o nella funzione. È ad esempio possibile riscrivere la vista `dbo.V1` come segue.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE VIEW dbo.V1  
    AS  
        SELECT City, sp.Name AS State  
        FROM Person.Address AS a   
        JOIN Person.StateProvince AS sp   
        ON sp.StateProvinceID = a.StateProvinceID;  
    ```  
  
-   Esaminare la definizione della funzione definita dall'utente. Se la funzione non esegue l'accesso ai dati dell'utente o del sistema, modificarla in modo da includere la clausola WITH SCHEMABINDING.  
  
-   Rimuovere la colonna dalla clausola OUTPUT.   
  
## <a name="see-also"></a>Vedere anche  
[Clausola OUTPUT &#40;Transact-SQL&#41;](~/t-sql/queries/output-clause-transact-sql.md)  
  

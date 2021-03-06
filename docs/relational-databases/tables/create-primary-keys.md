---
title: Creare chiavi primarie | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: table-view-index
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- primary keys [SQL Server], creating
ms.assetid: 85c623ca-4656-4d70-a9db-ee4d897cd214
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: bd476ff279b30d79f4f096f3978ec96c9333dce3
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/04/2018
ms.locfileid: "37789292"
---
# <a name="create-primary-keys"></a>Creazione di chiavi primarie
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

 > Per il contenuto relativo alle versioni precedenti di SQL Server, vedere [Creazione di chiavi primarie](https://msdn.microsoft.com/en-US/library/ms189039(SQL.120).aspx).

  È possibile definire una chiave primaria in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)]. Con la creazione di una chiave primaria è possibile creare automaticamente un indice cluster univoco o un indice non cluster corrispondente in base a quanto specificato.  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   In una tabella è possibile includere un solo vincolo PRIMARY KEY.  
  
-   Tutte le colonne specificate in un vincolo PRIMARY KEY devono essere definite come NOT NULL. Se non si specifica il supporto di valori Null, per tutte le colonne coinvolte in un vincolo PRIMARY KEY viene impostato NOT NULL.  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
 Per la creazione di una nuova tabella con una chiave primaria è richiesta l'autorizzazione CREATE TABLE per il database e l'autorizzazione ALTER per lo schema in cui viene creata la tabella.  
  
 Per la creazione di una chiave primaria in una tabella esistente è richiesta l'autorizzazione ALTER per la tabella.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-create-a-primary-key"></a>Per creare una chiave primaria  
  
1.  In Esplora oggetti fare clic con il pulsante destro del mouse sulla tabella nella quale aggiungere un vincolo univoco e scegliere **Progetta**.  
  
2.  In **Progettazione tabelle**fare clic sul selettore di riga per la colonna di database che si desidera definire come chiave primaria. Per selezionare più colonne, tenere premuto il tasto CTRL e fare clic sul selettore di riga delle altre colonne.  
  
3.  Fare clic con il pulsante destro del mouse sul selettore di riga per la colonna e selezionare **Imposta chiave primaria**.  
  
> [!CAUTION]  
>  Per ridefinire la chiave primaria, sarà necessario eliminare tutte le relazioni alla chiave primaria esistente prima di poterne creare una nuova. Verrà visualizzato un messaggio di avviso in cui si notificherà che nel corso del processo le relazioni esistenti verranno eliminate automaticamente.  
  
 Una colonna chiave primaria è contrassegnata da un simbolo di chiave primaria nel corrispondente selettore di riga.  
  
 Se una chiave primaria è composta da più colonne, è consentita la presenza di valori duplicati in una colonna ma è comunque richiesta l'univocità delle combinazioni di valori tratti da tutte le colonne nella chiave primaria.  
  
 Se si definisce una chiave composta, l'ordine delle colonne nella chiave primaria corrisponderà all'ordine delle colonne come visualizzate nella tabella. È comunque possibile modificare l'ordine delle colonne dopo la creazione della chiave primaria. Per altre informazioni, vedere [Modifica chiavi primarie](../../relational-databases/tables/modify-primary-keys.md).  
  
##  <a name="TsqlProcedure"></a> Uso di Transact-SQL  

### <a name="to-create-a-primary-key-in-an-existing-table"></a>Per creare una chiave primaria in una tabella esistente  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra delle query e fare clic su **Esegui**. Nell'esempio si crea una chiave primaria nella colonna `TransactionID`.  
  
    ```sql  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE Production.TransactionHistoryArchive   
    ADD CONSTRAINT PK_TransactionHistoryArchive_TransactionID PRIMARY KEY CLUSTERED (TransactionID);  
    GO  
    ```  
  
### <a name="to-create-a-primary-key-in-a-new-table"></a>Per creare una chiave primaria in una nuova tabella  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra delle query e fare clic su **Esegui**. Nell'esempio si crea una tabella e si definisce una chiave primaria nella colonna `TransactionID`.  
  
    ```sql  
    USE AdventureWorks2012;  
    GO  
    CREATE TABLE Production.TransactionHistoryArchive1  
    (  
       TransactionID int IDENTITY (1,1) NOT NULL,  
       CONSTRAINT PK_TransactionHistoryArchive_TransactionID PRIMARY KEY CLUSTERED (TransactionID)  
    );  
    GO  
    ```  

### <a name="to-create-a-primary-key-with-nonclustered-index-in-a-new-table"></a>Per creare una chiave primaria con un indice non cluster in una nuova tabella  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra delle query e fare clic su **Esegui**. Nell'esempio si crea una tabella e si definisce una chiave primaria nella colonna `CustomerID` e un indice cluster in `TransactionID`.  
  
    ```sql  
    -- Select appropriate database
    USE AdventureWorks2012;  
    GO  
    -- Create table to add the clustered index
    CREATE TABLE Production.TransactionHistoryArchive1  
    (  
       CustomerID uniqueidentifier DEFAULT NEWSEQUENTIALID(),
       TransactionID int IDENTITY (1,1) NOT NULL,  
       CONSTRAINT PK_TransactionHistoryArchive_TransactionID PRIMARY KEY NONCLUSTERED (uniqueidentifier)  
    );  
    GO  

    -- Now add the clustered index
    CREATE CLUSTERED INDEX CIX_TransactionID ON Production.TransactionHistoryArchive1 (TransactionID);
    GO
    ```  

## <a name="see-also"></a>Vedere anche    
[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)    
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)     
[table_constraint &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-table-constraint-transact-sql.md)    

---
Title: 'Tutorial: Additional tips and tricks for using SQL Server Management Studio'
description: 'Esercitazione che illustra suggerimenti e consigli aggiuntivi per usare SSMS. '
keywords: SQL Server, SSMS, SQL Server Management Studio
author: MashaMSFT
ms.author: mathoma
ms.date: 03/13/2018
ms.topic: Tutorial
ms.suite: sql
ms.prod: sql
ms.technology: ssms
ms.prod_service: sql-tools
ms.reviewer: sstein
manager: craigg
helpviewer_keywords:
- source controls [SQL Server Management Studio], tutorials
- Help [SQL Server], SQL Server Management Studio
- tutorials [SQL Server Management Studio]
- Transact-SQL tutorials
- SQL Server Management Studio [SQL Server], tutorials
ms.openlocfilehash: 80d50132c4e2b38ecda9d24b3c0f4c09b93ca4e6
ms.sourcegitcommit: b5ab9f3a55800b0ccd7e16997f4cd6184b4995f9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/23/2018
ms.locfileid: "34455255"
---
# <a name="tutorial-additional-tips-and-tricks-for-using-ssms"></a>Esercitazione: Suggerimenti e consigli per l'uso di SSMS
Questa esercitazione offre alcuni suggerimenti aggiuntivi per l'uso di SQL Server Management Studio (SSMS). Questo articolo illustra come: 

> [!div class="checklist"]
> * Inserire e rimuovere commenti nel testo Transact-SQL (T-SQL)
> * Impostare un rientro del testo
> * Filtrare oggetti in Esplora oggetti
> * Accedere al log degli errori di SQL Server
> * Trovare il nome dell'istanza di SQL Server

## <a name="prerequisites"></a>Prerequisites
Per completare questa esercitazione, sono necessari SQL Server Management Studio, l'accesso a un'istanza di SQL Server e un database AdventureWorks. 

- Installare [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).
- Installare [SQL Server 2017 Developer Edition](https://www.microsoft.com/sql-server/sql-server-downloads).
- Scaricare un [database di esempio AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases). Per informazioni su come ripristinare un database in SSMS, vedere [Ripristino di un database](https://docs.microsoft.com/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms). 


## <a name="commentuncomment-your-t-sql-code"></a>Inserire e rimuovere commenti nel codice T-SQL
È possibile inserire e rimuovere commenti in parti del testo usando il pulsante **Commento** sulla barra degli strumenti. Il testo che viene impostato come commento non viene eseguito. 

1. Aprire SQL Server Management Studio. 
2. Connettersi all'istanza di SQL Server.
3. Aprire una finestra Nuova query. 
4. Incollare il codice T-SQL seguente nella finestra di testo: 

  ```sql
    USE master
    GO

    -- Drop the database if it already exists
    IF  EXISTS (
        SELECT name 
            FROM sys.databases 
            WHERE name = N'TutorialDB'
            )

    DROP DATABASE TutorialDB
    GO

    CREATE DATABASE TutorialDB
    GO

    ALTER DATABASE [TutorialDB] SET QUERY_STORE=ON
    GO
 ``` 


5. Evidenziare la parte di testo **Alter Database** e quindi selezionare il pulsante **Commento** sulla barra degli strumenti: 

    ![Pulsante Commento](media/ssms-tricks/comment.png)
6. Selezionare **Esegui** per eseguire la parte di testo senza commenti. 
7. Evidenziare tutto ad eccezione del comando **Alter Database** e quindi selezionare il pulsante **Commento**:

    ![Commentare tutto](media/ssms-tricks/commenteverything.png)

8. Evidenziare la parte di testo **Alter Database** e quindi selezionare il pulsante **Rimuovi commento** per rimuovere i commenti:

    ![Rimuovere commenti dal testo](media/ssms-tricks/uncomment.png)
    
9. Selezionare **Esegui** per eseguire la parte di testo senza commenti. 

## <a name="indent-your-text"></a>Impostare un rientro del testo
È possibile usare i pulsanti di rientro sulla barra degli strumenti per aumentare o ridurre il rientro del testo. 

1. Aprire una finestra Nuova query. 
2. Incollare il codice T-SQL seguente nella finestra di testo: 

  ```sql
    USE master
    GO

    -- Drop the database if it already exists
    IF  EXISTS (
        SELECT name 
            FROM sys.databases 
            WHERE name = N'TutorialDB'
            )

    DROP DATABASE TutorialDB
    GO

    CREATE DATABASE TutorialDB
    GO

    ALTER DATABASE [TutorialDB] SET QUERY_STORE=ON
    GO
 ``` 
 
3. Evidenziare la parte di testo **Alter Database** e quindi selezionare il pulsante **Aumenta rientro** sulla barra degli strumenti per spostare il testo in avanti:

    ![Aumentare il rientro](media/ssms-tricks/increaseindent.png)

4. Evidenziare di nuovo la parte di testo **Alter Database** e quindi selezionare il pulsante **Riduci rientro** per riportare indietro il testo.

    ![Ridurre il rientro](media/ssms-tricks/decreaseindent.png)


## <a name="filter-objects-in-object-explorer"></a>Filtrare oggetti in Esplora oggetti
È possibile filtrare gli oggetti per semplificare il reperimento di oggetti specifici nei database con molti oggetti. In questa sezione viene illustrato come filtrare le tabelle, ma è possibile usare i passaggi seguenti in qualsiasi altro nodo in Esplora oggetti:

1. Connettersi all'istanza di SQL Server.
2. Espandere **Database** > **AdventureWorks** > **Tabelle**. Verranno visualizzate tutte le tabelle nel database.
5. Fare clic con il pulsante destro del mouse su **Tabelle** e quindi selezionare **Filtro** > **Impostazioni filtro**:

    ![Impostazioni filtro](media/ssms-tricks/filtersettings.png)

6. Nella finestra **Impostazioni filtro** è possibile modificare alcune delle impostazioni di filtro seguenti:
    - Filtra per nome: 
   
      ![Filtrare per nome](media/ssms-tricks/filterbyname.png)

    - Filtra per schema: 
    
      ![Filtrare per schema](media/ssms-tricks/filterbyschema.png)

7. Per cancellare il filtro, fare clic con il pulsante destro del mouse su **Tabelle** e quindi selezionare **Rimuovi filtro**.

    ![Rimuovere il filtro](media/ssms-tricks/removefilter.png)
    


## <a name="access-your-sql-server-error-log"></a>Accedere al log degli errori di SQL Server
Il log degli errori è un file che contiene i dettagli di ciò che si verifica nell'istanza di SQL Server. È possibile sfogliare il log degli errori in SSMS ed eseguire query su di esso. Il log degli errori è un file con estensione log che si trova sul disco.

### <a name="open-the-error-log-in-ssms"></a>Aprire il log degli errori in SSMS
1. Connettersi all'istanza di SQL Server.  
2. Espandere **Gestione** > **Log di SQL Server**. 
4. Fare clic con il pulsante destro del mouse sul log degli errori **Corrente** e quindi selezionare **Visualizza log di SQL Server**:

    ![Visualizzare il log degli errori in SSMS](media/ssms-tricks/viewerrorloginssms.png)

### <a name="query-the-error-log-in-ssms"></a>Eseguire query sul log degli errori in SSMS
1. Connettersi all'istanza di SQL Server.
2. Aprire una finestra Nuova query.
3. Incollare il codice T-SQL seguente nella finestra di query:

 ```sql
   sp_readerrorlog 0,1,'Server process ID' 
  ``` 

4. Sostituire il testo tra virgolette singole con il testo da cercare.
5. Eseguire la query, quindi esaminare i risultati:
   
    ![Eseguire query sul log degli errori](media/ssms-tricks/queryerrorlog.png)


### <a name="find-the-error-log-location-if-youre-connected-to-sql-server"></a>Trovare il percorso del log degli errori se si è connessi a SQL Server
1. Connettersi all'istanza di SQL Server.
2. Aprire una finestra Nuova query.
3. Incollare il codice T-SQL seguente nella finestra di query e selezionare **Esegui**:

 ```sql
    SELECT SERVERPROPERTY('ErrorLogFileName') AS 'Error log file location'  
  ``` 

4. I risultati illustrano il percorso del log degli errori nel file system: 

    ![Trovare il log degli errori mediante query](media/ssms-tricks/finderrorlogquery.png)

### <a name="find-the-error-log-location-if-you-cant-connect-to-sql-server"></a>Trovare il percorso del log degli errori se non è possibile connettersi a SQL Server
1. Aprire Gestione configurazione SQL Server. 
2. Espandere **Servizi**.
3. Fare clic con il pulsante destro del mouse sull'istanza di SQL Server e quindi selezionare **Proprietà**:

    ![Proprietà del server di Gestione configurazione](media/ssms-tricks/serverproperties.PNG)

4. Selezionare la scheda **Parametri di avvio**.
5. Nell'area **Parametri esistenti** il percorso dopo "-e" è il percorso del log degli errori: 
    
    ![Log degli errori](media/ssms-tricks/errorlog.png)
    
    In questo percorso sono presenti diversi file errorlog.*. Il nome del file che termina con *.log è il file del log degli errori corrente. I nomi di file che terminano con numeri sono i file di log precedenti. A ogni riavvio dell'istanza di SQL Server viene creato un nuovo log.

6. Aprire il file errorlog.log nel Blocco note. 

## <a name="determine-sql-server-name"></a>Trovare il nome di SQL Server
Per trovare il nome dell'istanza di SQL Server prima e dopo la connessione a SQL Server sono disponibili alcune opzioni.  

### <a name="before-you-connect-to-sql-server"></a>Prima di connettersi a SQL Server
1. Seguire la procedura per individuare il [log degli errori di SQL Server su disco](#finding-your-error-log-if-you-cannot-connect-to-sql). 
2. Aprire il file errorlog.log nel Blocco note.  
3. Cercare il testo *Server name is*.
    
    Ciò che è racchiuso tra virgolette singole è il nome dell'istanza di SQL Server a cui ci si connetterà:

    ![Trovare il nome del server nel log degli errori](media/ssms-tricks/servernameinlog.png)
    
    Il formato del nome è NOMEHOST\NOMEISTANZA. Se viene visualizzato solo il nome host, l'istanza installata è l'istanza predefinita e il suo nome è MSSQLSERVER. Quando ci si connette a un'istanza predefinita, è sufficiente immettere il nome host per connettersi all'istanza di SQL Server.  

### <a name="when-youre-connected-to-sql-server"></a>Quando si è connessi a SQL Server 
Quando si è connessi a SQL Server, il nome del server è disponibile in tre posizioni: 

1. Il nome del server è elencato in Esplora oggetti:

    ![Nome dell'istanza di SQL Server in Esplora oggetti](media/ssms-tricks/nameinobjectexplorer.png)
2. Il nome del server è elencato nella finestra di query:

    ![Nome dell'istanza di SQL Server nella finestra di query](media/ssms-tricks/nameinquerywindow.png)
3. Il nome del server è elencato in **Proprietà**.
    - Selezionare **Finestra Proprietà** dal menu **Visualizza**:

      ![Nome dell'istanza di SQL Server nella finestra Proprietà](media/ssms-tricks/nameinproperties.png)

### <a name="if-youre-connected-to-an-alias-or-availability-group-listener"></a>Se si è connessi a un alias o a un listener del gruppo di disponibilità 
Se si è connessi a un alias o a un listener del gruppo di disponibilità, questa informazione viene visualizzata in Esplora oggetti e Proprietà. In questo caso il nome di SQL Server potrebbe non essere immediatamente evidente e deve essere eseguita una query per recuperarlo: 

1. Connettersi all'istanza di SQL Server.
2. Aprire una finestra Nuova query.
3. Incollare il codice T-SQL seguente nella finestra: 

  ```sql
   select @@Servername 
 ``` 
4. Visualizzare i risultati della query per identificare il nome dell'istanza di SQL Server a cui si è connessi: 
    
    ![Eseguire una query per recuperare il nome di SQL Server](media/ssms-tricks/queryservername.png)



---
title: 'Lezione 7: Spostare i file di dati in archiviazione di Microsoft Azure | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 26aa534a-afe7-4a14-b99f-a9184fc699bd
caps.latest.revision: 9
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 44bc025ce3eb536e10f4c77410ea487e59f006ee
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37162712"
---
# <a name="lesson-7-move-your-data-files-to-windows-azure-storage"></a>Lezione 7: spostare i file di dati in Archiviazione di Windows Azure
  In questa lezione, verrà illustrato come spostare i file di dati in Archiviazione di Windows Azure (non l'istanza di SQL Server). È possibile seguire questa lezione anche senza aver completato le lezioni 4, 5 e 6.  
  
 Per spostare i file di dati nel Servizio di archiviazione Windows Azure è possibile utilizzare l'istruzione `ALTER DATABASE` che consente di modificare il percorso dei file di dati.  
  
 Per questa lezione si presuppone che l'utente abbia già completato i passaggi seguenti:  
  
-   Creazione di un account di Archiviazione di Windows Azure.  
  
-   Creazione di un contenitore nell'account di Archiviazione di Windows Azure.  
  
-   Creazione dei criteri in un contenitore con diritti di lettura, scrittura ed elenco. Generazione di una chiave SAS.  
  
-   Creazione di una credenziale di SQL Server nel computer di origine.  
  
 Successivamente, utilizzare i passaggi seguenti per spostare i file di dati in Archiviazione di Windows Azure:  
  
1.  Innanzitutto, creare un database di prova nel computer di origine e aggiungere alcuni dati.  
  
    ```tsql  
  
    USE master;   
    CREATE DATABASE TestDB1Alter;   
    GO   
    USE TestDB1Alter;   
    GO   
    CREATE TABLE Table1 (Col1 int primary key, Col2 varchar(20));   
    GO   
    INSERT INTO Table1 (Col1, Col2) VALUES (1, 'string1'), (2, 'string2');   
    GO  
  
    ```  
  
2.  Eseguire il codice seguente:  
  
    ```tsql  
  
    -- In the following statement, modify the path specified in FILENAME to   
    -- the new location of the file in Windows Azure Storage container.   
    ALTER DATABASE TestDB1Alter    
        MODIFY FILE ( NAME = TestDB1Alter,    
                    FILENAME = 'https://teststorageaccnt.blob.core.windows.net/testcontaineralter/TestDB1AlterData.mdf');   
    GO  
  
    ```  
  
3.  Quando si esegue questa operazione, verrà visualizzato il messaggio seguente: "File "TestDB1Alter" è stato modificato nel catalogo di sistema. Il nuovo percorso verrà utilizzato al successivo avvio del database."  
  
4.  Quindi, impostare il database come offline.  
  
    ```tsql  
  
    ALTER DATABASE TestDB1Alter SET OFFLINE;   
    GO  
  
    ```  
  
5.  A questo punto, è necessario copiare i file di dati in archiviazione di Azure usando uno dei seguenti metodi: [strumento AzCopy](http://blogs.msdn.com/b/windowsazurestorage/archive/2012/12/03/azcopy-uploading-downloading-files-for-windows-azure-blobs.aspx), [Put Page](https://msdn.microsoft.com/library/azure/ee691975.aspx), [riferimenti alla libreria Client di archiviazione](https://msdn.microsoft.com/library/azure/dn261237.aspx), o un oggetto strumento di terze parti storage explorer.  
  
     **Importante:** quando si usa questa nuova funzionalità avanzata, assicurarsi sempre che si crea un blob di pagine non un blob in blocchi.  
  
6.  Quindi, impostare il database come online.  
  
    ```tsql  
  
    ALTER DATABASE TestDB1Alter SET ONLINE;   
    GO  
  
    ```  
  
 **Lezione successiva:**  
  
 [Lezione 8. Ripristinare un database in Archiviazione di Windows Azure](lesson-7-restore-a-database-to-a-point-in-time.md)  
  
  

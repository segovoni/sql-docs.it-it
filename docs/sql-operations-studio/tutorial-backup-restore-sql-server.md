---
title: Backup e ripristino di un database tramite SQL Operations Studio (anteprima) | Microsoft Docs
description: Informazioni su come eseguire backup e ripristino di un database utilizzando SQL Operations Studio (anteprima)
ms.custom: tools|sos
ms.date: 11/15/2017
ms.prod: sql
ms.reviewer: alayu; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: tutorial
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 22a453caa9d29432381da6861a0f0c4e3e61d77e
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34582453"
---
# <a name="backup-and-restore-using-includename-sosincludesname-sos-shortmd"></a>Backup e ripristino mediante [!INCLUDE[name-sos](../includes/name-sos-short.md)]

In questa esercitazione si apprenderà come sfruttare[!INCLUDE[name-sos](../includes/name-sos-short.md)] al fine di:
> [!div class="checklist"]
> * Effettuare il backup di un database  
> * Visualizzare lo stato del backup
> * Generare lo script utilizzato per eseguire il backup
> * Ripristinare un database
> * Visualizzare lo stato dell'attività di ripristino

## <a name="prerequisites"></a>Prerequisiti

Questa esercitazione richiede il database *TutorialDB* su SQL Server. Per crearlo, completare la guida rapida seguente:

- [Connettersi ed eseguire query su SQL Server tramite[!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)


## <a name="backup-a-database"></a>Effettuare il backup di un database 

1. Aprire la dashboard del database TutorialDB (aprire la barra laterale **SERVER** con **CTRL+G**, espandere **Database**, fare clic con il pulsante destro del mouse su **TutorialDB** e selezionare **Gestisci**).  

2. Aprire la finestra di dialogo **Backup database** (fare clic su **Backup** sul widget **Attività**).

   ![Widget attività](./media/tutorial-backup-restore-sql-server/tasks.png)

3. In questa esercitazione utilizzeremo le opzioni predefinite per il backup. Fare clic su **Backup**.
   ![finestra di dialogo backup](./media/tutorial-backup-restore-sql-server/backup-dialog.png)

Dopo aver fatto clic su **Backup**, la finestra di dialogo **Backup database** si chiude e inizia il processo di backup.

## <a name="view-the-backup-status-and-view-the-backup-script"></a>Visualizzare lo stato del backup e lo script di backup

1. Aprire **Cronologia attività** tramite l'icona ad orologio nella *barra delle azioni* o premere **CTRL+T**.

   ![Cronologia attività](./media/tutorial-backup-restore-sql-server/task-history.png)

2. Per visualizzare lo script di backup nell'editor, premere il tasto destro su **Backup del database effettuato con successo** e selezionare **Script**.

   ![script di backup](./media/tutorial-backup-restore-sql-server/task-script.png) 

## <a name="restore-a-database-from-a-backup-file"></a>Ripristinare un database da un file di backup


1. Aprire la barra laterale **SERVER** (**CTRL+G**), premere il tasto destro sul vostro server e scegliere **Gestisci**.  

2. Aprire la finestra di dialogo **Ripristina database** (fare clic su **Ripristino** sul widget **attività**).

2. Selezionare **file di Backup** nel campo **ripristina da**.  

3. Fare clic sui puntini di sospensione (...) nel **percorso del file di Backup** e selezionare il file di backup più recente per *TutorialDB*.

3. Scrivere ora **TutorialDB_Restored** nel campo **database di destinazione** nell'area **destinazione** per ripristinare il file di backup in un nuovo database.

   ![ripristino](./media/tutorial-backup-restore-sql-server/restore.png)

4. Fare clic su **Ripristina**

5. Per visualizzare lo stato dell'operazione di ripristino, premere **CTRL + T** per aprire la **Cronologia attività** barra laterale.

   ![ripristino](./media/tutorial-backup-restore-sql-server/task-history-restore.png)


In questa esercitazione, si è appreso come:
> [!div class="checklist"]
> * Effettuare il backup di un database  
> * Visualizzare lo stato del backup
> * Generare lo script utilizzato per eseguire il backup
> * Ripristinare un database
> * Visualizzare lo stato dell'attività di ripristino


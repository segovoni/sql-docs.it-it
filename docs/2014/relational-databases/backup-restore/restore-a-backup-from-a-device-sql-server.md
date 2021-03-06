---
title: Ripristinare un backup da un dispositivo (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: backup-restore
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- restoring databases [SQL Server], device restores
- backup devices [SQL Server], restoring from
- database restores [SQL Server], device restores
- devices [SQL Server]
ms.assetid: 6e139de7-7de2-4d18-9df0-beac31ba7ff1
caps.latest.revision: 26
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 3134fd42f91c63b14abc9b7c77bc415c2e837859
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37285317"
---
# <a name="restore-a-backup-from-a-device-sql-server"></a>Ripristino di un backup da un dispositivo (SQL Server)
  In questo argomento viene descritto il ripristino di un backup da un dispositivo in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
> [!NOTE]  
>  Per informazioni sul backup di SQL Server nel servizio di archiviazione BLOB di Windows Azure, vedere [SQL Server Backup and Restore with Windows Azure Blob Storage Service](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Security](#Security)  
  
-   **Per ripristinare un backup da un dispositivo utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
 Se il database da ripristinare non esiste, per eseguire un'operazione RESTORE l'utente deve disporre delle autorizzazioni CREATE DATABASE. Se il database esiste, le autorizzazioni per l'istruzione RESTORE vengono assegnate per impostazione predefinita ai membri dei ruoli predefiniti del server **sysadmin** e **dbcreator** e al proprietario (**dbo**) del database. Per l'opzione FROM DATABASE_SNAPSHOT, il database esiste sempre.  
  
 Le autorizzazioni per l'istruzione RESTORE vengono assegnate ai ruoli in cui le informazioni sull'appartenenza sono sempre disponibili per il server. Poiché è possibile controllare l'appartenenza ai ruoli predefiniti del database solo quando il database è accessibile e non è danneggiato, condizioni che non risultano sempre vere quando si esegue un'operazione RESTORE, i membri del ruolo predefinito del database **db_owner** non dispongono delle autorizzazioni per l'istruzione RESTORE.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-restore-a-backup-from-a-device"></a>Per ripristinare un backup da un dispositivo  
  
1.  Dopo aver stabilito la connessione all'istanza appropriata del [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Esplora oggetti fare clic sul nome del server per espandere l'albero del server.  
  
2.  Espandere **Database**e, a seconda del database, selezionare un database utente o espandere **Database di sistema** e selezionare un database di sistema.  
  
3.  Fare clic con il pulsante destro del mouse sul database, scegliere **Attività**e quindi fare clic su **Ripristina**.  
  
4.  Fare clic sul tipo di operazione di ripristino desiderata,**Database**, **File e filegroup**o **Log delle transazioni**. Verrà aperta la finestra di dialogo appropriata.  
  
5.  Nella pagina **Generale** fare clic su **Dispositivo di origine** nella sezione **Origine ripristino**.  
  
6.  Fare clic su Sfoglia per la casella di testo **Dispositivo di origine** e verrà aperta la finestra di dialogo **Seleziona backup** .  
  
7.  Nella casella di testo **Supporti di backup** selezionare **Dispositivo di backup**e quindi fare clic sul pulsante **Aggiungi** per aprire la finestra di dialogo **Seleziona dispositivo di backup** .  
  
8.  Nella casella di testo **Dispositivo di backup** selezionare il dispositivo che si desidera utilizzare per l'operazione di ripristino.  
  
##  <a name="TsqlProcedure"></a> Uso di Transact-SQL  
  
#### <a name="to-restore-a-backup-from-a-device"></a>Per ripristinare un backup da un dispositivo  
  
1.  Connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Nell'istruzione [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) , specificare un dispositivo di backup logico o fisico da utilizzare per l'operazione di backup. Questo esempio mostra come eseguire il ripristino da un file su disco con il nome fisico `Z:\SQLServerBackups\AdventureWorks2012.bak`.  
  
```tsql  
RESTORE DATABASE AdventureWorks2012  
   FROM DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak' ;  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [RESTORE FILELISTONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql)   
 [RESTORE HEADERONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-headeronly-transact-sql)   
 [RESTORE LABELONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-labelonly-transact-sql)   
 [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql)   
 [Ripristinare un backup del database nel modello di recupero con registrazione minima &#40;Transact-SQL&#41;](restore-a-database-backup-under-the-simple-recovery-model-transact-sql.md)   
 [Ripristinare un Backup del Database &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md)   
 [Ripristinare un backup differenziale del database &#40;SQL Server&#41;](restore-a-differential-database-backup-sql-server.md)   
 [Ripristinare un database in una nuova posizione &#40;SQL Server&#41;](restore-a-database-to-a-new-location-sql-server.md)   
 [Backup di file e filegroup &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md)   
 [Eseguire il backup di un log delle transazioni &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md)   
 [Creare un backup differenziale del database &#40;SQL Server&#41;](create-a-differential-database-backup-sql-server.md)  
  
  

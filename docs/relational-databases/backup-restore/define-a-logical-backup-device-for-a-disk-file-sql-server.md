---
title: Definire un dispositivo di backup logico per un file su disco (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.suite: sql
ms.technology: backup-restore
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- backup devices [SQL Server], defining
- backup devices [SQL Server], disks
- disk backup devices [SQL Server]
- database backups [SQL Server], disks
- backing up databases [SQL Server], disks
ms.assetid: 86331d43-c738-4523-ae3d-7d6700348ed1
caps.latest.revision: 39
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 595a8f5849388ce08ec2a373187eec014c243de9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32923496"
---
# <a name="define-a-logical-backup-device-for-a-disk-file-sql-server"></a>Definizione di un dispositivo di backup logico per un file su disco (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  In questo argomento viene descritto come definire un dispositivo di backup logico per un file su disco in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)]. Un dispositivo logico è un nome definito dall'utente tramite cui viene fatto riferimento a un dispositivo di backup fisico specifico, ovvero un file su disco o un'unità nastro.  L'inizializzazione del dispositivo fisico viene eseguita successivamente, quando viene scritto un backup nel dispositivo di backup.  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
     [Indicazioni](#Recommendations)  
  
     [Security](#Security)  
  
-   **Per definire un dispositivo di backup logico per un file su disco utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   Il nome del dispositivo logico deve essere univoco tra tutti i dispositivi di backup logici nell'istanza del server. Per visualizzare i nomi dei dispositivi logici esistenti, eseguire una query nella vista del catalogo [sys.backup_devices](../../relational-databases/system-catalog-views/sys-backup-devices-transact-sql.md) .  
  
###  <a name="Recommendations"></a> Indicazioni  
  
-   È consigliabile utilizzare come disco di backup un disco diverso da quelli in cui sono archiviati i dati di database e i log. Questa condizione è necessaria per garantire l'accesso ai backup in caso di errore del disco contenente il log o i dati.  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
 È richiesta l'appartenenza al ruolo predefinito del server **diskadmin** .  
  
 Richiede l'autorizzazione di scrittura sul disco.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-define-a-logical-backup-device-for-a-disk-file"></a>Per definire un dispositivo di backup logico per un file su disco  
  
1.  Dopo aver stabilito la connessione all'istanza appropriata del [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Esplora oggetti fare clic sul nome del server per espandere l'albero del server.  
  
2.  Espandere **Oggetti server**e fare clic con il pulsante destro del mouse su **Dispositivi di backup**.  
  
3.  Fare clic su **Nuovo dispositivo di backup**. Verrà visualizzata la finestra di dialogo **Dispositivo di backup** .  
  
4.  Immettere un nome di dispositivo.  
  
5.  Per la destinazione fare clic su **File** e specificare il percorso completo del file.  
  
6.  Per definire il nuovo dispositivo, fare clic su **OK**.  
  
 Per eseguire il backup in questo nuovo dispositivo, aggiungerlo al campo **Backup su** nella finestra di dialogo **Backup database** (**Generale**). Per altre informazioni, vedere [Creare un backup completo del database &#40;SQL Server&#41;](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md).  
  
##  <a name="TsqlProcedure"></a> Uso di Transact-SQL  
  
#### <a name="to-define-a-logical-backup-for-a-disk-file"></a>Per definire un backup logico per un file su disco  
  
1.  Connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra delle query e fare clic su **Esegui**. Questo esempio mostra come usare [sp_addumpdevice](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md) per definire un dispositivo di backup logico per un file su disco. L'esempio aggiunge il dispositivo di backup del disco denominato `mydiskdump`, con il nome fisico `c:\dump\dump1.bak`.  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_addumpdevice 'disk', 'mydiskdump', 'c:\dump\dump1.bak' ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)   
 [Dispositivi di backup &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-devices-sql-server.md)   
 [sys.backup_devices &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-backup-devices-transact-sql.md)   
 [sp_addumpdevice &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md)   
 [sp_dropdevice &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdevice-transact-sql.md)   
 [Definizione di un dispositivo di backup logico per un'unità nastro &#40;SQL Server&#41;](../../relational-databases/backup-restore/define-a-logical-backup-device-for-a-tape-drive-sql-server.md)   
 [Visualizzare le proprietà e il contenuto di un dispositivo di backup logico &#40;SQL Server&#41;](../../relational-databases/backup-restore/view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
  

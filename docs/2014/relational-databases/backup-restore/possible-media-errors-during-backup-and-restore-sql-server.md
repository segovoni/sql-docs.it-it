---
title: Possibili errori relativi ai supporti durante il backup e il ripristino (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: backup-restore
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- media errors [SQL Server]
- CONTINUE_AFTER_ERROR option
- errors [SQL Server], backups
- backups [SQL Server], errors
- RESTORE VERIFYONLY statement
- backup media [SQL Server], error management
- page checksums [SQL Server]
- backup checksums [SQL Server]
- backing up [SQL Server], media errors
- RESTORE statement, media errors
- NO_CHECKSUM option
- checksums [SQL Server]
ms.assetid: 83a27b29-1191-4f8d-9648-6e6be73a9b7c
caps.latest.revision: 36
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 9887d5f158e39ddae24bda31db0fbb76cb5e3482
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37298521"
---
# <a name="possible-media-errors-during-backup-and-restore-sql-server"></a>Possibili errori relativi ai supporti durante il backup e il ripristino (SQL Server)
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] includono un'opzione che permette di recuperare un database anche in presenza di errori. Un importante e nuovo meccanismo di rilevazione degli errori prevede l'utilizzo facoltativo di un checksum del backup, creato durante un'operazione di backup e convalidato durante un'operazione di ripristino. È quindi possibile controllare se un'operazione verifica la presenza di errori e se ne deve essere o meno arrestata l'esecuzione quando viene rilevato un errore. Se un backup contiene un checksum, le istruzioni RESTORE e RESTORE VERIFYONLY verificano la presenza di errori.  
  
> [!NOTE]  
>  I backup con mirroring consentono di disporre di un massimo di quattro copie (mirror) di set di supporti, offrendo copie alternative per il recupero in caso di errori che dipendono da supporti danneggiati. Per altre informazioni, vedere [Mirrored Backup Media Sets &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md).  
  
  
  
##  <a name="BckChecksums"></a> Checksum di backup  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sono supportati tre tipi di checksum: della pagine, dei blocchi dei log e del backup. Durante la generazione di un checksum del backup, l'istruzione BACKUP verifica che i dati letti dal database siano consistenti con l'eventuale indicazione di checksum o di pagina incompleta presente nel database.  
  
 L'istruzione BACKUP consente di eseguire il calcolo facoltativo di un checksum del backup nel flusso del backup stesso. Se in una pagina specifica sono presenti informazioni relative al checksum della pagina o a una pagina incompleta, durante il backup della pagina verrà inoltre verificato lo stato del checksum e della pagina incompleta, nonché l'ID della pagina. Non verranno aggiunti checksum alle pagine durante la creazione di un checksum del backup. Il backup delle pagine viene eseguito solo se queste esistono nel database e non implica la modifica delle pagine stesse.  
  
 Le procedure di verifica e creazione dei checksum del backup comportano un certo overhead, pertanto l'utilizzo di questo tipo di checksum può influire negativamente sulle prestazioni, interessando sia il carico di lavoro che la velocità effettiva del backup. I checksum del backup sono pertanto facoltativi. Quando si decide di generare checksum durante un backup, eseguire un attento monitoraggio dell'overhead della CPU nonché dell'impatto di eventuali carichi di lavoro eseguiti simultaneamente nel sistema.  
  
 L'istruzione BACKUP non modifica mai la pagina di origine sul disco né il contenuto di una pagina.  
  
 Quando i checksum di backup sono abilitati, l'operazione di backup esegue i passaggi descritti di seguito:  
  
1.  Prima di scrivere una pagina sui supporti di backup, l'operazione di backup verifica le eventuali informazioni esistenti a livello di pagina, ovvero esegue il rilevamento dei checksum della pagina o delle pagine incomplete. Se non esiste alcun tipo di checksum, il backup non può verificare la pagina. Le pagine non verificate vengono incluse nello stato in cui si trovano, e il relativo contenuto viene aggiunto al checksum complessivo del backup.  
  
     Se durante la verifica dell'operazione di backup viene rilevato un errore di pagina, il backup non riesce.  
  
    > [!NOTE]  
    >  Per ulteriori informazioni sui checksum delle pagine e sul rilevamento delle pagine incomplete, vedere l'opzione PAGE_VERIFY dell'istruzione ALTER DATABASE. Per altre informazioni, vedere [Opzioni ALTER DATABASE SET &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).  
  
2.  Indipendentemente dalla presenza di valori di checksum per la pagina, viene generato un checksum di backup separato per i flussi di backup. Le operazioni di ripristino possono utilizzare facoltativamente il checksum del backup per verificare che il backup non sia danneggiato. Il checksum del backup viene archiviato nei supporti di backup e non nelle pagine del database. È possibile utilizzare facoltativamente il checksum del backup in fase di ripristino.  
  
3.  Il set di backup viene contrassegnato come contenente checksum di backup (nella colonna **has_backup_checksums** di **msdb..backupset)**. Per altre informazioni, vedere [backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql).  
  
 Durante un'operazione di ripristino, se nel supporto di backup sono presenti checksum di backup, per impostazione predefinita le istruzioni RESTORE e RESTORE VERIFYONLY verificheranno solo i checksum di backup e delle pagine. In assenza di un checksum di backup, l'operazione di backup proseguirà senza verifica, in quanto, in tal caso, l'operazione di ripristino non è in grado di verificare in modo affidabile i checksum delle pagine.  
  
## <a name="response-to-page-checksum-errors-during-a-backup-or-restore-operation"></a>Risposta a errori di checksum di pagina durante un'operazione di backup o ripristino  
 Per impostazione predefinita, dopo avere rilevato un errore di checksum della pagina, l'operazione BACKUP o RESTORE non riesce e l'operazione RESTORE VERIFYONLY continua. Tuttavia, è possibile controllare se un'operazione specificata non riesce sul rilevamento di un errore o continua nel migliore dei modi.  
  
 Se un'operazione BACKUP continua dopo aver rilevato errori, l'operazione esegue i passaggi indicati di seguito:  
  
1.  Contrassegna il set di backup sul supporto come contenente errori e tiene traccia della pagina nella tabella **suspect_pages** del database **msdb**. Per altre informazioni, vedere [suspect_pages &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/suspect-pages-transact-sql).  
  
2.  Registra l'errore nel log degli errori di SQL Server.  
  
3.  Contrassegna il set di backup come contenente questo tipo di errore nella colonna **is_damaged** di **msdb.backupset**. Per altre informazioni, vedere [backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql).  
  
4.  Visualizza un messaggio per indicare che il backup è stato generato correttamente, ma contiene errori di pagina.  
  
##  <a name="RelatedTasks"></a> Attività correlate  
 **Per abilitare o disabilitare i checksum per i backup**  
  
-   [Abilitare o disabilitare il checksum di backup durante il backup o il ripristino &#40;SQL Server&#41;](enable-or-disable-backup-checksums-during-backup-or-restore-sql-server.md)  
  
 **Per controllare la risposta a un errore durante un'operazione di backup**  
  
-   [Specifica se un'operazione di backup o ripristino viene arrestata o prosegue in seguito a un errore &#40;SQL Server&#41;](specify-if-backup-or-restore-continues-or-stops-after-error.md)  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)   
 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)   
 [backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql)   
 [Set di supporti di backup con mirroring &#40;SQL Server&#41;](mirrored-backup-media-sets-sql-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)   
 [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql)  
  
  

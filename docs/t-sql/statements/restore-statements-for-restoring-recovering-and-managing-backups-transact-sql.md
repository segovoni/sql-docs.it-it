---
title: Le istruzioni di ripristino per il ripristino, il ripristino, la gestione dei backup (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- restoring files [SQL Server], RESTORE statement
- RESTORE statement, about restore operations
- database restores [SQL Server], RESTORE statement
- restoring databases [SQL Server], RESTORE statement
- database backups [SQL Server], RESTORE statement
- backing up databases [SQL Server], RESTORE statement
- file restores [SQL Server], RESTORE statement
- transaction log backups [SQL Server], RESTORE statement
ms.assetid: fb29a151-f312-4f85-b857-5deeca0de8ce
caps.latest.revision: 15
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 81443218a21a232248d3f237aba38cfc0d833b7e
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="restore-statements-for-restoring-recovering-and-managing-backups-transact-sql"></a>Istruzioni RESTORE per il ripristino, il recupero e la gestione dei backup (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  In questa sezione vengono descritte le istruzioni RESTORE per i backup. Oltre all'istruzione principale per il ripristino e il recupero dei backup, RESTORE {DATABASE | LOG}, sono disponibili numerose istruzioni RESTORE ausiliarie che semplificano la gestione dei backup e la pianificazione delle sequenze di ripristino. I comandi RESTORE ausiliari sono: RESTORE FILELISTONLY, RESTORE HEADERONLY, RESTORE LABELONLY, RESTORE REWINDONLY e RESTORE VERIFYONLY.  
  
> [!IMPORTANT]  
>  Nelle versioni precedenti di SQL Server qualsiasi utente poteva ottenere informazioni sui set e i dispositivi di backup tramite le istruzioni Transact-SQL RESTORE FILELISTONLY, RESTORE HEADERONLY, RESTORE LABELONLY e RESTORE VERIFYONLY. Poiché tali istruzioni rivelano informazioni sul contenuto dei file di backup, per eseguirle in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] e versioni successive è necessaria l'autorizzazione CREATE DATABASE. Questo requisito consente di proteggere i file di backup in modo da rendere le informazioni di backup più sicure rispetto alle versioni precedenti. Per informazioni su questa autorizzazione, vedere [GRANT - autorizzazioni per database &#40;Transact-SQL&#41;](../../t-sql/statements/grant-database-permissions-transact-sql.md).  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|.|Description|  
|---------------|-----------------|  
|[RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)|Descrive le istruzioni Transact-SQL RESTORE DATABASE e RESTORE LOG utilizzate per ripristinare e recuperare un database dai backup eseguiti con il comando BACKUP. RESTORE DATABASE viene utilizzata per i database con tutti i modelli di recupero. RESTORE LOG viene utilizzata solo con i modelli di recupero con registrazione completa e con registrazione minima delle operazioni bulk. RESTORE DATABASE può essere inoltre utilizzata per ripristinare un database in base a uno snapshot del database.|  
|[Argomenti RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-arguments-transact-sql.md)|Descrive gli argomenti riportati nella sezione "Sintassi" dell'istruzione RESTORE e delle istruzioni ausiliarie correlate RESTORE FILELISTONLY, RESTORE HEADERONLY, RESTORE LABELONLY, RESTORE REWINDONLY e RESTORE VERIFYONLY. La maggior parte degli argomenti sono supportati solo da un subset di queste sei istruzioni. Informazioni dettagliate sono contenute nella descrizione dell'argomento.|  
|[RESTORE FILELISTONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-filelistonly-transact-sql.md)|Descrive l'istruzione Transact-SQL RESTORE FILELISTONLY, che consente di restituire un set di risultati contenente un elenco dei file di database e di log inclusi nel set di backup.|  
|[RESTORE HEADERONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-headeronly-transact-sql.md)|Descrive l'istruzione Transact-SQL RESTORE HEADERONLY, che consente di restituire un set di risultati contente tutte le informazioni di intestazione del backup per tutti i set di backup in un dispositivo di backup specifico.|  
|[RESTORE LABELONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-labelonly-transact-sql.md)|Descrive l'istruzione Transact-SQL RESTORE LABELONLY, che consente di restituire un set di risultati contenente informazioni sui supporti di backup identificati dal dispositivo di backup specificato.|  
|[RESTORE REWINDONLY &#40; Transact-SQL &#41;](../../t-sql/statements/restore-statements-rewindonly-transact-sql.md)|Descrive l'istruzione Transact-SQL RESTORE REWINDONLY, che consente di riavvolgere e chiudere i dispositivi nastro lasciati aperti da istruzioni BACKUP o RESTORE eseguiti con l'opzione NOREWIND.|  
|[RESTORE VERIFYONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-verifyonly-transact-sql.md)|Descrive l'istruzione Transact-SQL RESTORE VERIFYONLY, che consente di verificare il backup ma non di ripristinarlo e di controllare che il set di backup sia completo e l'intero backup leggibile. Non viene verificata la struttura dei dati.|  
  
## <a name="see-also"></a>Vedere anche  
 [Backup e ripristino di database SQL Server](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)  
  
  
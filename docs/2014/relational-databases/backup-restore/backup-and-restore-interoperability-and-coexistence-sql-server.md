---
title: 'Backup e ripristino: interoperabilità e coesistenza (SQL Server) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: backup-restore
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- file restores [SQL Server], related features
- restoring [SQL Server], files
- restoring files [SQL Server], related features
- backups [SQL Server], files or filegroups
- file backups [SQL Server], related features
ms.assetid: 69f212b8-edcd-4c5d-8a8a-679ced33c128
caps.latest.revision: 45
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 655e4079fdd1bbdeaea6dd99fd5c36a0cac7f762
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37180138"
---
# <a name="backup-and-restore-interoperability-and-coexistence-sql-server"></a>Backup e ripristino: interoperabilità e coesistenza (SQL Server)
  In questo argomento vengono fornite alcune considerazioni sul backup e il ripristino di alcune funzionalità di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], tra cui ripristino dei file e avvio del database, ripristino online e indici disabilitati, mirroring del database, ripristino a fasi e indici full-text.  
  
 **Contenuto dell'argomento:**  
  
-   [Ripristino dei file e avvio del database](#FileRestoreAndDbStartup)  
  
-   [Ripristino online e indici disabilitati](#OnlineRestoreAndDisabledIndexes)  
  
-   [Mirroring del database e procedure di backup e ripristino](#DbMandBnR)  
  
-   [Ripristino a fasi e indici full-text](#PiecemealAndFTIndexes)  
  
-   [Backup e ripristino di file e compressione](#FileBnRandCompression)  
  
-   [Attività correlate](#RelatedTasks)  
  
##  <a name="FileRestoreAndDbStartup"></a> Ripristino dei file e avvio del database  
 Le informazioni contenute in questa sezione sono rilevanti solo per i database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che includono più filegroup.  
  
> [!NOTE]  
>  Quando un database viene avviato, viene eseguito un recupero e attivata la modalità online solo per i filegroup i cui file erano online al momento della chiusura del database.  
  
 Se si verifica un problema durante l'avvio del database, il recupero non riesce e il database viene contrassegnato come sospetto. Se è possibile isolare uno o più file in cui è presente il problema, l'amministratore del database può attivare la modalità offline per i file e tentare di riavviare il database. Per attivare la modalità offline per un file, è possibile utilizzare l'istruzione [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) seguente:  
  
 ALTER DATABASE *database_name* MODIFY FILE (nome **='*`filename`*'**, OFFLINE)  
  
 Se l'avvio ha esito positivo, tutti i filegroup che includono un file offline rimangono in modalità offline.  
  
##  <a name="OnlineRestoreAndDisabledIndexes"></a> Ripristino online e indici disabilitati  
 Le informazioni contenute in questa sezione sono rilevanti solo per i database che includono più filegroup e, in base al modello di recupero con registrazione minima, almeno un filegroup di sola lettura.  
  
 In questi casi, se un database è online, è possibile creare, eliminare, abilitare o disabilitare l'indice solo se tutti i filegroup che contengono una parte qualsiasi dell'indice sono online.  
  
 Per informazioni sul ripristino di filegroup offline, vedere [Ripristino in linea&#40;SQL Server&#41;](online-restore-sql-server.md).  
  
##  <a name="DbMandBnR"></a> Mirroring del database e procedure di backup e ripristino  
 Le informazioni contenute in questa sezione sono rilevanti solo per i database basati sul modello di recupero con registrazione completa che includono più filegroup.  
  
> [!NOTE]  
>  La funzionalità del mirroring di database verrà rimossa in una delle prossime versioni di Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. In alternativa, usare [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] .  
  
 Il mirroring del database è una soluzione per aumentare la disponibilità del database. Il mirroring viene implementato a livello di singolo database e funziona solo con database che utilizzano il modello di recupero con registrazione completa. Per altre informazioni, vedere [Mirroring del database &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md).  
  
> [!NOTE]  
>  Per distribuire le copie di un subset dei filegroup in un database, è necessario replicare solo gli oggetti dei filegroup che si desidera copiare in altri server. Per altre informazioni sulla replica, vedere [Replica di SQL Server](../../relational-databases/replication/sql-server-replication.md).  
  
### <a name="creating-the-mirror-database"></a>Creazione del database mirror  
 Il database mirror viene creato ripristinando i backup del database principale nel server mirror senza eseguirne il recupero (WITH NORECOVERY). Il ripristino deve mantenere lo stesso nome del database. Per altre informazioni, vedere [Preparare un database mirror per il mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md),  
  
 È possibile creare il database mirror utilizzando una sequenza di ripristino a fasi, se supportata. Non è tuttavia possibile avviare l'esecuzione del mirroring fino a quando non sono stati ripristinati tutti i filegroup e, in genere, fino a quando non sono stati ripristinati i backup del log necessari per portare il database mirror a un punto nel tempo sufficientemente vicino al database principale. Per altre informazioni, vedere [Ripristini a fasi &#40;SQL Server&#41;](piecemeal-restores-sql-server.md).  
  
### <a name="restrictions-on-backup-and-restore-during-mirroring"></a>Restrizioni relative a operazioni di backup e ripristino durante il mirroring  
 Mentre è attiva una sessione di mirroring del database, vengono applicate le restrizioni seguenti:  
  
-   Non sono consentite operazioni di backup e ripristino del database mirror.  
  
-   È consentito il backup del database principale, ma non è consentito utilizzare BACKUP LOG WITH NORECOVERY.  
  
-   Il ripristino del database principale non è consentito.  
  
##  <a name="PiecemealAndFTIndexes"></a> Ripristino a fasi e indici full-text  
 Le informazioni contenute in questa sezione sono rilevanti solo per i database che includono più filegroup e, in base al modello di recupero con registrazione minima, solo per i filegroup in sola lettura.  
  
 Gli indici full-text vengono archiviati nei filegroup del database e possono essere influenzati dall'esecuzione di un ripristino a fasi. Se l'indice full-text si trova nello stesso filegroup di uno o più dati della tabella associati, il ripristino a fasi verrà eseguito nel modo previsto.  
  
> [!NOTE]  
>  Per visualizzare l'ID del filegroup che contiene un indice full-text, selezionare la colonna data_space_id di [sys.fulltext_indexes](/sql/relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql).  
  
### <a name="full-text-indexes-and-tables-in-separate-filegroups"></a>Indici full-text e tabelle in filegroup distinti  
 Se un indice full-text si trova in un filegroup distinto rispetto ai dati delle tabelle associati, il funzionamento del ripristino a fasi dipenderà dal primo filegroup di cui viene eseguito il ripristino e per cui viene attivata la modalità online.  
  
-   Se il ripristino e l'attivazione della modalità online vengono eseguiti prima per il filegroup contenente l'indice full-text e quindi per il filegroup contenente i dati delle tabelle associati, il funzionamento della ricerca full-text è quello previsto non appena l'indice full-text è online.  
  
-   Se il ripristino e l'attivazione della modalità online vengono eseguiti prima per il filegroup contenente i dati delle tabelle e poi per il filegroup contenente l'indice full-text, è possibile che il comportamento della funzionalità full-text risulti diverso. Questa situazione si verifica poiché le istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] che attivano un popolamento, ricompilano il catalogo o riorganizzano il catalogo hanno esito negativo fino a quando non viene riattivata la modalità online per l'indice. Tali istruzioni includono CREATE FULLTEXT INDEX, ALTER FULLTEXT INDEX, DROP FULLTEXT INDEX e ALTER FULLTEXT CATALOG.  
  
     In questo caso, considerare in particolare i fattori seguenti:  
  
    -   Se all'indice full-text è associato il rilevamento delle modifiche, le istruzioni DML eseguite dall'utente avranno esito negativo fino a quando non viene attivata la modalità online per il filegroup. Anche l'operazione di eliminazione avrà esito negativo se il filegroup dell'indice non è online.  
  
    -   Indipendentemente dal rilevamento delle modifiche, le query full-text hanno esito negativo perché l'indice non è disponibile. Se si tenta di eseguire una query full-text quando il filegroup contenente l'indice full-text è offline, viene restituito un errore.  
  
    -   Le funzioni di stato, ad esempio FULLTEXTCATALOGPROPERTY, hanno esito positivo solo quando non devono accedere all'indice full-text. L'accesso ai metadati full-text online, ad esempio, ha esito positivo, mentre **uniquekeycount, itemcount** non riesce.  
  
     Dopo il ripristino e l'attivazione della modalità online per il filegroup dell'indice full-text, i dati dell'indice e delle tabelle risultano coerenti.  
  
 Non appena il filegroup della tabella di base e il filegroup dell'indice full-text sono online, qualsiasi popolamento full-text sospeso viene ripreso.  
  
##  <a name="FileBnRandCompression"></a> Backup e ripristino di file e compressione  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supporta la compressione dei dati con il file system NTFS per i filegroup e i database in sola lettura.  
  
 Il ripristino dei file in un filegroup di sola lettura è supportato per i file NTFS compressi. Il backup e il ripristino di questi filegroup vengono eseguiti sostanzialmente come per qualsiasi filegroup di sola lettura, con le eccezioni seguenti:  
  
-   Il ripristino di un file di lettura/scrittura, inclusi i file primari o di log di un database di lettura/scrittura, su un volume compresso ha esito negativo e viene visualizzato un messaggio di errore.  
  
-   Il ripristino di un database di sola lettura su un volume compresso è consentito.  
  
> [!NOTE]  
>  È consigliabile non memorizzare i file di log di database di lettura/scrittura in file system compressi.  
  
##  <a name="RelatedTasks"></a> Attività correlate  
  
-   [Preparazione di un database mirror per il mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md)  
  
-   [Backup e ripristino di indici e cataloghi full-text](../search/back-up-and-restore-full-text-catalogs-and-indexes.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Backup e ripristino di database SQL Server](back-up-and-restore-of-sql-server-databases.md)   
 [Backup e ripristino di database replicati](../replication/administration/back-up-and-restore-replicated-databases.md)   
 [Repliche secondarie attive: Backup in repliche secondarie &#40;gruppi di disponibilità AlwaysOn&#41;](../../database-engine/availability-groups/windows/active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md)  
  
  

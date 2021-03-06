---
title: Ripristinare un backup del log delle transazioni (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: backup-restore
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.restoretlog.options.f1
- sql12.swb.restoretlog.general.f1
helpviewer_keywords:
- restore log
- backing up transaction logs [SQL Server], restoring
- transaction log backups [SQL Server], restoring
- restoring transaction logs [SQL Server], restoring backups
- transaction log restores [SQL Server], SQL Server Management Studio
ms.assetid: 1de2b888-78a6-4fb2-a647-ba4bf097caf3
caps.latest.revision: 35
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 85c4008e1872a48126c67e47cc8d68ed0867828d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37237021"
---
# <a name="restore-a-transaction-log-backup-sql-server"></a>Ripristinare un backup del log delle transazioni (SQL Server)
  In questo argomento viene descritto il ripristino di un backup del log delle transazioni in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Prerequisiti](#Prerequisites)  
  
     [Security](#Security)  
  
-   **Per ripristinare un backup del log delle transazioni utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   [Attività correlate](#RelatedTasks)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Prerequisites"></a> Prerequisiti  
  
-   È necessario ripristinare i backup in base all'ordine in cui sono stati creati. Prima di ripristinare un determinato backup del log delle transazioni, è necessario ripristinare i backup precedenti riportati di seguito senza eseguire il rollback delle transazioni di cui non è stato eseguito il commit, ovvero utilizzando WITH NORECOVERY:  
  
    -   Il backup completo del database e l'eventuale ultimo backup differenziale che precedono il backup del log delle transazioni. Prima della creazione del backup completo o differenziale del database più recente, è necessario che il database utilizzi il modello di recupero con registrazione completa o il modello di recupero con registrazione minima delle operazioni bulk.  
  
    -   Tutti i backup del log delle transazioni eseguiti dopo il backup completo del database o il backup differenziale (in caso di ripristino di un backup) e prima del backup del log delle transazioni specifico. I backup del log devono essere applicati nella sequenza in cui sono stati creati, senza gap nella catena di log.  
  
         Per altre informazioni sui backup di log delle transazioni, vedere [Backup di log delle transazioni &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) e [Applicare backup di log delle transazioni &#40;SQL Server&#41;](apply-transaction-log-backups-sql-server.md).  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
 Le autorizzazioni per l'istruzione RESTORE vengono assegnate ai ruoli in cui le informazioni sull'appartenenza sono sempre disponibili per il server. Poiché è possibile controllare l'appartenenza ai ruoli predefiniti del database solo quando il database è accessibile e non è danneggiato, condizioni che non risultano sempre vere quando si esegue un'operazione RESTORE, i membri del ruolo predefinito del database **db_owner** non dispongono delle autorizzazioni per l'istruzione RESTORE.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
> [!WARNING]  
>  Il normale processo di ripristino prevede la selezione dei backup di log nella finestra di dialogo **Ripristina database** insieme ai backup differenziali e dei dati.  
  
#### <a name="to-restore-a-transaction-log-backup"></a>Per ripristinare un backup del log delle transazioni  
  
1.  Dopo aver stabilito la connessione all'istanza appropriata del [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Esplora oggetti fare clic sul nome del server per espandere l'albero del server.  
  
2.  Espandere **Database**e, a seconda del database, selezionare un database utente o espandere **Database di sistema** e selezionare un database di sistema.  
  
3.  Fare clic con il pulsante destro del mouse sul database, scegliere **Attività**, **Ripristina**, quindi fare clic su **Log delle transazioni**per aprire la finestra di dialogo **Ripristina log delle transazioni** .  
  
    > [!NOTE]  
    >  Se **Log delle transazioni** non è disponibile, potrebbe essere necessario ripristinare un backup completo o differenziale. Utilizzare la finestra di dialogo di backup **Database** .  
  
4.  Nella casella di riepilogo a discesa **Database** della pagina **Generale** selezionare il nome di un database. Tale elenco include solo database nello stato di ripristino in corso.  
  
5.  Per specificare l'origine e il percorso dei set di backup da ripristinare, fare clic su una delle opzioni seguenti:  
  
    -   **Da backup precedenti del database**  
  
         Selezionare il database da ripristinare dall'elenco a discesa. Nell'elenco sono inclusi solo i database di cui è stato eseguito il backup in base alla cronologia dei backup di **msdb** .  
  
    -   **Da file o nastro**  
  
         Fare clic sul pulsante Sfoglia (**...**) per aprire la finestra di dialogo **Seleziona dispositivi di backup** . Nella casella **Tipi di supporti di backup** selezionare uno dei tipi di dispositivi elencati. Per selezionare uno o più dispositivi per la casella **Supporti di backup** , fare clic su **Aggiungi**.  
  
         Dopo avere aggiunto i dispositivi desiderati nella casella di riepilogo **Dispositivi di backup** , fare clic su **OK** per tornare alla pagina **Generale** .  
  
6.  Nella griglia **Selezionare i backup del log delle transazioni da ripristinare** selezionare i backup che si desidera ripristinare. Nella griglia sono elencati i backup del log delle transazioni disponibili per il database selezionato. Un backup di log è disponibile solo se il relativo valore **Primo LSN** è maggiore del valore **Ultimo LSN** del database. I backup di log vengono elencati in base all'ordine dei numeri di sequenza del file di log (LSN) in essi contenuti e devono essere ripristinati in base a tale ordine.  
  
     Nella tabella seguente vengono elencate le intestazioni delle colonne della griglia con una descrizione dei rispettivi valori.  
  
    |Intestazione|valore|  
    |------------|-----------|  
    |**Restore**|Le caselle di controllo selezionate indicano i set di backup da ripristinare.|  
    |**Nome**|Nome del set di backup.|  
    |**Componente**|Componente di cui viene eseguito il backup: **Database**, **File**, o \<blank> (nel caso di log delle transazioni).|  
    |**Database**|Nome del database su cui viene eseguita l'operazione di backup.|  
    |**Data inizio**|Data e ora di inizio dell'operazione di backup, visualizzate in base alle impostazioni internazionali del client.|  
    |**Data fine**|Data e ora di fine dell'operazione di backup, visualizzate in base alle impostazioni internazionali del client.|  
    |**Primo LSN**|Numero di sequenza del file di log della prima transazione nel set di backup. Vuoto per i backup dei file.|  
    |**Ultimo LSN**|Numero di sequenza del file di log dell'ultima transazione nel set di backup. Vuoto per i backup dei file.|  
    |**LSN checkpoint**|Numero di sequenza del file di log del checkpoint più recente al momento della creazione del backup.|  
    |**LSN completo**|Numero di sequenza del file di log dell'operazione più recente di backup completo del database.|  
    |**Server**|Nome dell'istanza del motore di database in cui è stata eseguita l'operazione di backup.|  
    |**Nome utente**|Nome dell'utente che ha eseguito l'operazione di backup.|  
    |**Dimensione**|Dimensioni in byte del set di backup.|  
    |**Posizione**|Posizione del set di backup nel volume.|  
    |**Scadenza**|Data e ora di scadenza del set di backup.|  
  
7.  Selezionare una delle opzioni seguenti:  
  
    -   **Temporizzazione**  
  
         Mantenere l'impostazione predefinita (**Più recente**) oppure selezionare una data e un'ora specifiche, facendo clic sul pulsante Sfoglia per visualizzare la finestra di dialogo **Ripristino temporizzato** .  
  
    -   **Transazione contrassegnata**  
  
         Consente di ripristinare il database fino a una transazione contrassegnata in precedenza. Se si seleziona questa opzione, verrà visualizzata la finestra di dialogo **Seleziona transazione contrassegnata** , che include una griglia in cui sono elencate le transazioni contrassegnate disponibili nei backup del log delle transazioni selezionati.  
  
         Per impostazione predefinita, il ripristino viene eseguito fino alla transazione contrassegnata esclusa. Per ripristinare anche la transazione contrassegnata, selezionare l'opzione **Includi transazione contrassegnata**.  
  
         Nella tabella seguente vengono elencate le intestazioni delle colonne della griglia con una descrizione dei rispettivi valori.  
  
        |Intestazione|valore|  
        |------------|-----------|  
        |\<vuoto>|Consente di visualizzare una casella di controllo per selezionare il contrassegno.|  
        |**Contrassegno transazione**|Nome della transazione contrassegnata specificato dall'utente durante l'esecuzione del commit della transazione.|  
        |**Data**|Data e ora assegnate alla transazione quando ne è stato eseguito il commit. Vengono visualizzate la data e l'ora della transazione registrate nella tabella **msdbgmarkhistory** , non nella data e ora del computer client.|  
        |**Descrizione**|Eventuale descrizione della transazione contrassegnata specificata dall'utente quando è stato eseguito il commit della transazione.|  
        |**LSN**|Numero di sequenza del file di log (LSN) della transazione contrassegnata.|  
        |**Database**|Nome del database in cui è stato eseguito il commit della transazione contrassegnata.|  
        |**Nome utente**|Nome dell'utente del database che ha eseguito il commit della transazione contrassegnata.|  
  
8.  Per visualizzare o selezionare le opzioni avanzate, fare clic su **Opzioni** nel riquadro **Selezione pagina** .  
  
9. Nella sezione **Opzioni di ripristino** le scelte disponibili sono:  
  
    -   **Mantieni le impostazioni di replica (WITH KEEP_REPLICATION)**  
  
         Consente di mantenere le impostazioni di replica durante il ripristino di un database pubblicato in un server diverso da quello in cui è stato creato il database.  
  
         Questa opzione è disponibile solo con il **lascia il database pronto per l'utilizzo eseguendo il rollback di transazioni non sottoposte a commit...**  opzione (descritta più avanti), che equivale al ripristino di un backup con il `RECOVERY` opzione.  
  
         Si seleziona questa opzione equivale all'uso di `KEEP_REPLICATION` opzione un [!INCLUDE[tsql](../../includes/tsql-md.md)] `RESTORE` istruzione.  
  
    -   **Chiedi conferma prima del ripristino di ogni backup**  
  
         Prima di ripristinare ogni set di backup successivo al primo, questa opzione visualizza la finestra di dialogo **Continua con il ripristino** , in cui viene richiesta conferma della continuazione della sequenza di ripristino. In questa finestra di dialogo vengono visualizzati il nome del set di supporti successivo, se disponibile, il nome del set di backup e la descrizione del set di backup.  
  
         Questa opzione risulta particolarmente utile quando è necessario cambiare nastri per diversi set di supporti. Ad esempio, è possibile utilizzarla quando nel server è disponibile un solo dispositivo nastro. Attendere di essere pronti per procedere prima di fare clic su **OK**.  
  
         Se si fa clic su **No** , il database verrà mantenuto nello stato di ripristino in corso. Se lo si desidera, è possibile continuare la sequenza di ripristino dopo il completamento dell'ultimo ripristino. Se il backup successivo è un backup di dati o differenziale, utilizzare nuovamente l'attività **Ripristina database** . Se il backup successivo è un backup del log, utilizzare l'attività **Ripristina log delle transazioni** .  
  
    -   **Limita accesso al database ripristinato (WITH RESTRICTED_USER)**  
  
         Consente di rendere disponibile il database ripristinato solo per i membri di **db_owner**, **dbcreator**o **sysadmin**.  
  
         Si seleziona questa opzione equivale all'uso di `RESTRICTED_USER` opzione un [!INCLUDE[tsql](../../includes/tsql-md.md)] `RESTORE` istruzione.  
  
10. Nel gruppo di opzioni **Stato di recupero** specificare lo stato desiderato per il database dopo l'operazione di ripristino.  
  
    -   **Lascia il database pronto per l'uso eseguendo il rollback delle transazioni di cui non è stato eseguito il commit. I log delle transazioni aggiuntivi non possono essere ripristinati. (RESTORE WITH RECOVERY)**  
  
         Esegue il recupero del database. Questa opzione equivale al `RECOVERY` opzione un [!INCLUDE[tsql](../../includes/tsql-md.md)] `RESTORE` istruzione.  
  
         Selezionare questa opzione solo se non sono disponibili file di log da ripristinare.  
  
    -   **Lascia il database non operativo e non eseguire il rollback delle transazioni di cui non è stato eseguito il commit. I log delle transazioni aggiuntivi possono essere ripristinati. (RESTORE WITH NORECOVERY)**  
  
         Il database viene lasciato nello stato `RESTORING`. Questa opzione equivale all'uso di `NORECOVERY` opzione un [!INCLUDE[tsql](../../includes/tsql-md.md)] `RESTORE` istruzione.  
  
         Quando si seleziona questa opzione, l'opzione **Mantieni le impostazioni di replica** non è disponibile.  
  
        > [!IMPORTANT]  
        >  Nel caso di un database mirror o secondario, selezionare sempre questa opzione.  
  
    -   **Lascia il database in modalità sola lettura. Annulla le transazioni di cui non è stato eseguito il commit e salva le azioni di rollback in un file standby in modo che gli effetti del recupero possano essere annullati. (RESTORE WITH STANDBY)**  
  
         Il database viene lasciato nello stato di standby. Questa opzione equivale all'uso di `STANDBY` opzione un [!INCLUDE[tsql](../../includes/tsql-md.md)] `RESTORE` istruzione.  
  
         Se si seleziona questa opzione è necessario specificare un file standby.  
  
11. Facoltativamente, specificare un nome per il file standby nella casella di testo **File standby** . Questa opzione è necessaria se il database viene lasciato in modalità sola lettura. È possibile cercare il file standby per selezionarlo oppure digitarne direttamente il percorso nella casella di testo.  
  
##  <a name="TsqlProcedure"></a> Uso di Transact-SQL  
  
> [!IMPORTANT]  
>  È consigliabile specificare sempre in modo esplicito WITH NORECOVERY oppure WITH RECOVERY in ogni istruzione RESTORE per evitare ambiguità. Questa precauzione è particolarmente importante durante la scrittura di script.  
  
#### <a name="to-restore-a-transaction-log-backup"></a>Per ripristinare un backup del log delle transazioni  
  
1.  Eseguire l'istruzione RESTORE LOG per applicare il backup del log delle transazioni specificando:  
  
    -   Nome del database a cui verrà applicato il log delle transazioni.  
  
    -   Il dispositivo di backup da cui verrà ripristinato il backup del log delle transazioni.  
  
    -   Clausola NORECOVERY.  
  
     La sintassi di base per questa istruzione è la seguente:  
  
     RESTORE LOG *nome_database* FROM <dispositivo_backup> WITH NORECOVERY.  
  
     Dove *nome_database* è il nome del database e <dispositivo_backup> è il nome del dispositivo che contiene il backup del log in fase di ripristino.  
  
2.  Ripetere il passaggio 1 per ogni backup del log delle transazioni che si desidera applicare.  
  
3.  Dopo aver ripristinato l'ultimo backup della sequenza di ripristino, per recuperare il database utilizzare una delle istruzioni seguenti:  
  
    -   Recuperare il database nell'ambito dell'ultima istruzione RESTORE LOG:  
  
        ```  
        RESTORE LOG <database_name> FROM <backup_device> WITH RECOVERY;  
        GO  
        ```  
  
    -   Posticipare il recupero del database utilizzando un'istruzione RESTORE DATABASE separata:  
  
        ```  
        RESTORE LOG <database_name> FROM <backup_device> WITH NORECOVERY;   
        RESTORE DATABASE <database_name> WITH RECOVERY;  
        GO  
        ```  
  
         Il posticipo del recupero del database consente di verificare di avere ripristinato tutti i backup del log necessari. Questo approccio è spesso consigliato quando si esegue un ripristino temporizzato.  
  
    > [!IMPORTANT]  
    >  Se si sta creando un database mirror, omettere il passaggio di recupero. Un database mirror deve rimanere nello stato RESTORING.  
  
###  <a name="TsqlExample"></a> Esempi (Transact-SQL)  
 Per impostazione predefinita, il database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] utilizza il modello di recupero con registrazione minima. Per gli esempi seguenti è necessario modificare questo database in modo da utilizzare il modello di recupero con registrazione completa, come illustrato di seguito:  
  
```tsql  
ALTER DATABASE AdventureWorks2012 SET RECOVERY FULL;  
```  
  
#### <a name="a-applying-a-single-transaction-log-backup"></a>A. Applicazione di un singolo backup del log delle transazioni  
 Nell'esempio seguente viene innanzitutto ripristinato il database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] da un backup completo del database che risiede in un dispositivo di backup denominato `AdventureWorks2012_1`. Viene quindi applicato il primo backup del log delle transazioni che risiede nel dispositivo di backup denominato `AdventureWorks2012_log`e infine viene recuperato il database.  
  
```tsql  
RESTORE DATABASE AdventureWorks2012  
   FROM AdventureWorks2012_1  
   WITH NORECOVERY;  
GO  
RESTORE LOG AdventureWorks2012  
   FROM AdventureWorks2012_log  
   WITH FILE = 1,  
   WITH NORECOVERY;  
GO  
RESTORE DATABASE AdventureWorks2012  
   WITH RECOVERY;  
GO  
```  
  
#### <a name="b-applying-multiple-transaction-log-backups"></a>B. Applicazione di più backup del log delle transazioni  
 Nell'esempio seguente viene innanzitutto ripristinato il database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] da un backup completo del database che risiede in un dispositivo di backup denominato `AdventureWorks2012_1`. Vengono quindi applicati in successione i primi tre backup del log delle transazioni che risiedono in uno dispositivo di backup denominato `AdventureWorks2012_log`e infine viene recuperato il database.  
  
```tsql  
RESTORE DATABASE AdventureWorks2012  
   FROM AdventureWorks2012_1  
   WITH NORECOVERY;  
GO  
RESTORE LOG AdventureWorks2012  
   FROM AdventureWorks2012_log  
   WITH FILE = 1,  
   NORECOVERY;  
GO  
RESTORE LOG AdventureWorks2012  
   FROM AdventureWorks2012_log  
   WITH FILE = 2,  
   WITH NORECOVERY;  
GO  
RESTORE LOG AdventureWorks2012  
   FROM AdventureWorks2012_log  
   WITH FILE = 3,  
   WITH NORECOVERY;  
GO  
RESTORE DATABASE AdventureWorks2012  
   WITH RECOVERY;  
GO  
```  
  
##  <a name="RelatedTasks"></a> Attività correlate  
  
-   [Eseguire il backup di un log delle transazioni &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md)  
  
-   [Ripristinare un Backup del Database &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md)  
  
-   [Ripristinare un database al punto di errore nel modello di recupero con registrazione completa &#40;Transact-SQL&#41;](restore-database-to-point-of-failure-full-recovery.md)  
  
-   [Ripristinare un database di SQL Server fino a un punto specifico &#40;modello di recupero con registrazione completa&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)  
  
-   [Ripristino di un database fino a una transazione contrassegnata &#40;SQL Server Management Studio&#41;](restore-a-database-to-a-marked-transaction-sql-server-management-studio.md)  
  
## <a name="see-also"></a>Vedere anche  
 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)   
 [Applicare backup di log delle transazioni &#40;SQL Server&#41;](apply-transaction-log-backups-sql-server.md)  
  
  

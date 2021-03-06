---
title: Creare un nuovo cluster di failover di SQL Server (programma di installazione) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- adding nodes
- failover clustering [SQL Server], creating clusters
- nodes [Faillover Clustering], removing
- nodes [Faillover Clustering], adding
- clusters [SQL Server], creating
- removing nodes
ms.assetid: 30e06a7d-75e9-44e2-bca3-b3b0c4a33f61
caps.latest.revision: 75
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 672699fe7c941098b0b689a49a30e12c6cc71ee8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37155802"
---
# <a name="create-a-new-sql-server-failover-cluster-setup"></a>Creare un nuovo cluster di failover di SQL Server (programma di installazione)
  Per installare o aggiornare un cluster di failover di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , è necessario eseguire il programma di installazione in ogni nodo del cluster di failover. Per aggiungere un nodo a un cluster di failover di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] esistente, è necessario eseguire il programma di installazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nel nodo che deve essere aggiunto all'istanza del cluster di failover di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Non eseguire il programma di installazione nel nodo attivo per gestire gli altri nodi.  
  
 Il cluster di failover di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] viene configurato nei modi riportati di seguito a seconda del tipo di esecuzione del clustering dei nodi:  
  
-   Nodi nella stessa subnet o nello stesso set di subnet: la dipendenza delle risorse indirizzo IP viene impostata su AND per questi tipi di configurazioni.  
  
-   Nodi in subnet diverse: la dipendenza delle risorse indirizzo IP viene impostata su OR e questa configurazione è definita configurazione di cluster di failover su più subnet di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Per altre informazioni, vedere [Clustering su più subnet di SQL Server &#40;SQL Server&#41;](../windows/sql-server-multi-subnet-clustering-sql-server.md).  
  
 Le opzioni riportate di seguito sono disponibili per l'installazione del cluster di failover di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] :  
  
 **Opzione 1: installazione integrata con la funzionalità per l'aggiunta del nodo**  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] L'installazione integrata del cluster di failover prevede i passaggi seguenti:  
  
-   Creazione e configurazione di un'istanza del cluster di failover di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] a nodo singolo. Una volta configurato il nodo, è disponibile un'istanza del cluster di failover in grado di funzionare correttamente, ma senza disponibilità elevata poiché nel cluster di failover è presente solo un nodo.  
  
-   In ogni nodo da aggiungere al cluster di failover di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , eseguire il programma di installazione per aggiungere il nodo specifico con la funzionalità relativa.  
  
    -   Se il nodo da aggiungere dispone di subnet aggiuntive o diverse, è possibile specificare indirizzi IP aggiuntivi. Se il nodo da aggiungere è su una subnet diversa, è necessario anche confermare che la dipendenza delle risorse di indirizzo IP è stata impostata su OR. Per altre informazioni sui diversi scenari possibili durante le operazioni di aggiunta del nodo, vedere [Aggiungere o rimuovere nodi in un cluster di failover di SQL Server &#40;programma di installazione&#41;](add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md).  
  
 **Opzione 2: installazione avanzata o aziendale**  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] L'installazione avanzata o aziendale del cluster di failover prevede i passaggi seguenti:  
  
-   In ogni nodo che può essere proprietario del nuovo cluster di failover di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] eseguire i passaggi di installazione per la preparazione del cluster di failover elencati nella sezione relativa alla [preparazione](#prepare). Dopo aver eseguito la preparazione del cluster di failover in un nodo, viene creato il file Configuration.ini in cui sono elencate tutte le impostazioni specificate. Anziché effettuare i passaggi seguenti, nei nodi aggiuntivi da preparare è possibile fornire il file Configuration.ini generato automaticamente dal primo nodo come input alla riga di comando del programma di installazione. Per altre informazioni, vedere [installare SQL Server 2014 tramite un File di configurazione](../../../database-engine/install-windows/install-sql-server-using-a-configuration-file.md). Questo passaggio consente di preparare i nodi per l'esecuzione del clustering, tuttavia al termine del passaggio non è ancora presente alcuna istanza operativa di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
-   Dopo aver preparato i nodi per il clustering, eseguire il programma di installazione in uno dei nodi preparati. Durante questo passaggio l'istanza del cluster di failover viene configurata e completata. Al termine del passaggio sarà disponibile un'istanza del cluster di failover di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] operativa e tutti i nodi preparati in precedenza per tale istanza saranno i possibili proprietari del cluster di failover di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] appena creato.  
  
     Se si sta eseguendo il clustering di nodi in più subnet, tramite il programma di installazione sarà possibile rilevare l'unione di tutte le subnet in tutti i nodi che dispongono dell'istanza del cluster di failover preparata di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Sarà inoltre possibile specificare più indirizzi IP per le subnet. Ogni nodo preparato deve essere il possibile proprietario di almeno un indirizzo IP.  
  
     Se ogni indirizzo IP specificato per le subnet è supportato in tutti i nodi preparati, la dipendenza viene impostata su AND.  
  
     Se ogni indirizzo IP specificato per le subnet non è supportato in tutti i nodi preparati, la dipendenza viene impostata su OR. Per altre informazioni, vedere [Clustering su più subnet di SQL Server &#40;SQL Server&#41;](../windows/sql-server-multi-subnet-clustering-sql-server.md).  
  
    > [!NOTE]  
    >  Per eseguire il completamento del cluster di failover, è necessario che sia presente il cluster di failover Windows sottostante. In caso contrario, durante il programma di installazione si verifica un errore e il programma viene terminato.  
  
 Per altre informazioni su come aggiungere nodi a un'istanza del cluster di failover esistente o su come rimuoverli, vedere [Aggiungere o rimuovere nodi in un cluster di failover di SQL Server &#40;programma di installazione&#41;](add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md).  
  
 Per altre informazioni sull'installazione remota, vedere [Aggiornamenti di versione ed edizione supportati](../../../database-engine/install-windows/supported-version-and-edition-upgrades.md).  
  
 Per altre informazioni sull'installazione di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] in un cluster di failover Windows, vedere [Come eseguire il clustering di SQL Server Analysis Services](http://go.microsoft.com/fwlink/p/?LinkId=396548).  
  
## <a name="prerequisites"></a>Prerequisiti  
 Prima di avviare l'installazione, vedere gli argomenti seguenti della documentazione online di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] :  
  
-   [Pianificazione di un'installazione di SQL Server](../../install/planning-a-sql-server-installation.md)  
  
-   [Operazioni preliminari all'installazione del clustering di failover](before-installing-failover-clustering.md)  
  
-   [Considerazioni sulla sicurezza per un'installazione di SQL Server](../../install/security-considerations-for-a-sql-server-installation.md)  
  
-   [Clustering su più subnet di SQL Server &#40;SQL Server&#41;](../windows/sql-server-multi-subnet-clustering-sql-server.md)  
  
> [!NOTE]  
>  Prendere nota del percorso dell'unità condivisa in Amministrazione cluster prima di eseguire il programma di installazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Questa informazione è necessaria per creare un nuovo cluster di failover.  
  
### <a name="to-install-a-new-includessnoversionincludesssnoversion-mdmd-failover-cluster-using-integrated-install-with-add-node"></a>Per installare un nuovo cluster di failover di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tramite l'installazione integrata con la funzionalità per l'aggiunta del nodo.  
  
1.  Inserire il supporto di installazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , quindi nella cartella radice fare doppio clic sul file Setup.exe. Per eseguire l'installazione da una condivisione di rete, spostarsi nella cartella radice nella condivisione, quindi fare doppio clic sul file Setup.exe. Per altre informazioni sulla procedura di installazione dei prerequisiti, vedere [Operazioni preliminari all'installazione del clustering di failover](before-installing-failover-clustering.md).  
  
2.  L'Installazione guidata consente di avviare il Centro installazione [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Per creare una nuova installazione cluster di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], fare clic su **Installazione nuovo cluster di failover di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]** nella pagina di installazione.  
  
3.  Controllo configurazione sistema consente di eseguire un'operazione di individuazione nel computer. Per continuare, [!INCLUDE[clickOK](../../../includes/clickok-md.md)]. È possibile fare clic su **Mostra dettagli**per visualizzare i dettagli sullo schermo oppure su **Visualizza report dettagliato**per visualizzarli come report HTML.  
  
4.  Scegliere **Avanti**per continuare.  
  
5.  Nella pagina File di supporto per l'installazione fare clic su **Installa** per installare i file specifici.  
  
6.  Controllo configurazione sistema verifica lo stato del sistema del computer prima che l'installazione continui. Al termine della verifica, fare clic su **Avanti** per continuare. È possibile fare clic su **Mostra dettagli**per visualizzare i dettagli sullo schermo oppure su **Visualizza report dettagliato**per visualizzarlo come report HTML.  
  
7.  Nella pagina codice Product Key indicare se si installa un'edizione gratuita di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]o se si dispone di una chiave PID per una versione di produzione del prodotto. Per altre informazioni, vedere [edizioni e componenti di SQL Server 2014](../../editions-and-components-of-sql-server-2016.md).  
  
8.  Nella pagina Condizioni di licenza leggere il contratto di licenza, quindi selezionare la casella di controllo per accettarne le condizioni. Per migliorare [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], è inoltre possibile abilitare l'opzione relativa all'utilizzo delle funzionalità e inviare report a [!INCLUDE[msCoName](../../../includes/msconame-md.md)]. Per continuare, fare clic su **Avanti** . Per terminare l'installazione, fare clic su **Annulla**.  
  
9. Nella pagina Selezione funzionalità selezionare i componenti per l'installazione. Dopo aver selezionato il nome della funzionalità desiderata, nel riquadro a destra verrà visualizzata una descrizione per ogni gruppo di componenti. È possibile selezionare qualsiasi combinazione di caselle di controllo, ma solo il [!INCLUDE[ssDE](../../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] in modalità tabulare e [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] in modalità multidimensionale supportano il clustering di failover. Gli altri componenti selezionati verranno eseguiti in modo autonomo senza funzionalità di failover nel nodo corrente in cui si esegue il programma di installazione. Per altre informazioni sulle modalità di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] , vedere [Determinare la modalità server di un'istanza di Analysis Services](../../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md).  
  
     I prerequisiti per le funzionalità selezionate vengono visualizzati nel riquadro di destra. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verranno installati i prerequisiti che non sono stati ancora installati durante la procedura di installazione descritta più avanti in questo argomento.  
  
     È possibile specificare una directory personalizzata per i componenti condivisi utilizzando il campo presente nella parte inferiore della pagina. Per modificare il percorso di installazione per i componenti condivisi, aggiornare il percorso nel campo disponibile nella parte inferiore della finestra di dialogo oppure fare clic sul pulsante con i puntini di sospensione per spostarsi in una directory di installazione. Il percorso di installazione predefinito è C:\Programmi\\[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] \\.  
  
     [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] supporta anche l'installazione dei database di sistema (Master, Model, MSDB e TempDB) e dei database utente del [!INCLUDE[ssDE](../../../includes/ssde-md.md)] in una condivisione file SMB (Server Message Block). Per altre informazioni sull'installazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] usando una condivisione file SMB come opzione di archiviazione, vedere [Installazione di SQL Server con l'opzione di archiviazione su condivisione file SMB](../../../database-engine/install-windows/install-sql-server-with-smb-fileshare-as-a-storage-option.md).  
  
     Il percorso specificato per i componenti condivisi deve essere un percorso assoluto. La cartella non deve essere compressa o crittografata. Le unità di cui è stato eseguito il mapping non sono supportate. Se [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] viene installato in un sistema operativo a 64 bit, saranno visualizzate le opzioni seguenti:  
  
    1.  Directory funzionalità condivise  
  
    2.  Directory funzionalità condivise (x86)  
  
     Il percorso specificato per ogni opzione descritta in precedenza deve essere diverso.  
  
    > [!NOTE]  
    >  Quando si seleziona la funzionalità Servizi [!INCLUDE[ssDE](../../../includes/ssde-md.md)] , vengono selezionate automaticamente sia la replica sia la ricerca full-text. Data Quality Services (DQS) è selezionato quando si seleziona la funzionalità servizi [!INCLUDE[ssDE](../../../includes/ssde-md.md)] . Se si deseleziona una di queste funzionalità secondarie, viene deselezionata anche la funzionalità Servizi [!INCLUDE[ssDE](../../../includes/ssde-md.md)] .  
  
10. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Il programma di installazione esegue uno o più set di regole basati sulle funzionalità selezionate per convalidare la configurazione.  
  
11. Nella pagina Configurazione dell'istanza specificare se installare un'istanza predefinita o denominata. Per ulteriori informazioni, vedere [Instance Configuration](../../install/instance-configuration.md).  
  
     **Nome di rete di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]**: specificare un nome di rete per il nuovo cluster di failover di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Si tratta del nome utilizzato per identificare il cluster di failover nella rete.  
  
    > [!NOTE]  
    >  Nelle precedenti versioni dei cluster di failover di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] questo nome era noto come nome virtuale di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
     **ID istanza** : per impostazione predefinita, come ID istanza viene utilizzato il nome dell'istanza. Tale nome viene utilizzato per identificare le directory di installazione e le chiavi del Registro di sistema per l'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Si tratta del caso delle istanze predefinite e delle istanze denominate. Per un'istanza predefinita, il nome di istanza e l'ID istanza sono MSSQLSERVER. Per usare un ID istanza non predefinito, selezionare la casella **ID istanza** e specificare un valore.  
  
    > [!NOTE]  
    >  Le normali istanze autonome di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], sia che si tratti di istanze predefinite o denominate, non usano un valore che non sia predefinito per la casella **ID istanza** .  
  
     **Directory radice istanza** : per impostazione predefinita, la directory radice dell'istanza è C:\Programmi\\[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]\\. Per specificare una directory radice non predefinita, utilizzare il campo disponibile oppure fare clic sul pulsante con i puntini di sospensione per individuare una cartella di installazione.  
  
     **Istanze e funzionalità di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] rilevate nel computer**: nella griglia vengono visualizzate le istanze di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] presenti nel computer in cui viene eseguito il programma di installazione. Se nel computer è già installata un'istanza predefinita, è necessario installare un'istanza denominata di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Per continuare, fare clic su **Avanti** .  
  
12. Utilizzare la pagina Gruppo risorse cluster per specificare il nome del gruppo di risorse cluster in cui verranno memorizzate le risorse del server virtuale di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Per specificare il nome del gruppo di risorse cluster di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , sono disponibili due opzioni:  
  
    -   Utilizzare la casella di riepilogo a discesa per specificare un gruppo esistente.  
  
    -   Digitare il nome di un nuovo gruppo da creare. Il nome "Archiviazione disponibile" non è un nome di gruppo valido.  
  
13. Nella pagina Selezione dischi cluster selezionare la risorsa disco del cluster condivisa del cluster di failover di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Il disco di cluster è l'unità in cui verranno memorizzati i dati di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . È possibile specificare più di un disco. Nella griglia Dischi condivisi disponibili vengono visualizzati un elenco dei dischi disponibili, l'indicazione dell'eventuale qualifica di ogni disco come disco condiviso e una descrizione di ogni risorsa disco. Per continuare, fare clic su **Avanti** .  
  
    > [!NOTE]  
    >  La prima unità viene utilizzata come unità predefinita per tutti i database, tuttavia è possibile modificarla nelle pagine di configurazione del [!INCLUDE[ssDE](../../../includes/ssde-md.md)] o di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .  
    >   
    >  Nella pagina Selezione dischi cluster è possibile scegliere di non selezionare alcun disco condiviso se si desidera utilizzare una condivisione file SMB come cartella di dati.  
  
14. Nella pagina Configurazione rete cluster specificare le risorse di rete per l'istanza del cluster di failover:  
  
    -   **Impostazioni di rete** : specificare il tipo e l'indirizzo IP per l'istanza del cluster di failover.  
  
     Per continuare, fare clic su **Avanti** .  
  
15. Utilizzare questa pagina per specificare i criteri di sicurezza cluster.  
  
    -   [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)] e versioni successive: l'utilizzo di SID del servizio (ID di sicurezza del server) rappresenta l'impostazione consigliata e predefinita. Non è disponibile alcuna opzione per modificare questo elemento in gruppi di sicurezza. Per informazioni sulla funzionalità dei SID del servizio in [!INCLUDE[nextref_longhorn](../../../includes/nextref-longhorn-md.md)], vedere [Configurare account di servizio e autorizzazioni di Windows](../../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md). Questa funzionalità è stata testata nell'installazione autonoma e cluster in [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)].  
  
    -   In [!INCLUDE[winxpsvr](../../../includes/winxpsvr-md.md)]specificare i gruppi di dominio per i servizi [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Tutte le autorizzazioni per le risorse sono controllate da gruppi a livello di dominio che includono gli account del servizio [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] come membri del gruppo.  
  
     Per continuare, fare clic su **Avanti** .  
  
16. Il flusso di lavoro relativo alla parte rimanente di questo argomento dipende dalle funzionalità specificate per l'installazione. Le pagine visualizzate dipendono dalle selezioni effettuate ([!INCLUDE[ssDE](../../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]e [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]).  
  
17. Nella pagina Configurazione server - Account di servizio specificare gli account di accesso per i servizi [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . I servizi effettivamente configurati in questa pagina dipendono dalle funzionalità selezionate per l'installazione.  
  
     È possibile assegnare lo stesso account di accesso a tutti i servizi di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] oppure configurare singolarmente l'account di ogni servizio. Il tipo di avvio viene impostato su manuale per tutti i servizi compatibili con i cluster, ad esempio la ricerca full-text [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent, e non può essere modificato durante l'installazione. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] consiglia di configurare gli account del servizio singolarmente per assegnare i privilegi minimi a ogni servizio, in modo che ai servizi [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vengano concesse le autorizzazioni minime necessarie per completare le attività. Per altre informazioni, vedere [Configurazione Server - Account di servizio](../../install/server-configuration-service-accounts.md) e [Configurare account di servizio e autorizzazioni di Windows](../../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
     Per specificare lo stesso account di accesso per tutti gli account del servizio in questa istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], immettere le credenziali nei campi visualizzati nella parte inferiore della pagina.  
  
     **Nota sulla protezione** [!INCLUDE[ssNoteStrongPass](../../../includes/ssnotestrongpass-md.md)]  
  
     Dopo aver specificato le informazioni di accesso per i servizi [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , fare clic su **Avanti**.  
  
18. Usare la scheda **Configurazione server - Regole di confronto** per specificare regole di confronto non predefinite per [!INCLUDE[ssDE](../../../includes/ssde-md.md)] e [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Per altre informazioni, vedere [Configurazione del server - Regole di confronto](../../install/server-configuration-collation.md).  
  
19. Utilizzare la pagina Configurazione [!INCLUDE[ssDE](../../../includes/ssde-md.md)] - Provisioning account per specificare gli elementi seguenti:  
  
    -   Modalità di sicurezza: selezionare Autenticazione di Windows o l'autenticazione Modalità mista per l'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Se si seleziona l'autenticazione Modalità mista, è necessario specificare una password complessa per l'account amministratore di sistema [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] predefinito.  
  
         Quando viene stabilita la connessione tra un dispositivo e [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], il meccanismo di sicurezza è lo stesso sia in modalità mista che di autenticazione di Windows. Per altre informazioni, vedere [configurazione del motore di Database - Provisioning Account](../../install/database-engine-configuration-account-provisioning.md).  
  
    -   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Amministratori: è necessario specificare almeno un amministratore di sistema per l'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Per aggiungere l'account usato per eseguire il programma di installazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , fare clic su **Aggiungi utente corrente**. Per aggiungere o rimuovere account dall'elenco degli amministratori di sistema, fare clic su **Aggiungi** o **Rimuovi**, quindi modificare l'elenco di utenti, gruppi o computer con privilegi di amministratore per l'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Per altre informazioni, vedere [configurazione del motore di Database - Provisioning Account](../../install/database-engine-configuration-account-provisioning.md).  
  
     Dopo aver modificato l'elenco, [!INCLUDE[clickOK](../../../includes/clickok-md.md)]. Verificare l'elenco di amministratori nella finestra di dialogo di configurazione. Quando l'elenco è completo, fare clic su **Avanti**.  
  
20. Utilizzare la pagina Configurazione di [!INCLUDE[ssDE](../../../includes/ssde-md.md)] - Directory dati per specificare directory di installazione non predefinite. Per eseguire l'installazione in directory predefinite, fare clic su **Avanti**.  
  
    > [!IMPORTANT]  
    >  Se si specificano directory di installazione non predefinite, verificare che le cartelle di installazione siano univoche per questa istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Nessuna delle directory presenti in questa finestra di dialogo deve essere condivisa con le directory di altre istanze di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. È necessario che le directory dei dati si trovino nel disco di cluster condiviso per il cluster di failover.  
  
    > [!NOTE]  
    >  Per specificare un file server SMB (Server Message Block) come directory di dati, impostare la **directory radice dati predefinita** sulla condivisione file nel formato \\\NomeServer\NomeCondivisione\\...  
  
     Per altre informazioni, vedere [Configurazione del motore di database - Directory dati](../../install/database-engine-configuration-data-directories.md).  
  
21. Utilizzare la pagina Configurazione [!INCLUDE[ssDE](../../../includes/ssde-md.md)] - FILESTREAM per abilitare la funzione FILESTREAM per l'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Per altre informazioni su FILESTREAM, vedere [Configurazione del motore di database - Filestream](../../install/database-engine-configuration-filestream.md). Per continuare, fare clic su **Avanti** .  
  
22. Utilizzare la pagina Configurazione [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] - Provisioning account per specificare gli utenti o gli account che disporranno di autorizzazioni di amministratore per [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. È necessario specificare almeno un amministratore di sistema per [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Per aggiungere l'account usato per eseguire il programma di installazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , fare clic su **Aggiungi utente corrente**. Per aggiungere o rimuovere account dall'elenco degli amministratori di sistema, fare clic su **Aggiungi** o **Rimuovi**, quindi modificare l'elenco di utenti, gruppi o computer che disporranno di privilegi di amministratore per [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Per altre informazioni, vedere [configurazione di Analysis Services - Provisioning Account](../../install/analysis-services-configuration-account-provisioning.md).  
  
     Dopo aver modificato l'elenco, [!INCLUDE[clickOK](../../../includes/clickok-md.md)]. Verificare l'elenco di amministratori nella finestra di dialogo di configurazione. Quando l'elenco è completo, fare clic su **Avanti**.  
  
23. Utilizzare la pagina Configurazione di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] - Directory dati per specificare directory di installazione non predefinite. Per eseguire l'installazione in directory predefinite, fare clic su **Avanti**.  
  
    > [!IMPORTANT]  
    >  Se si specificano directory di installazione non predefinite, verificare che le cartelle di installazione siano univoche per questa istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Nessuna delle directory presenti in questa finestra di dialogo deve essere condivisa con le directory di altre istanze di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. È necessario che le directory dei dati si trovino nel disco di cluster condiviso per il cluster di failover.  
  
     Per altre informazioni, vedere [Configurazione di Analysis Services - Directory dati](../../install/analysis-services-configuration-data-directories.md).  
  
24. Utilizzare la pagina Configurazione di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] per specificare il tipo di installazione di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] da creare. Per l'installazione di cluster di failover, l'opzione è impostata su Installazione di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] non configurata. È necessario configurare i servizi [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] dopo aver completato l'installazione.  
  
     Per altre informazioni sulle modalità di configurazione di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], vedere [Opzioni di configurazione di Reporting Services &#40;SSRS&#41;](../../install/reporting-services-configuration-options-ssrs.md).  
  
25. Controllo configurazione sistema esegue uno o più set di regole per convalidare la configurazione con le funzionalità di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] specificate.  
  
26. Nella pagina Inizio installazione è presente una visualizzazione albero delle opzioni specificate durante l'installazione. Per continuare, fare clic su **Installa**. Il programma di installazione consentirà innanzitutto di installare i prerequisiti obbligatori per le funzionalità selezionate e, successivamente, le funzionalità stesse.  
  
27. Durante l'installazione, nella pagina Stato dell'installazione è possibile monitorare lo stato di avanzamento del processo.  
  
28. Al termine dell'installazione, nella pagina **Operazione completata** viene visualizzato un collegamento al file di log di riepilogo del processo di installazione e ad altre note importanti. Per completare il processo di installazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , fare clic su **Chiudi**.  
  
29. Se viene richiesto, riavviare il computer. È importante leggere il messaggio visualizzato nell'Installazione guidata al termine dell'installazione. Per altre informazioni sui file di log del programma di installazione, vedere [Visualizzare e leggere i file di log del programma di installazione di SQL Server](../../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md).  
  
30. Per aggiungere nodi al failover a nodo singolo creato, eseguire il programma di installazione in ogni nodo aggiuntivo e seguire i passaggi descritti per l'operazione AddNode. Per altre informazioni, vedere [Aggiungere o rimuovere nodi in un cluster di failover di SQL Server &#40;programma di installazione&#41;](add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md).  
  
    > [!NOTE]  
    >  Se si aggiungono più nodi, è possibile utilizzare il file di configurazione per distribuire le installazioni. Per altre informazioni, vedere [installare SQL Server 2014 tramite un File di configurazione](../../../database-engine/install-windows/install-sql-server-using-a-configuration-file.md).  
    >   
    >  L'edizione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in corso di installazione deve corrispondere in tutti i nodi di un cluster di failover di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Quando si aggiunge un nuovo nodo a un cluster di failover di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] esistente, assicurarsi di specificare che l'edizione corrisponda a quella del cluster di failover esistente.  
  
##  <a name="prepare"></a> Preparazione  
  
#### <a name="advancedenterprise-failover-cluster-install-step-1-prepare"></a>Passaggio 1 dell'installazione avanzata o aziendale del cluster di failover: preparazione  
  
1.  Inserire il supporto di installazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , quindi nella cartella radice fare doppio clic sul file Setup.exe. Per eseguire l'installazione da una condivisione di rete, spostarsi nella cartella radice nella condivisione, quindi fare doppio clic sul file Setup.exe. Per altre informazioni sulla procedura di installazione dei prerequisiti, vedere [Operazioni preliminari all'installazione del clustering di failover](before-installing-failover-clustering.md). È possibile che venga richiesto di installare i prerequisiti se non sono già stati installati in precedenza.  
  
2.  È necessario Windows Installer 4.5 che può essere installato mediante l'Installazione guidata. Se viene richiesto, riavviare il computer, quindi eseguire nuovamente il programma di installazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
3.  Una volta installati i prerequisiti, l'Installazione guidata avvia Centro installazione [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Per preparare il nodo per il clustering, spostarsi nella pagina **Avanzate** , quindi fare clic su **Preparazione cluster avanzata**.  
  
4.  Controllo configurazione sistema consente di eseguire un'operazione di individuazione nel computer. Per continuare, [!INCLUDE[clickOK](../../../includes/clickok-md.md)]. È possibile fare clic su **Mostra dettagli**per visualizzare i dettagli sullo schermo oppure su **Visualizza report dettagliato**per visualizzarlo come report HTML.  
  
5.  Nella pagina File di supporto per l'installazione fare clic su **Installa** per installare i file specifici.  
  
6.  Controllo configurazione sistema verifica lo stato del sistema del computer prima che l'installazione continui. Al termine della verifica, fare clic su **Avanti** per continuare. È possibile fare clic su **Mostra dettagli**per visualizzare i dettagli sullo schermo oppure su **Visualizza report dettagliato**per visualizzarlo come report HTML.  
  
7.  Nella pagina Selezione lingua è possibile specificare la lingua per l'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] se si sta eseguendo l'installazione in un sistema operativo localizzato e se nei supporti di installazione sono inclusi i Language Pack sia per l'inglese sia per la lingua corrispondente al sistema operativo. Per altre informazioni sul supporto di lingue diverse e sulle considerazioni relative all'installazione, vedere le [versioni della lingua locale in SQL Server](../../install/local-language-versions-in-sql-server.md).  
  
     Scegliere **Avanti**per continuare.  
  
8.  Nella pagina Codice Product Key fare clic per indicare se si installa un'edizione gratuita di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]o se si dispone di una chiave PID per una versione di produzione del prodotto. Per altre informazioni, vedere [edizioni e componenti di SQL Server 2014](../../editions-and-components-of-sql-server-2016.md).  
  
    > [!NOTE]  
    >  È necessario specificare lo stesso codice Product Key in tutti i nodi in preparazione per lo stesso cluster di failover.  
  
9. Nella pagina Condizioni di licenza leggere il contratto di licenza, quindi selezionare la casella di controllo per accettarne le condizioni. Per migliorare [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], è inoltre possibile abilitare l'opzione relativa all'utilizzo delle funzionalità e inviare report a [!INCLUDE[msCoName](../../../includes/msconame-md.md)]. Per continuare, fare clic su **Avanti** . Per terminare l'installazione, fare clic su **Annulla**.  
  
10. Nella pagina Selezione funzionalità selezionare i componenti per l'installazione. Dopo aver selezionato il nome della funzionalità desiderata, nel riquadro a destra verrà visualizzata una descrizione per ogni gruppo di componenti. È possibile selezionare qualsiasi combinazione di caselle di controllo, ma solo il [!INCLUDE[ssDE](../../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] in modalità tabulare e [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] in modalità multidimensionale supportano il clustering di failover. Gli altri componenti selezionati verranno eseguiti in modo autonomo senza funzionalità di failover nel nodo corrente in cui si esegue il programma di installazione. Per altre informazioni sulle modalità di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] , vedere [Determinare la modalità server di un'istanza di Analysis Services](../../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md).  
  
     I prerequisiti per le funzionalità selezionate vengono visualizzati nel riquadro di destra. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verranno installati i prerequisiti che non sono stati ancora installati durante la procedura di installazione descritta più avanti in questo argomento.  
  
     È possibile specificare una directory personalizzata per i componenti condivisi utilizzando il campo presente nella parte inferiore della pagina. Per modificare il percorso di installazione per i componenti condivisi, aggiornare il percorso nel campo disponibile nella parte inferiore della finestra di dialogo oppure fare clic sul pulsante con i puntini di sospensione per spostarsi in una directory di installazione. Il percorso di installazione predefinito è C:\Programmi\\[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]\\.  
  
    > [!NOTE]  
    >  Quando si seleziona la funzionalità Servizi [!INCLUDE[ssDE](../../../includes/ssde-md.md)] , vengono selezionate automaticamente sia la replica sia la ricerca full-text. Se si deseleziona una di queste funzionalità secondarie, viene deselezionata anche la funzionalità Servizi [!INCLUDE[ssDE](../../../includes/ssde-md.md)] .  
  
11. Nella pagina Configurazione dell'istanza specificare se installare un'istanza predefinita o denominata. Per ulteriori informazioni, vedere [Instance Configuration](../../install/instance-configuration.md).  
  
     **ID istanza** : per impostazione predefinita, come ID istanza viene utilizzato il nome dell'istanza. Tale nome viene utilizzato per identificare le directory di installazione e le chiavi del Registro di sistema per l'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Si tratta del caso delle istanze predefinite e delle istanze denominate. Per un'istanza predefinita, il nome di istanza e l'ID istanza sono MSSQLSERVER. Per utilizzare un ID istanza non predefinito, selezionare la casella di testo **ID istanza** e specificare un valore.  
  
    > [!NOTE]  
    >  Le normali istanze autonome di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], sia che si tratti di istanze predefinite o denominate, utilizzano un valore predefinito per la casella di testo **ID istanza** .  
  
    > [!IMPORTANT]  
    >  Utilizzare lo stesso ID istanza per tutti i nodi preparati per il cluster di failover.  
  
     **Directory radice istanza** : per impostazione predefinita, la directory radice dell'istanza è C:\Programmi\\[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]\\. Per specificare una directory radice non predefinita, utilizzare il campo disponibile oppure fare clic sul pulsante con i puntini di sospensione per individuare una cartella di installazione.  
  
     **Istanze installate** : nella griglia vengono visualizzate le istanze di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] presenti nel computer in cui viene eseguito il programma di installazione. Se nel computer è già installata un'istanza predefinita, è necessario installare un'istanza denominata di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Per continuare, fare clic su **Avanti** .  
  
12. Nella pagina Requisiti di spazio su disco viene calcolato lo spazio su disco necessario per le funzionalità specificate e vengono confrontati i requisiti con lo spazio su disco disponibile nel computer in cui è in esecuzione il programma di installazione.  
  
13. Utilizzare questa pagina per specificare i criteri di sicurezza cluster.  
  
    -   [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)] e versioni successive: l'utilizzo di SID del servizio (ID di sicurezza del server) rappresenta l'impostazione consigliata e predefinita. Non è disponibile alcuna opzione per modificare questo elemento in gruppi di sicurezza. Per informazioni sulla funzionalità dei SID del servizio in [!INCLUDE[nextref_longhorn](../../../includes/nextref-longhorn-md.md)], vedere [Configurare account di servizio e autorizzazioni di Windows](../../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md). Questa funzionalità è stata testata nell'installazione autonoma e cluster in [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)].  
  
    -   In [!INCLUDE[winxpsvr](../../../includes/winxpsvr-md.md)]specificare i gruppi di dominio per i servizi [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Tutte le autorizzazioni per le risorse sono controllate da gruppi a livello di dominio che includono gli account del servizio [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] come membri del gruppo.  
  
     Per continuare, fare clic su **Avanti** .  
  
14. Il flusso di lavoro relativo alla parte rimanente di questo argomento dipende dalle funzionalità specificate per l'installazione. Le pagine visualizzate dipendono dalle selezioni effettuate.  
  
15. Nella pagina Configurazione server - Account di servizio specificare gli account di accesso per i servizi [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . I servizi effettivamente configurati in questa pagina dipendono dalle funzionalità selezionate per l'installazione.  
  
     È possibile assegnare lo stesso account di accesso a tutti i servizi di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] oppure configurare singolarmente l'account di ogni servizio. Il tipo di avvio viene impostato su manuale per tutti i servizi compatibili con i cluster, ad esempio la ricerca full-text [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent, e non può essere modificato durante l'installazione. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] consiglia di configurare gli account del servizio singolarmente per assegnare i privilegi minimi a ogni servizio, in modo che ai servizi [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vengano concesse le autorizzazioni minime necessarie per completare le attività. Per altre informazioni, vedere [Configurazione Server - Account di servizio](../../install/server-configuration-service-accounts.md) e [Configurare account di servizio e autorizzazioni di Windows](../../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
     Per specificare lo stesso account di accesso per tutti gli account del servizio in questa istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], immettere le credenziali nei campi visualizzati nella parte inferiore della pagina.  
  
     **Nota sulla protezione** [!INCLUDE[ssNoteStrongPass](../../../includes/ssnotestrongpass-md.md)]  
  
     Dopo aver specificato le informazioni di accesso per i servizi [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , fare clic su **Avanti**.  
  
16. Usare la scheda **Configurazione server - Regole di confronto** per specificare regole di confronto non predefinite per [!INCLUDE[ssDE](../../../includes/ssde-md.md)] e [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Per altre informazioni, vedere [Configurazione del server - Regole di confronto](../../install/server-configuration-collation.md).  
  
17. Usare la pagina **Configurazione server - Filestream** per abilitare FILESTREAM per l'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Per altre informazioni, vedere [Configurazione del Motore di database - Filestream](../../install/database-engine-configuration-filestream.md). Per continuare, fare clic su **Avanti** .  
  
18. Utilizzare la pagina Configurazione di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] per specificare il tipo di installazione di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] da creare. Per l'installazione di cluster di failover, l'opzione è impostata su Installazione di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] non configurata. È necessario configurare i servizi [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] dopo aver completato l'installazione.  
  
     Per altre informazioni sulle modalità di configurazione di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], vedere [Opzioni di configurazione di Reporting Services &#40;SSRS&#41;](../../install/reporting-services-configuration-options-ssrs.md).  
  
19. Nella pagina Segnalazione errori specificare le informazioni da inviare a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] per migliorare [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Per impostazione predefinita, l'opzione per la segnalazione di errori è abilitata.  
  
20. Controllo configurazione sistema esegue uno o più set di regole per convalidare la configurazione con le funzionalità di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] specificate.  
  
21. Nella pagina Inizio installazione è presente una visualizzazione albero delle opzioni specificate durante l'installazione. Per continuare, fare clic su **Installa**. Il programma di installazione consentirà innanzitutto di installare i prerequisiti obbligatori per le funzionalità selezionate e, successivamente, le funzionalità stesse.  
  
     Durante l'installazione, nella pagina Stato dell'installazione è possibile monitorare lo stato di avanzamento del processo. Al termine dell'installazione, nella pagina **Operazione completata** viene visualizzato un collegamento al file di log di riepilogo del processo di installazione e ad altre note importanti.  
  
22. Per completare il processo di installazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , fare clic su **Chiudi**.  
  
23. Se viene richiesto, riavviare il computer. È importante leggere il messaggio visualizzato nell'Installazione guidata al termine dell'installazione. Per altre informazioni sui file di log del programma di installazione, vedere [Visualizzare e leggere i file di log del programma di installazione di SQL Server](../../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md).  
  
24. Ripetere i passaggi precedenti per preparare gli altri nodi per il cluster di failover. Per eseguire la preparazione negli altri nodi, è inoltre possibile utilizzare il file di configurazione generato automaticamente. Per altre informazioni, vedere [installare SQL Server 2014 tramite un File di configurazione](../../../database-engine/install-windows/install-sql-server-using-a-configuration-file.md).  
  
## <a name="complete"></a>Operazione completata  
  
#### <a name="advancedenterprise-failover-cluster-install-step-2-complete"></a>Passaggio 2 dell'installazione avanzata o aziendale del cluster di failover: completamento  
  
1.  Dopo aver preparato tutti i nodi nel modo descritto nel passaggio relativo alla [preparazione](#prepare), eseguire il programma di installazione in uno dei nodi preparati, preferibilmente in quello proprietario del disco condiviso. Nella pagina **Avanzate** di Centro installazione [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fare clic su **Completamento cluster avanzato**.  
  
2.  Controllo configurazione sistema consente di eseguire un'operazione di individuazione nel computer. Per continuare, [!INCLUDE[clickOK](../../../includes/clickok-md.md)]. È possibile fare clic su **Mostra dettagli**per visualizzare i dettagli sullo schermo oppure su **Visualizza report dettagliato**per visualizzarli come report HTML.  
  
3.  Nella pagina File di supporto per l'installazione fare clic su **Installa** per installare i file specifici.  
  
4.  Controllo configurazione sistema verifica lo stato del sistema del computer prima che l'installazione continui. Al termine della verifica, fare clic su **Avanti** per continuare. È possibile fare clic su **Mostra dettagli**per visualizzare i dettagli sullo schermo oppure su **Visualizza report dettagliato**per visualizzarlo come report HTML.  
  
5.  Nella pagina Selezione lingua è possibile specificare la lingua per l'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] se si sta eseguendo l'installazione in un sistema operativo localizzato e se nei supporti di installazione sono inclusi i Language Pack sia per l'inglese sia per la lingua corrispondente al sistema operativo. Per altre informazioni sul supporto di lingue diverse e sulle considerazioni relative all'installazione, vedere le [versioni della lingua locale in SQL Server](../../install/local-language-versions-in-sql-server.md).  
  
     Scegliere **Avanti**per continuare.  
  
6.  Utilizzare la pagina Configurazione nodi del cluster per selezionare il nome dell'istanza preparata per il clustering, quindi specificare il nome di rete per il nuovo cluster di failover di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Si tratta del nome utilizzato per identificare il cluster di failover nella rete.  
  
    > [!NOTE]  
    >  Nelle precedenti versioni dei cluster di failover di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] questo nome era noto come nome virtuale di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
7.  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Il programma di installazione esegue uno o più set di regole basati sulle funzionalità selezionate per convalidare la configurazione.  
  
8.  Utilizzare la pagina Gruppo risorse cluster per specificare il nome del gruppo di risorse cluster in cui verranno memorizzate le risorse del server virtuale di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Per specificare il nome del gruppo di risorse del cluster di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , Sono disponibili due opzioni:  
  
    -   Utilizzare l'elenco per specificare un gruppo esistente da utilizzare.  
  
    -   Digitare il nome di un nuovo gruppo da creare. Il nome "Archiviazione disponibile" non è un nome di gruppo valido.  
  
9. Nella pagina Selezione dischi cluster selezionare la risorsa disco del cluster condivisa del cluster di failover di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Il disco di cluster è l'unità in cui verranno memorizzati i dati di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . È possibile specificare più di un disco. Nella griglia Dischi condivisi disponibili vengono visualizzati un elenco dei dischi disponibili, l'indicazione dell'eventuale qualifica di ogni disco come disco condiviso e una descrizione di ogni risorsa disco. Per continuare, fare clic su **Avanti** .  
  
    > [!NOTE]  
    >  La prima unità viene utilizzata come unità predefinita per tutti i database, tuttavia è possibile modificarla nelle pagine di configurazione del [!INCLUDE[ssDE](../../../includes/ssde-md.md)] o di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .  
  
10. Nella pagina Configurazione rete cluster specificare le risorse di rete per l'istanza del cluster di failover:  
  
    -   **Impostazioni di rete** : specificare il tipo e l'indirizzo IP per tutti i nodi e le subnet dell'istanza del cluster di failover. È possibile specificare più indirizzi IP per un cluster di failover su più subnet, tuttavia è supportato un solo indirizzo IP per subnet. Ogni nodo preparato deve essere proprietario di almeno un indirizzo IP. Se si dispone di più subnet nel cluster di failover di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , sarà richiesto di impostare la dipendenza delle risorse indirizzo IP su OR.  
  
     Per continuare, fare clic su **Avanti** .  
  
11. Il flusso di lavoro relativo alla parte rimanente di questo argomento dipende dalle funzionalità specificate per l'installazione. Le pagine visualizzate dipendono dalle selezioni effettuate.  
  
12. Utilizzare la pagina Configurazione [!INCLUDE[ssDE](../../../includes/ssde-md.md)] - Provisioning account per specificare gli elementi seguenti:  
  
    -   Modalità di sicurezza: selezionare Autenticazione di Windows o l'autenticazione Modalità mista per l'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Se si seleziona l'autenticazione Modalità mista, è necessario specificare una password complessa per l'account amministratore di sistema [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] predefinito.  
  
         Quando viene stabilita la connessione tra un dispositivo e [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], il meccanismo di sicurezza è lo stesso sia in modalità mista che di autenticazione di Windows. Per altre informazioni, vedere [configurazione del motore di Database - Provisioning Account](../../install/database-engine-configuration-account-provisioning.md).  
  
    -   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Amministratori: è necessario specificare almeno un amministratore di sistema per l'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Per aggiungere l'account usato per eseguire il programma di installazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , fare clic su **Aggiungi utente corrente**. Per aggiungere o rimuovere account dall'elenco degli amministratori di sistema, fare clic su **Aggiungi** o **Rimuovi**, quindi modificare l'elenco di utenti, gruppi o computer con privilegi di amministratore per l'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Per altre informazioni, vedere [configurazione del motore di Database - Provisioning Account](../../install/database-engine-configuration-account-provisioning.md).  
  
     Dopo aver modificato l'elenco, [!INCLUDE[clickOK](../../../includes/clickok-md.md)]. Verificare l'elenco di amministratori nella finestra di dialogo di configurazione. Quando l'elenco è completo, fare clic su **Avanti**.  
  
13. Utilizzare la pagina Configurazione di [!INCLUDE[ssDE](../../../includes/ssde-md.md)] - Directory dati per specificare directory di installazione non predefinite. Per eseguire l'installazione in directory predefinite, fare clic su **Avanti**.  
  
    > [!IMPORTANT]  
    >  Se si specificano directory di installazione non predefinite, verificare che le cartelle di installazione siano univoche per questa istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Nessuna delle directory presenti in questa finestra di dialogo deve essere condivisa con le directory di altre istanze di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. È necessario che le directory dei dati si trovino nel disco di cluster condiviso per il cluster di failover.  
  
     Per altre informazioni, vedere [Configurazione del motore di database - Directory dati](../../install/database-engine-configuration-data-directories.md).  
  
14. Utilizzare la pagina Configurazione [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] - Provisioning account per specificare gli utenti o gli account che disporranno di autorizzazioni di amministratore per [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. È necessario specificare almeno un amministratore di sistema per [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Per aggiungere l'account usato per eseguire il programma di installazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , fare clic su **Aggiungi utente corrente**. Per aggiungere o rimuovere account dall'elenco degli amministratori di sistema, fare clic su **Aggiungi** o **Rimuovi**, quindi modificare l'elenco di utenti, gruppi o computer che disporranno di privilegi di amministratore per [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Per altre informazioni, vedere [configurazione di Analysis Services - Provisioning Account](../../install/analysis-services-configuration-account-provisioning.md).  
  
     Dopo aver modificato l'elenco, [!INCLUDE[clickOK](../../../includes/clickok-md.md)]. Verificare l'elenco di amministratori nella finestra di dialogo di configurazione. Quando l'elenco è completo, fare clic su **Avanti**.  
  
15. Utilizzare la pagina Configurazione di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] - Directory dati per specificare directory di installazione non predefinite. Per eseguire l'installazione in directory predefinite, fare clic su **Avanti**.  
  
    > [!IMPORTANT]  
    >  Se si specificano directory di installazione non predefinite, verificare che le cartelle di installazione siano univoche per questa istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Nessuna delle directory presenti in questa finestra di dialogo deve essere condivisa con le directory di altre istanze di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. È necessario che le directory dei dati si trovino nel disco di cluster condiviso per il cluster di failover.  
  
     Per altre informazioni, vedere [Configurazione di Analysis Services - Directory dati](../../install/analysis-services-configuration-data-directories.md).  
  
16. Controllo configurazione sistema esegue uno o più set di regole per convalidare la configurazione con le funzionalità di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] specificate.  
  
17. Nella pagina Inizio installazione è presente una visualizzazione albero delle opzioni specificate durante l'installazione. Per continuare, fare clic su **Installa**. Il programma di installazione consentirà innanzitutto di installare i prerequisiti obbligatori per le funzionalità selezionate e, successivamente, le funzionalità stesse.  
  
18. Durante l'installazione, nella pagina Stato dell'installazione è possibile monitorare lo stato di avanzamento del processo.  
  
19. Al termine dell'installazione, nella pagina **Operazione completata** viene visualizzato un collegamento al file di log di riepilogo del processo di installazione e ad altre note importanti. Per completare il processo di installazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , fare clic su **Chiudi**. A questo punto tutti i nodi preparati per lo stesso cluster di failover appartengono al cluster di failover di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] completato.  
  
## <a name="next-steps"></a>Passaggi successivi  
 **Configurare la nuova installazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]**: per ridurre la superficie di attacco di un sistema, in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vengono installati e abilitati in modo selettivo i servizi e le funzionalità principali. Per ulteriori informazioni, vedere [Surface Area Configuration](../../../relational-databases/security/surface-area-configuration.md).  
  
 Per altre informazioni sui file di log, vedere [Visualizzare e leggere i file di log del programma di installazione di SQL Server](../../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Installazione di SQL Server 2014 dal prompt dei comandi](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)  
  
  

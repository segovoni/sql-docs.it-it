---
title: sp_addmergepublication (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_addmergepublication
- sp_addmergepublication_TSQL
helpviewer_keywords:
- sp_addmergepublication
ms.assetid: 28a629a1-7374-4614-9b04-279d290a942a
caps.latest.revision: 72
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: ad636ff51a7a64cf1d46e8bb39b4937137454dd4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32993358"
---
# <a name="spaddmergepublication-transact-sql"></a>sp_addmergepublication (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Viene creata una nuova pubblicazione di tipo merge. Questa stored procedure viene eseguita nel server di pubblicazione nel database in fase di pubblicazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_addmergepublication [ @publication = ] 'publication'   
    [ , [ @description = ] 'description'   
    [ , [ @retention = ] retention ]   
    [ , [ @sync_mode = ] 'sync_mode' ]   
    [ , [ @allow_push = ] 'allow_push' ]   
    [ , [ @allow_pull = ] 'allow_pull' ]   
    [ , [ @allow_anonymous = ] 'allow_anonymous' ]   
    [ , [ @enabled_for_internet = ] 'enabled_for_internet' ]   
    [ , [ @centralized_conflicts = ] 'centralized_conflicts' ]   
    [ , [ @dynamic_filters = ] 'dynamic_filters' ]   
    [ , [ @snapshot_in_defaultfolder = ] 'snapshot_in_default_folder' ]   
    [ , [ @alt_snapshot_folder = ] 'alternate_snapshot_folder' ]   
    [ , [ @pre_snapshot_script = ] 'pre_snapshot_script' ]   
    [ , [ @post_snapshot_script = ] 'post_snapshot_script' ]   
    [ , [ @compress_snapshot = ] 'compress_snapshot' ]   
    [ , [ @ftp_address = ] 'ftp_address' ]   
    [ , [ @ftp_port = ] ftp_port ]   
    [ , [ @ftp_subdirectory = ] 'ftp_subdirectory' ]   
    [ , [ @ftp_login = ] 'ftp_login' ]   
    [ , [ @ftp_password = ] 'ftp_password' ]   
    [ , [ @conflict_retention = ] conflict_retention ]   
    [ , [ @keep_partition_changes = ] 'keep_partition_changes' ]   
    [ , [ @allow_subscription_copy = ] 'allow_subscription_copy' ]   
    [ , [ @allow_synctoalternate = ] 'allow_synctoalternate' ]   
    [ , [ @validate_subscriber_info = ] 'validate_subscriber_info' ]   
    [ , [ @add_to_active_directory = ] 'add_to_active_directory' ]   
    [ , [ @max_concurrent_merge = ] maximum_concurrent_merge ]   
    [ , [ @max_concurrent_dynamic_snapshots = ] max_concurrent_dynamic_snapshots ]  
    [ , [ @use_partition_groups = ] 'use_partition_groups' ]  
    [ , [ @publication_compatibility_level = ] 'backward_comp_level' ]  
    [ , [ @replicate_ddl = ] replicate_ddl ]  
    [ , [ @allow_subscriber_initiated_snapshot = ] 'allow_subscriber_initiated_snapshot' ]   
    [ , [ @allow_web_synchronization = ] 'allow_web_synchronization' ]   
    [ , [ @web_synchronization_url = ] 'web_synchronization_url' ]  
    [ , [ @allow_partition_realignment = ] 'allow_partition_realignment' ]  
    [ , [ @retention_period_unit = ] 'retention_period_unit' ]  
    [ , [ @generation_leveling_threshold = ] generation_leveling_threshold ]  
    [ , [ @automatic_reinitialization_policy = ] automatic_reinitialization_policy ]  
    [ , [ @conflict_logging = ] 'conflict_logging' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publication =** ] **'***pubblicazione***'**  
 Nome della pubblicazione di tipo merge da creare. *pubblicazione* viene **sysname**e non prevede alcun valore predefinito e non corrispondere alla parola chiave tutti. Il nome della pubblicazione deve essere univoco all'interno del database.  
  
 [  **@description =** ] **'***descrizione***'**  
 Descrizione della pubblicazione. *Descrizione* viene **nvarchar(255**, con un valore predefinito è NULL.  
  
 [  **@retention =** ] *conservazione*  
 È il periodo di memorizzazione in memorizzazione unità di tempo, per cui si desidera salvare le modifiche per il dato *pubblicazione*. *conservazione* viene **int**, con un valore predefinito di 14 unità. Unità del periodo di conservazione sono definite da *retention_period_unit*. Se la sottoscrizione non viene sincronizzata entro il periodo di memorizzazione specificato e se le modifiche che tale sottoscrizione avrebbe dovuto ricevere sono state rimosse tramite un'operazione di rimozione nel server di distribuzione, la sottoscrizione scade e pertanto dovrà essere reinizializzata. Il periodo di memorizzazione massimo consentito equivale al numero di giorni tra il 31 dicembre 9999 e la data corrente.  
  
> [!NOTE]  
>  Il periodo di memorizzazione per le pubblicazioni di tipo merge è caratterizzato da un periodo di tolleranza di 24 ore per consentire l'adeguamento dei Sottoscrittori appartenenti a fusi orari diversi. Se, ad esempio, si imposta un periodo di memorizzazione di un giorno, il periodo di memorizzazione effettivo sarà di 48 ore.  
  
 [  **@sync_mode =** ] **'***sync_mode***'**  
 Modalità di sincronizzazione iniziale dei Sottoscrittori della pubblicazione. *sync_mode* viene **nvarchar(10)**, e può essere uno dei valori seguenti.  
  
|Value|Description|  
|-----------|-----------------|  
|**native** (impostazione predefinita)|Genera l'output in modalità nativa del programma per la copia bulk per tutte le tabelle.|  
|**character**|Genera l'output in modalità carattere del programma per la copia bulk per tutte le tabelle. Necessario per supportare [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssEW](../../includes/ssew-md.md)] e non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sottoscrittori.|  
  
 [  **@allow_push =** ] **'***allow_push***'**  
 Specifica se è consentito creare sottoscrizioni push per la pubblicazione specificata. *allow_push* viene **nvarchar(5**, con un valore predefinito è TRUE, che consente le sottoscrizioni push nella pubblicazione.  
  
 [  **@allow_pull =** ] **'***allow_pull***'**  
 Specifica se è consentito creare sottoscrizioni pull per la pubblicazione specificata. *allow_pull* viene **nvarchar(5**, con un valore predefinito è TRUE, che consente le sottoscrizioni pull nella pubblicazione. È necessario specificare true per supportare [!INCLUDE[ssEW](../../includes/ssew-md.md)] sottoscrittori.  
  
 [  **@allow_anonymous =** ] **'***allow_anonymous***'**  
 Specifica se è consentito creare sottoscrizioni anonime per la pubblicazione specificata. *allow_anonymous* viene **nvarchar(5**, con un valore predefinito è TRUE, che consente sottoscrizioni anonime per la pubblicazione. Per supportare [!INCLUDE[ssEW](../../includes/ssew-md.md)] sottoscrittori, è necessario specificare **true**.  
  
 [  **@enabled_for_internet =** ] **'***enabled_for_internet***'**  
 Specifica se la pubblicazione è abilitata per Internet e determina se è possibile utilizzare FTP per il trasferimento dei file di snapshot in un Sottoscrittore. *enabled_for_internet* viene **nvarchar(5**, con un valore predefinito è FALSE. Se **true**, i file di sincronizzazione per la pubblicazione vengono inseriti nella directory C:\Program Files\Microsoft SQL Server\MSSQL\MSSQL.x\repldata\ftp. La directory Ftp deve essere creata dall'utente. Se **false**, la pubblicazione non è abilitata per l'accesso a Internet.  
  
 [  **@centralized_conflicts =**] **'***centralized_conflicts***'**  
 Questo parametro è deprecato ed è supportato solo per compatibilità con gli script di versioni precedenti. Utilizzare *conflict_logging* per specificare il percorso in cui sono archiviati i record dei conflitti.  
  
 [  **@dynamic_filters =**] **'***dynamic_filters***'**  
 Consente alla pubblicazione di tipo merge di utilizzare i filtri di riga con parametri. *dynamic_filters* viene **nvarchar(5**, con un valore predefinito è FALSE.  
  
> [!NOTE]  
>  Si consiglia di non specificare questo parametro ma di consentire a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di determinare automaticamente se vengono utilizzati i filtri di riga con parametri. Se si specifica un valore di **true** per *dynamic_filters*, è necessario definire un filtro di riga con parametri per l'articolo. Per altre informazioni, vedere [Definizione e modifica di un filtro di riga con parametri per un articolo di merge](../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).  
  
 [  **@snapshot_in_defaultfolder =** ] **'***snapshot_in_default_folder***'**  
 Viene specificato se i file di snapshot sono archiviati nella cartella predefinita. *snapshot_in_default_folder* viene **nvarchar(5**, con un valore predefinito è TRUE. Se **true**, i file di snapshot sono disponibili nella cartella predefinita. Se **false**, verranno archiviati i file di snapshot nella posizione alternativa specificata da *alternate_snapshot_folder*. Una posizione alternativa può essere un altro server, un'unità di rete oppure un supporto rimovibile, ad esempio un CD o un disco rimovibile. È inoltre possibile archiviare i file di snapshot in un sito FTP (File Transfer Protocol) in modo da poterli recuperare successivamente tramite il Sottoscrittore. Si noti che questo parametro può essere true e una posizione specificata da *alt_snapshot_folder*. Tale combinazione indica che i file di snapshot vengono archiviati sia nella posizione predefinita che in posizioni alternative.  
  
 [  **@alt_snapshot_folder =** ] **'***alternate_snapshot_folder***'**  
 Specifica la posizione della cartella alternativa per lo snapshot. *alternate_snapshot_folder* viene **nvarchar(255**, con un valore predefinito è NULL.  
  
 [  **@pre_snapshot_script =** ] **'***pre_snapshot_script***'**  
 Specifica un puntatore a un **SQL** percorso del file. *pre_snapshot_script* viene **nvarchar(255**, con un valore predefinito è NULL. Durante l'applicazione dello snapshot in un Sottoscrittore, l'agente di merge esegue lo script pre-snapshot prima degli script degli oggetti replicati. Lo script viene eseguito nel contesto di sicurezza utilizzato dall'agente di merge durante la connessione al database di sottoscrizione. Gli script di pre-snapshot non vengono eseguiti nei [!INCLUDE[ssEW](../../includes/ssew-md.md)] sottoscrittori.  
  
 [  **@post_snapshot_script =** ] **'***post_snapshot_script***'**  
 Specifica un puntatore a un **SQL** percorso del file. *post_snapshot_script* viene **nvarchar(255**, con un valore predefinito è NULL. L'agente di merge esegue lo script post-snapshot dopo l'applicazione di tutti gli altri script di oggetti replicati e dei dati durante una sincronizzazione iniziale. Lo script viene eseguito nel contesto di sicurezza utilizzato dall'agente di merge durante la connessione al database di sottoscrizione. Gli script di post-snapshot non vengono eseguiti nei [!INCLUDE[ssEW](../../includes/ssew-md.md)] sottoscrittori.  
  
 [  **@compress_snapshot =** ] **'***compress_snapshot***'**  
 Specifica che lo snapshot scritto il **@alt_snapshot_folder** deve essere compresso nel si trova il [!INCLUDE[msCoName](../../includes/msconame-md.md)] formato CAB. *compress_snapshot* viene **nvarchar(5**, con un valore predefinito è FALSE. **false** indica che non lo snapshot verrà compresso; **true** indica che lo snapshot verrà compresso. I file di snapshot di dimensioni superiori a 2GB non possono essere compressi. I file di snapshot compressi vengono decompressi nella posizione dove viene eseguito l'agente di merge; in genere le sottoscrizioni pull vengono utilizzate con gli snapshot compressi in modo che i file vengono decompressi nel Sottoscrittore. Non è possibile comprimere lo snapshot all'interno della cartella predefinita. Per supportare [!INCLUDE[ssEW](../../includes/ssew-md.md)] sottoscrittori, è necessario specificare **false**.  
  
 [  **@ftp_address =** ] **'***ftp_address***'**  
 Indirizzo di rete del servizio FTP per il database di distribuzione. *ftp_address* viene **sysname**, con un valore predefinito è NULL. Specifica la posizione dei file di snapshot della pubblicazione, dove i file possono essere prelevati dall'agente di merge di un Sottoscrittore. Poiché questa proprietà viene archiviata per ogni pubblicazione, ogni pubblicazione può essere un altro *ftp_address*. La pubblicazione deve supportare la propagazione di snapshot tramite FTP.  
  
 [  **@ftp_port=** ] *ftp_port*  
 Numero di porta del servizio FTP per il database di distribuzione. *ftp_port* viene **int**, con un valore predefinito è 21. Specifica la posizione dei file di snapshot della pubblicazione, dove i file possono essere prelevati dall'agente di merge di un Sottoscrittore. Poiché questa proprietà viene archiviata per ogni pubblicazione, ogni pubblicazione può avere un proprio *ftp_port*.  
  
 [  **@ftp_subdirectory =** ] **'***ftp_subdirectory***'**  
 Specifica la posizione dei file di snapshot, dove i file possono essere prelevati dall'agente di merge del Sottoscrittore se la pubblicazione supporta la propagazione di snapshot tramite FTP. *ftp_subdirectory* viene **nvarchar(255**, con un valore predefinito è NULL. Poiché questa proprietà viene archiviata per ogni pubblicazione, ogni pubblicazione può avere un proprio *ftp_subdirctory* oppure scegliere di non una sottodirectory con un valore NULL.  
  
 Durante la pregenerazione degli snapshot per le pubblicazioni con filtri con parametri, lo snapshot dei dati per ogni partizione del Sottoscrittore deve essere archiviato nella propria cartella. La struttura di directory per gli snapshot pregenerati tramite FTP deve rispettare la struttura seguente:  
  
 *alternate_snapshot_folder*\ftp\\*publisher_publicationDB_publication*\\*partitionID*.  
  
> [!NOTE]  
>  I valori riportati sopra in corsivo dipendono dai dettagli della pubblicazione e dalla partizione del Sottoscrittore.  
  
 [  **@ftp_login =** ] **'***ftp_login***'**  
 Nome utente utilizzato per la connessione al servizio FTP. *ftp_login* viene **sysname**, con un valore predefinito di 'anonymous'.  
  
 [  **@ftp_password =** ] **'***ftp_password***'**  
 Password utente utilizzata per la connessione al servizio FTP. *ftp_password* viene **sysname**, con un valore predefinito è NULL.  
  
> [!IMPORTANT]  
>  Non usare una password vuota. Usare una password complessa.  
  
 [  **@conflict_retention =** ] *conflict_retention*  
 Viene specificato il periodo di memorizzazione dei conflitti espresso in giorni. *conflict_retention* viene **int**, con valore predefinito è 14 giorni prima il conflitto riga viene eliminata dalla tabella dei conflitti.  
  
 [  **@keep_partition_changes =** ] **'***keep_partition_changes***'**  
 Specifica se abilitare le ottimizzazioni delle modifiche alle partizioni quando non è possibile utilizzare le partizioni pre-calcolate. *keep_partition_changes* viene **nvarchar(5**, con un valore predefinito è TRUE. **false** significa che le modifiche di partizione non viene ottimizzate e quando non si utilizzano partizioni pre-calcolate, le partizioni inviate a tutti i sottoscrittori verranno verificate quando si modificano i dati in una partizione. **true** significa che le modifiche di partizione viene ottimizzate e vengono coinvolti solo i sottoscrittori con righe nelle partizioni modificate. Quando si utilizzano partizioni pre-calcolate, impostare *use_partition_groups* a **true** e impostare *keep_partition_changes* a **false**. Per altre informazioni, vedere [Ottimizzare le prestazioni dei filtri con parametri con le partizioni pre-calcolate](../../relational-databases/replication/merge/parameterized-filters-optimize-for-precomputed-partitions.md).  
  
> [!NOTE]  
>  Se si specifica un valore di **true** per *keep_partition_changes*, specificare un valore di **1** per il parametro dell'agente Snapshot **- MaxNetworkOptimization** . Per ulteriori informazioni su questo parametro, vedere [agente Snapshot repliche](../../relational-databases/replication/agents/replication-snapshot-agent.md). Per informazioni su come specificare i parametri dell'agente, vedere [amministrazione agente di replica](../../relational-databases/replication/agents/replication-agent-administration.md).  
  
 Con [!INCLUDE[ssEW](../../includes/ssew-md.md)] sottoscrittori, *keep_partition_changes* deve essere impostato su true per assicurarsi che le eliminazioni vengono propagate correttamente. Se impostato su false, nel Sottoscrittore potrebbero essere presenti più righe rispetto al previsto.  
  
 [  **@allow_subscription_copy=** ] **'***allow_subscription_copy***'**  
 Abilita o disabilita la funzione di copia dei database di sottoscrizione che sottoscrivono la pubblicazione. *allow_subscription_copy* viene **nvarchar(5**, con un valore predefinito è FALSE. Le dimensioni del database di sottoscrizione copiato devono essere inferiori a 2 gigabyte (GB)  
  
 [  **@allow_synctoalternate =** ] **'***allow_synctoalternate***'**  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [  **@validate_subscriber_info =** ] **'***validate_subscriber_info***'**  
 Visualizza un elenco delle funzioni utilizzate per definire una partizione del Sottoscrittore dei dati pubblicati quando vengono utilizzati i filtri di riga con parametri. *validate_subscriber_info* viene **nvarchar(500)**, con un valore predefinito è NULL. Queste informazioni vengono utilizzate dall'agente di merge per convalidare la partizione del Sottoscrittore. Ad esempio, se [SUSER_SNAME](../../t-sql/functions/suser-sname-transact-sql.md) viene utilizzato nel filtro di riga con parametri, il parametro deve essere `@validate_subscriber_info=N'SUSER_SNAME()'`.  
  
> [!NOTE]  
>  Si consiglia di non specificare questo parametro e di consentire invece a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di determinare il criterio di filtro in modo automatico.  
  
 [  **@add_to_active_directory =** ] **'***add_to_active_directory***'**  
 Questo parametro è deprecato ed è supportato solo per compatibilità con gli script di versioni precedenti. Non è più possibile aggiungere informazioni di pubblicazione in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Active Directory.  
  
 [  **@max_concurrent_merge =** ] *maximum_concurrent_merge*  
 Numero massimo di processi di merge simultanei. *maximum_concurrent_merge* viene **int** con un valore predefinito è 0. Il valore **0** per questa proprietà indica che non sono previsti limiti al numero di processi di merge simultanei in esecuzione in qualsiasi momento. Questa proprietà imposta un limite per il numero di processi di merge che è possibile eseguire contemporaneamente in una pubblicazione di tipo merge. Se è stata pianificata l'esecuzione simultanea di un numero di processi maggiore del limite consentito, i processi in eccesso vengono inseriti in una coda dove rimangono in attesa fino al completamento del processo di merge attualmente in esecuzione.  
  
 [  **@max_concurrent_dynamic_snapshots =**] *max_concurrent_dynamic_snapshots*  
 Numero massimo di sessioni dell'agente snapshot che possono essere eseguite simultaneamente per generare snapshot dei dati filtrati per le partizioni del Sottoscrittore. *maximum_concurrent_dynamic_snapshots* viene **int** con un valore predefinito è 0. Se **0**, non vi è alcun limite al numero sessioni di snapshot. Se è stata pianificata l'esecuzione simultanea di un numero di processi di snapshot superiore al limite consentito, i processi in eccesso vengono inseriti in una coda in cui rimangono in attesa fino al completamento del processo di snapshot in esecuzione.  
  
 [  **@use_partition_groups =** ] **'***use_partition_groups***'**  
 Specifica che le partizioni pre-calcolate devono essere utilizzate per ottimizzare il processo di sincronizzazione. *use_partition_groups* viene **nvarchar(5**, e può essere uno dei valori seguenti:  
  
|Value|Description|  
|-----------|-----------------|  
|**true**|La pubblicazione utilizza partizioni pre-calcolate.|  
|**false**|La pubblicazione non utilizza partizioni pre-calcolate.|  
|NULL(default)|Il sistema decide sulla strategia di partizionamento.|  
  
 Le partizioni pre-calcolate vengono utilizzate per impostazione predefinita. Per evitare di utilizzare partizioni pre-calcolate, *use_partition_groups* deve essere impostato su **false**. Se è NULL, il sistema decide se è possibile utilizzare le partizioni pre-calcolate. Se precalcolate partizioni non possono essere utilizzate quindi questo valore verrà impostato **false** senza generare alcun errore. In questi casi, *keep_partition_changes* può essere impostato su **true** per fornire una sorta di ottimizzazione. Per ulteriori informazioni, vedere [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md) e [Ottimizza prestazioni filtro con parametri con le partizioni precalcolate](../../relational-databases/replication/merge/parameterized-filters-optimize-for-precomputed-partitions.md).  
  
 [  **@publication_compatibility_level =** ] *backward_comp_level*  
 Indica la compatibilità con le versioni precedenti della pubblicazione. *backward_comp_level* viene **nvarchar(6)**, e può essere uno dei valori seguenti:  
  
|Value|Versione|  
|-----------|-------------|  
|**90RTM**|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|  
|**100RTM**|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|  
  
 [  **@replicate_ddl =** ] *replicate_ddl*  
 Indica se per la pubblicazione è supportata la replica dello schema. *replicate_ddl* viene **int**, con un valore predefinito è 1. **1** indica che vengono replicate istruzioni di data definition language (DDL) eseguite nel server di pubblicazione, e **0** indica che le istruzioni DDL non vengono replicate. Per altre informazioni, vedere [Apportare modifiche allo schema nei database di pubblicazione](../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md).  
  
 Il *@replicate_ddl* parametro viene rispettato quando un'istruzione DDL aggiunge una colonna. Il *@replicate_ddl* parametro viene ignorato quando un'istruzione DDL modifica o elimina una colonna per i motivi seguenti.  
  
-   Quando viene eliminata una colonna, è necessario aggiornare sysarticlecolumns per evitare che le nuove istruzioni DML, compresi la colonna eliminata che potrebbe causare l'agente di distribuzione. Il *@replicate_ddl* parametro verrà ignorato perché la replica deve replicare sempre la modifica dello schema.  
  
-   Quando una colonna viene modificata, è probabile che venga modificato il tipo di dati di origine o il supporto dei valori Null, di conseguenza le istruzioni DML contengono un valore che potrebbe non essere compatibile con la tabella nel Sottoscrittore. Tali istruzioni DML potrebbero determinare la mancata esecuzione dell'agente di distribuzione. Il *@replicate_ddl* parametro verrà ignorato perché la replica deve replicare sempre la modifica dello schema.  
  
-   Quando un'istruzione DDL aggiunge una nuova colonna, sysarticlecolumns non include la nuova colonna. Le istruzioni DML non tenteranno di replicare i dati per la nuova colonna. Il parametro viene rispettato perché la replica o la non replica di DDL è accettabile.  
  
 [  **@allow_subscriber_initiated_snapshot =** ] **'***allow_subscriber_initiated_snapshot***'**  
 Indica se i Sottoscrittori di questa pubblicazione possono avviare il processo di snapshot per generare lo snapshot filtrato per la relativa partizione dati. *allow_subscriber_initiated_snapshot* viene **nvarchar(5**, con un valore predefinito è FALSE. **true** indica che i sottoscrittori possono avviare il processo di snapshot.  
  
 [  **@allow_web_synchronization =** ] **'***allow_web_synchronization***'**  
 Specifica se la pubblicazione è abilitata per la sincronizzazione Web. *allow_web_synchronization* viene **nvarchar(5**, con un valore predefinito è FALSE. **true** specifica che le sottoscrizioni della pubblicazione possono essere sincronizzate tramite HTTPS. Per altre informazioni, vedere [Web Synchronization for Merge Replication](../../relational-databases/replication/web-synchronization-for-merge-replication.md). Per supportare [!INCLUDE[ssEW](../../includes/ssew-md.md)] sottoscrittori, è necessario specificare **true**.  
  
 [  **@web_synchronization_url=** ] **'***web_synchronization_url***'**  
 Specifica il valore predefinito dell'URL Internet utilizzato per la sincronizzazione tramite il Web. *web_synchronization_url si*s **nvarchar(500)**, con un valore predefinito è NULL. Definisce l'URL Internet predefinito se ne è stato esplicitamente impostato quando [sp_addmergepullsubscription_agent](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md) viene eseguita.  
  
 [  **@allow_partition_realignment =** ] **'***allow_partition_realignment***'**  
 Determina se le eliminazioni vengono inviate al Sottoscrittore quando la modifica della riga nel server di pubblicazione provoca la modifica della partizione. *allow_partition_realignment* viene **nvarchar(5**, con un valore predefinito è TRUE. **true** le eliminazioni vengono inviate al sottoscrittore in modo da riflettere i risultati di una modifica della partizione mediante la rimozione dei dati che non sono più parte della partizione del sottoscrittore. **false** lascia che i dati di una vecchia partizione nel Sottoscrittore, in cui le modifiche apportate a tali dati nel server di pubblicazione non verranno replicate nel Sottoscrittore, ma le modifiche apportate nel Sottoscrittore verranno replicate nel server di pubblicazione. Impostazione *allow_partition_realignment* a **false** viene utilizzato per mantenere i dati in una sottoscrizione di una vecchia partizione quando i dati devono essere accessibili per fini cronologici.  
  
> [!NOTE]  
>  Dati che rimangono nel Sottoscrittore impostazione *allow_partition_realignment* a **false** devono essere considerati come se fosse di sola lettura; tuttavia, questo non viene applicato dal sistema di replica.  
  
 [  **@retention_period_unit =** ] **'***retention_period_unit***'**  
 Specifica le unità per il periodo di memorizzazione impostato *conservazione*. *retention_period_unit* viene **nvarchar(10)**, e può essere uno dei valori seguenti.  
  
|Value|Versione|  
|-----------|-------------|  
|**giorno** (impostazione predefinita)|Il periodo di memorizzazione è specificato in giorni.|  
|**week**|Il periodo di memorizzazione è specificato in settimane.|  
|**month**|Il periodo di memorizzazione è specificato in mesi.|  
|**year**|Il periodo di memorizzazione è specificato in anni.|  
  
 [  **@generation_leveling_threshold=** ] *generation_leveling_threshold*  
 Viene specificato il numero di modifiche contenute in una generazione. Una generazione è una raccolta di modifiche recapitate a un server di pubblicazione o a un Sottoscrittore. *generation_leveling_threshold* viene **int**, con valore predefinito è 1000.  
  
 [  **@automatic_reinitialization_policy =** ] *automatic_reinitialization_policy*  
 Specifica se le modifiche vengono caricate dal sottoscrittore prima di una reinizializzazione automatica richiesta da una modifica apportata alla pubblicazione, dove il valore **1** è stato specificato per **@force_reinit_subscription**. *automatic_reinitialization_policy* è di tipo bit e il valore predefinito pari a 0. **1** significa che le modifiche vengono caricate dal sottoscrittore prima che si verifichi una reinizializzazione automatica.  
  
> [!IMPORTANT]  
>  Se si aggiunge, elimina o modifica un filtro con parametri, le modifiche in sospeso nel Sottoscrittore non possono essere caricate nel server di pubblicazione durante la reinizializzazione. Per caricare le modifiche in sospeso, sincronizzare tutte le sottoscrizioni prima di modificare il filtro.  
  
 [  **@conflict_logging =** ] **'***conflict_logging***'**  
 Specifica la posizione di archiviazione dei record dei conflitti. *conflict_logging* viene **nvarchar(15)**, e può essere uno dei valori seguenti:  
  
|Value|Description|  
|-----------|-----------------|  
|**publisher**|I record con conflitti vengono archiviati nel server di pubblicazione.|  
|**subscriber**|I record con conflitti vengono archiviati nel Sottoscrittore che ha causato il conflitto. Non supportato per [!INCLUDE[ssEW](../../includes/ssew-md.md)] i sottoscrittori.|  
|**both**|I record con conflitti vengono archiviati nel server di pubblicazione e nel Sottoscrittore.|  
|NULL (predefinito)|La replica imposta automaticamente *conflict_logging* a **entrambi** quando il valore *backward_comp_level* è **90RTM** e **publisher** in tutti gli altri casi.|  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_addmergepublication** viene utilizzata nella replica di tipo merge.  
  
 Per elencare oggetti di pubblicazione in Active Directory tramite il **@add_to_active_directory** parametro, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oggetto sia già stato creato in Active Directory.  
  
 Se esistono più pubblicazioni che pubblicano lo stesso oggetto di database, solo per le pubblicazioni con un *replicate_ddl* valore **1** replicherà ALTER TABLE, ALTER VIEW, ALTER PROCEDURE, ALTER FUNCTION e Istruzioni ALTER TRIGGER DDL. Una istruzione ALTER TABLE DROP COLUMN DDL verrà tuttavia replicata da tutte le pubblicazioni che stanno pubblicando la colonna eliminata.  
  
 Per [!INCLUDE[ssEW](../../includes/ssew-md.md)] sottoscrittori, il valore di *alternate_snapshot_folder* viene utilizzato solo quando il valore di *snapshot_in_default_folder* è **false**.  
  
 Con abilitata la replica DDL (* * replicate_ddl **= 1**) per una pubblicazione, per facilitare la DDL da non replicare le modifiche della pubblicazione [sp_changemergepublication &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md)devono essere eseguiti prima per impostare *replicate_ddl* alla **0**. Dopo le istruzioni DDL non di replica sono stati emessi, **sp_changemergepublication** può essere eseguito nuovamente per riattivare la replica DDL.  
  
## <a name="example"></a>Esempio  
 [!code-sql[HowTo#sp_AddMergePub](../../relational-databases/replication/codesnippet/tsql/sp-addmergepublication-t_1.sql)]  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server o **db_owner** ruolo predefinito del database possono eseguire **sp_addmergepublication**.  
  
## <a name="see-also"></a>Vedere anche  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Pubblicare dati e oggetti di database](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [sp_changemergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md)   
 [sp_dropmergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergepublication-transact-sql.md)   
 [sp_helpmergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md)   
 [Stored procedure per la replica &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  

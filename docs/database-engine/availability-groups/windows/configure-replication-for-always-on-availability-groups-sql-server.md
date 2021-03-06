---
title: Configurare la replica per i gruppi di disponibilità AlwaysOn (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], interoperability
- replication [SQL Server], AlwaysOn Availability Groups
ms.assetid: 4e001426-5ae0-4876-85ef-088d6e3fb61c
caps.latest.revision: 17
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 2ea2fb342bc881d79f8e3184535bbe888e939068
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34770467"
---
# <a name="configure-replication-for-always-on-availability-groups-sql-server"></a>Configurare la replica per i gruppi di disponibilità AlwaysOn (SQL Server)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  La configurazione della replica in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] e dei gruppi di disponibilità AlwaysOn richiede sette passaggi. Ogni passaggio è descritto in dettaglio nelle sezioni seguenti.  
  
1.  [Configurare le pubblicazioni e le sottoscrizioni del database.](#step1)  
  
2.  [Configurare il gruppo di disponibilità AlwaysOn.](#step2)  
  
3.  [Assicurare che tutti gli host della replica secondaria vengano configurati per la replica.](#step3)  
  
4.  [Configurare gli host della replica secondaria come server di pubblicazione di replica.](#step4)  
  
5.  [Reindirizzare il server di pubblicazione originale al nome del listener gruppo di disponibilità.](#step5)  
  
6.  [Eseguire la stored procedure di convalida per verificare la configurazione.](#step6)  
  
7.  [Aggiungere il server di pubblicazione originale a Monitoraggio replica.](#step7)  
  
 I passaggi 1 e 2 possono essere effettuati in qualsiasi ordine.  
  
##  <a name="step1"></a> 1. Configurare le pubblicazioni e le sottoscrizioni del database  
 **Configurare il server di distribuzione**  
  
 Il database di distribuzione non può trovarsi in un gruppo di disponibilità.  
  
1.  Configurare la distribuzione sul server di distribuzione. Se per la configurazione vengono usate stored procedure, eseguire **sp_adddistributor**. Utilizzare il parametro *@password* per identificare la password che sarà utilizzata quando un server di pubblicazione remoto si connette al server di distribuzione. La password sarà necessaria anche per ogni server di pubblicazione remoto quando viene configurato il server di distribuzione remoto.  
  
    ```  
    USE master;  
    GO  
    EXEC sys.sp_adddistributor  
        @distributor = 'MyDistributor',  
        @password = '**Strong password for distributor**';  
    ```  
  
2.  Creare il database di distribuzione nel server di distribuzione. Se per la configurazione vengono usate stored procedure, eseguire **sp_adddistributiondb**.  
  
    ```  
    USE master;  
    GO  
    EXEC sys.sp_adddistributiondb  
        @database = 'distribution',  
        @security_mode = 1;  
    ```  
  
3.  Configurare il server di pubblicazione remoto. Se per la configurazione del server di distribuzione vengono usate stored procedure, eseguire **sp_adddistpublisher**. Il parametro *@security_mode* viene usato per determinare in che modo la stored procedure di convalida del server di pubblicazione eseguita dagli agenti di replica si connette alla replica primaria corrente. Se impostato su 1, per connettersi alla replica primaria corrente viene utilizzata l'Autenticazione di Windows. Se impostato su 0, viene usata l'autenticazione [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] con i valori *@login* e *@password* specificati. L'account di accesso e la password specificati devono essere validi per ogni replica secondaria per consentire alla stored procedure di convalida di connettersi a tale replica.  
  
    > [!NOTE]  
    >  Se gli eventuali agenti di replica modificati vengono eseguiti in un computer diverso dal server di distribuzione, l'utilizzo dell'Autenticazione di Windows per la connessione alla replica primaria richiederà l'autenticazione Kerberos per consentire la configurazione per la comunicazione tra i computer host della replica. L'utilizzo di un account di accesso di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] per la connessione alla replica primaria corrente non richiede l'autenticazione Kerberos.  
  
    ```  
    USE master;  
    GO  
    EXEC sys.sp_adddistpublisher  
        @publisher = 'AGPrimaryReplicaHost',  
        @distribution_db = 'distribution',  
        @working_directory = '\\MyReplShare\WorkingDir',  
        @login = 'MyPubLogin',  
        @password = '**Strong password for publisher**';  
    ```  
  
 Per altre informazioni, vedere [sp_adddistpublisher &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md).  
  
 **Configurare il server di pubblicazione nel server di pubblicazione originale**  
  
1.  Configurare la distribuzione remota. Se per la configurazione del server di pubblicazione vengono usate stored procedure, eseguire **sp_adddistributor**. Specificare per *@password* lo stesso valore usato al momento dell'esecuzione di **sp_adddistrbutor** nel server di distribuzione per configurare la distribuzione.  
  
    ```  
    exec sys.sp_adddistributor  
        @distributor = 'MyDistributor',  
        @password = 'MyDistPass'  
    ```  
  
2.  Abilitare il database per la replica. Se per la configurazione del server di pubblicazione vengono usate stored procedure, eseguire **sp_replicationdboption**. Se è necessario configurare la replica transazionale e di tipo merge per il database, è necessario abilitarne ognuna.  
  
    ```  
    USE master;  
    GO  
    EXEC sys.sp_replicationdboption  
        @dbname = 'MyDBName',  
        @optname = 'publish',  
        @value = 'true';  
  
    EXEC sys.sp_replicationdboption  
        @dbname = 'MyDBName',  
        @optname = 'merge publish',  
        @value = 'true';  
    ```  
  
3.  Creare la pubblicazione di replica, articoli e sottoscrizioni. Per ulteriori informazioni sulla configurazione della replica, vedere Pubblicazione di dati e oggetti di database.  
  
##  <a name="step2"></a> 2. Configurare il gruppo di disponibilità AlwaysOn  
 Nella replica primaria prevista creare il gruppo di disponibilità con il database pubblicato (o da pubblicare) come database membro. In caso di utilizzo della Creazione guidata Gruppo di disponibilità, è possibile consentire alla procedura guidata di sincronizzare inizialmente i database di tipo replica secondaria o eseguire manualmente l'inizializzazione mediante backup e ripristino.  
  
 Creare un listener DNS per il gruppo di disponibilità che sarà utilizzato dagli agenti di replica per connettersi alla replica primaria corrente. Il nome del listener specificato sarà utilizzato come destinazione di reindirizzamento per la coppia server di pubblicazione originale/database pubblicato. Ad esempio, se si utilizza DDL per configurare il gruppo di disponibilità, è possibile utilizzare l'esempio di codice seguente per specificare un listener per un gruppo di disponibilità esistente denominato `MyAG`:  
  
```  
ALTER AVAILABILITY GROUP 'MyAG'   
    ADD LISTENER 'MyAGListenerName' (WITH IP (('10.120.19.155', '255.255.254.0')));  
```  
  
 Per altre informazioni, vedere [Creazione e configurazione di gruppi di disponibilità &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/creation-and-configuration-of-availability-groups-sql-server.md).  
  
##  <a name="step3"></a> 3. Assicurare che tutti gli host della replica secondaria siano configurati per la replica  
 In ogni host della replica secondaria verificare che [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sia stato configurato per supportare la replica. È possibile eseguire la query seguente in ogni host della replica secondaria per determinare se la replica è installata:  
  
```  
USE master;  
GO  
DECLARE @installed int;  
EXEC @installed = sys.sp_MS_replication_installed;  
SELECT @installed;  
```  
  
 Se il parametro *@installed* è 0, è necessario aggiungere la replica all'installazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
##  <a name="step4"></a> 4. Configurare gli host della replica secondaria come server di pubblicazione di replica  
 Una replica secondaria non può essere utilizzata come server di pubblicazione o di ripubblicazione della replica, ma è necessario configurare la replica in modo che dopo un failover possa essere utilizzata la replica secondaria. Nel server di distribuzione configurare la distribuzione per ogni host della replica secondaria. Specificare lo stesso database di distribuzione e la stessa directory di lavoro specificati quando il server di pubblicazione originale è aggiunto al server di distribuzione. Se per la configurazione della distribuzione vengono usate stored procedure, eseguire **sp_adddistpublisher** per associare i server di pubblicazione remoti al server di distribuzione. Se il parametro *@login* e *@password* sono stati utilizzati per il server di pubblicazione originale, specificare gli stessi valori per ognuno quando si aggiungono host della replica secondaria come server di pubblicazione.  
  
```  
EXEC sys.sp_adddistpublisher  
    @publisher = 'AGSecondaryReplicaHost',  
    @distribution_db = 'distribution',  
    @working_directory = '\\MyReplShare\WorkingDir',  
    @login = 'MyPubLogin',  
    @password = '**Strong password for publisher**';  
```  
  
 Configurare la distribuzione per ogni host della replica secondaria. Identificare il server di distribuzione del server di pubblicazione originale come server di distribuzione remoto. Usare la password specificata quando **sp_adddistributor** è stato eseguito inizialmente nel server di distribuzione. Se per la configurazione della distribuzione vengono usate stored procedure, il parametro *@password* per **sp_adddistributor** viene usato per specificare la password.  
  
```  
EXEC sp_adddistributor   
    @distributor = 'MyDistributor',  
    @password = '**Strong password for distributor**';  
```  
  
 In ogni host della replica secondaria verificare che i Sottoscrittori push delle pubblicazioni del database vengano visualizzati come server collegati. Se per la configurazione dei server di pubblicazione remoti vengono usate stored procedure, eseguire **sp_addlinkedserver** per aggiungere i Sottoscrittori, se non già presenti, come server collegati ai server di pubblicazione.  
  
```  
EXEC sys.sp_addlinkedserver   
    @server = 'MySubscriber';  
```  
  
##  <a name="step5"></a> 5. Reindirizzare il server di pubblicazione originale al nome del listener gruppo di disponibilità  
 Nel database di distribuzione del server di distribuzione eseguire la stored procedure **sp_redirect_publisher** per associare il server di pubblicazione originale e il database pubblicato al nome del listener del gruppo di disponibilità.  
  
```  
USE distribution;  
GO  
EXEC sys.sp_redirect_publisher   
@original_publisher = 'MyPublisher',  
    @publisher_db = 'MyPublishedDB',  
    @redirected_publisher = 'MyAGListenerName';  
```  
  
##  <a name="step6"></a> 6. Eseguire la stored procedure di convalida della replica per verificare la configurazione  
 Nel database di distribuzione del server di distribuzione eseguire la stored procedure **sp_validate_replica_hosts_as_publishers** per verificare che tutti gli host della replica siano configurati come server di pubblicazione per il database pubblicato.  
  
```  
USE distribution;  
GO  
DECLARE @redirected_publisher sysname;  
EXEC sys.sp_validate_replica_hosts_as_publishers  
    @original_publisher = 'MyPublisher',  
    @publisher_db = 'MyPublishedDB',  
    @redirected_publisher = @redirected_publisher output;  
```  
  
 La stored procedure **sp_validate_replica_hosts_as_publishers** deve essere eseguita da un account di accesso con autorizzazioni sufficienti in ogni host della replica del gruppo di disponibilità per richiedere informazioni sul gruppo di disponibilità. A differenza di **sp_validate_redirected_publisher**, usa le credenziali del chiamante e non l'account di accesso incluso in msdb.dbo.MSdistpublishers per connettersi alle repliche del gruppo di disponibilità.  
  
> [!NOTE]  
>  **sp_validate_replica_hosts_as_publishers** avrà esito negativo e verrà visualizzato il messaggio di errore seguente durante la convalida degli host della replica secondaria che non consentono l'accesso in lettura o richiedono che venga specificata la finalità di lettura.  
>   
>  Msg 21899, Livello 11, Stato 1, Procedura **sp_hadr_verify_subscribers_at_publisher**, Riga 109  
>   
>  La query sul server di pubblicazione reindirizzato 'MyReplicaHostName' per determinare la presenza di voci sysserver per i sottoscrittori del server di pubblicazione originale 'MyOriginalPublisher' non è riuscita restituendo l'errore '976', messaggio di errore 'Errore 976, Livello 14, Stato 1, Messaggio: Il database di destinazione, 'MyPublishedDB', partecipa a un gruppo di disponibilità e non è attualmente accessibile per le query. Lo spostamento dei dati è sospeso o la replica di disponibilità non è abilitata per l'accesso in lettura. Per consentire l'accesso in sola lettura a questo e ad altri database nel gruppo di disponibilità, abilitare l'accesso in lettura a una o più repliche di disponibilità secondarie nel gruppo.  Per altre informazioni, vedere l'istruzione **ALTER AVAILABILITY GROUP** nella documentazione online di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
>   
>  Sono stati rilevati uno o più errori di convalida del server di pubblicazione per l'host della replica 'MyReplicaHostName'.  
  
 Tale comportamento è previsto. È necessario verificare la presenza delle voci del Sottoscrittore in questi host della replica secondaria eseguendo una query per le voci sysserver direttamente sull'host.  
  
##  <a name="step7"></a> 7. Aggiungere il server di pubblicazione originale a Monitoraggio replica  
 In ogni replica del gruppo di disponibilità aggiungere il server di pubblicazione originale a Monitoraggio replica.  
  
##  <a name="RelatedTasks"></a> Attività correlate  
 **Replica**  
  
-   [Gestione di un database di pubblicazione AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/maintaining-an-always-on-publication-database-sql-server.md)  
  
-   [Replica, Rilevamento modifiche, Change Data Capture e Gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/replicate-track-change-data-capture-always-on-availability.md)  
  
-   [Amministrazione &#40;Replica&#41;](../../../relational-databases/replication/administration/administration-replication.md)  
  
 **Per creare e configurare un gruppo di disponibilità**  
  
-   [Usare la Creazione guidata Gruppo di disponibilità &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Utilizzare la finestra di dialogo Nuovo gruppo di disponibilità &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [Creare un gruppo di disponibilità &#40;Transact-SQL&#41;](../../../database-engine/availability-groups/windows/create-an-availability-group-transact-sql.md)  
  
-   [Creare un gruppo di disponibilità &#40;PowerShell di SQL Server&#41;](../../../database-engine/availability-groups/windows/create-an-availability-group-sql-server-powershell.md)  
  
-   [Specificare l'URL dell'endpoint quando si aggiunge o si modifica una replica di disponibilità &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
-   [Creare un endpoint del mirroring del database per i gruppi di disponibilità AlwaysOn &#40;PowerShell di SQL Server&#41;](../../../database-engine/availability-groups/windows/database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [Creare un join di una replica secondaria a un gruppo di disponibilità &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [Preparare manualmente un database secondario per un gruppo di disponibilità &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [Creare un join di un database secondario a un gruppo di disponibilità &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [Creare o configurare un listener del gruppo di disponibilità &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Prerequisiti, restrizioni e raccomandazioni per i gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md)   
 [Panoramica di gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Gruppi di disponibilità AlwaysOn: interoperabilità &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/always-on-availability-groups-interoperability-sql-server.md)   
 [Replica di SQL Server](../../../relational-databases/replication/sql-server-replication.md)  
  
  

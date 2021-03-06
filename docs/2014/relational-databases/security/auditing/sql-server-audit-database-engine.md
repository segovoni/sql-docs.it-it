---
title: Controllo di SQL Server (motore di database) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: security
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- audit
helpviewer_keywords:
- SQL Server Audit
- audits [SQL Server], SQL Server Audit
ms.assetid: 0c1fca2e-f22b-4fe8-806f-c87806664f00
caps.latest.revision: 55
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: d684a808a2bb6c8c9aa23c6dce969acb933c44db
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37238781"
---
# <a name="sql-server-audit-database-engine"></a>SQL Server Audit (Database Engine)
  Il*controllo* di un'istanza del [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] o di un database individuale comporta il rilevamento e la registrazione di eventi che si verificano nel [!INCLUDE[ssDE](../../../includes/ssde-md.md)]. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Audit consente di creare controlli del server che possono contenere specifiche del controllo del server per gli eventi a livello di server e specifiche del controllo del database per gli eventi a livello di database. Gli eventi controllati possono essere scritti nei registri eventi o nei file di controllo.  
  
 Per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]sono disponibili numerosi livelli di controllo, a seconda dei requisiti legislativi o standard previsti per la propria installazione. In[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Audit sono disponibili gli strumenti e i processi necessari per abilitare, archiviare e visualizzare controlli in vari oggetti server e di database.  
  
 È possibile registrare gruppi di azioni di controllo del server per istanza e gruppi di azioni di controllo del database o azioni di controllo del database per database. L'evento di controllo si verificherà ogni volta che viene rilevata un'azione controllabile.  
  
 Tutte le edizioni dei controlli a livello server di supporto [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . I controlli a livello di database sono limitati alle edizioni Enterprise, Developer e alle copie di valutazione. Per ulteriori informazioni, vedere [Features Supported by the Editions of SQL Server 2014](../../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="sql-server-audit-components"></a>Componenti di SQL Server Audit  
 Per *controllo* si intende la combinazione di più elementi in un unico pacchetto per un gruppo specifico di azioni server o del database. Tramite la combinazione dei componenti di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Audit viene generato un output denominato controllo, così come tramite la combinazione della definizione del report con elementi grafici e dati viene generato un report.  
  
 Per creare un controllo, in[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Audit vengono usati gli *eventi estesi* . Per ulteriori informazioni sugli eventi estesi, vedere [eventi estesi](../../extended-events/extended-events.md).  
  
### <a name="sql-server-audit"></a>SQL Server Audit  
 L'oggetto *SQL Server Audit* raccoglie un'unica istanza di azioni a livello di server o di database e gruppi di azioni da monitorare. Il controllo si trova a livello dell'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Per ogni istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] è possibile disporre di più controlli.  
  
 Quando si definisce un controllo, è necessario specificare il percorso per l'output dei risultati, ovvero la destinazione del controllo. Il controllo viene creato con stato *disabilitato* e non controlla alcuna azione in modo automatico. In seguito all'abilitazione del controllo, la relativa destinazione riceve dati dal controllo stesso.  
  
### <a name="server-audit-specification"></a>Specifica controllo server  
 L'oggetto *specifica controllo server* appartiene a un controllo. È possibile creare una specifica del controllo del server per ogni controllo, poiché entrambi vengono creati nell'ambito dell'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
 Nella specifica del controllo del server vengono raccolti molti gruppi di azioni a livello di server, generati dalla funzionalità degli eventi estesi. In una specifica del controllo del server è possibile includere *gruppi di azioni di controllo* , ovvero gruppi predefiniti di azioni che rappresentano gli eventi atomici che si verificano nel [!INCLUDE[ssDE](../../../includes/ssde-md.md)]. Tali azioni vengono inviate al controllo che le registra nella destinazione.  
  
 I gruppi di azioni di controllo a livello di server sono descritti nell'argomento [Azioni e gruppi di azioni di SQL Server Audit](sql-server-audit-action-groups-and-actions.md).  
  
### <a name="database-audit-specification"></a>Specifica controllo database  
 Anche l'oggetto *specifica controllo database* appartiene a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Audit. È possibile creare una specifica del controllo del database per ogni database di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] e per ogni controllo.  
  
 Nella specifica del controllo del database vengono raccolte azioni di controllo a livello di database generate dalla funzionalità degli eventi estesi. A questa specifica è possibile aggiungere gruppi di azioni di controllo o eventi di controllo. Gli*eventi di controllo* sono le azioni atomiche che possono essere controllate dal motore di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , mentre i*gruppi di azioni di controllo* sono gruppi predefiniti di azioni. Sia gli eventi di controllo che i gruppi di azioni si trovano nell'ambito del database di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Tali azioni vengono inviate al controllo che le registra nella destinazione. In una specifica del controllo di un database utente non includere oggetti con ambito server, ad esempio viste di sistema.  
  
 I gruppi di azioni di controllo a livello di database e le azioni di controllo sono descritti nell'argomento [Azioni e gruppi di azioni di SQL Server Audit](sql-server-audit-action-groups-and-actions.md).  
  
### <a name="target"></a>Destinazione  
 I risultati di un controllo vengono inviati a una destinazione, che può essere un file, il registro eventi di sicurezza o il registro eventi applicazioni di Windows. È necessario esaminare e archiviare periodicamente tali registri per garantire che nella destinazione sia disponibile spazio sufficiente per scrivere record aggiuntivi.  
  
> [!IMPORTANT]  
>  Qualsiasi utente autenticato può leggere e scrivere nel registro eventi applicazioni di Windows, per cui sono necessarie autorizzazioni inferiori rispetto al registro eventi di sicurezza di Windows e risulta pertanto meno sicuro di quest'ultimo.  
  
 Per scrivere nel registro eventi di sicurezza di Windows, è necessario che l'account di servizio di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] venga aggiunto ai criteri **Generazione controlli di sicurezza** . Per impostazione predefinita, gli account di sistema locale, Servizio Locale e Servizio di rete appartengono a tali criteri. Questa impostazione può essere configurata tramite lo snap-in dei criteri di sicurezza (secpol.msc) È inoltre necessario che i criteri di sicurezza **Controlla accesso agli oggetti** siano abilitati sia per **Esito positivo** che per **Esito negativo**. Questa impostazione può essere configurata tramite lo snap-in dei criteri di sicurezza (secpol.msc) Nelle [!INCLUDE[wiprlhext](../../../includes/wiprlhext-md.md)] o Windows Server 2008, è possibile impostare più granulare **applicazione generata** criterio dalla riga di comando usando il programma criteri di controllo (`AuditPol.exe)`. Per altre informazioni sulla procedura per abilitare la scrittura nel registro di protezione di Windows, vedere [Scrittura di eventi di controllo di SQL Server nel registro di sicurezza](write-sql-server-audit-events-to-the-security-log.md). Per ulteriori informazioni sul programma Auditpol.exe, vedere l'articolo 921469 della Microsoft Knowledge Base, [Utilizzo dei Criteri di gruppo per configurare impostazioni di controllo della sicurezza dettagliate](http://support.microsoft.com/kb/921469/). I registri eventi di Windows sono globali nel sistema operativo Windows. Per ulteriori informazioni sui registri eventi di Windows, vedere la pagina relativa ai [cenni preliminari sul Visualizzatore eventi](http://go.microsoft.com/fwlink/?LinkId=101455). Se sono necessarie autorizzazioni più specifiche sul controllo, utilizzare la destinazione del file binario.  
  
 Quando si salvano informazioni di controllo in un file, per contribuire a impedirne l'alterazione, è possibile limitare l'accesso al percorso del file nei modi seguenti:  
  
-   L'account del servizio [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] deve disporre dell'autorizzazione in lettura e in scrittura.  
  
-   Gli amministratori di controllo richiedono in genere l'autorizzazione in lettura e in scrittura. Ciò presuppone che gli amministratori di controllo siano account di Windows per quanto riguarda l'amministrazione dei file di controllo, ad esempio per la copia in diverse condivisioni, per il backup e così via.  
  
-   I lettori di controllo autorizzati a leggere i file di controllo devono disporre dell'autorizzazione in lettura.  
  
 Se dispongono dell'autorizzazione, gli altri utenti di Windows possono leggere il file di controllo anche quando si verifica un'operazione di scrittura in un file da parte del [!INCLUDE[ssDE](../../../includes/ssde-md.md)] . [!INCLUDE[ssDE](../../../includes/ssde-md.md)] non accetta un blocco esclusivo che impedisce le operazioni di lettura.  
  
 Poiché [!INCLUDE[ssDE](../../../includes/ssde-md.md)] può accedere al file, gli accessi [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] che dispongono dell'autorizzazione CONTROL SERVER possono utilizzare [!INCLUDE[ssDE](../../../includes/ssde-md.md)] per accedere ai file di controllo. Per registrare un utente che sta leggendo il file di controllo, definire un controllo in master.sys.fn_get_audit_file. In tal modo viene registrato l'accesso al file di controllo tramite [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]effettuato dagli account di accesso dotati dell'autorizzazione CONTROL SERVER.  
  
 Se un amministratore di controllo copia il file in un percorso diverso (ad esempio, per scopi di archiviazione e così via), gli ACL sul nuovo percorso devono avere solo le autorizzazioni seguenti:  
  
-   Amministratore di controllo: lettura/scrittura  
  
-   Lettore di controllo: lettura  
  
 Si consiglia di generare i report di controllo da un'istanza separata di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], ad esempio un'istanza di [!INCLUDE[ssExpress](../../../includes/ssexpress-md.md)]a cui hanno accesso solo gli amministratori di controllo o i lettori di controllo. Utilizzando un'istanza di [!INCLUDE[ssDE](../../../includes/ssde-md.md)] separata per la segnalazione, è possibile evitare che utenti non autorizzati abbiano accesso al record di controllo.  
  
 È possibile offrire protezione aggiuntiva contro l'accesso non autorizzato crittografando la cartella in cui viene archiviato il file di controllo tramite la crittografia unità BitLocker di Windows o Encrypting File System di Windows.  
  
 Per ulteriori informazioni sui record di controllo scritti nella destinazione, vedere [SQL Server Audit Records](sql-server-audit-records.md).  
  
## <a name="overview-of-using-sql-server-audit"></a>Panoramica sull'utilizzo di SQL Server Audit  
 Per definire un controllo, è possibile utilizzare [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../../includes/tsql-md.md)] . In seguito alla creazione e all'abilitazione del controllo, la destinazione riceverà le voci.  
  
 L'utilità **Visualizzatore eventi** disponibile in Windows consente di leggere i registri eventi di Windows. Per le destinazioni file, è possibile usare il **Visualizzatore file di log** in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] o la funzione [fn_get_audit_file](/sql/relational-databases/system-functions/sys-fn-get-audit-file-transact-sql) per leggere il file di destinazione.  
  
 Di seguito viene descritto il processo generale di creazione e utilizzo di un controllo.  
  
1.  Creare un controllo e definire la destinazione.  
  
2.  Creare una specifica del controllo del server o una specifica del controllo del database che esegue il mapping al controllo. Abilitare la specifica del controllo.  
  
3.  Abilitare il controllo.  
  
4.  Leggere gli eventi di controllo tramite il **Visualizzatore eventi**di Windows, il **Visualizzatore file di log**o la funzione fn_get_audit_file.  
  
 Per ulteriori informazioni, vedere [Create a Server Audit and Server Audit Specification](create-a-server-audit-and-server-audit-specification.md) e [Create a Server Audit and Database Audit Specification](create-a-server-audit-and-database-audit-specification.md).  
  
## <a name="considerations"></a>Considerazioni  
 Se durante la fase iniziale del controllo si verifica un errore, il server non si avvierà. In questo caso, per avviare il server è possibile usare l'opzione **-f** della riga di comando.  
  
 Se in seguito a un errore a livello del controllo il server si arresta o non si avvia perché per il controllo è specificata l'impostazione ON_FAILURE=SHUTDOWN, l'evento MSG_AUDIT_FORCED_SHUTDOWN verrà scritto nel registro. Poiché l'arresto si verificherà quando questa impostazione viene incontrata la prima volta, l'evento verrà scritto solo una volta. Tale evento viene scritto dopo il messaggio di errore relativo al controllo che provoca l'arresto. Per ignorare l'arresto provocato dal controllo, un amministratore può avviare [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in modalità utente singolo usando il flag **–m** . Se l'avvio viene eseguito in modalità utente singolo, verrà effettuato il downgrade di qualsiasi controllo per la cui sessione è specificata l'esecuzione di ON_FAILURE=SHUTDOWN come ON_FAILURE=CONTINUE. Se [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] viene avviato tramite il flag **–m** , nel log degli errori verrà scritto il messaggio MSG_AUDIT_SHUTDOWN_BYPASSED.  
  
 Per altre informazioni sulle opzioni di avvio del servizio, vedere [Opzioni di avvio del servizio del motore di database](../../../database-engine/configure-windows/database-engine-service-startup-options.md).  
  
### <a name="attaching-a-database-with-an-audit-defined"></a>Collegamento di un database con un controllo definito  
 Il collegamento di un database che dispone di una specifica del controllo e per cui è specificato un GUID che non esiste nel server provocherà una specifica del controllo *orfana* . Poiché nell'istanza del server non esiste un controllo con GUID corrispondente, non verrà registrato alcun evento di controllo. Per risolvere questo problema, utilizzare il comando ALTER DATABASE AUDIT SPECIFICATION per connettere la specifica del controllo orfana a un controllo del server esistente oppure utilizzare il comando CREATE SERVER AUDIT per creare un nuovo controllo del server con il GUID specificato.  
  
 È possibile collegare un database per cui è definita una specifica di controllo a un'altra edizione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] che non supporta [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Audit, ad esempio [!INCLUDE[ssExpress](../../../includes/ssexpress-md.md)] , ma gli eventi di controllo non verranno registrati.  
  
### <a name="database-mirroring-and-sql-server-audit"></a>Mirroring del database e SQL Server Audit  
 Un database che dispone di una specifica del controllo del database definita e che utilizza il mirroring del database includerà la specifica del controllo del database. Per funzionare correttamente sull'istanza SQL Server con mirroring, è necessario che siano configurati gli elementi seguenti:  
  
-   Il server mirror deve disporre di un controllo con lo stesso GUID per consentire alla specifica del controllo del database di scrivere i record di controllo. Questa impostazione può essere configurata usando il comando CREATE AUDIT WITH GUID`=`*\<GUID controllo del Server di origine*>.  
  
-   Per le destinazioni del file binario, l'account di servizio del server mirror deve disporre delle autorizzazioni appropriate per il percorso in cui verrà scritto l'itinerario di controllo.  
  
-   Per le destinazioni del registro eventi di Windows, i criteri di sicurezza nel computer in cui si trova il server mirror devono consentire all'account di servizio di accedere al registro eventi applicazioni o di sicurezza.  
  
### <a name="auditing-administrators"></a>Controllo degli amministratori  
 I membri del `sysadmin` ruolo predefinito del server vengono identificati come i **dbo** utente in ogni database. Per controllare le azioni degli amministratori, controllare le azioni dell'utente **dbo** .  
  
## <a name="creating-and-managing-audits-with-transact-sql"></a>Creazione e gestione di controlli con Transact-SQL  
 È possibile utilizzare istruzioni DDL, DMV e funzioni, nonché viste del catalogo per implementare tutti gli aspetti di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Audit.  
  
### <a name="data-definition-language-statements"></a>Istruzioni DDL (Data Definition Language)  
 Per creare, modificare ed eliminare specifiche del controllo, è possibile utilizzare le istruzioni DDL seguenti:  
  
|||  
|-|-|  
|[ALTER AUTHORIZATION](/sql/t-sql/statements/alter-authorization-transact-sql)|[CREATE SERVER AUDIT](/sql/t-sql/statements/create-server-audit-transact-sql)|  
|[ALTER DATABASE AUDIT SPECIFICATION](/sql/t-sql/statements/alter-database-audit-specification-transact-sql)|[CREATE SERVER AUDIT SPECIFICATION](/sql/t-sql/statements/create-server-audit-specification-transact-sql)|  
|[ALTER SERVER AUDIT](/sql/t-sql/statements/alter-server-audit-specification-transact-sql)|[DROP DATABASE AUDIT SPECIFICATION](/sql/t-sql/statements/drop-database-encryption-key-transact-sql)|  
|[ALTER SERVER AUDIT SPECIFICATION](/sql/t-sql/statements/alter-server-audit-transact-sql)|[DROP SERVER AUDIT](/sql/t-sql/statements/drop-server-audit-transact-sql)|  
|[CREATE DATABASE AUDIT SPECIFICATION](/sql/t-sql/statements/create-database-audit-specification-transact-sql)|[DROP SERVER AUDIT SPECIFICATION](/sql/t-sql/statements/drop-server-audit-specification-transact-sql)|  
  
### <a name="dynamic-views-and-functions"></a>Viste e funzioni dinamiche  
 Nella tabella seguente vengono elencate le viste e le funzioni dinamiche che è possibile utilizzare per il controllo di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
|Viste e funzioni dinamiche|Description|  
|---------------------------------|-----------------|  
|[sys.dm_audit_actions](/sql/relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql)|Restituisce una riga per ogni azione di controllo che può essere segnalata nel log di controllo e per ogni gruppo di azioni di controllo che possono essere configurate come parte di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Audit.|  
|[sys.dm_server_audit_status](/sql/relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql)|Fornisce informazioni sullo stato corrente del controllo.|  
|[sys.dm_audit_class_type_map](/sql/relational-databases/system-dynamic-management-views/sys-dm-audit-class-type-map-transact-sql)|Restituisce una tabella che esegue il mapping del campo class_type nel log di controllo al campo class_desc in sys.dm_audit_actions.|  
|[fn_get_audit_file](/sql/relational-databases/system-functions/sys-fn-get-audit-file-transact-sql)|Restituisce informazioni da un file di controllo creato da un controllo del server.|  
  
### <a name="catalog-views"></a>Viste del catalogo  
 Nella tabella seguente vengono elencate le viste del catalogo che è possibile utilizzare per il controllo di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
|Viste del catalogo|Description|  
|-------------------|-----------------|  
|[sys.database_ audit_specifications](/sql/relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql)|Contiene informazioni sulle specifiche del controllo del database in un controllo di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in un'istanza del server.|  
|[sys.database_audit_specification_details](/sql/relational-databases/system-catalog-views/sys-database-audit-specification-details-transact-sql)|Contiene informazioni sulle specifiche del controllo del database in un controllo di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in un'istanza del server per tutti i database.|  
|[sys.server_audits](/sql/relational-databases/system-catalog-views/sys-server-audits-transact-sql)|Contiene una riga per ogni controllo di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in un'istanza del server.|  
|[sys.server_audit_specifications](/sql/relational-databases/system-catalog-views/sys-server-audit-specifications-transact-sql)|Contiene informazioni sulle specifiche del controllo del server in un controllo di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in un'istanza del server.|  
|[sys.server_audit_specifications_details](/sql/relational-databases/system-catalog-views/sys-server-audit-specification-details-transact-sql)|Contiene informazioni sui dettagli (azioni) delle specifiche del controllo del server in un controllo di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in un'istanza del server.|  
|[sys.server_file_audits](/sql/relational-databases/system-catalog-views/sys-server-file-audits-transact-sql)|Contiene informazioni estese sul tipo di controllo dei file in un controllo di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in un'istanza del server.|  
  
## <a name="permissions"></a>Autorizzazioni  
 A ogni funzionalità e comando per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Audit sono associati requisiti di autorizzazione singoli.  
  
 Per creare, modificare o eliminare un controllo del server o una specifica del controllo del server, le entità server devono disporre dell'autorizzazione ALTER ANY SERVER AUDIT o CONTROL SERVER. Per creare, modificare o eliminare una specifica del controllo del database, le entità di database devono disporre dell'autorizzazione ALTER ANY DATABASE AUDIT o dell'autorizzazione ALTER o CONTROL per il database. Le entità devono inoltre disporre dell'autorizzazione necessaria per connettersi al database o dell'autorizzazione ALTER ANY SERVER AUDIT o CONTROL SERVER.  
  
 Se non specificato diversamente, per visualizzare le viste del catalogo un'entità deve disporre di uno degli elementi seguenti:  
  
-   Appartenenza al ruolo predefinito del server sysadmin.  
  
-   Autorizzazione CONTROL SERVER.  
  
-   Autorizzazione VIEW SERVER STATE.  
  
-   Autorizzazione ALTER ANY AUDIT.  
  
-   Autorizzazione VIEW AUDIT STATE, che concede all'entità solo l'accesso alla vista del catalogo sys.server_audits.  
  
 Per utilizzare le viste a gestione dinamica, un'entità deve disporre dell'autorizzazione VIEW SERVER STATE o ALTER ANY AUDIT.  
  
 Per altre informazioni su come concedere diritti e autorizzazioni, vedere [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql).  
  
> [!CAUTION]  
>  Le entità nel ruolo sysadmin possono alterare qualsiasi componente del controllo, mentre quelle nel ruolo db_owner possono alterare le specifiche del controllo in un database. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Audit convaliderà una situazione in cui un accesso che crea o modifica una specifica del controllo dispone almeno dell'autorizzazione ALTER ANY DATABASE AUDIT, ma non esegue alcuna convalida quando si collega un database. È necessario presupporre che tutte le specifiche del controllo del database siano attendibile come le entità nel ruolo sysadmin o db_owner.  
  
## <a name="related-tasks"></a>Related Tasks  
 [Creazione di un controllo del server e di una specifica del controllo del server](create-a-server-audit-and-server-audit-specification.md)  
  
 [Creazione di un controllo del server e di una specifica del controllo del database](create-a-server-audit-and-database-audit-specification.md)  
  
 [Visualizzazione di un log di controllo di SQL Server](view-a-sql-server-audit-log.md)  
  
 [Scrittura di eventi di controllo di SQL Server nel registro di sicurezza](write-sql-server-audit-events-to-the-security-log.md)  
  
## <a name="topics-closely-related-to-auditing"></a>Argomenti strettamente correlati al controllo  
 [Proprietà server &#40;pagina Sicurezza&#41;](../../../database-engine/configure-windows/server-properties-security-page.md)  
 Viene illustrato come attivare il controllo degli account di accesso per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. I record di controllo vengono archiviati nel registro applicazioni di Windows.  
  
 [Opzione di configurazione del server c2 audit mode](../../../database-engine/configure-windows/c2-audit-mode-server-configuration-option.md)  
 Viene illustrata la modalità di controllo conforme alla sicurezza C2 in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Categoria di eventi Security Audit &#40;SQL Server Profiler&#41;](../../../relational-databases/event-classes/security-audit-event-category-sql-server-profiler.md)  
 Vengono illustrati gli eventi di controllo che è possibile utilizzare in [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)]. Per altre informazioni, vedere [SQL Server Profiler](../../../tools/sql-server-profiler/sql-server-profiler.md).  
  
 [Traccia SQL](../../sql-trace/sql-trace.md)  
 Illustrate le modalità di uso di Traccia SQL all'interno di applicazioni personalizzate per creare tracce manualmente anziché tramite [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Profiler.  
  
 [Trigger DDL](../../triggers/ddl-triggers.md)  
 Vengono illustrate le modalità di utilizzo di trigger DDL (Data Definition Language) per tenere traccia delle modifiche apportate ai database.  
  
 [Microsoft TechNet: SQL Server TechCenter: Sicurezza e protezione di SQL Server 2005](http://go.microsoft.com/fwlink/?LinkId=101152)  
 Fornisce informazioni aggiornate sulla sicurezza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>Vedere anche  
 [Azioni e gruppi di azioni di SQL Server Audit](sql-server-audit-action-groups-and-actions.md)   
 [Record di SQL Server Audit](sql-server-audit-records.md)  
  
  

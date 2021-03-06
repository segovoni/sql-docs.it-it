---
title: Modello di sicurezza dell'agente di replica | Microsoft Docs
ms.custom: ''
ms.date: 04/26/2018
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Snapshot Agent, security
- agents [SQL Server replication], security
- Distribution Agent, security
- logins [SQL Server replication], permissions for agents
- security [SQL Server replication], agent security model
- Log Reader Agent, security
- Queue Reader Agent, security
- Merge Agent, security
- replication [SQL Server], agents and profiles
ms.assetid: 6d09fc8d-843a-4a7a-9812-f093d99d8192
caps.latest.revision: 72
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4ec5d963309568078b0fa942c8285f7189e7e7eb
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37358363"
---
# <a name="replication-agent-security-model"></a>Modello di sicurezza dell'agente di replica
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Il modello di sicurezza dell'agente di replica consente un controllo accurato degli account utilizzati per l'esecuzione e le connessioni degli agenti. È possibile specificare un account diverso per ogni agente. Per altre informazioni su come specificare gli account, vedere [Gestire gli account di accesso e le password nella replica](../../../relational-databases/replication/security/manage-logins-and-passwords-in-replication.md).  
  
> [!IMPORTANT]  
>  Quando un membro del ruolo predefinito del server **sysadmin** configura la replica, è possibile configurare gli agenti di replica in modo che rappresentino l'account di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent. A tale scopo è necessario non specificare un account di accesso e una password per un agente di replica. Si tratta comunque di un approccio non consigliato. Ai fini della sicurezza, è consigliabile invece specificare un account per ogni agente dotato delle autorizzazioni minime descritte nella sezione "Autorizzazioni richieste per gli agenti" più avanti in questo argomento.  
  
 Gli agenti di replica, come tutti i file eseguibili, vengono eseguiti nel contesto di un account di Windows. Utilizzano tale account per le connessioni con sicurezza integrata di Windows. L'account con il quale viene eseguito l'agente dipende dalla modalità di avvio di quest'ultimo:  
  
-   Avvio dell'agente da un processo predefinito di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent: quando si utilizza un processo di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent per avviare un agente di replica, l'agente viene eseguito nel contesto di un account specificato al momento della configurazione della replica. Per ulteriori informazioni su [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent e la replica, vedere la sezione "Sicurezza agente in SQL Server Agent" più avanti in questo argomento. Per altre informazioni sulle autorizzazioni necessarie per l'account usato per l'esecuzione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent, vedere [Configurare SQL Server Agent](http://msdn.microsoft.com/library/2e361a62-9e92-4fcd-80d7-d6960f127900).  
  
-   Avvio dell'agente da una riga dei comandi MS-DOS, direttamente o tramite uno script: l'agente viene eseguito nel contesto dell'account dell'utente che esegue l'agente dalla riga di comando.  
  
-   Avvio dell'agente da un'applicazione che utilizza oggetti RMO (Replication Management Objects) o un controllo ActiveX: l'agente viene eseguito nel contesto dell'applicazione che chiama gli oggetti RMO o il controllo ActiveX.  
  
    > [!NOTE]  
    >  I controlli ActiveX sono deprecati.  
  
 È consigliabile stabilire le connessioni nel contesto della sicurezza integrata di Windows. Per motivi di compatibilità con le versioni precedenti, è anche possibile utilizzare la sicurezza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Per ulteriori informazioni sulle procedure consigliate, vedere [Replication Security Best Practices](../../../relational-databases/replication/security/replication-security-best-practices.md).  
  
## <a name="permissions-that-are-required-by-agents"></a>Autorizzazioni richieste per gli agenti  
 Gli account utilizzati per l'esecuzione e le connessioni degli agenti richiedono varie autorizzazioni. Tali autorizzazioni sono descritte nella tabella seguente. È consigliabile eseguire ogni agente con un account di Windows differente e assegnare all'account solo le autorizzazioni necessarie. Per informazioni sull'elenco di accesso alla pubblicazione, rilevante per numerosi agenti, vedere [Proteggere il server di pubblicazione](../../../relational-databases/replication/security/secure-the-publisher.md).  
  
> [!NOTE]  
>  Controllo account utente in alcuni sistemi operativi Windows può impedire l'accesso amministrativo alla condivisione snapshot. Le autorizzazioni per la condivisione snapshot devono pertanto essere concesse in modo esplicito agli account di Windows utilizzati dall'agente snapshot, dall'agente di distribuzione e dall'agente di merge. È necessario eseguire questa operazione anche se gli account di Windows sono membri del gruppo Administrators. Per altre informazioni, vedere [Proteggere la cartella snapshot](../../../relational-databases/replication/security/secure-the-snapshot-folder.md).  
  
|Agent|Autorizzazioni|  
|-----------|-----------------|  
|agente snapshot|L'account di Windows con cui viene eseguito l'agente viene utilizzato per le connessioni al server di distribuzione. Tale account deve:<br /><br /> - Essere almeno un membro del ruolo predefinito del database **db_owner** nel database di distribuzione.<br /><br /> - Avere le autorizzazioni di lettura, scrittura e modifica per la condivisione snapshot.<br /><br /> <br /><br /> Tenere presente che l'account usato per la *connessione* al server di pubblicazione deve essere almeno membro del ruolo predefinito del database **db_owner** nel database di pubblicazione.|  
|Agente di lettura log|L'account di Windows con cui viene eseguito l'agente viene utilizzato per le connessioni al server di distribuzione. Tale account deve essere almeno membro del ruolo predefinito del database **db_owner** nel database di distribuzione.<br /><br /> L'account utilizzato per la connessione al server di pubblicazione deve essere almeno membro del ruolo predefinito del database **db_owner** nel database di pubblicazione.<br /><br /> In caso di selezione delle opzioni **sync_type** , i parametri *replication support only*, *initialize with backup*o *initialize from lsn*e l'agente di lettura log devono essere in esecuzione dopo aver eseguito **sp_addsubscription**, in modo che gli script impostati vengano scritti nel database di distribuzione. L'agente di lettura log deve essere in esecuzione con un account membro del ruolo predefinito del server **sysadmin** . Quando l'opzione **sync_type** è impostata su *Automatic*, non sono richieste azioni dell'agente di lettura log speciali.|  
|Agente di distribuzione per una sottoscrizione push|L'account di Windows con cui viene eseguito l'agente viene utilizzato per le connessioni al server di distribuzione. Tale account deve:<br /><br /> - Essere almeno un membro del ruolo predefinito del database **db_owner** nel database di distribuzione.<br /><br /> - Essere un membro dell'elenco di accesso alla pubblicazione.<br /><br /> - Avere le autorizzazioni di lettura per la condivisione snapshot.<br /><br /> - Avere le autorizzazioni di lettura per la directory di installazione del provider OLE DB per il Sottoscrittore se la sottoscrizione riguarda un Sottoscrittore non SQL Server.<br /><br /> - Quando si esegue la replica dei dati line-of-business, l'agente di distribuzione deve avere le autorizzazioni di scrittura per la replica **C:\Programmi\Microsoft SQL Server\XX\COMfolder** dove XX rappresenta l'ID istanza.<br /><br /> <br /><br /> Si noti che l'account usato per la *connessione* al Sottoscrittore deve essere almeno membro del ruolo predefinito del database **db_owner** nel database di sottoscrizione o avere autorizzazioni equivalenti se la sottoscrizione riguarda un Sottoscrittore non SQL Server.<br /><br /> Si noti anche che quando si usa `-subscriptionstreams >= 2` sull'agente di distribuzione è necessario concedere anche l'autorizzazione **View Server State** per i sottoscrittori per rilevare i deadlock.|  
|Agente di distribuzione per una sottoscrizione pull|L'account di Windows con cui viene eseguito l'agente viene utilizzato per le connessioni al Sottoscrittore. Tale account deve essere almeno membro del ruolo predefinito del database **db_owner** nel database di sottoscrizione. L'account utilizzato per la connessione al server di distribuzione deve:<br /><br /> - Essere un membro dell'elenco di accesso alla pubblicazione.<br /><br /> - Avere le autorizzazioni di lettura per la condivisione snapshot.<br /><br /> - Quando si esegue la replica dei dati line-of-business, l'agente di distribuzione deve avere le autorizzazioni di scrittura per la replica **C:\Programmi\Microsoft SQL Server\XX\COMfolder** dove XX rappresenta l'ID istanza.<br /><br /> <br /><br /> Si noti che quando si usa `-subscriptionstreams >= 2` sull'agente di distribuzione è necessario concedere anche l'autorizzazione **View Server State** per i sottoscrittori per rilevare i deadlock.|  
|Agente di merge per una sottoscrizione push|L'account di Windows con cui viene eseguito l'agente viene utilizzato per le connessioni al server di pubblicazione e al server di distribuzione. Tale account deve:<br /><br /> - Essere almeno un membro del ruolo predefinito del database **db_owner** nel database di distribuzione.<br /><br /> - Essere un membro dell'elenco di accesso alla pubblicazione.<br /><br /> - Essere un account di accesso associato a un utente con autorizzazioni di lettura/scrittura nel database di pubblicazione.<br /><br /> - Avere le autorizzazioni di lettura per la condivisione snapshot.<br /><br /> <br /><br /> Si noti che l'account usato per la *connessione* al Sottoscrittore deve essere almeno membro del ruolo predefinito del database **db_owner** nel database di sottoscrizione.|  
|Agente di merge per una sottoscrizione pull|L'account di Windows con cui viene eseguito l'agente viene utilizzato per le connessioni al Sottoscrittore. Tale account deve essere almeno membro del ruolo predefinito del database **db_owner** nel database di sottoscrizione. L'account utilizzato per la connessione al server di pubblicazione e al server di distribuzione deve:<br /><br /> - Essere un membro dell'elenco di accesso alla pubblicazione.<br /><br /> - Essere un account di accesso associato a un utente con autorizzazioni di lettura/scrittura nel database di pubblicazione.<br /><br /> - Essere un account di accesso associato a un utente nel database di distribuzione. L'utente può essere l'utente **Guest** .<br /><br /> - Avere le autorizzazioni di lettura per la condivisione snapshot.|  
|Agente di lettura coda|L'account di Windows con cui viene eseguito l'agente viene utilizzato per le connessioni al server di distribuzione. Tale account deve essere almeno membro del ruolo predefinito del database **db_owner** nel database di distribuzione.<br /><br /> L'account utilizzato per la connessione al server di pubblicazione deve essere almeno membro del ruolo predefinito del database **db_owner** nel database di pubblicazione.<br /><br /> L'account utilizzato per la connessione al Sottoscrittore deve essere almeno membro del ruolo predefinito del database **db_owner** nel database di sottoscrizione.|  
  
## <a name="agent-security-under-sql-server-agent"></a>Sicurezza agente in SQL Server Agent  
 Quando si configura la replica mediante [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], le procedure [!INCLUDE[tsql](../../../includes/tsql-md.md)] o gli oggetti RMO, per impostazione predefinita viene creato un processo di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent per ogni agente. Gli agenti vengono quindi eseguiti nel contesto di un passaggio del processo, indipendentemente dal fatto che l'esecuzione sia continua, in base a una pianificazione o su richiesta. È possibile visualizzare tali processi nella cartella **Processi** in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]. Nella tabella seguente sono elencati i nomi dei processi.  
  
|Agente|Nome processo|  
|-----------|--------------|  
|agente snapshot|**\<ServerPubblicazione>-\<DatabasePubblicazione>-\<ServerPubblicazione>-\<intero>**|  
|Agente snapshot per una partizione di una pubblicazione di tipo merge|**Dyn_\<ServerPubblicazione>-\<DatabasePubblicazione>-\<Pubblicazione>-\<GUID>**|  
|Agente di lettura log|**\<ServerPubblicazione>-\<DatabasePubblicazione>-\<intero>**|  
|Agente di merge per le sottoscrizioni pull|**\<ServerPubblicazione>-\<DatabasePubblicazione>-\<Pubblicazione>-\<Sottoscrittore>-\<DatabaseSottoscrizione>-\<intero>**|  
|Agente di merge per le sottoscrizioni push|**\<ServerPubblicazione>-\<DatabasePubblicazione>-\<Pubblicazione>-\<Sottoscrittore>-\<intero>**|  
|Agente di distribuzione per le sottoscrizioni push|**\<ServerPubblicazione>-\<DatabasePubblicazione>-\<Pubblicazione>-\<Sottoscrittore>-\<intero>***|  
|Agente di distribuzione per le sottoscrizioni pull|**\<ServerPubblicazione>-\<DatabasePubblicazione>-\<Pubblicazione>-\<Sottoscrittore>-\<DatabaseSottoscrizione>-\<GUID>***\*|  
|Agente di distribuzione per le sottoscrizioni push di Sottoscrittori non SQL Server|**\<ServerPubblicazione>-\<DatabasePubblicazione>-\<Pubblicazione>-\<Sottoscrittore>-\<intero>**|  
|Agente di lettura coda|**[\<DatabaseDistribuzione>].\<intero>**|  
  
 \*Per le sottoscrizioni push a pubblicazioni Oracle, il nome del processo è **\<ServerPubblicazione>-\<ServerPubblicazione**> anziché **\<ServerPubblicazione>-\<DatabasePubblicazione>**.  
  
 \*\*Per le sottoscrizioni pull a pubblicazioni Oracle, il nome del processo è **\<ServerPubblicazione>-\<DatabaseDistribuzione**> anziché **\<ServerPubblicazione>-\<DatabasePubblicazione>**.  
  
 Durante la configurazione della replica si specificano gli account utilizzati per l'esecuzione degli agenti. Tutti i passaggi del processo, tuttavia, vengono eseguiti nel contesto di sicurezza di un *proxy*e pertanto la replica esegue internamente i mapping seguenti per gli account dell'agente specificati:  
  
-   Viene innanzitutto eseguito il mapping tra l'account e una credenziale utilizzando l'istruzione [!INCLUDE[tsql](../../../includes/tsql-md.md)] [CREATE CREDENTIAL](../../../t-sql/statements/create-credential-transact-sql.md) statement. I proxy di[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent utilizzano le credenziali per archiviare le informazioni sugli account utente di Windows.  
  
-   Viene chiamata la stored procedure [sp_add_proxy](../../../relational-databases/system-stored-procedures/sp-add-proxy-transact-sql.md) e le credenziali vengono utilizzate per creare un proxy.  
  
> [!NOTE]  
>  Queste informazioni vengono fornite allo scopo di illustrare i processi richiesti per l'esecuzione degli agenti nel contesto di sicurezza appropriato. Non è in genere necessario interagire direttamente con le credenziali o i proxy creati.  
  
## <a name="see-also"></a>Vedere anche  
 [Replication Security Best Practices](../../../relational-databases/replication/security/replication-security-best-practices.md)   
 [Sicurezza e protezione &#40;replica&#41;](../../../relational-databases/replication/security/security-and-protection-replication.md)   
 [Proteggere la cartella snapshot](../../../relational-databases/replication/security/secure-the-snapshot-folder.md)  
  
  

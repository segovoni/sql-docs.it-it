---
title: Gestire un'applicazione di servizio SharePoint di Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: bfda2e04-2d82-4534-bb50-90925f7386ae
caps.latest.revision: 15
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 6539627f9b1fc5fc41b9cc535efd5cb4c5949ecc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37153872"
---
# <a name="manage-a-reporting-services-sharepoint-service-application"></a>Gestire un'applicazione di servizio SharePoint di Reporting Services
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Le applicazioni di servizio vengono gestite da Amministrazione centrale SharePoint. Le pagine Gestione e Proprietà consentono di aggiornare la configurazione dell'applicazione di servizio e le attività di amministrazione comuni.  
  
 In questo argomento vengono illustrate le informazioni seguenti:  
  
-   [Per aprire le pagine di gestione delle applicazioni di servizio](#bkmk_openpages)  
  
-   [Pagina Impostazioni sistema](#bkmk_systemsettings)  
  
-   [Gestione processi](#bkmk_managejobs)  
  
-   [Gestione chiavi](#bkmk_keymgt)  
  
-   [Account di esecuzione](#bkmk_executionaccount)  
  
-   [Impostazioni posta elettronica](#bkmk_email)  
  
-   [Avvisi e sottoscrizioni provisioning](#bkmk_provisionsubscriptions)  
  
## <a name="to-open-service-application-properties-page"></a>Per aprire la pagina delle proprietà delle applicazioni di servizio  
 Per aprire la pagina delle proprietà di un'applicazione di servizio [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], completare le azioni seguenti:  
  
1.  Nel gruppo Gestione applicazioni di Amministrazione centrale fare clic su **Gestisci applicazioni di servizio**.  
  
2.  Fare clic accanto al nome dell'applicazione di servizio oppure sulla colonna **Tipo** per selezionare l'intera riga, quindi fare clic su **Proprietà** sulla barra multifunzione di SharePoint.  
  
 Per altre informazioni sulle proprietà dell'applicazione di servizio, vedere [Step 3: Create a Reporting Services Service Application](../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md#bkmk_create_serrviceapplication).  
  
##  <a name="bkmk_openpages"></a> Per aprire le pagine di gestione delle applicazioni di servizio  
 Per aprire le pagine di gestione di un'applicazione di servizio [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , completare le azioni seguenti:  
  
1.  Nel gruppo Gestione applicazioni di Amministrazione centrale fare clic su **Gestisci applicazioni di servizio**.  
  
2.  Fare clic sul nome dell'applicazione di servizio per visualizzare la pagina **Gestione applicazione di Reporting Services** .  
  
3.  In alternativa, è possibile fare clic accanto al nome oppure sulla colonna **Tipo** per l'applicazione di servizio in modo da selezionare l'intera riga, quindi fare clic su **Gestisci** sulla barra multifunzione di SharePoint.  
  
##  <a name="bkmk_systemsettings"></a> Pagina Impostazioni sistema  
 La pagina Impostazioni sistema consente di configurare il comportamento e l'esperienza utente dell'applicazione di servizio, inclusi diversi timeout.  
  
-   [Impostazioni report](#bkmk_report_settings_section)  
  
-   [Impostazioni sessione](#bkmk_session_settings_section)  
  
-   [Impostazioni di sistema per la registrazione](#bkmk_logging_settings_section)  
  
-   [Impostazioni di sicurezza](#bkmk_security_settings_section)  
  
-   [Impostazioni del client](#bkmk_client_settings_section)  
  
###  <a name="bkmk_report_settings_section"></a> Impostazioni report  
  
|Impostazione|Commenti|  
|-------------|--------------|  
|Timeout immagini esterne|Il valore predefinito è 600 secondi.|  
|Compressione snapshot|Il valore predefinito è SQL.|  
|Timeout report di sistema|Il valore predefinito è 1800 secondi.<br /><br /> Consente di specificare se si desidera impostare un timeout per l'elaborazione del report nel server di report dopo un numero specifico di secondi. Tale valore viene applicato all'elaborazione dei report in un server di report. L'impostazione non ha effetto sull'elaborazione dei dati nel server di database che fornisce i dati per il report. Il conteggio del timer per l'elaborazione del report inizia al momento della selezione del report e termina all'apertura del report. Il valore specificato deve essere sufficiente per consentire il completamento dell'elaborazione sia dei dati che del report.|  
|Limite snapshot sistema|Il valore predefinito è -1, che indica che non vi sono limiti.<br /><br /> Consente di impostare un valore predefinito a livello di sito per il numero di copie della cronologia del report da conservare. Il valore predefinito specifica un'impostazione iniziale che definisce il numero di snapshot che può essere archiviato per ogni report. È possibile specificare limiti diversi nelle pagine delle proprietà dei singoli report.|  
|Durata parametri memorizzati|Il valore predefinito è 180.|  
|Soglia parametri memorizzati|Il valore predefinito è 1500 giorni.|  
  
###  <a name="bkmk_session_settings_section"></a> Impostazioni sessione  
  
|Impostazione|Commenti|  
|-------------|--------------|  
|Timeout sessione|Il valore predefinito è 600 secondi.|  
|Usa cookie di sessione|Il valore predefinito è TRUE.|  
|Timeout report RDLX|Il valore predefinito è 1800 secondi.|  
  
###  <a name="bkmk_logging_settings_section"></a> Impostazioni di sistema per la registrazione  
  
|Impostazione|Commenti|  
|-------------|--------------|  
|Abilita registrazione di esecuzione|Il valore predefinito è TRUE.<br /><br /> Consente di specificare se il server di report deve generare log di traccia, nonché il numero di giorni per cui conservare tali log. , I log vengono archiviati nel computer del server di report, nella cartella \Microsoft SQL Server\MSSQL.n\ReportServer\Log. Viene creato un nuovo file di log a ogni riavvio del servizio. Per altre informazioni sui file di log, vedere [Report Server Service Trace Log](report-server/report-server-service-trace-log.md)|  
|Giorni di mantenimento del log di esecuzione|Il valore predefinito è 60 giorni.|  
  
 In [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] è supportata la registrazione ULS di SharePoint.  Per altre informazioni, vedere [Abilitare gli eventi di Reporting Services per il log di traccia di SharePoint &#40;ULS&#41;](report-server/turn-on-reporting-services-events-for-the-sharepoint-trace-log-uls.md)  
  
###  <a name="bkmk_security_settings_section"></a> Impostazioni di sicurezza  
  
|Impostazione|Commenti|  
|-------------|--------------|  
|Abilita sicurezza integrata|Il valore predefinito è TRUE.<br /><br /> Consente di specificare se è possibile stabilire una connessione all'origine dati di un report utilizzando il token di sicurezza di Windows dell'utente che ha richiesto il report.|  
|Abilita definizione report di carico|Il valore predefinito è TRUE.|  
|Abilita errori remoti|Il valore predefinito è FALSE.|  
|Abilita errori dettagliati test connessione|Il valore predefinito è TRUE.|  
  
###  <a name="bkmk_client_settings_section"></a> Impostazioni del client  
  
|Impostazione|Commenti|  
|-------------|--------------|  
|Abilita download Generatore report|Il valore predefinito è TRUE.<br /><br /> Consente di specificare se i client sono in grado di visualizzare il pulsante per il download dell'applicazione Generatore report.|  
|URL di avvio del Generatore report|Consente di specificare un URL personalizzato se per il server di report non viene utilizzato l'URL predefinito di Generatore report. Questa impostazione è facoltativa. Se non si specifica un valore, verrà utilizzato l'URL predefinito, che consente di avviare Generatore report. Per avviare Generatore report 3.0 come applicazione ClickOnce, immettere il valore seguente: http://\<nomecomputer>/ReportServer/ReportBuilder/ReportBuilder_3_0_0_0.application.|  
|Abilita stampa client|Il valore predefinito è TRUE.<br /><br /> Consente di specificare se gli utenti possono scaricare il controllo lato client, che fornisce opzioni di stampa.|  
|Modifica timeout sessione|Il valore predefinito è 7200 secondi.|  
|Modifica limite cache di sessione|Il valore predefinito è 5.|  
  
##  <a name="bkmk_managejobs"></a> Gestione processi  
 È possibile visualizzare ed eliminare i processi in esecuzione, ad esempio i processi creati dalle sottoscrizioni del report e da quelle guidate dai dati. La pagina non viene utilizzata per gestire le sottoscrizioni, bensì i processi attivati da una sottoscrizione. Ad esempio, tramite una sottoscrizione pianificata per essere eseguita una volta ogni ora verrà generato un processo una volta ogni ora che verrà visualizzato nella pagina **Gestione processi** .  
  
 ![gestire processi in esecuzione](media/ssrs-manage-jobs.gif "gestire processi in esecuzione")  
  
##  <a name="bkmk_keymgt"></a> Gestione chiavi  
 Nella tabella seguente sono riepilogate le pagine Gestione chiavi  
  
> [!IMPORTANT]  
>  La modifica periodica della chiave di crittografia di Reporting Services è una procedura consigliata ai fini della sicurezza. È consigliabile modificare la chiave immediatamente dopo un aggiornamento della versione principale di Reporting Services. Modificando la chiave di crittografia di Reporting Services dopo un aggiornamento si riduce il rischio di ulteriori interruzioni del servizio rispetto invece all'eseguire questa operazione all'esterno del ciclo di aggiornamento.  
  
|Pagina|Description|  
|----------|-----------------|  
|Backup della chiave di crittografia|1) Digitare una password nelle caselle **Password:** e **Conferma password** , quindi fare clic su **Esporta**. Se la password digitata non soddisfa i requisiti di complessità dei criteri di dominio, verrà visualizzato un avviso.<br /><br /> 2) Viene chiesto di specificare un percorso in cui salvare il file della chiave. È consigliabile archiviare i file della chiave in un computer separato da quello che è in esecuzione [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. Il nome file predefinito corrisponde al nome dell'applicazione di servizio.|  
|Ripristina chiave di crittografia|1) Digitare o individuare il file della chiave nella casella **Percorso file**<br /><br /> 2) Nella casella **Password** digitare la password usata per eseguire il backup del file di crittografia.<br /><br /> 3) Fare clic su **OK**|  
|Cambia chiave di crittografia|Questa operazione comporta la creazione di una chiave nuova e l'esecuzione di una nuova operazione di crittografia del contenuto crittografato. Se si dispone di grandi quantità di contenuto, questa operazione può richiedere diverse ore.<br /><br /> Al termine dell'operazione di modifica della chiave di crittografia, è consigliabile eseguire un backup della nuova chiave.|  
|Elimina contenuto crittografato|Il contenuto eliminato non può essere recuperato.<br /><br /> **\*\* Importante \*\*** L'azione di eliminazione e ricreazione della chiave simmetrica non può essere invertita o annullata. e può comportare conseguenze significative nell'installazione corrente. Se si elimina la chiave, verranno eliminati anche tutti i dati esistenti crittografati con questa chiave simmetrica. I dati eliminati possono includere stringhe di connessione a origini dei dati esterne per i report, stringhe di connessione archiviate e alcune informazioni relative alle sottoscrizioni.|  
  
##  <a name="bkmk_executionaccount"></a> Account di esecuzione  
 Utilizzare questa pagina per configurare un account da utilizzare per l'esecuzione automatica. L'account verrà utilizzato in circostanze particolari, ovvero quando non sono disponibili altre origini di credenziali, in particolare:  
  
-   Quando il server di report si connette a un'origine dei dati per cui non sono necessarie credenziali. Tra gli esempi di origini dati che potrebbero non necessitare di credenziali rientrano i documenti XML e alcune applicazioni di database client.  
  
-   Quando il server di report si connette a un altro server per recuperare file di immagine esterni o altre risorse a cui si fa riferimento in un report.  
  
 L'impostazione di questo account è facoltativa, tuttavia se non viene eseguita viene limitato l'utilizzo di immagini e connessioni esterne ad alcune origini dati. Quando si recuperano immagini di file esterni, il server di report verifica se è possibile eseguire una connessione anonima. Se la connessione è protetta da password, il server di report utilizza l'account per l'esecuzione automatica dei report per connettersi al server remoto. Durante il recupero di dati per un report, il server di report rappresenta l'utente corrente, richiede all'utente di specificare le credenziali, utilizza le credenziali archiviate oppure utilizza l'account per l'esecuzione automatica se la connessione all'origine dati non specifica **alcun** tipo di credenziale. Il server di report non consente la delega o la rappresentazione delle credenziali dell'account di servizio quando ci si connette ad altri computer, pertanto è necessario utilizzare l'account per l'esecuzione automatica se non sono disponibili altre credenziali.  
  
 L'account specificato deve essere diverso da quello utilizzato per l'esecuzione dell'account del servizio. Se il server di report viene eseguito in una distribuzione con scalabilità orizzontale, è necessario configurare questo account allo stesso modo in ogni server di report.  
  
 È possibile utilizzare qualsiasi account utente di Windows. Per ottenere risultati ottimali, scegliere un account che disponga delle autorizzazioni di lettera e di accesso alla rete per supportare le connessioni ad altri computer. Deve disporre di autorizzazioni di lettura per qualsiasi immagine o file di dati esterno da utilizzare in un report. Non specificare un account locale se tutte le origini dati e tutte le immagini esterne per i report non sono archiviate sul computer del server di report. Utilizzare l'account solo per l'elaborazione automatica dei report.  
  
 ![Contenuto correlato di PowerShell](media/rs-powershellicon.jpg "Contenuto correlato di PowerShell")  
  
 Di seguito è riportato un esempio del comando PowerShell per restituire l'elenco delle applicazioni di servizio di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] con la proprietà UEAccount:  
  
```  
Get-SPRSServiceApplication | select typename, name, service, ueaccountname  
```  
  
 Per altre informazioni, vedere [cmdlet di PowerShell per Reporting Services SharePoint Mode](../../2014/reporting-services/powershell-cmdlets-for-reporting-services-sharepoint-mode.md).  
  
### <a name="options"></a>Opzioni  
 **Specifica account di esecuzione**  
 Selezionare questa opzione per specificare un account.  
  
 **Account**  
 Immettere un account utente di dominio di Windows. Usare questo formato: *\<domini>\\<account utente\>*.  
  
 **Password**  
 Digitare la password.  
  
 **Conferma password**  
 Immettere nuovamente la password.  
  
##  <a name="bkmk_email"></a> Impostazioni posta elettronica  
 Utilizzare questa pagina per specificare le impostazioni SMTP (Simple Mail Transport Protocol) che consentono il recapito tramite posta elettronica dal server di report. È possibile utilizzare l'estensione per il recapito tramite posta elettronica del server di report per distribuire report o notifiche di elaborazione dei report utilizzando sottoscrizioni tramite posta elettronica. L'estensione per il recapito tramite posta elettronica del server di report richiede un server SMTP e un indirizzo di posta elettronica da utilizzare nel campo Da.  
  
### <a name="options"></a>Opzioni  
 **Utilizza Server SMTP**  
 Consente di specificare che il reindirizzamento della posta elettronica del server di report viene eseguito tramite un server SMTP.  
  
 **Server SMTP in uscita**  
 Consente di specificare il server o il gateway SMTP da utilizzare. È possibile utilizzare un server locale o un server SMTP nella rete.  
  
 **Da indirizzo**  
 Consente di specificare l'indirizzo di posta elettronica da utilizzare nel campo Da di un messaggio di posta elettronica generato. È necessario specificare un account utente che abbia l'autorizzazione per l'invio di posta elettronica dal server SMTP.  
  
##  <a name="bkmk_provisionsubscriptions"></a> Avvisi e sottoscrizioni provisioning  
 Utilizzare questa pagina per verificare se SQL Server Agent è in esecuzione ed effettuare il provisioning dell'accesso per consentire l'utilizzo di SQL Server Agent da parte di Reporting Services. SQL Server Agent è necessario per gli avvisi dati, le pianificazioni e le sottoscrizioni di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . [Provisioning di sottoscrizioni e avvisi per le applicazioni di servizio SSRS](install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md)  
  
## <a name="proxy-association"></a>Associazione del proxy  
 Al momento della creazione dell'applicazione di servizio Reporting Services, è stata selezionata l'applicazione Web da associare e per la quale effettuare il provisioning delle autorizzazioni per l'accesso da parte dell'applicazione di servizio Reporting Services. Se è stato scelto di non eseguire l'associazione o si desidera modificare l'associazione, attenersi alla procedura seguente.  
  
1.  In Gestione applicazioni di Amministrazione centrale SharePoint fare clic su **Configura associazioni applicazione di servizio**.  
  
2.  Nella pagina Associazioni applicazione di servizio modificare la visualizzazione in **Applicazioni di servizio**.  
  
3.  Trovare e fare clic sul nome del nuovo [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] applicazione del servizio. È possibile fare clic anche sull' **impostazione predefinita** del nome del gruppo proxy di applicazione per aggiungere il proxy per impostare il gruppo piuttosto che completare i passaggi seguenti.  
  
4.  Nella casella di selezione **Modifica il gruppo di connessioni seguente** scegliere **Personalizza**.  
  
5.  Selezionare la casella relativa al proxy e fare clic su **OK**.  
  
  

---
title: Proprietà server (pagina Avanzate) - Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: tools
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.swb.reportserver.serverproperties.advanced.f1
ms.assetid: 07b78a84-a6aa-4502-861d-349720ef790e
caps.latest.revision: 18
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 336a201dde0a1afba761e135d561079ce5c95d75
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34550402"
---
# <a name="server-properties-advanced-page---reporting-services"></a>Proprietà server (pagina Avanzate) - Reporting Services

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)]

Questa pagina consente di impostare le proprietà di sistema nel server di report. Le proprietà di sistema possono essere impostate in diversi modi. Questo strumento fornisce un'interfaccia utente grafica che consente di impostare le proprietà senza dovere scrivere codice.

Per aprire questa pagina, avviare SQL Server Management Studio, connettersi a un'istanza del server di report, fare clic con il pulsante destro del mouse sul nome del server di report e scegliere **Proprietà**. Selezionare **Avanzate** per aprire la pagina.

## <a name="options"></a>Opzioni

**EnableMyReports**  
Indica se la caratteristica Report personali è abilitata. Un valore **true** indica che la caratteristica è abilitata.  

**MyReportsRole**  
Nome del ruolo utilizzato durante la creazione dei criteri di sicurezza nelle cartelle Report personali dell'utente. Il valore predefinito è **My Reports Role**.  

**EnableClientPrinting**  
Determina se il controllo ActiveX RSClientPrint è disponibile per il download dal server di report. I valori validi sono **true** e **false**. Il valore predefinito è **true**. Per altre informazioni sulle impostazioni aggiuntive necessarie per questo controllo, vedere [Abilitare e disabilitare la stampa sul lato client per Reporting Services](../../reporting-services/report-server/enable-and-disable-client-side-printing-for-reporting-services.md).  

**EnableExecutionLogging**  
Indica se la registrazione per l'esecuzione di report è attivata. Il valore predefinito è **true**. Per altre informazioni sul log di esecuzione del server di report, vedere [Vista ExecutionLog ed ExecutionLog3 del server di report](../../reporting-services/report-server/report-server-executionlog-and-the-executionlog3-view.md).  

**ExecutionLogDaysKept**  
Numero di giorni durante i quali le informazioni sulle esecuzioni dei report vengono conservate nel log di esecuzione. I valori validi per questa proprietà sono compresi tra **-1** e **2**,**147**,**483**,**647**. Se il valore è **-1** le voci non vengono eliminate dalla tabella del log di esecuzione. Il valore predefinito è **60**.  

> [!NOTE] 
> Se si imposta un valore **0** vengono *eliminate* tutte le voci dal log di esecuzione. Il valore **-1** mantiene le voci del log di esecuzione e non le elimina.

**SessionTimeout**  
Intervallo, in secondi, durante il quale una sessione rimane attiva. Il valore predefinito è **600**.  

**SharePointIntegratedMode**  
Proprietà di sola lettura che indica la modalità del server. Se il valore è False, il server di report è in esecuzione in modalità nativa.  

**SiteName**  
Nome del sito del server di report visualizzato nel titolo della pagina del portale Web. Il valore predefinito è [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Questa proprietà può essere una stringa vuota. La lunghezza massima è di 8.000 caratteri.  

**StoredParametersLifetime**  
Specifica il numero massimo di giorni per cui è possibile conservare un parametro archiviato. I valori validi sono compresi tra **-1**, **+1** e **2,147,483,647**. Il valore predefinito è **180** giorni.  

**StoredParametersThreshold**  
Specifica il numero massimo di valori dei parametri che possono essere archiviati nel server di report. I valori validi sono compresi tra **-1**, **+1** e **2,147,483,647**. Il valore predefinito è **1500**.  

**UseSessionCookies**  
Indica se il server di report deve utilizzare cookie di sessione per le comunicazioni con i browser dei client. Il valore predefinito è **true**.  

**ExternalImagesTimeout**  
Determina l'intervallo di tempo consentito per il recupero di un file di immagine esterno prima del timeout della connessione. Il valore predefinito è **600** secondi.  

**SnapshotCompression**  
Definisce come vengono compressi gli snapshot. Il valore predefinito è **SQL**. I valori validi sono i seguenti:

|Valori|Descrizione|
|---------|---------|
|**SQL**|Gli snapshot vengono compressi quando vengono archiviati nel database del server di report. Tale compressione è il comportamento corrente.|
|**Nessuno**|Gli snapshot non vengono compressi.|
|**Tutto**|Gli snapshot vengono compressi per tutte le opzioni di archiviazione, incluso il database del server di report o il file system.|

**SystemReportTimeout**  
Valore di timeout  predefinito per l'elaborazione dei report, espresso in secondi, per tutti i report gestiti nello spazio dei nomi del server di report. È possibile eseguire l'override del valore a livello di report. Se questa proprietà è impostata, il server di report tenta di arrestare l'elaborazione di un report quando scade il tempo specificato. I valori validi sono compresi tra **-1** e **2**,**147**,**483**,**647**. Se il valore è **-1**durante l'elaborazione non si verifica alcun timeout dei report nello spazio dei nomi. Il valore predefinito è **1800**.  

**SystemSnapshotLimit**  
Numero massimo di snapshot archiviati per un report. I valori validi sono compresi tra **-1** e **2**,**147**,**483**,**647**. Se il valore è **-1**, non vi sono limiti per gli snapshot.  

**EnableIntegratedSecurity**  
Determina se la sicurezza integrata di Windows è supportata per le connessioni alle origini dati dei report. Il valore predefinito è **True**. I valori validi sono i seguenti:

|Valori|Descrizione|
|---------|---------|
|**True**|La sicurezza integrata di Windows è attivata.|
|**False**|La sicurezza integrata di Windows non è attivata. Le origini dati dei report configurate per l'utilizzo della sicurezza integrata di Windows non verranno eseguite.|

**EnableLoadReportDefinition**  
Selezionare questa opzione per specificare se gli utenti possono eseguire report ad hoc da un report di Generatore report. Selezionando questa opzione si imposta la proprietà **EnableLoadReportDefinition** sul server di report.  

Se si deseleziona questa opzione, la proprietà viene impostata su False. Il server di report non genererà report click-through per i report che usano un modello di report come origine dati. Qualsiasi chiamata al metodo LoadReportDefinition verrà bloccata.  

La disattivazione di questa opzione consente di attenuare i rischi di attacchi Denial of Service condotti da utenti malintenzionati tramite overload del server di report con richieste LoadReportDefinition.  

**EnableRemoteErrors**  
Include informazioni esterne sugli errori, ad esempio, informazioni sull'errore relative alle origini dati del report, nei messaggi di errore restituiti agli utenti che richiedono i report dai computer remoti. I valori validi sono **true** e **false**. Il valore predefinito è **false**. Per altre informazioni, vedere [Abilita errori remoti &#40;Reporting Services&#41;](../../reporting-services/report-server/enable-remote-errors-reporting-services.md).  

**EnableReportDesignClientDownload**  
Specifica se il pacchetto di installazione di Generatore report può essere scaricato dal server di report. Se si deseleziona questa impostazione, l'URL di Generatore report non funziona. 

**EditSessionCacheLimit**  
Consente di specificare il numero di voci della cache di dati che possono essere attive in una sessione di modifica del report. Il numero predefinito è 5.  

**EditSessionTimeout**  
Consente di specificare il numero di secondi prima del timeout di una sessione di modifica del report. Il valore predefinito è 7200 secondi (due ore).  

**EnableCustomVisuals** ***(solo Server di report di Microsoft Power BI)***  
Se i server di report di Microsof Power BI consentono la visualizzazione di oggetti visivi personalizzati di Power BI. I valori sono True e False.  Il valore predefinito è True.  

**EnablePowerBIReportExportData** ***(solo Server di report di Microsoft Power BI)***  
Se i server di report di Microsof Power BI consentono l'esportazione dei dati da oggetti visivi di Power BI. I valori sono True e False.  Il valore predefinito è True.  

**ScheduleRefreshTimeoutMinutes** ***(solo server di report di Microsoft Power BI)***  
Timeout in minuti per l'aggiornamento dei dati nell'aggiornamento pianificato dei report di Power BI con modelli AS incorporati. Il valore predefinito è 120 minuti.

**EnableTestConnectionDetailedErrors**  
Indica se inviare messaggi di errore dettagliati al computer client quando gli utenti verificano le connessioni all'origine dati mediante il server di report. Il valore predefinito è **true**. Se l'opzione viene impostata su **false**, vengono inviati solo messaggi di errore generici.

**AccessControlAllowCredentials**  
Indica se la risposta alla richiesta del client può essere esposta quando il flag "credenziali" è impostato su true. Il valore predefinito è **false**.

**AccessControlAllowHeaders** Elenco separato da virgole delle intestazioni consentite dal server quando un client invia una richiesta. Questa proprietà può essere una stringa vuota. Specificando * si consentono tutte le intestazioni.

**AccessControlAllowMethods** Elenco separato da virgole dei metodi HTTP consentiti dal server quando un client invia una richiesta. I valori predefiniti sono (GET, PUT, POST, PATCH, DELETE). Specificando * si consentono tutte le intestazioni.

**AccessControlAllowOrigin** Elenco separato da virgole delle origini consentite dal server quando un client invia una richiesta. Il valore predefinito è vuoto, il che impedisce tutte le richieste. Se si specifica * si consentono tutte le origini quando le credenziali non sono impostate; se vengono specificate credenziali, è necessario specificare un elenco esplicito delle origini.

**AccessControlExposeHeaders** Elenco separato da virgole delle intestazioni che il server esporrà ai client. Il valore predefinito è vuoto.

**AccessControlMaxAge** Specifica il numero di secondi durante i quali i risultati della richiesta preliminare possono essere memorizzati nella cache. Il valore predefinito è 600 (10 minuti).

## <a name="see-also"></a>Vedere anche

[Impostare le proprietà di un server di report &#40;Management Studio&#41;](../../reporting-services/tools/set-report-server-properties-management-studio.md)   
[Eseguire la connessione a un server di report in Management Studio](../../reporting-services/tools/connect-to-a-report-server-in-management-studio.md)   
[Proprietà di Reporting Services](../../reporting-services/report-server-web-service/net-framework/reporting-services-properties.md)   
[Guida sensibile al contesto del server di report in Management Studio](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)   
[Proprietà di sistema del server di report](../../reporting-services/report-server-web-service/net-framework/reporting-services-properties-report-server-system-properties.md)   
[Utilizzare script per l'esecuzione di attività di distribuzione e di amministrazione](../../reporting-services/tools/script-deployment-and-administrative-tasks.md)   
[Abilitare e disabilitare la funzionalità Report personali](../../reporting-services/report-server/enable-and-disable-my-reports.md)  

Altre domande? [Visitare il forum su Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)

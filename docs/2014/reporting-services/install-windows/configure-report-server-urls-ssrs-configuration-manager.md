---
title: Configurare gli URL del server di report (Gestione configurazione SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Report Server Windows service, virtual directories
- report servers [Reporting Services], virtual directories
- virtual directories [Reporting Services]
- Report Manager [Reporting Services], virtual directories
ms.assetid: a0134ef0-086c-443e-93b9-7213a3d76393
caps.latest.revision: 7
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 085eaf6b8b21462f675d2eca2033cbf8cfa4efa3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37230601"
---
# <a name="configure-report-server-urls--ssrs-configuration-manager"></a>Configurare gli URL del server di report (Gestione configurazione SSRS)
  In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], gli URL vengono utilizzati per accedere al servizio Web ReportServer e gestione Report. Per poter utilizzare una delle due applicazioni, è necessario configurare almeno un URL ciascuno per il servizio Web e per Gestione report. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sono disponibili valori predefiniti per entrambi gli URL dell'applicazione, appropriati per la maggior parte degli scenari di distribuzione, incluse le distribuzioni side-by-side con altri servizi e applicazioni Web.  
  
-   Se è stata eseguita l'installazione utilizzando la configurazione predefinita, gli URL sono stati creati automaticamente mediante i valori predefiniti.  
  
-   Se si utilizza lo strumento di configurazione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] per creare o modificare gli URL, è possibile accettare i valori predefiniti per un URL o specificarne di personalizzati. Un collegamento di test dell'URL viene visualizzato nella pagina in cui si definisce l'URL, per verificare immediatamente che le impostazioni specificate consentano una connessione valida. Per istruzioni dettagliate su come configurare e testare un URL, vedere [configurare un URL &#40;Gestione configurazione SSRS&#41;](configure-a-url-ssrs-configuration-manager.md).  
  
## <a name="defining-a-report-server-url"></a>Definizione di un URL del server di report  
 L'URL identifica con precisione il percorso di un'istanza di un'applicazione del server di report nella rete. Quando si crea un URL del server di report, è necessario specificare le parti seguenti.  
  
|Parte|Description|  
|----------|-----------------|  
|Nome host|Una rete TCP/IP utilizza un indirizzo IP per identificare in modo univoco un dispositivo in rete. È presente un indirizzo IP fisico per ogni scheda di rete installata in un computer. Se l'indirizzo IP viene risolto in un'intestazione host, è possibile specificare l'intestazione host. Se il server di report viene distribuito in una rete aziendale, è possibile utilizzare il nome di rete del computer.|  
|Port|Una porta TCP è un endpoint nel dispositivo. Il server di report sarà in attesa delle richieste su una porta designata.|  
|Directory virtuale|Una porta viene spesso condivisa da più servizi o applicazioni Web. Per tale motivo, un URL del server di report include sempre una directory virtuale corrispondente all'applicazione che riceve la richiesta. È necessario specificare nomi delle directory virtuali univoci per ogni applicazione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in attesa sullo stesso indirizzo IP e sulla stessa porta.|  
|Impostazioni SSL|È possibile configurare gli URL in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] per l'utilizzo di un certificato SSL esistente precedentemente installato nel computer. Per altre informazioni, vedere [configurare connessioni SSL in un Server di Report in modalità nativa](../security/configure-ssl-connections-on-a-native-mode-report-server.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] documentazione Online.|  
  
## <a name="default-urls"></a>URL predefiniti  
 Quando si accede a un server di report o a Gestione report tramite il relativo URL, quest'ultimo deve includere il nome host e non l'indirizzo IP. In una rete TCP/IP l'indirizzo IP verrà risolto in un nome host o nel nome di rete del computer. Se per configurare gli URL sono stati utilizzati i valori predefiniti, dovrebbe essere possibile accedere al servizio Web ReportServer utilizzando gli URL che specificano come nome host il nome del computer o localhost:  
  
-   http://\<nomecomputer > / reportserver  
  
-   http://localhost/reportserver  
  
 Le impostazioni che rendono disponibili questi URL sono incluse nella tabella seguente. Nella tabella vengono indicati i valori predefiniti che consentono la connessione del server di report tramite URL che includono un nome host:  
  
|Parte|valore|Spiegazione|  
|----------|-----------|-----------------|  
|Indirizzo IP|Tutti assegnati|Il DNS nella rete risolve il nome host incluso nell'URL nell'indirizzo IP del computer. Se l'indirizzo IP è incluso nell'URL definito, una richiesta inviata a un host specifico raggiungerà la destinazione desiderata.|  
|Port|80|La porta 80 è la porta predefinita per le connessioni TCP/IP in un computer. Poiché il server di report è in ascolto sulla porta 80, è possibile omettere il numero di porta dall'URL. Se si specifica un'altra porta, è necessario specificarla nell'URL.|  
|Directory virtuale|ReportServer|Si noti che entrambi gli URL di esempio includono il nome della directory virtuale. A meno che non si personalizzi la definizione dell'URL, è sempre necessario specificare il nome della directory virtuale dell'applicazione nell'URL.|  
  
> [!NOTE]  
>  Una prenotazione URL sottostante consente l'utilizzo di qualsiasi nome host valido in un URL. Lo strumento di configurazione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] crea una prenotazione URL in HTTP.SYS utilizzando una sintassi che consente la risoluzione delle varianti del nome host in una determinata istanza del server di report. Per altre informazioni sulle prenotazioni URL, vedere [sulle prenotazioni e registrazione URL &#40;Gestione configurazione SSRS&#41;](about-url-reservations-and-registration-ssrs-configuration-manager.md).  
  
## <a name="server-side-permissions-on-a-report-server-url"></a>Autorizzazioni sul lato server per un URL del server di report  
 All'account del servizio del server di report vengono concesse in modo esclusivo le autorizzazioni per ogni endpoint URL. Solo tale account dispone dei diritti necessari per accettare le richieste indirizzate agli URL di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Per l'account vengono creati e gestiti elenchi di controllo di accesso discrezionale (DACL, Discretionary Access Control List) quando si configura l'identità del servizio tramite il programma di installazione o lo strumento di configurazione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Se si modifica l'account del servizio, lo strumento di configurazione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] aggiornerà tutte le prenotazioni URL create per includere le nuove informazioni sull'account. Per altre informazioni, vedere [sintassi delle prenotazioni URL &#40;Gestione configurazione SSRS&#41;](url-reservation-syntax-ssrs-configuration-manager.md).  
  
## <a name="authenticating-client-requests-sent-to-a-report-server-url"></a>Autenticazione delle richieste client inviate a un URL del server di report  
 Per impostazione predefinita, il tipo di autenticazione supportato negli endpoint URL è l'autenticazione di Windows. Si tratta dell'estensione di sicurezza predefinita. Se si implementa un provider di autenticazione personalizzata o basata su form, è necessario modificare le impostazioni di autenticazione nel server di report. Se si desidera, è inoltre possibile modificare le impostazioni di autenticazione di Windows in modo che corrispondano al sottosistema di autenticazione utilizzato nella rete. Per altre informazioni, vedere [l'autenticazione con il Server di Report](../security/authentication-with-the-report-server.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] documentazione Online.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 [Configurare un URL &#40;Gestione configurazione SSRS&#41;](configure-a-url-ssrs-configuration-manager.md)  
 In questo argomento vengono fornite istruzioni per l'impostazione e la modifica di una prenotazione URL tramite lo strumento di configurazione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 [Su prenotazioni e registrazione URL &#40;Gestione configurazione SSRS&#41;](about-url-reservations-and-registration-ssrs-configuration-manager.md)  
 Gli URL vengono utilizzati per accedere ad applicazioni e report. In questo argomento vengono descritti gli URL dell'applicazione e gli URL predefiniti e vengono fornite informazioni sul funzionamento delle prenotazioni URL e della registrazione URL in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 [Sintassi delle prenotazioni URL &#40;Gestione configurazione SSRS&#41;](url-reservation-syntax-ssrs-configuration-manager.md)  
 Le prenotazioni URL predefinite usate in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sono valide per la maggior parte degli scenari. Se, tuttavia, si desidera limitare l'accesso o estendere la distribuzione per consentire accesso Internet o Extranet, potrebbe essere necessario personalizzare le impostazioni in base alle esigenze. In questo argomento viene descritta la sintassi di una prenotazione URL e vengono forniti alcuni consigli utili per la creazione di prenotazioni personalizzate per la distribuzione.  
  
 [URL nei file di configurazione &#40;Gestione configurazione SSRS&#41;](urls-in-configuration-files-ssrs-configuration-manager.md)  
 Il file RSReportServer.config contiene più voci per le prenotazioni URL e gli URL utilizzati per il recapito tramite posta elettronica di Gestione report e del server di report. In questo argomento viene fornito un riepilogo delle impostazioni di configurazione degli URL, utile per la comprensione delle relative analogie e differenze.  
  
 [Le distribuzioni del Server di Report le prenotazioni URL per istanze multiple &#40;Gestione configurazione SSRS&#41;](url-reservations-for-multi-instance-report-server-deployments.md)  
 Quando si installano più istanze di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in un singolo computer, aumenta la probabilità che vengano rilevati URL duplicati durante la registrazione di un URL. Per evitare questi errori, seguire i consigli indicati in questo argomento per la creazione di prenotazioni URL specifiche dell'istanza.  
  
## <a name="see-also"></a>Vedere anche  
 [Configurare un URL &#40;Gestione configurazione SSRS&#41;](configure-a-url-ssrs-configuration-manager.md)   
 [URL del servizio Web &#40;modalità nativa SSRS&#41;](../../sql-server/install/web-service-url-ssrs-native-mode.md)  
  
  

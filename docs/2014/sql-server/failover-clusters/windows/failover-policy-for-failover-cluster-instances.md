---
title: Criteri di failover per istanze del cluster di failover | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- flexible failover policy
ms.assetid: 39ceaac5-42fa-4b5d-bfb6-54403d7f0dc9
caps.latest.revision: 43
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f3b48cf86ed58813c8bcaccea0506e55feb7927a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37238191"
---
# <a name="failover-policy-for-failover-cluster-instances"></a>Criteri di failover per istanze del cluster di failover
  In un'istanza del cluster di failover (FCI, Failover Cluster Instance) di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , solo un nodo può possedere il gruppo di risorse del cluster WSFC (Windows Server Failover Cluster) a un'ora specificata. Le richieste del client vengono servite tramite questo nodo nell'istanza FCI. In caso di errore e riavvio non eseguito, la proprietà del gruppo viene spostata in un altro nodo WSFC nell'istanza FCI. Questo processo viene chiamato failover. [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] aumenta l'affidabilità di rilevamento dell'errore e offre criteri di failover flessibili.  
  
 Un'istanza FCI di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dipende dal servizio WSFC sottostante per il rilevamento del failover. Pertanto, due meccanismi determinano il comportamento del failover per l'istanza FCI: la prima è la funzionalità di WSFC nativa e la seconda è la funzionalità aggiunta dall'installazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
-   Il cluster WSFC gestisce la configurazione del quorum che assicura una destinazione del failover univoca in un failover automatico. Il servizio WSFC determina se il cluster è sempre nell'integrità del quorum ottimale e porta di conseguenza il gruppo di risorse online e offline.  
  
-   L'istanza [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] attiva riporta periodicamente un set di diagnostica del componente al gruppo di risorse WSFC su una connessione dedicata. Il gruppo di risorse WSFC gestisce i criteri del failover che definiscono le condizioni di errore che attivano operazioni di riavvio e failover.  
  
 In questo argomento viene illustrato il secondo meccanismo. Per altre informazioni sul comportamento di WSFC per la configurazione del quorum e il rilevamento dell'integrità, vedere [Modalità quorum WSFC e configurazione del voto &#40;SQL Server&#41;](wsfc-quorum-modes-and-voting-configuration-sql-server.md).  
  
> [!IMPORTANT]  
>  I failover automatici da e verso un'istanza FCI non sono consentiti in un gruppo di disponibilità AlwaysOn. I failover manuali da e verso un'istanza FCI sono consentiti in un gruppo di disponibilità AlwaysOn.  
  
##  <a name="Concepts"></a> Panoramica dei criteri di failover  
 Il processo del failover si può essere suddiviso nei passaggi indicati di seguito.  
  
1.  [Monitoraggio dello stato di integrità](failover-policy-for-failover-cluster-instances.md#monitor)  
  
2.  [Determinazione di errori](failover-policy-for-failover-cluster-instances.md#determine)  
  
3.  [Risposta agli errori](failover-policy-for-failover-cluster-instances.md#respond)  
  
###  <a name="monitor"></a> Monitoraggio dello stato di integrità  
 Tre sono i tipi di stato di integrità che vengono monitorati per l'istanza FCI:  
  
-   [Stato del servizio SQL Server](failover-policy-for-failover-cluster-instances.md#service)  
  
-   [Velocità di risposta dell'istanza di SQL Server](failover-policy-for-failover-cluster-instances.md#instance)  
  
-   [Diagnostica dei componenti di SQL Server](failover-policy-for-failover-cluster-instances.md#component)  
  
####  <a name="service"></a> Stato del servizio SQL Server  
 Il servizio WSFC esegue il monitoraggio lo stato iniziale del servizio SQL Server sul nodo FCI attivo per rilevare quando viene arrestato il servizio SQL Server.  
  
####  <a name="instance"></a> Velocità di risposta dell'istanza di SQL Server  
 Durante l'avvio di SQL Server, il servizio WSFC utilizza la DLL risorse del motore di database di SQL Server per creare una nuova connessione a un thread separato utilizzata esclusivamente per il monitoraggio dello stato di integrità. In tal modo si assicura che l'istanza di SQL disponga delle risorse richieste per restituire lo stato di integrità durante il caricamento. Tramite questa connessione dedicata, SQL Server esegue la stored procedure di sistema [sp_server_diagnostics &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql) in modalità ripetizione per restituire periodicamente lo stato di integrità dei componenti di SQL Server per la DLL risorse.  
  
 La DLL risorse determina la velocità di risposta dell'istanza di SQL utilizzando un timeout di controllo integrità. La proprietà HealthCheckTimeout consente di definire il tempo di attesa della DLL risorse per la stored procedure sp_server_diagnostics prima che venga stabilita la mancata risposta da parte dell'istanza di SQL al servizio WSFC. Questa proprietà è configurabile utilizzando T-SQL così come nello snap-in Gestione cluster di failover. Per altre informazioni, vedere [Configurazione delle impostazioni HealthCheckTimeout](configure-healthchecktimeout-property-settings.md). Di seguito viene descritta l'influenza di questa proprietà sulle impostazioni del timeout e dell'intervallo di ripetizione:  
  
-   Tramite la DLL risorse viene chiamata la stored procedure sp_server_diagnostics e impostato l'intervallo di ripetizione su un terzo dell'impostazione HealthCheckTimeout.  
  
-   Se la stored procedure sp_server_diagnostics è lenta o non consente la restituzione di informazioni, tramite la DLL risorse si attenderà l'intervallo specificato da HealthCheckTimeout, prima di restituire al servizio WSFC la mancata risposta da parte dell'istanza SQL.  
  
-   Se la connessione dedicata viene persa, la DLL risorse ritenterà la connessione all'istanza di SQL per il tempo specificato da HealthCheckTimeout prima che riporti al servizio WSFC che l'istanza SQL non risponde.  
  
####  <a name="component"></a> Diagnostica dei componenti di SQL Server  
 La stored procedure di sistema sp_server_diagnostics raccoglie periodicamente i dati di diagnostica dei componenti sull'istanza di SQL. Le informazioni diagnostiche raccolte vengono visualizzate in una riga per ognuno dei componenti seguenti e passate al thread chiamante.  
  
1.  sistema  
  
2.  resource  
  
3.  processo query  
  
4.  io_subsystem  
  
5.  eventi  
  
 I componenti system, resource e query process vengono utilizzati per il rilevamento di errori. I componenti io_subsytem ed events vengono utilizzati solo per scopi diagnostici.  
  
 Ogni set di righe di informazioni viene scritto anche nel log di diagnostica dei cluster di SQL Server. Per altre informazioni, vedere [Visualizzazione e lettura del log di diagnostica dell'istanza del cluster di failover](view-and-read-failover-cluster-instance-diagnostics-log.md).  
  
> [!TIP]  
>  La stored procedure sp_server_diagnostic viene utilizzata dalla tecnologia SQL Server AlwaysOn, ma è anche disponibile per essere usata da qualsiasi istanza di SQL Server per il rilevamento e la risoluzione dei problemi.  
  
####  <a name="determine"></a> Determinazione di errori  
 La DLL risorse del motore di database di SQL Server determina se lo stato di integrità rilevato è una condizione di errore utilizzando la proprietà FailureConditionLevel. La proprietà FailureConditionLevel definisce quale stato integrità rilevato causa il riavvio o il failover. Sono disponibili più livelli di opzioni, da nessun riavvio o failover automatico a tutte le possibili condizioni di errore che comportano un riavvio o un failover automatico. Per altre informazioni su come configurare questa proprietà, vedere [Configurare le impostazioni della proprietà FailureConditionLevel](configure-failureconditionlevel-property-settings.md).  
  
 Le condizioni di errore vengono impostate in base a un ordine crescente. In ognuno dei livelli 1-5 sono incluse tutte le condizioni dei livelli precedenti oltre alle proprie condizioni specifiche. Pertanto, in ogni livello la probabilità di un failover o di un riavvio è maggiore. I livelli delle condizioni di errore sono descritti nella tabella seguente.  
  
 Rivedere [sp_server_diagnostics &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql) poiché questa stored procedure di sistema gioca un ruolo importante nei livelli di condizione di errore.  
  
|Level|Condizione|Description|  
|-----------|---------------|-----------------|  
|0|Nessun failover o riavvio automatico|Viene indicato che con qualsiasi condizione di errore non verrà attivato automaticamente alcun failover o riavvio. Questo livello serve solo per scopi di manutenzione del sistema.|  
|1|Failover o riavvio in caso di server non disponibile|Viene indicato che verrà attivato un riavvio o un failover del server se si verifica la condizione seguente:<br /><br /> Indisponibilità del servizio SQL Server.|  
|2|Failover o riavvio in caso di mancata risposta da parte del server|Viene indicato che verrà attivato un riavvio o un failover del server se si verifica una qualsiasi delle condizioni seguenti:<br /><br /> Indisponibilità del servizio SQL Server.<br /><br /> L'istanza di SQL Server non risponde (la DLL risorse non può ricevere dati da sp_server_diagnostics entro le impostazioni HealthCheckTimeout).|  
|3*|Failover o riavvio in caso di errori critici del server|Viene indicato che verrà attivato un riavvio o un failover del server se si verifica una qualsiasi delle condizioni seguenti:<br /><br /> Indisponibilità del servizio SQL Server.<br /><br /> L'istanza di SQL Server non risponde (la DLL risorse non può ricevere dati da sp_server_diagnostics entro le impostazioni HealthCheckTimeout).<br /><br /> La stored procedure di sistema sp_server_diagnostics restituisce l'errore di sistema.|  
|4|Failover o riavvio in caso di errori del server con gravità moderata|Viene indicato che verrà attivato un riavvio o un failover del server se si verifica una qualsiasi delle condizioni seguenti:<br /><br /> Indisponibilità del servizio SQL Server.<br /><br /> L'istanza di SQL Server non risponde (la DLL risorse non può ricevere dati da sp_server_diagnostics entro le impostazioni HealthCheckTimeout).<br /><br /> La stored procedure di sistema sp_server_diagnostics restituisce l'errore di sistema.<br /><br /> La stored procedure di sistema sp_server_diagnostics restituisce l'errore di risorsa.|  
|5|Failover o riavvio in caso di qualsiasi condizione di errore qualificata|Viene indicato che verrà attivato un riavvio o un failover del server se si verifica una qualsiasi delle condizioni seguenti:<br /><br /> Indisponibilità del servizio SQL Server.<br /><br /> L'istanza di SQL Server non risponde (la DLL risorse non può ricevere dati da sp_server_diagnostics entro le impostazioni HealthCheckTimeout).<br /><br /> La stored procedure di sistema sp_server_diagnostics restituisce l'errore di sistema.<br /><br /> La stored procedure di sistema sp_server_diagnostics restituisce l'errore di risorsa.<br /><br /> La stored procedure di sistema sp_server_diagnostics restituisce l'errore di elaborazione query.|  
  
 *Valore predefinito  
  
####  <a name="respond"></a> Risposta agli errori  
 Una volta rilevata una o più condizioni di errore, il servizio WSFC risponde agli errori in base allo stato del quorum WSFC e alle impostazioni di riavvio e failover del gruppo di risorse di FCI. Se l'istanza FCI ha perso il quorum WSFC, l'intera istanza FCI viene portata offline e perde la disponibilità elevata. Se l'istanza FCI ancora mantiene il quorum WSFC, è possibile che il servizio WSFC risponda prima tentando di riavviare il nodo in errore e quindi eseguendo il failover se i tentativi del riavvio non riescono. Le impostazioni di riavvio e failover vengono configurate nello snap-in Gestione cluster di failover. Per altre informazioni su queste impostazioni, vedere [Proprietà \<risorsa>: scheda Criteri](http://technet.microsoft.com/library/cc725685.aspx).  
  
 Per altre informazioni, vedere [Modalità quorum WSFC e configurazione del voto &#40;SQL Server&#41;](wsfc-quorum-modes-and-voting-configuration-sql-server.md).  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-server-configuration-transact-sql)  
  
  

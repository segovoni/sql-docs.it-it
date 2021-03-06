---
title: Panoramica di Monitoraggio mirroring del database | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.dbmmonitor.main.f1
helpviewer_keywords:
- Database Mirroring Monitor [SQL Server], interface
ms.assetid: 8ebbdcd6-565a-498f-b674-289c84b985eb
caps.latest.revision: 37
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e0a6c5fe31a244e60e57a14453a29f1392fdcb73
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37330521"
---
# <a name="database-mirroring-monitor-overview"></a>Panoramica di Monitoraggio mirroring del database
  Se si dispone delle autorizzazioni corrette, è possibile utilizzare Monitoraggio mirroring del database per monitorare eventuali subset dei database con mirroring su un'istanza del server. Il monitoraggio consente di verificare se e quanto correttamente i dati vengono trasmessi alla sessione di mirroring del database. Monitoraggio mirroring del database è inoltre utile per individuare e risolvere la causa di una riduzione del flusso di dati.  
  
 È possibile registrare uno o più database con mirroring per il monitoraggio singolarmente su ogni partner di failover. Quando si registra un database, Monitoraggio mirroring del database memorizza nella cache le informazioni seguenti relative al database:  
  
-   Nome database  
  
-   Nomi delle due istanze dei server partner  
  
-   Gli ultimi ruoli noti di ogni partner (principale o mirror)  
  
## <a name="permissions"></a>Autorizzazioni  
 Per monitorare il mirroring del database, è necessario essere membri del ruolo predefinito del server **sysadmin** o del ruolo predefinito del database **dbm_monitor** nel database **msdb** nell'istanza del server. Se l'utente è membro di **sysadmin** o di **dbm_monitor** su una sola delle istanze del server partner, il monitoraggio può connettersi solo a tale partner e non riesce a recuperare informazioni dall'altro partner.  
  
 Se l'utente è membro solo di **dbm_monitor** su un'istanza del server, disporrà di autorizzazioni limitate su tale istanza. L'utente sarà in grado di visualizzare esclusivamente la riga di stato più recente. Se l'utente si connette a un'istanza del server usando le autorizzazioni per **dbm_monitor** , Monitoraggio mirroring del database avvisa che l'utente ha autorizzazioni limitate.  
  
> [!IMPORTANT]  
>  Il ruolo predefinito del database **dbm_monitor** viene creato nel database **msdb** quando il primo database viene registrato in Monitoraggio mirroring del database. Il nuovo ruolo **dbm_monitor** non include alcun membro fino a quando un amministratore di sistema non provvede all'assegnazione di utenti al ruolo stesso.  
  
## <a name="navigation-tree"></a>Albero di navigazione  
 Se uno o più database sono stati registrati per il monitoraggio tramite Monitoraggio mirroring del database, nell'albero di navigazione viene visualizzato un elenco dei database registrati. L'albero viene aggiornato automaticamente ogni 30 secondi. Selezionare un database registrato per visualizzarne lo stato. Per ulteriori informazioni, vedere "Riquadro dei dettagli" di seguito in questo argomento.  
  
 Per ogni database registrato sono visualizzate le informazioni seguenti:  
  
 *<Nome_database>* **(** *\<Stato>* **,** *<SERVER_PRINCIPALE>* **->** *<SERVER_MIRROR>* **)**  
  
 *<Nome_database>*  
 Nome di un database con mirroring registrato in Monitoraggio mirroring del database.  
  
 *\<Stato>*  
 Gli stati possibili e le relative icone sono indicati di seguito:  
  
|Icona|Stato|Description|  
|----------|------------|-----------------|  
|Icona avviso|**Unknown**|Il monitoraggio non è connesso ad alcun partner. Le uniche informazioni disponibili sono relative agli elementi memorizzati nella cache dal monitoraggio.|  
|Icona avviso|**Sincronizzazione in corso**|La posizione del contenuto del database mirror precede quella del database principale. L'istanza del server principale invia record di log all'istanza del server mirror, che applica le modifiche al database mirror per eseguirne il rollforward.<br /><br /> All'avvio della sessione di mirroring del database, i database mirror e principale sono in questo stato.|  
|Cilindro del database standard|**Sincronizzato**|Quando il server mirror è sufficientemente aggiornato rispetto al server principale, lo stato del database diventa **Sincronizzato**. Il database resta in questo stato fino a quando il server principale continua a inviare modifiche al server mirror e quest'ultimo continua ad applicare le modifiche al database mirror.<br /><br /> Per la modalità a protezione elevata, il failover automatico e quello manuale sono entrambi possibili, senza perdita di dati.<br /><br /> In modalità a prestazioni elevate è possibile che si verifichi la perdita di dati anche nello stato **Sincronizzato** .|  
|Icona avviso|**Sospeso**|Il database principale è disponibile, ma non viene inviato alcun log al server mirror.|  
|Icona Errori|**Disconnesso**|L'istanza del server non può connettersi al proprio partner.|  
  
 *<PRINCIPAL_SERVER>*  
 Nome del partner che rappresenta attualmente l'istanza del server principale. Il nome è nel formato seguente:  
  
 *<SYSTEM_NAME>*[**\\***<nome_istanza>*]  
  
 dove *<NOME_SISTEMA>* è il nome del sistema contenente l'istanza del server. Per un'istanza del server non predefinita, viene anche visualizzato il nome dell'istanza, *<NOME_SISTEMA>***\\***<nome_istanza>*.  
  
 *<MIRROR_SERVER>*  
 Nome del partner che rappresenta attualmente l'istanza del server mirror. Il formato è identico a quello del server principale.  
  
## <a name="detail-pane"></a>Riquadro dei dettagli  
 L'aspetto del monitoraggio dipende dal fatto che un database sia selezionato o meno. Quando si apre il monitoraggio, nel riquadro dei dettagli viene visualizzato un collegamento **Registra database con mirroring** . Fare clic sul collegamento per registrare un database. I database registrati sono elencati di seguito nel nodo **Monitoraggio mirroring del database** nell'albero di navigazione. Monitoraggio mirroring del database tenta sempre di connettersi a ogni istanza del server per la quale dispone di credenziali memorizzate.  
  
 Quando si seleziona un database, il suo stato viene visualizzato nella pagina a schede **Stato** nel riquadro dei dettagli. Il contenuto di questa pagina deriva dalle istanze del server principale e del server mirror. La pagina viene compilata in modo asincrono man mano che lo stato viene raccolto attraverso connessioni separate alle istanze del server principale e del server mirror. Lo stato viene aggiornato automaticamente ogni 30 secondi.  
  
> [!NOTE]  
>  Non è possibile modificare la frequenza di aggiornamento del monitoraggio, ma è possibile aggiornare la tabella dello stato dalla finestra di dialogo **Cronologia mirroring del database** .  
  
 Un amministratore di sistema può visualizzare la configurazione corrente degli avvisi per il database selezionando la pagina a schede **Avvisi** . Da questa pagina è possibile accedere alla finestra di dialogo **Imposta valori di soglia avvisi** per abilitare e configurare una o più soglie degli avvisi.  
  
 Nell'intestazione sopra le schede, il riquadro dei dettagli visualizza l'ora dell'ultimo aggiornamento delle informazioni di stato nel monitoraggio nel formato **Ultimo aggiornamento:***\<data>**\<ora>*. Monitoraggio mirroring del database recupera in genere le informazioni di stato dalle istanze del server principale e mirror in momenti diversi. Viene visualizzato l'orario relativo alla meno recente delle due operazioni.  
  
## <a name="action-menu"></a>Menu Azione  
 Il menu **Azione** include sempre i comandi seguenti:  
  
|Comando|Description|  
|-------------|-----------------|  
|**Registra database con mirroring...**|Apre la finestra di dialogo **Registra database con mirroring** . Utilizzare questa finestra di dialogo per registrare uno o più database con mirroring su una determinata istanza del server aggiungendo il database o i database a Monitoraggio mirroring del database. Quando viene aggiunto un database, Monitoraggio mirroring del database memorizza nella cache le informazioni relative al database, ai suoi partner e alla modalità di connessione a questi ultimi.|  
|**Gestione connessioni a istanze server…**|Selezionare questo comando per accedere alla finestra di dialogo **Gestione connessioni a istanze server** , nella quale è possibile scegliere un'istanza del server per la quale specificare le credenziali da utilizzare nel monitoraggio per la connessione a un determinato partner.<br /><br /> Per modificare le credenziali per un partner, trovare la relativa voce nella griglia **Istanze server** e fare clic su **Modifica** nella riga corrispondente. Verrà visualizzata la finestra di dialogo **Connetti al server** con il nome corretto dell'istanza del server e i controlli delle credenziali inizializzati sul valore attualmente memorizzato nella cache. Modificare le informazioni di autenticazione in base alle esigenze e fare clic su **Connetti**. Se le credenziali hanno privilegi sufficienti, la colonna **Connetti tramite** viene aggiornata con le nuove credenziali.|  
  
 Se si seleziona un database, il menu **Azione** include anche i comandi seguenti.  
  
|Comando|Description|  
|-------------|-----------------|  
|**Annulla registrazione del database**|Consente di rimuovere il database selezionato da Monitoraggio mirroring del database.|  
|**Imposta valori soglia avvisi…**|Aprire la finestra di dialogo **Imposta valori di soglia avvisi** , nella quale un amministratore di sistema può abilitare o disabilitare gli avvisi per il database su ogni partner e modificare la soglia di ogni avviso. È consigliabile impostare una soglia per un determinato avviso su entrambi i partner per assicurare che l'avviso venga mantenuto in caso di failover del database. La soglia appropriata per ogni partner dipende dalle capacità in termini di prestazioni del sistema di tale partner.<br /><br /> Un evento viene scritto nel log eventi per una prestazione solo se il relativo valore è uguale o superiore alla relativa soglia quando la tabella dello stato è in fase di aggiornamento. Se un valore di picco raggiunge la soglia solo temporaneamente tra gli aggiornamenti di stato, tale picco non viene segnalato.|  
  
 **Per monitorare il mirroring del database tramite SQL Server Management Studio**  
  
-   [Avviare Monitoraggio mirroring del database &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Monitoraggio del mirroring del database &#40;SQL Server&#41;](database-mirroring-sql-server.md)   
 [Avvio della Configurazione guidata sicurezza mirroring del database &#40;SQL Server Management Studio&#41;](start-the-configuring-database-mirroring-security-wizard.md)  
  
  

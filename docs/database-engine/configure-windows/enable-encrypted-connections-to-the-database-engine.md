---
title: Abilitazione di connessioni crittografate al Motore di database | Microsoft Docs
ms.custom: 
ms.date: 06/12/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connections [SQL Server], encrypted
- SSL [SQL Server]
- Secure Sockets Layer (SSL)
- encryption [SQL Server], connections
- cryptography [SQL Server], connections
- certificates [SQL Server], installing
- requesting encrypted connections
- installing certificates
- security [SQL Server], encryption
ms.assetid: e1e55519-97ec-4404-81ef-881da3b42006
caps.latest.revision: 48
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 5dba6e8516e97ce603b529b8ad4c07eac0db2981
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="enable-encrypted-connections-to-the-database-engine"></a>Abilitazione di connessioni crittografate al Motore di database
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  In questo argomento viene descritto come abilitare connessioni crittografate per un'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] specificando un certificato per il [!INCLUDE[ssDE](../../includes/ssde-md.md)] tramite Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . È necessario che sia disponibile un certificato per il computer server e che il computer client sia impostato per considerare attendibile l'autorità radice del certificato. Il processo di provisioning consiste nell'installazione di un certificato tramite l'importazione in Windows.  
  
 Il certificato deve essere emesso per l'opzione **Autenticazione server**. Il nome del certificato deve essere il nome di dominio completo (FQDN) del computer.  
  
 I certificati per gli utenti vengono archiviati nel computer locale. Per installare un certificato per l'uso da parte di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è necessario eseguire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager con un account che dispone di privilegi di amministratore locale.
 
  
 Il client deve essere in grado di verificare la proprietà del certificato utilizzato dal server. Se il client dispone del certificato chiave pubblica dell'autorità di certificazione che ha firmato il certificato del server, non sono necessarie ulteriori operazioni di configurazione. [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows sono inclusi i certificati chiave pubblica di numerose autorità di certificazione. Se il certificato del server è stato firmato da un'autorità di certificazione pubblica o privata per la quale il client non dispone del certificato chiave pubblica, è necessario installare il certificato chiave pubblica dell'autorità di certificazione che ha firmato il certificato del server.  
  
> [!NOTE]  
>  Per utilizzare la crittografia in un cluster di failover, è necessario installare il certificato server con il nome DNS completo del server virtuale in tutti i nodi del cluster di failover. Se ad esempio si dispone di un cluster costituito da due nodi, denominati rispettivamente test1.*\<nomeazienda>*.com e test2.*\<<nomeazienda>*.com, e di un server virtuale denominato virtsql, è necessario installare un certificato per virtsql.*\<nomeazienda>*.com in entrambi i nodi. È possibile impostare il valore dell'opzione **ForceEncryption**su **Sì**.  

> [!NOTE]
> Se si creano connessioni crittografate per un indicizzatore di ricerca di Azure a SQL Server in una macchina virtuale di Azure, vedere [Configurare una connessione da un indicizzatore di Ricerca di Azure a SQL Server in una VM Azure](https://azure.microsoft.com/documentation/articles/search-howto-connecting-azure-sql-iaas-to-azure-search-using-indexers/). 
  
 
##  <a name="SSMSProcedure"></a>  
  
###  <a name="Provision"></a> Per installare e rendere disponibile un certificato nel server  
  
1.  Fare clic sul menu **Start** , scegliere **Esegui**, digitare **MMC** nella casella **Apri** e fare clic su **OK**.  
  
2.  Nella console MMC scegliere **Aggiungi/Rimuovi snap-in** dal menu **File**.  
  
3.  Nella finestra di dialogo **Aggiungi/Rimuovi snap-in** fare clic su **Aggiungi**.  
  
4.  Nella finestra di dialogo **Aggiungi snap-in autonomo** fare clic su **Certificati**e quindi su **Aggiungi**.  
  
5.  Nella finestra di dialogo **Snap-in certificati** fare clic su **Account del computer**e quindi su **Fine**.  
  
6.  Nella finestra di dialogo **Aggiungi snap-in autonomo** fare clic su **Chiudi**.  
  
7.  Nella finestra di dialogo **Aggiungi/Rimuovi snap-in** fare clic su **OK**.  
  
8.  Nello snap-in **Certificati** espandere **Certificati**e **Personale**, fare clic con il pulsante destro del mouse su **Certificati**, scegliere **Tutte le attività**e quindi fare clic su **Importa**.  

9. Fare clic con il pulsante destro del mouse sul certificato importato, scegliere **Tutte le attività**e quindi fare clic su **Gestisci chiavi private**. Nella finestra di dialogo **Sicurezza** aggiungere l'autorizzazione di lettura per un account utente usato dall'account del servizio SQL Server.  
  
10. Completare l' **Importazione guidata certificati**per aggiungere un certificato al computer e chiudere la console MMC. Per ulteriori informazioni sull'aggiunta di un certificato a un computer, vedere la documentazione di Windows.  
  
###  <a name="Export"></a> Per esportare il certificato del server  
  
1.  Nello snap-in **Certificati** individuare il certificato nella cartella **Certificati** / **Personale** , fare clic con il pulsante destro del mouse su **Certificato**, scegliere **Tutte le attività**e quindi fare clic su **Esporta**.  
  
2.  Completare l' **Esportazione guidata certificati**e archiviare il file di certificato in una posizione appropriata.  
  
###  <a name="ConfigureServerConnections"></a> Per configurare il server in modo che accetti connessioni crittografate  
  
1.  In **Gestione configurazione SQL Server** espandere **Configurazione di rete SQL Server**, fare clic con il pulsante destro del mouse su **Protocolli per** *\<istanza server>* e quindi scegliere **Proprietà**.  
  
2.  Nella scheda **Certificato** della finestra di dialogo **Proprietà - Protocolli per***\<nome istanza>* **** selezionare il certificato desiderato nell'elenco a discesa per la casella **Certificato** e quindi fare clic su **OK**.  
  
3.  Nella casella **ForceEncryption** della scheda **Flag** selezionare **Sì**e quindi fare clic su **OK** per chiudere la finestra di dialogo.  
  
4.  Riavviare il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
###  <a name="ConfigureClientConnections"></a> Per configurare il client in modo che richieda connessioni crittografate  
  
1.  Copiare il certificato originale o il file di certificato esportato nel computer client.  
  
2.  Nel computer client usare lo snap-in **Certificati** per installare il certificato radice o il file di certificato esportato.  
  
3.  Nel riquadro della console fare clic con il pulsante destro del mouse su **Configurazione SQL Server Native Client**e quindi scegliere **Proprietà**.  
  
4.  Nella casella **Imponi crittografia protocolli** della pagina **Flag** fare clic su **Sì**.  
  
###  <a name="EncryptConnection"></a> Per crittografare una connessione da SQL Server Management Studio  
  
1.  Nella barra degli strumenti di Esplora oggetti fare clic su **Connetti**e quindi su **Motore di database**.  
  
2.  Nella finestra di dialogo **Connetti al server** completare le informazioni di connessione e quindi fare clic su **Opzioni**.  
  
3.  Nella scheda **Proprietà connessione** fare clic su **Crittografa connessione**.  
  
## <a name="see-also"></a>Vedere anche

[Supporto di TLS 1.2 per Microsoft SQL Server](https://support.microsoft.com/kb/3135244)  


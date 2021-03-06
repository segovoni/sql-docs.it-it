---
title: Risolvere i problemi di utilità SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f5f47c2a-38ea-40f8-9767-9bc138d14453
caps.latest.revision: 8
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 81b35d1af874c97bf2e61e9c1234d7ad7876e229
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37328141"
---
# <a name="troubleshoot-the-sql-server-utility"></a>Risoluzione dei problemi relativi a Utilità SQL Server
  La risoluzione dei problemi relativi a Utilità [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] potrebbe includere la risoluzione di un'operazione non riuscita di registrazione di un'istanza di SQL Server con un punto di controllo dell'utilità, la risoluzione dei problemi relativi a raccolte dati con errori che generano icone grigie nella visualizzazione elenco dell'istanza gestita in un punto di controllo dell'utilità, la riduzione dei colli di bottiglia delle prestazioni o la risoluzione dei problemi di integrità delle risorse. Per altre informazioni sulla riduzione dei problemi di integrità delle risorse identificati da un [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] dell'utilità, vedere [risolvere i problemi di integrità risorse di SQL Server &#40;utilità SQL Server&#41;](../relational-databases/manage/troubleshoot-sql-server-resource-health-sql-server-utility.md).  
  
## <a name="failed-operation-to-enroll-an-instance-of-sql-server-into-a-sql-server-utility"></a>Operazione di registrazione di un'istanza di SQL Server in Utilità SQL Server non riuscita  
 Se ci si connette all'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] eseguire la registrazione tramite [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] l'autenticazione e si specifica un account proxy che appartiene a un dominio di Active Directory diverso rispetto a quello in cui si trova il punto di controllo utilità Convalida istanza ha esito positivo, ma il operazione di registrazione ha esito negativo con messaggio di errore seguente:  
  
 Eccezione durante l'esecuzione di un'istruzione o un batch Transact-SQL. (Microsoft.SqlServer.ConnectionInfo)  
  
 Ulteriori informazioni: Non è stato possibile ottenere informazioni relative al gruppo/utente di Windows NT '\<NomeDominio\NomeAccount>', codice di errore 0x5. (Microsoft SQL Server, Errore: 15404)  
  
 Questo problema si verifica nello scenario di esempio seguente:  
  
1.  Il punto di controllo dell'utilità è un membro di "Domain_1".  
  
2.  Esiste una relazione di trust di dominio unidirezionale, ovvero, "Domain_1" non è considerato attendibile da "Domain_2" ma "Domain_2" è considerato attendibile da "Domain_1".  
  
3.  L'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] da registrare in Utilità [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] è anche un membro di "Domain_1".  
  
4.  Durante l'operazione di registrazione, connettersi all'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] per eseguire la registrazione utilizzando "sa". Specificare un account proxy da "Domain_2".  
  
5.  La convalida riesce, ma la registrazione no.  
  
 La soluzione alternativa per questo problema, utilizzando l'esempio precedente, è connettersi all'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] per eseguire la registrazione in Utilità [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] utilizzando "sa" e fornire un account proxy da "Domain_1".  
  
## <a name="failed-wmi-validation"></a>Convalida WMI non riuscita  
 Se WMI non è configurato correttamente in un'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], le operazioni di creazione del punto di controllo dell'utilità e di registrazione dell'istanza gestita visualizzano un avviso, ma l'operazione non viene bloccata. Inoltre, se si modifica il [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] configurazione dell'account dell'agente in modo che [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent non dispone dell'autorizzazione per le classi WMI obbligatorie, la raccolta dei dati nell'istanza gestita interessata di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] non riesce a caricare il punto di controllo utilità. Ciò comporta la visualizzazione di icone grigie nel punto di controllo dell'utilità.  
  
 La raccolta dati con errori genera icone di stato grigie nella visualizzazione elenco del punto di controllo dell'utilità per le istanze gestite interessate di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. La cronologia processo nell'istanza gestita di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] mostra errori di sysutility_mi_collect_and_upload nel passaggio 2 (dati fase raccolti dallo script di PowerShell).  
  
 I messaggi di errore semplificati sono:  
  
 L'esecuzione del comando è stata arrestata perché la variabile della shell "ErrorActionPreference" è impostata sull'arresto: accesso negato.  
  
 Errore: \<data e ora (MM/GG/AAAA hh.mm.ss) >: eccezione intercettata durante la raccolta delle proprietà della cpu.  È probabile che una query WMI non sia riuscita.  AVVISO.  
  
 Per risolvere questo problema, verificare le impostazioni di configurazione seguenti:  
  
-   In Windows Server 2003, il servizio SQL Server Agent deve essere parte del gruppo di monitoraggio delle prestazioni di Windows nell'istanza gestita di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
-   Il servizio WMI deve essere abilitato e configurato nell'istanza gestita di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
-   Il repository WMI potrebbe essere danneggiato nell'istanza gestita di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
-   La libreria delle prestazioni potrebbe essere mancante o danneggiata nell'istanza gestita di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 Per verificare che l'istanza specificata di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sia configurata correttamente per la segnalazione dei dati al punto di controllo dell'utilità, verificare che le classi seguenti siano disponibili nell'istanza specificata di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] e che siano accessibili da parte dell'account del servizio di SQL Server Agent:  
  
-   Win32_MountPoint  
  
-   Win32_PerfRawData_PerfProc_Process  
  
-   Win32_PerfRawData_PerfOS_Processor  
  
-   Win32_Processor  
  
-   Win32_Volume  
  
-   Win32_LogicalDisk  
  
 È possibile utilizzare il cmdlet Get-WmiObject di PowerShell in ognuna delle classi per verificare che ogni classe sia accessibile. Eseguire i cmdlet seguenti nell'istanza gestita di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:  
  
```  
Get-WmiObject Win32_MountPoint -ErrorAction Stop | Out-Null  
Get-WmiObject Win32_PerfRawData_PerfProc_Process -ErrorAction Stop| Out-Null  
Get-WmiObject Win32_PerfRawData_PerfOS_Processor -ErrorAction Stop | Out-Null  
Get-WmiObject Win32_Processor -ErrorAction Stop | Out-Null  
Get-WmiObject Win32_Volume -ErrorAction Stop | Out-Null  
Get-WmiObject Win32_LogicalDisk -ErrorAction Stop | Out-Null  
```  
  
 Per altre informazioni sulla risoluzione dei problemi relativi a WMI, vedere l'articolo relativo alla [risoluzione dei problemi WMI](http://go.microsoft.com/fwlink/?LinkId=178250). Si noti che le query in queste operazioni dell'Utilità SQL Server vengono eseguite localmente, pertanto il contenuto relativo alla risoluzione dei problemi DCOM e remoti non si applica.  
  
## <a name="failed-data-collection"></a>Raccolta dati con errori  
 Se [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] eventi di raccolta dati di utilità esito negativo, considerare le possibilità seguenti:  
  
-   Non modificare le proprietà del set di raccolta "Informazioni utilità" in un'istanza gestita di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]e non abilitare/disabilitare manualmente la raccolta dati, in quanto viene controllata da un processo dell'agente Utilità.  
  
-   Convalida WMI non riuscita o non supportata. Per ulteriori informazioni, vedere la sezione Convalida WMI non riuscita in precedenza in questo argomento.  
  
-   Aggiornare i dati in visualizzazione elenco dell'istanza gestita, come i dati in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] punti di visualizzazione di utilità non viene aggiornato automaticamente. Per aggiornare i dati, fare doppio clic sul **istanze gestite** nodo il **navigazione di Esplora utilità** riquadro, quindi selezionare **Aggiorna**, o fare clic sul [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] nome della visualizzazione elenco dell'istanza, quindi selezionare **Aggiorna**. Si tenga presente che, dopo la registrazione di un'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] con un punto di controllo dell'utilità, possono essere necessari fino a 30 minuti affinché i dati vengano visualizzati nel dashboard e i punti di visualizzazione nel riquadro del contenuto Esplora utilità.  
  
-   Utilizzare Gestione configurazione SQL Server per verificare che l'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] è in esecuzione.  
  
-   Se la raccolta o il caricamento dei dati non riesce a causa di problemi di timeout, aggiornare la funzione dbo.fn_sysutility_mi_get_collect_script() nel database MSDB. In particolare, nella funzione "Invoke-BulkCopyCommand()" aggiungere la riga:  
  
    ```  
    $bulkCopy.BulkCopyTimeout=180  
    ```  
  
     Il valore di timeout predefinito è di 30 secondi.  
  
-   Se l'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] non è di tipo cluster, verificare che il servizio [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent sia in esecuzione e che sia configurato per essere avviato automaticamente nel punto di controllo dell'utilità e nell'istanza gestita di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
-   Verificare che un account valido di cui è in uso per eseguire la raccolta dei dati nell'istanza gestita di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. È possibile, ad esempio, che la password sia scaduta. Se la password del proxy è scaduta, aggiornare le credenziali della password in SSMS, come indicato di seguito:  
  
    1.  In **Esplora oggetti**di SSMS espandere il nodo **Sicurezza** , quindi espandere il nodo **Credenziali** .  
  
    2.  Fare clic su **UtilityAgentProxyCredential_\<GUID >** e selezionare **proprietà**.  
  
    3.  Nella finestra di dialogo Proprietà credenziali aggiornare le credenziali come desiderato per il **UtilityAgentProxyCredential_\<GUID >** credenziale.  
  
    4.  Scegliere **OK** per confermare la modifica.  
  
-   TCP/IP deve essere abilitato nel punto di controllo utilità e nell'istanza gestita di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Abilitare TCP/IP tramite [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Configuration Manager.  
  
-   È necessario avviare e configurare per l'avvio automatico il servizio SQL Server Browser nel punto di controllo dell'utilità. Se l'organizzazione non consente l'utilizzo del servizio SQL Server Browser, utilizzare i passaggi seguenti per consentire a un'istanza gestita di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] di connettersi al punto di controllo dell'utilità:  
  
    1.  Sulla barra delle applicazioni di Windows nell'istanza gestita di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], fare clic su **avviare**, quindi fare clic su **Esegui...** .  
  
    2.  Digitare "cliconfg.exe" nella casella, quindi fare clic su **OK**.  
  
    3.  Se viene richiesto di consentire l'avvio di SQL Client Configuration Utility EXE, fare clic su**Continua**.  
  
    4.  Nella finestra di dialogo **Configurazione di rete client di SQL Server** selezionare la scheda **Alias** , quindi fare clic su **Aggiungi**.  
  
    5.  Nella finestra di dialogo **Aggiungi configurazione libreria di rete** effettuare le operazioni seguenti:  
  
    6.  Specificare TCP/IP nell'elenco delle librerie di rete.  
  
    7.  Specificare NomeComputer\NomeIstanza per il punto di controllo dell'utilità nella casella di testo **Alias server** .  
  
    8.  Specificare NomeComputer per il punto di controllo dell'utilità nella casella di testo **Nome server** .  
  
    9. Deselezionare la casella di controllo **Determina porta in modo dinamico** .  
  
    10. Specificare il numero della porta su cui il punto di controllo dell'utilità è in attesa nella casella di testo **Numero porta** .  
  
    11. Scegliere **OK** per salvare le modifiche.  
  
    12. Ripetere questi passaggi per ogni istanza gestita di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] che si connette a un punto di controllo utilità in cui il servizio SQL Server Browser non è abilitato.  
  
-   Assicurarsi che le istanze gestite di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sono connessi alla rete.  
  
-   Se sono presenti database con lo stesso nome ma con impostazioni diverse per la distinzione tra maiuscole e minuscole su un'istanza gestita di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], l'identificazione tra il database e i relativi punti di visualizzazione può risultare errata, causando errori nella raccolta dati. Ad esempio, in un database denominato "MYDATABASE" potrebbero essere visualizzati stati di integrità per un database denominato "MyDatabase". In questo scenario non viene generato alcun errore. La raccolta dati con errori può essere anche il risultato di mancate corrispondenze tra maiuscole e minuscole in altri oggetti visualizzati nel punto di controllo dell'utilità, ad esempio tra i nomi dei file di database e i nomi dei gruppi di file.  
  
-   Se un'istanza gestita di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] è ospitata in un computer Windows Server 2003, l'account del servizio [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent deve appartenere al gruppo di sicurezza Performance Monitor Users o Administrators. In caso contrario, la raccolta dati non riuscirà e restituirà un errore di accesso negato. Per aggiungere un [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] account del servizio dell'agente al gruppo di sicurezza Performance Monitor Users, procedere come segue:  
  
    1.  Aprire **Gestione computer**, quindi **Utenti e gruppi locali**, quindi fare clic su **Gruppi**.  
  
    2.  Fare clic con il pulsante destro del mouse su **Performance Monitor Users** e scegliere **Aggiungi a gruppo**.  
  
    3.  Scegliere **Aggiungi**.  
  
    4.  Immettere l'account che il servizio SQL Server Agent sta utilizzando, quindi fare clic su **OK**.  
  
    5.  Se l'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] è già registrata con il punto di controllo dell'utilità prima di aggiungere l'utente a questo gruppo, riavviare il servizio [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent.  
  
## <a name="see-also"></a>Vedere anche  
 [Attività e funzionalità di Utilità SQL Server](../relational-databases/manage/sql-server-utility-features-and-tasks.md)   
 [Risolvere i problemi relativi all'integrità delle risorse di SQL Server &#40;Utilità SQL Server&#41;](../relational-databases/manage/troubleshoot-sql-server-resource-health-sql-server-utility.md)  
  
  

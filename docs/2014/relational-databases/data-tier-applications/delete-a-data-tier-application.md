---
title: Eliminare un'applicazione livello dati | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-data-tier-apps
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.deletedacwizard.introduction.f1
- sql12.swb.deletedacwizard.deletedac.f1
- sql12.swb.deletedacwizard.summary.f1
- sql12.swb.deletedacwizard.choosemethod.f1
helpviewer_keywords:
- How to [DAC], delete
- data-tier application [SQL Server], delete
- wizard [DAC], delete
- delete DAC
ms.assetid: 16fe1c18-4486-424d-81d6-d276ed97482f
caps.latest.revision: 15
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e3613ce8ccee33accac25dc702d70fea9536587e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37166922"
---
# <a name="delete-a-data-tier-application"></a>Eliminazione di un'applicazione livello dati
  È possibile eliminare un'applicazione livello dati utilizzando la procedura guidata Elimina applicazione livello dati o uno script Windows PowerShell. È possibile specificare se il database associato viene mantenuto, scollegato o eliminato.  
  
-   **Prima di iniziare:**  [Limitazioni e restrizioni](#LimitationsRestrictions), [Autorizzazioni](#Permissions)  
  
-   **Per aggiornare un'applicazione livello dati (DAC) tramite:**  [la procedura guidata Registra applicazione livello dati](#UsingDeleteDACWizard), [PowerShell](#DeleteDACPowerShell)  
  
## <a name="before-you-begin"></a>Prima di iniziare  
 Quando si elimina un'istanza di applicazione livello dati (DAC), è necessario selezionare una tra tre opzioni in cui viene specificata l'azione che verrà eseguita con il database associato all'applicazione livello dati. Tutte e tre le opzioni consentono di eliminare i metadati che definiscono l'applicazione livello dati. Le opzioni differiscono tra loro per le azioni relative al database associato all'applicazione livello dati. Con la procedura guidata non viene eliminato alcun oggetto a livello di istanza associato all'applicazione livello dati o al database, come ad esempio gli account di accesso.  
  
|Opzione|Azioni di database|  
|------------|----------------------|  
|Elimina registrazione|Il database associato rimane intatto.|  
|Scollega database|Il database associato viene scollegato. L'istanza del Motore di database non potrà fare riferimento al database, ma i file di dati e di log rimarranno invariati.|  
|Elimina database|Il database associato viene eliminato. I file di dati e di log vengono eliminati.|  
  
###  <a name="LimitationsRestrictions"></a> Limitazioni e restrizioni  
 Non esistono meccanismi automatici per ripristinare i metadati della definizione o il database dell'applicazione livello dati dopo l'eliminazione dell'applicazione. Il metodo per ricompilare manualmente l'istanza di applicazione livello dati dipende dall'opzione di eliminazione scelta.  
  
|Opzione|Metodo di ricompilazione dell'istanza di applicazione livello dati|  
|------------|-------------------------------------|  
|Elimina registrazione|Registrare un'applicazione livello dati dal database rimasto.|  
|Scollega database|Collegare nuovamente il database tramite **sp_attachdb** o [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], quindi registrare una nuova istanza di applicazione livello dati dal database.|  
|Elimina database|Ripristinare il database da un backup completo eseguito prima dell'eliminazione dell'applicazione livello dati, quindi registrare una nuova istanza di applicazione livello dati dal database.|  
  
> [!WARNING]  
>  La ricompilazione di un'istanza di applicazione livello dati mediante la registrazione di un'applicazione livello dati da un database ripristinato o ricollegato non implica la ricreazione di alcune parti dell'applicazione originale, quali i criteri di selezione dei server.  
  
###  <a name="Permissions"></a> Permissions  
 Un'applicazione livello dati può essere eliminata unicamente da membri del ruolo predefinito del server **sysadmin** o **serveradmin** oppure dal proprietario del database. È inoltre possibile avviare la procedura guidata usando l'account dell'amministratore di sistema di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] predefinito denominato **sa** .  
  
##  <a name="UsingDeleteDACWizard"></a> Utilizzo della procedura guidata Elimina applicazione livello dati  
 **Per eliminare un'applicazione livello dati tramite una procedura guidata**  
  
1.  In **Esplora oggetti**espandere il nodo dell'istanza contenente l'applicazione livello dati da eliminare.  
  
2.  Espandere il nodo **Gestione** .  
  
3.  Espandere il nodo **Applicazioni livello dati** .  
  
4.  Fare clic con il pulsante destro del mouse sull'applicazione livello dati (DAC) da eliminare, quindi selezionare **Elimina applicazione livello dati**.  
  
5.  Completare le finestre di dialogo della procedura guidata.  
  
    1.  [Introduzione](#Introduction)  
  
    2.  [Seleziona metodo](#Choose_method)  
  
    3.  [Riepilogo](#Summary)  
  
    4.  [Elimina applicazione livello dati](#Delete_datatier_application)  
  
##  <a name="Introduction"></a> Pagina Introduzione  
 In questa pagina vengono descritti i passaggi per l'eliminazione di un'applicazione livello dati.  
  
 **Non visualizzare più questa pagina** - Fare clic sulla casella di controllo per evitare che la pagina venga visualizzata nuovamente in futuro.  
  
 **Avanti >**: consente di passare alla pagina **Seleziona metodo**.  
  
 **Annulla** : consente di terminare la procedura guidata senza eliminare un'applicazione livello dati o un database.  
  
##  <a name="Choose_method"></a> Pagina Seleziona metodo  
 Utilizzare questa pagina per specificare l'opzione per la gestione del database associato all'applicazione livello dati da eliminare.  
  
 **Elimina registrazione** : consente di rimuovere i metadati che definiscono l'applicazione livello dati lasciando intatto il database associato.  
  
 **Scollega database** : consente di rimuovere i metadati che definiscono l'applicazione livello dati e scollegare il database associato.  
  
 L'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)]non può più fare riferimento al database, ma i dati e il file di log rimangono intatti.  
  
 **Elimina database** : consente di rimuovere i metadati che definiscono l'applicazione livello dati ed eliminare il database associato.  
  
 I dati e i file di log per il database vengono definitivamente eliminati.  
  
 **\< Indietro** : consente di tornare alla pagina **Introduzione** .  
  
 **Avanti >**: consente di passare alla pagina **Riepilogo**.  
  
 **Annulla** : consente di terminare la procedura guidata senza eliminare l'applicazione livello dati o il database.  
  
##  <a name="Summary"></a> Pagina Riepilogo  
 Utilizzare questa pagina per verificare le azioni eseguite dalla procedura guidata in caso di eliminazione dell'istanza di applicazione livello dati.  
  
 **Controlla selezioni** : consente di verificare l'applicazione livello dati, il database e il metodo di eliminazione visualizzato nella casella. Se le informazioni sono corrette, selezionare **Avanti** o **Fine** per eliminare l'applicazione livello dati. Se l'applicazione livello dati e le informazioni del database non sono corrette, selezionare **Annulla** , quindi l'applicazione livello dati corretta. Se il metodo di eliminazione non è corretto, scegliere **Indietro** per tornare alla pagina **Seleziona metodo** e selezionare un altro metodo.  
  
 **\< Indietro** : consente di tornare alla pagina **Seleziona metodo** per selezionare un altro metodo di eliminazione.  
  
 **Avanti >**: consente di eliminare l'istanza DAC usando il metodo selezionato nella pagina precedente e passare alla pagina **Elimina applicazione del livello dati**.  
  
 **Annulla** : consente di terminare la procedura guidata senza eliminare l'istanza di applicazione livello dati.  
  
##  <a name="Delete_datatier_application"></a> Pagina Elimina applicazione livello dati  
 In questa pagina viene indicato l'esito positivo o negativo dell'operazione di eliminazione.  
  
 **Eliminazione dell'applicazione livello dati** : consente di visualizzare l'esito positivo o negativo di ogni azione eseguita per l'eliminazione dell'istanza di applicazione livello dati. Verificare le informazioni che determinano l'esito positivo o negativo di ciascuna azione. Ogni azione che ha rilevato un errore avrà un collegamento nella colonna **Risultato** . Selezionare il collegamento per visualizzare un report dell'errore per l'azione.  
  
 **Salva report** : consente di salvare il report dell'eliminazione come file HTML. Nel file viene riportato lo stato di ogni azione, inclusi tutti gli errori generati da qualsiasi azione. La cartella predefinita è una cartella SQL Server Management Studio\DAC Packages contenuta all'interno della cartella Documenti dell'account di Windows.  
  
 **Fine** : consente di terminare la procedura guidata.  
  
##  <a name="DeleteDACPowerShell"></a> Eliminazione di un'applicazione livello dati con PowerShell  
 **Eliminazione di un'applicazione livello dati mediante uno script di PowerShell**  
  
1.  Creare un oggetto server SMO e impostarlo sull'istanza contenente l'applicazione livello dati da eliminare.  
  
2.  Aprire un `ServerConnection` oggetti e connettersi alla stessa istanza.  
  
3.  Uso `add_DacActionStarted` e `add_DacActionFinished` per sottoscrivere eventi di aggiornamento dell'applicazione livello dati.  
  
4.  Specificare l'applicazione livello dati da eliminare.  
  
5.  Utilizzare uno dei tre set di codice, in base all'opzione di eliminazione appropriata:  
  
    -   Per eliminare la registrazione dell'applicazione livello dati ma lasciare intatto il database, usare il `Unmanage()` (metodo).  
  
    -   Per eliminare la registrazione dell'applicazione livello dati e scollegare il database, utilizzare il metodo `Uninstall()` e specificare `DetachDatabase`.  
  
    -   Per eliminare la registrazione dell'applicazione livello dati ed eliminare il database, usare il `Uninstall()` metodo e specificare `DropDatabase`.  
  
### <a name="example-deleting-the-dac-but-leaving-the-database-powershell"></a>Esempio di eliminazione dell'applicazione livello dati conservando il database (PowerShell)  
 L'esempio seguente elimina un'applicazione livello dati denominata MyApplication usando il `Unmanage()` metodo per eliminare l'applicazione livello dati ma lasciare intatto il database.  
  
```  
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = get-item .  
  
## Open a Common.ServerConnection to the same instance.  
$serverconnection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection($srv.ConnectionContext.SqlConnectionObject)  
$serverconnection.Connect()  
$dacstore = New-Object Microsoft.SqlServer.Management.Dac.DacStore($serverconnection)  
  
## Subscribe to the DAC delete events.  
$dacstore.add_DacActionStarted({Write-Host `n`nStarting at $(get-date) :: $_.Description})  
$dacstore.add_DacActionFinished({Write-Host Completed at $(get-date) :: $_.Description})  
  
## Specify the DAC to delete.  
$dacName  = "MyApplication"  
  
## Only delete the DAC definition from msdb, the associated database remains active.  
$dacstore.Unmanage($dacName)  
```  
  
### <a name="example-deleting-the-dac-and-detaching-the-database-powershell"></a>Esempio di eliminazione dell'applicazione livello dati con scollegamento del database (PowerShell)  
 L'esempio seguente elimina un'applicazione livello dati denominata MyApplication usando il `Uninstall()` metodo per eliminare l'applicazione livello dati e scollegare il database.  
  
```  
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = get-item .  
  
## Open a Common.ServerConnection to the same instance.  
$serverconnection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection($srv.ConnectionContext.SqlConnectionObject)  
$serverconnection.Connect()  
$dacstore = New-Object Microsoft.SqlServer.Management.Dac.DacStore($serverconnection)  
  
## Subscribe to the DAC delete events.  
$dacstore.add_DacActionStarted({Write-Host `n`nStarting at $(get-date) :: $_.Description})  
$dacstore.add_DacActionFinished({Write-Host Completed at $(get-date) :: $_.Description})  
  
## Specify the DAC to delete.  
$dacName  = "MyApplication"  
  
## Delete the DAC definition from msdb and detach the associated database.  
$dacstore.Uninstall($dacName, [Microsoft.SqlServer.Management.Dac.DacUninstallMode]::DetachDatabase)  
```  
  
### <a name="example-deleting-the-dac-and-dropping-the-database-powershell"></a>Esempio di eliminazione dell'applicazione livello dati con eliminazione del database (PowerShell)  
 Nell'esempio seguente viene eliminata un'applicazione livello dati denominata MyApplication utilizzando il metodo `Uninstall()` per eliminare l'applicazione livello dati eliminando il database.  
  
```  
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = get-item .  
  
## Open a Common.ServerConnection to the same instance.  
$serverconnection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection($srv.ConnectionContext.SqlConnectionObject)  
$serverconnection.Connect()  
$dacstore = New-Object Microsoft.SqlServer.Management.Dac.DacStore($serverconnection)  
  
## Subscribe to the DAC delete events.  
$dacstore.add_DacActionStarted({Write-Host `n`nStarting at $(get-date) :: $_.Description})  
$dacstore.add_DacActionFinished({Write-Host Completed at $(get-date) :: $_.Description})  
  
## Specify the DAC to delete.  
$dacName  = "MyApplication"  
  
## Delete the DAC definition from msdb and drop the associated database.  
## $dacstore.Uninstall($dacName, [Microsoft.SqlServer.Management.Dac.DacUninstallMode]::DropDatabase)  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Applicazioni livello dati](data-tier-applications.md)   
 [Applicazioni livello dati](data-tier-applications.md)   
 [Distribuire un'applicazione livello dati](deploy-a-data-tier-application.md)   
 [Registrare un database come applicazione livello dati](register-a-database-as-a-dac.md)   
 [Backup e ripristino di database SQL Server](../backup-restore/back-up-and-restore-of-sql-server-databases.md)   
 [Collegamento e scollegamento di un database &#40;SQL Server&#41;](../databases/database-detach-and-attach-sql-server.md)  
  
  

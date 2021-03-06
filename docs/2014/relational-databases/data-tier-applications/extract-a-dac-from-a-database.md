---
title: Estrarre un'applicazione livello dati da un database | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-data-tier-apps
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.extractdacwizard.buildandsave.f1
- sql12.swb.extractdacwizard.setdacproperties.f1
- sql12.swb.extractdacwizard.validationandsummary.f1
- sql12.swb.extractdacwizard.introduction.f1
- sql12.swb.extractdacwizard.selectdatapage.f1
helpviewer_keywords:
- extract DAC
- How to [DAC], extract
- data-tier application [SQL Server], extract
- wizard [DAC], extract
ms.assetid: ae52a723-91c4-43fd-bcc7-f8de1d1f90e5
caps.latest.revision: 19
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9eb33630708143700d7f5ce6749cf720c71a65fd
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37211501"
---
# <a name="extract-a-dac-from-a-database"></a>Estrarre un'applicazione livello dati da un database
  Usare la **procedura guidata Estrai applicazione livello dati** o uno script di Windows PowerShell per estrarre un pacchetto di applicazione livello dati da un database di SQL Server esistente. Il processo di estrazione crea un file di pacchetto DAC che contiene le definizioni degli oggetti di database e i relativi elementi a livello di istanza. Ad esempio, un file di pacchetto di applicazione livello dati contiene tutte le tabelle di database, le stored procedure, le viste e gli utenti, nonché gli account di accesso che eseguono il mapping agli utenti del database.  
  
-   **Prima di iniziare:**  [Limitazioni e restrizioni](#LimitationsRestrictions), [Autorizzazioni](#Permissions)  
  
-   **Per estrarre una DAC, utilizzando:**[Creazione guidata applicazione livello dati estrarre The](#UsingDACExtractWizard), [PowerShell  ](#ExtractDACPowerShell)  
  
## <a name="before-you-begin"></a>Prima di iniziare  
 È possibile estrarre un'applicazione livello dati dai database che risiedono in istanze di [!INCLUDE[ssSDS](../../includes/sssds-md.md)], o [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] Service Pack 4, o versioni successive. Se il processo di estrazione viene eseguito rispetto a un database distribuito da un'applicazione livello dati, vengono estratte solo le definizioni degli oggetti nel database. Il processo non fa riferimento l'applicazione livello dati registrata nel `msdb` (**master** in [!INCLUDE[ssSDS](../../includes/sssds-md.md)]). Il processo di estrazione non consente di registrare la definizione DAC nell'istanza corrente del motore di database. Per ulteriori informazioni sulla registrazione di un'applicazione livello dati, vedere [Register a Database As a DAC](register-a-database-as-a-dac.md).  
  
###  <a name="LimitationsRestrictions"></a> Limitazioni e restrizioni  
 Un'applicazione livello dati può essere estratta solo da un database in [!INCLUDE[ssSDS](../../includes/sssds-md.md)]o [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 4 (SP4) o versioni successive. Non è possibile estrarre un'applicazione livello dati se il database include oggetti non supportati nell'applicazione livello dati o utenti contenuti. Per ulteriori informazioni sui tipi di oggetti supportati in un'applicazione livello dati, vedere [DAC Support For SQL Server Objects and Versions](dac-support-for-sql-server-objects-and-versions.md).  
  
###  <a name="Permissions"></a> Permissions  
 L'estrazione di un'applicazione livello dati richiede almeno le autorizzazioni ALTER ANY LOGIN e VIEW DEFINITION nell'ambito del database, oltre alle autorizzazioni SELECT su **sys.sql_expression_dependencies**. L'estrazione di un'applicazione del livello dati può essere effettuata da membri del ruolo predefinito del server securityadmin che sono anche membri del ruolo predefinito del database database_owner nel database dal cui viene estratta l'applicazione del livello dati. Possono estrarre un'applicazione livello dati anche i membri del ruolo predefinito del server sysadmin o dell'account amministratore di sistema SQL Server predefinito denominato **sa** .  
  
##  <a name="UsingDACExtractWizard"></a> Utilizzo della Procedura guidata Estrai applicazione livello dati  
 **Per estrarre un'applicazione livello dati utilizzando una procedura guidata**  
  
1.  In **Esplora oggetti**, espandere il nodo dell'istanza contenente il database da cui è necessario estrarre l'applicazione livello dati.  
  
2.  Espandere il nodo di **Database** .  
  
3.  Fare clic con il pulsante destro del mouse sul nodo del database da cui si deve estrarre l'applicazione livello dati, scegliere **Attività**e selezionare **Estrai applicazione livello dati**  
  
4.  Completare le finestre di dialogo della procedura guidata.  
  
    1.  [Pagina Introduzione](#Introduction)  
  
    2.  [Pagina Seleziona dati](#SelectData)  
  
    3.  [Pagina Imposta proprietà](#SetProperties)  
  
    4.  [Pagina Convalida e riepilogo](#ValidateSummary)  
  
    5.  [Pagina Compila pacchetto](#BuildPackage)  
  
###  <a name="Introduction"></a> Pagina Introduzione  
 In questa pagina vengono descritti i passaggi per l'estrazione di un'applicazione livello dati.  
  
 **Non visualizzare più questa pagina** - Fare clic sulla casella di controllo per evitare che la pagina venga visualizzata nuovamente in futuro.  
  
 **Avanti >**: consente di passare alla pagina **Seleziona metodo**.  
  
 **Annulla** : termina la procedura guidata senza estrarre un'applicazione livello dati dal database.  
  
###  <a name="SelectData"></a> Pagina Seleziona dati  
 Utilizzare questa pagina della procedura guidata per selezionare i dati di riferimento che si desidera includere nel file del pacchetto di applicazione livello dati. L'inserimento di dati nel pacchetto di applicazione livello dati è facoltativo. Il pacchetto di applicazione livello dati include già lo schema di tutti gli oggetti di database e gli oggetti istanza supportati correlati al database.  
  
 È possibile includere un massimo di 10 MB di dati di riferimento nel file di pacchetto di applicazione livello dati. Per poter essere incluse nell'applicazione livello dati, tuttavia, le tabelle non devono contenere tipi di dati BLOB (Binary Large Object, oggetto binario di grandi dimensioni), ad esempio **image** o **varchar(max)**. Per estrarre maggiori quantità di dati per il trasferimento a un altro database, utilizzare SQL Server Integration Services, l'utilità di copia bulk o una delle numerose altre tecniche di migrazione dei dati.  
  
 **Tabella di database** : selezionare la casella di controllo accanto alle tabelle di database contenenti i dati da includere nel pacchetto di applicazione livello dati. È possibile selezionare fino a dieci tabelle contenenti un massimo di 10.000 righe.  
  
###  <a name="SetProperties"></a> Pagina Imposta proprietà  
 Utilizzare questa pagina della procedura guidata per descrivere l'applicazione livello dati. Queste proprietà vengono utilizzate per identificare l'applicazione livello dati e distinguerla dalle altre.  
  
 **Nome** identifica l'applicazione livello dati. Può essere diverso dal nome del file del pacchetto di applicazione livello dati e deve descrivere l'applicazione. Ad esempio, se il database viene utilizzato per un'applicazione finanziaria, si può chiamare DAC Finanza.  
  
 **Versione (usare xx.xx.xx.xx, dove x è un numero)** : valore numerico che identifica la versione dell'applicazione livello dati. La versione DAC viene utilizzata in Visual Studio per identificare la versione della DAC alla quale stanno lavorando gli sviluppatori. Quando si distribuisce un'applicazione livello dati, la versione viene archiviata nel `msdb` del database e può essere visualizzata successivamente nel **Data-tier Applications** nodo [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **Descrizione** : facoltativa. Viene descritta l'applicazione livello dati. Quando si distribuisce un'applicazione livello dati, la descrizione viene archiviata nel `msdb` del database e può essere visualizzata successivamente nel **Data-tier Applications** nodo [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
 **Salva nel file del pacchetto di applicazione livello dati (nome file con estensione dacpac):** salva l'applicazione livello dati in un file del pacchetto di applicazione livello dati, con estensione dacpac. Fare clic sul pulsante **Sfoglia** per specificare il nome e il percorso del file.  
  
 **Sovrascrivi file esistente** : selezionare questa casella di controllo per sostituire il file del pacchetto di applicazione livello dati se ne esiste già uno con lo stesso nome.  
  
###  <a name="ValidateSummary"></a> Pagina Convalida e riepilogo  
 In questa pagina della procedura guidata viene verificato che tutti gli oggetti di database siano supportati da un'applicazione livello dati. Controlla inoltre le dipendenze attraverso gli oggetti di database per determinare il set di oggetti che possono essere inclusi correttamente nella DAC. Successivamente, visualizza il report di convalida e riepiloga le opzioni selezionate nella procedura guidata. Per modificare un'opzione, fare clic su **Indietro**. Per avviare l'estrazione di un'applicazione livello dati, fare clic su **Avanti**.  
  
> [!NOTE]  
>  Se uno o più oggetti non sono supportati da una DAC, il pulsante **Avanti** è disabilitato e il processo di estrazione non può continuare. In tal caso, è consigliabile rimuovere gli oggetti non supportati ed eseguire nuovamente la procedura guidata.  
  
 **Riepilogo** n riepilogo delle opzioni selezionate viene visualizzato in **Proprietà DAC**. I risultati della convalida vengono elencati in **Oggetti DAC**. La convalida può dare tre tipi di risultati:  
  
-   **Oggetti inclusi correttamente in DAC**- Questi oggetti e le loro dipendenze sono supportati e possono essere inclusi correttamente nella DAC.  
  
-   **Oggetti inclusi in DAC con avvisi**- Questi oggetti sono supportati, ma dipendono da altri oggetti che non sono supportati in una DAC.  
  
-   **Oggetti non inclusi in DAC**- Questi oggetti non sono supportati e devono essere rimossi dal database prima di estrarre correttamente una DAC.  
  
 Il processo di convalida controlla più livelli delle dipendenze. Ad esempio, se una stored procedure dipende da una tabella che utilizza il tipo di dati CLR non supportato, la stored procedure sarà elencata sotto **Oggetti inclusi in DAC con avvisi**.  
  
 Se uno o più oggetti non sono supportati da una DAC, il pulsante **Avanti** è disabilitato e il processo di estrazione non può continuare. In tal caso, è consigliabile rimuovere gli oggetti non supportati ed eseguire nuovamente questa procedura guidata.  
  
 **Salva report** : consente di salvare nel riepilogo un file basato su HTML che elenca tutti gli oggetti sotto il nodo **Oggetti DAC** . Questo report può essere utile quando alcuni oggetti di database non sono supportati in una DAC. Utilizzare il report per modificare o rimuovere gli oggetti che non sono supportati, prima di tentare di estrarre nuovamente la DAC.  
  
###  <a name="BuildPackage"></a> Pagina Compila pacchetto  
 Utilizzare questa pagina per monitorare l'avanzamento della procedura guidata durante l'estrazione dell'applicazione livello dati.  
  
 **Azione** : durante l'azione **Crea e salva il file del pacchetto di applicazione livello dati** , la procedura guidata estrae un'applicazione livello dati dal database SQL Server. Quindi, nella memoria viene creato un pacchetto di applicazione livello dati che viene salvato nel percorso specificato. Fare clic sui collegamenti nella colonna **Risultato** per vedere il risultato del passaggio corrispondente.  
  
 **Salva report** fare clic per salvare i risultati dello stato della procedura guidata in un file.  
  
 **Fine** fare clic per chiudere la procedura guidata una volta completata o se si verifica un errore.  
  
##  <a name="ExtractDACPowerShell"></a> Estrarre un'applicazione livello dati tramite PowerShell  
 **Per estrarre un'applicazione livello dati da un database con il metodo Extract() in uno script di PowerShell**  
  
1.  Creare un oggetto server SMO e impostarlo sull'istanza contenente il database da cui si desidera estrarre l'applicazione livello dati.  
  
2.  Aggiungere una variabile che specifichi il nome del database.  
  
3.  Specificare i metadati per l'applicazione livello dati, quali nome dell'applicazione livello dati, versione e descrizione.  
  
4.  Specificare il percorso e il nome per il file del pacchetto di applicazione livello dati.  
  
5.  Eseguire il metodo Extract con le informazioni specificate in precedenza.  
  
### <a name="example-powershell"></a>Esempio (PowerShell)  
 L'esempio seguente estrae un'applicazione livello dati denominata MyApplication da un database denominato MyDB.  
  
```  
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = get-item .  
  
## Specify the database to extract to a DAC.  
$dbname = "MyDB"  
  
## Specify the DAC metadata.  
$applicationname = "MyApplication"  
$version = "1.0.0.0"  
$description = "This DAC defines the database used by my application."  
  
## Specify the location and name for the extracted DAC package.  
$dacpacPath = "C:\MyDACs\MyApplication.dacpac"  
  
## Extract the DAC.  
$extractionunit = New-Object Microsoft.SqlServer.Management.Dac.DacExtractionUnit($srv, $dbname, $applicationname, $version)  
$extractionunit.Description = $description  
$extractionunit.Extract($dacpacPath)  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Applicazioni livello dati](data-tier-applications.md)  
  
  

---
title: Creazione di file di Script (AccessToSQL) | Documenti Microsoft
ms.prod: sql
ms.custom: ''
ms.date: 08/17/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 64dfe192-965c-49d4-a3ea-848fbc5f619f
caps.latest.revision: 21
author: Shamikg
ms.author: Shamikg
manager: murato
ms.openlocfilehash: cd6227abb8cc311d16a0eadf6e491f7b82d9f48b
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34773457"
---
# <a name="creating-script-files-accesstosql"></a>Creazione di file di script (AccessToSQL)
Il primo passaggio prima di avviare l'applicazione console SSMA consiste nel creare il file di script e se è necessario creare il file di valore della variabile e il file di connessione del server.  
  
Il file di script può essere suddiviso in tre sezioni, dei quali..,:  
  
1.  **configurazione:** consente all'utente di impostare i parametri di configurazione per l'applicazione console.  
  
2.  **Server:** consente all'utente di impostare l'origine/destinazione le definizioni del server. Questo può essere anche in un file di connessione server separato.  
  
3.  **i comandi script:** consente all'utente di eseguire i comandi del flusso di lavoro SSMA.  
  
Ogni sezione viene descritta in dettaglio di seguito:  
  
## <a name="configuring-access-console-settings"></a>Configurazione delle impostazioni di accesso console  
Le configurazioni di uno script vengono visualizzate nel file di script della console.  
  
Se viene specificato uno degli elementi nel nodo configurazione, vengono impostate come l'impostazione globale, ovvero sono applicabili per tutti i comandi di script. Tali elementi di configurazione possono essere impostati anche all'interno di ogni comando della sezione del comando script se l'utente desidera eseguire l'override dell'impostazione globale.  
  
Le opzioni configurabili dall'utente includono:  
  
1.  **Provider di finestra di output:** se i messaggi esclusione di attributo è impostato su 'true', le specifiche del comando messaggi non viene visualizzati nella console. La descrizione degli attributi è indicata di seguito:  
  
    -   destinazione: Specifica se l'output è necessario ottenere stampato in un file o stdout. Questo è false per impostazione predefinita.  
  
    -   nome del file: il percorso del file (facoltativo).  
  
    -   i messaggi di esclusione: Elimina i messaggi sulla console. Questo è 'false' per impostazione predefinita.  
  
    **Esempio:**  
  
    ```xml  
    <output-providers>  
  
      <output-window  
  
        suppress-messages="<true/false>"   (optional)  
  
        destination="<file/stdout>"        (optional)  
  
        file-name="<file-name>"            (optional)  
  
       />  
  
    </output-providers>  
    ```  
    *o*  
  
    ```xml  
    <…All commands…>  
  
      <output-window  
  
         suppress-messages="<true/false>"   (optional)  
  
         destination="<file/stdout>"        (optional)  
  
         file-name="<file-name>"            (optional)  
  
       />  
  
    </…All commands…>  
    ```  
  
2.  **Il Provider di connessione della migrazione di dati:** consente di specificare quali server di origine/destinazione viene considerato per la migrazione dei dati.  Origine utilizzare-ultimo usato indica l'ultimo server di origine utilizzato viene utilizzato per la migrazione dei dati. Allo stesso modo destinazione utilizzare-ultimo usato indica l'ultimo server di destinazione utilizzato viene utilizzato per la migrazione dei dati. L'utente può anche specificare il server (origine o destinazione) utilizzando il server di origine di attributi o i server di destinazione.  
  
    Solo uno o l'altro attributo specificato può essere utilizzato ad esempio:  
  
    - origine utilizzare-ultimo usato = "true" (impostazione predefinita) o server di origine = "source_servername"  
  
    - destinazione utilizzare-ultimo usato = "true" (impostazione predefinita) o server di destinazione = "target_servername"  
  
    **Esempio:**  
  
    ```xml  
    <output-providers>  
  
      <data-migration-connection   source-use-last-used="true"  
  
                                   target-server="target_1"/>  
  
    </output-providers>  
    ```  
    *o*  
  
    ```xml  
    <migrate-data>  
  
      <data-migration-connection   source-server="source_1"  
  
                                   target-use-last-used="true"/>  
  
    </migrate-data>  
    ```  
  
3.  **Popup di Input dell'utente:** in questo modo la gestione degli errori, quando gli oggetti vengono caricati dal database. L'utente fornisce le modalità di input e, in caso di errore, la console prosegue come se l'utente specifica.  
  
    Le modalità di includono:  
  
    -   **chiedere-utente -** chiede di continue('yes') o generato un errore ('no').  
  
    -   **errore -** la console viene visualizzato un errore e arresta l'esecuzione.  
  
    -   **continuare-** console procede con l'esecuzione.  
  
    La modalità predefinita è **errore**.  
  
    **Esempio:**  
  
    ```xml  
    <output-providers>  
  
      <user-input-popup mode="<ask-user/continue/error>"/>  
  
    </output-providers>  
    ```  
    *o*  
  
    ```xml  
    <!-- Connect to target database -->  
  
    <connect-target-database server="target_0">  
  
      <user-input-popup mode="<ask-user/continue/error>"/>  
  
    </connect-target-database>  
    ```  
  
4.  **Ristabilire la connessione del Provider:** ciò consente all'utente configurare le impostazioni di riconnessione in caso di errori di connessione. Può essere impostato per i server di origine e di destinazione.  
  
    Le modalità di riconnessione sono:  
  
    -   riconnettersi-last-usato-server: se la connessione non è attiva, tenta di ristabilire la connessione e l'ultimo server utilizzato al massimo 5 volte.  
  
    -   generare un errore: se la connessione non è attiva, viene generato un errore.  
  
    La modalità predefinita è **genera un errore**.  
  
    **Esempio:**  
  
    ```xml  
    <output-providers>  
  
     <reconnect-manager on-source-reconnect="<reconnect-to-last-used-server/generate-an-error>"  
  
                        on-target-reconnect="<reconnect-to-last-used-server/generate-an-error>"/>  
  
    </output-providers>  
    ```  
    *o*  
  
    ```xml  
    <!--synchronization-->  
  
    <synchronize-target>  
  
      <reconnect-manager on-target-reconnect="reconnect-to-last-used-server"/>  
  
    </synchronize-target>  
    ```  
    *o*  
  
    ```xml  
    <!--data migration-->  
  
    <migrate-data server="target_0">  
  
      <reconnect-manager  
  
        on-source-reconnect="reconnect-to-last-used-server"  
  
        on-target-reconnect="generate-an-error"/>  
  
    </migrate-data>  
    ```  
  
5.  **Provider di sovrascrittura di convertitore:** ciò consente all'utente di gestire gli oggetti che sono già presenti nella destinazione della metabase. Le possibili azioni includono:  
  
    -   Errore: la console viene visualizzato un errore e arresta l'esecuzione.  
  
    -   sovrascrivere: sovrascrive i valori dell'oggetto esistente. Questa azione viene eseguita per impostazione predefinita.  
  
    -   ignorare: la console ignora gli oggetti che esistono già nel database  
  
    -   utente chiedere: richiede l'input dell'utente ('Sì' / 'no')  
  
    **Esempio:**  
  
    ```xml  
    <output-providers>  
  
      <object-overwrite action="<error|skip|overwrite|ask-user>"/>  
  
    </output-providers>  
    ```  
    *o*  
  
    ```xml  
    <convert-schema object-name="ssma.TT1">  
  
      <object-overwrite action="<error|skip|overwrite|ask-user>"/>  
  
    </convert-schema>  
    ```  
  
6.  **Provider di prerequisiti non riuscito:** in questo modo all'utente di gestire tutti i prerequisiti necessari per l'elaborazione di un comando. Per impostazione predefinita, la modalità strict è 'false'. Se è impostata su 'true', un'eccezione viene generato l'errore soddisfare i prerequisiti.  
  
    **Esempio:**  
  
    ```xml  
    <output-providers>  
  
      <prerequisites strict-mode="<true|false>"/>  
  
    </output-providers>  
    ```  
  
7.  **Operazione di arresto:** durante l'operazione intermedio, se l'utente desidera arrestare l'operazione, quindi **'Ctrl + C'** tasti di scelta rapida può essere utilizzato. SSMA per l'accesso Console rimarrà in attesa di completamento dell'operazione e termina l'esecuzione della console.  
  
    Se l'utente desidera arrestare l'esecuzione immediatamente, quindi, **'Ctrl + C'** tasti di scelta rapida è possibile premere nuovamente per la chiusura improvvisa di applicazione Console di SSMA.  
  
8.  **Provider di stato di avanzamento:** segnala lo stato di avanzamento di ogni comando della console. Questo è disabilitato per impostazione predefinita. Gli attributi di creazione di rapporti di stato includono quanto segue:  
  
    -   off  
  
    -   ogni 1%  
  
    -   ogni 2%  
  
    -   ogni 5%  
  
    -   ogni 10%  
  
    -   ogni 20%  
  
    **Esempio:**  
  
    ```xml  
    <output-providers>  
  
     <progress-reporting enable="<true|false>"           (optional)  
  
                         report-messages="<true|false>"  (optional)  
  
                         report-progress="every-1%|every-2%|every-5%|every-10%|every-20%|off" (optional)/>  
  
    </output-providers>  
    ```  
    *o*  
  
    ```xml  
    <…All commands…>  
  
      <progress-reporting  
  
        enable="<true|false>"              (optional)  
  
        report-messages="<true|false>"     (optional)  
  
        report-progress="every-1%|every-2%|every-5%|every-10%|every-20%|off"     (optional)/>  
  
    </…All commands…>  
    ```  
  
9. **Livello di dettaglio del logger:** set di accedere a livello di dettaglio. Questo corrisponde all'opzione di tutte le categorie nell'interfaccia utente. Per impostazione predefinita, il livello di dettaglio del log è "error".  
  
    Le opzioni a livello di logger includono:  
  
    -   Errore irreversibile: vengono registrati i messaggi solo-errore irreversibile.  
  
    -   Errore: vengono registrati solo i messaggi di errore ed errore irreversibile.  
  
    -   Avviso: tutti i livelli, ad eccezione dei messaggi di debug e le informazioni vengono registrati.  
  
    -   Info: tutti i livelli, ad eccezione del fatto che vengono registrati i messaggi di debug.  
  
    -   eseguire il debug: tutti i livelli di messaggi registrati.  
  
    > [!NOTE]  
    > Messaggi obbligatori vengono registrati in qualsiasi livello.  
  
    **Esempio:**  
  
    ```xml  
    <output-providers>  
  
      <log-verbosity level="fatal-error/error/warning/info/debug"/>  
  
    </output-providers>  
    ```  
    *o*  
  
    ```xml  
    <…All commands…>  
  
      <log-verbosity level="fatal-error/error/warning/info/debug"/>  
  
    </…All commands…>  
    ```  
  
10. **Password crittografata di sostituzione:** se 'true', la password come testo non crittografato specificato è nell'area di definizione di server dei file di connessione del server o nel file di script, le sostituzioni archiviata spazio di archiviazione protetto, se presente. Se non viene specificata in testo non crittografato, l'utente viene richiesto di immettere la password.  
  
    In questo caso, si verificano due casi:  
  
    1.  Se ignorare l'opzione è **false**, l'ordine di ricerca sarà protetto archiviazione -&gt;File Script -&gt;File connessione Server -&gt; Chiedi conferma all'utente.  
  
    2.  Se l'opzione di override è **true**, sarà l'ordine di ricerca di File di Script -&gt;File connessione Server -&gt;Chiedi conferma all'utente.  
  
    **Esempio:**  
  
    ```xml  
    <output-providers>  
  
      <encrypted-password override="<true/false>"/>  
  
    </output-providers>  
    ```  
  
È l'opzione non è configurabile.  
  
-   **Numero massimo di tentativi di riconnessione:** quando una connessione stabilita verifica il timeout o interruzioni a causa di errori di rete, il server è necessario per essere riconnessa. I tentativi di riconnessione è consentiti un massimo di **5** tentativi dopo il quale, la console viene eseguita automaticamente la riconnessione. La funzionalità di riconnessione automatica consente di ridurre il lavoro richiesto nell'eseguire nuovamente lo script.  
  
## <a name="server-connection-parameters"></a>Parametri di connessione server  
Parametri di connessione di server possono essere definiti nel file di script o nel file di connessione del server. Consultare il [creano i file di connessione del Server &#40;AccessToSQL&#41; ](../../ssma/access/creating-the-server-connection-files-accesstosql.md) sezione per ulteriori dettagli.  
  
## <a name="script-commands"></a>Comandi script  
Il file script contiene una sequenza di comandi del flusso di lavoro di migrazione in formato XML. L'applicazione console SSMA elabora la migrazione nell'ordine i comandi visualizzati nel file di script.  
  
Ad esempio, una migrazione di dati tipici di una tabella specifica in un database di Access segue la gerarchia di: Database -&gt; tabella.  
  
Quando tutti i comandi nel file di script vengono eseguiti correttamente, l'applicazione console SSMA viene chiusa e restituisce il controllo all'utente. Il contenuto di un file script è più o meno statica con informazioni sulla variabile contenuti in un [file valore variabile](http://msdn.microsoft.com/808595c3-8ef1-40bd-a93e-5cf237950e08) o, in una sezione separata all'interno del file di script per i valori delle variabili.  
  
**Esempio:**  
  
```xml  
<!--Sample of script file commands -->  
  
<ssma-script-file>  
  
  <script-commands>  
  
    <create-new-project project-folder="$project_folder$"  
  
                        project-name="$project_name$"  
  
                        overwrite-if-exists="true"/>  
  
    <connect-source-database server="source_2"/>  
  
    <save-project/>  
  
    <close-project/>  
  
  </script-commands>  
  
</ssma-script-file>  
```  
Modelli costituito da 3 file di script (per l'esecuzione di vari scenari di), file di valore della variabile e un file di connessione del server sono disponibili nella cartella Scripts Console di esempio di directory del prodotto:  
  
-   AssessmentReportGenerationSample.xml  
  
-   ConversionAndDataMigrationSample.xml  
  
-   VariableValueFileSample.xml  
  
-   ServersConnectionFileSample.xml  
  
È possibile eseguire i modelli (file) dopo la modifica dei parametri visualizzati al suo interno per rilevanza.  
  
Elenco completo dei comandi di script è reperibile nella [in esecuzione la Console di SSMA &#40;AccessToSQL&#41;](../../ssma/access/executing-the-ssma-console-accesstosql.md)  
  
## <a name="script-file-validation"></a>Convalida file di script  
L'utente può facilmente convalidare il file di script nel file di definizione dello schema **'A2SSConsoleScriptSchema.xsd'** disponibile nella cartella 'Schemi'.  
  
## <a name="next-step"></a>Passaggio successivo
Il passaggio successivo nella console di gestione viene [creazione di file di valore variabile &#40;AccessToSQL&#41;](../../ssma/access/creating-variable-value-files-accesstosql.md).  
  
## <a name="see-also"></a>Vedere anche  
[Creazione di file di valore della variabile &#40;AccessToSQL&#41;](../../ssma/access/creating-variable-value-files-accesstosql.md)  
  

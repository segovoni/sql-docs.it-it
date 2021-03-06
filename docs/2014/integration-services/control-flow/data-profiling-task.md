---
title: Attività Profiling dati | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataprofilingtask.f1
helpviewer_keywords:
- Data Profiling task [Integration Services], about Data Profiling task
- data profiling
- profiling data
ms.assetid: 248ce233-4342-42c5-bf26-f4387ea152cf
caps.latest.revision: 32
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 48075a70eba052e6996fa096cde9f8f3b5f946e2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37213541"
---
# <a name="data-profiling-task"></a>Attività Profiling dati
  L'attività Profiling dati calcola i diversi profili che consentono di familiarizzare con un'origine dati e identificare i problemi nei dati che devono essere corretti.  
  
 È possibile utilizzare l'attività Profiling dati in un pacchetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] per eseguire il profiling dei dati archiviati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e identificare i possibili problemi relativi alla qualità dei dati.  
  
> [!NOTE]  
>  In questo argomento vengono descritti i requisiti e le caratteristiche dell'attività Profiling dati. Per la procedura dettagliata relativa all'uso dell'attività Profiling dati, vedere la sezione [Attività Profiling dati e visualizzatore](data-profiling-task-and-viewer.md).  
  
## <a name="requirements-and-limitations"></a>Requisiti e limitazioni  
 L'attività Profiling dati funziona solo con i dati archiviati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L'attività non funziona con origini dati di terze parti o basate su file.  
  
 Per eseguire un pacchetto contenente l'attività Profiling dati, inoltre, è necessario utilizzare un account che disponga di autorizzazioni di lettura/scrittura per il database tempdb.  
  
## <a name="data-profiler-viewer"></a>Visualizzatore profiler dati  
 Dopo avere utilizzato l'attività per calcolare i profili dei dati e salvare tali profili in un file, è possibile utilizzare il Visualizzatore profilo dati autonomo per esaminare l'output del profilo. Il Visualizzatore profilo dati supporta anche la funzione drill-down che consente di analizzare i problemi di qualità dei dati identificati nell'output del profilo. Per altre informazioni, vedere [Visualizzatore profilo dati](data-profile-viewer.md).  
  
> [!IMPORTANT]  
>  Il file di output potrebbe contenere dati sensibili relativi al database e i dati inclusi nel database. Per suggerimenti su come migliorare la sicurezza di questo file, vedere [Accesso ai file utilizzati dai pacchetti](../access-to-files-used-by-packages.md).  
>   
>  La funzionalità di drill-down, disponibile nel Visualizzatore profilo dati, consente di inviare query in tempo reale all'origine dati originale.  
  
## <a name="available-profiles"></a>Profili disponibili  
 L'attività Profiling dati consente di calcolare otto profili dati diversi. Cinque di questi profili analizzano singole colonne e i tre rimanenti analizzano più colonne o relazioni tra colonne e tabelle.  
  
 Nei cinque profili seguenti vengono analizzate colonne singole.  
  
|Profili che analizzano colonne singole|Description|  
|----------------------------------------------|-----------------|  
|Profilo Distribuzione lunghezze di colonna|Segnala tutte le singole lunghezze dei valori stringa nella colonna selezionata e la percentuale di righe nella tabella che ogni lunghezza rappresenta.<br /><br /> Questo profilo consente di identificare problemi nei dati, ad esempio valori non validi. Si analizza, ad esempio, una colonna che contiene i codici degli stati degli Stati Uniti a due caratteri e si individuano valori con lunghezza superiore a due caratteri.|  
|Profilo Rapporto di valori Null nella colonna|Segnala la percentuale di valori Null nella colonna selezionata.<br /><br /> Questo profilo consente di identificare problemi nei dati, ad esempio un rapporto di valori di colonna Null inaspettatamente elevato. Si analizza, ad esempio, una colonna contenente CAP e si individua una percentuale eccessivamente elevata di codici mancanti.|  
|Profilo Criteri di ricerca colonna|Segnala un set di espressioni regolari che coprono la percentuale specificata di valori in una colonna stringa.<br /><br /> Questo profilo consente di identificare problemi nei dati, ad esempio stringhe non valide. Questo profilo può inoltre indicare espressioni regolari che possono essere utilizzate in futuro per convalidare nuovi valori. Un profilo di criteri di ricerca di una colonna contenente codici postali ZIP (Stati Uniti) potrebbe ad esempio produrre le seguenti espressioni regolari: \d{5}-\d{4}, \d{5} e \d{9}. Se vengono visualizzate altre espressioni regolari, è probabile che i dati contengano valori non validi o in formato non corretto.|  
|Profilo Statistiche di colonna|Segnala le statistiche, ad esempio minimo, massimo, medio e deviazione standard per le colonne numeriche e minima e massima per `datetime` colonne.<br /><br /> Questo profilo consente di identificare problemi nei dati, ad esempio date non valide. Si analizza, ad esempio, una colonna di date cronologiche e si individua una data massima successiva alla data corrente.|  
|Profilo Distribuzione valori di colonna|Segnala tutti i valori distinct nella colonna selezionata e la percentuale di righe nella tabella che ogni valore rappresenta. Può inoltre segnalare valori che rappresentano più di una percentuale specificata di righe nella tabella.<br /><br /> Questo profilo consente di identificare problemi nei dati, ad esempio un numero non corretto di valori distinct in una colonna. Si analizza, ad esempio, una colonna che si suppone contenga gli stati degli Stati Uniti e si individuano più di 50 valori distinct.|  
  
 I seguenti tre profili analizzano più colonne o relazioni tra colonne e tabelle.  
  
|Profili che consentono di analizzare più colonne|Description|  
|--------------------------------------------|-----------------|  
|Profilo Chiave candidata|Segnala se una colonna o un set di colonne è una chiave o una chiave approssimativa, per la tabella selezionata.<br /><br /> Questo profilo consente inoltre di identificare problemi nei dati, ad esempio valori duplicati in una potenziale colonna chiave.|  
|Profilo Dipendenza funzionale|Segnala la misura in cui i valori in una colonna (la colonna dipendente) dipendono dai valori in un'altra colonna o in un set di colonne (la colonna determinante).<br /><br /> Questo profilo consente inoltre di identificare problemi nei dati, ad esempio valori non validi. Si analizza, ad esempio, la dipendenza tra una colonna che contiene i codici postali ZIP (Stati Uniti) e una colonna che contiene gli stati degli Stati Uniti. Benché uno stesso codice postale debba essere sempre associato allo stesso stato, il profilo individua alcune violazioni di questa dipendenza.|  
|Profilo di inclusione di valori|Consente di calcolare la sovrapposizione nei valori tra due colonne o set di colonne. Questo profilo può determinare se una colonna o un set di colonne è adatto per fungere da chiave esterna tra le tabelle selezionate.<br /><br /> Questo profilo consente inoltre di identificare problemi nei dati, ad esempio valori non validi. Si analizza, ad esempio, la colonna ProductID di una tabella Sales e si individua che la colonna contiene valori non disponibili nella colonna ProductID della tabella Products.|  
  
## <a name="prerequisites-for-a-valid-profile"></a>Prerequisiti per un profilo valido  
 Un profilo non è valido se non vengono selezionate tabelle e colonne non vuote e colonne che contengono tipi di dati validi per il profilo.  
  
### <a name="valid-data-types"></a>Tipi di dati validi  
 Alcuni dei profili disponibili sono significativi solo per determinati tipi di dati. Ad esempio, il calcolo di un profilo di criteri di ricerca colonna per una colonna che contiene valori numerici o `datetime` non è significativo e quindi tale profilo non è valido.  
  
|Profilo|Tipi di dati validi*|  
|-------------|------------------------|  
|ColumnStatisticsProfile|Colonne di tipo numerico o di tipo `datetime` (no `mean` e `stddev` per la colonna `datetime`)|  
|ColumnNullRatioProfile|Tutte le colonne**|  
|ColumnValueDistributionProfile|Colonne di `integer` , digitare `char` tipo, e `datetime` tipo|  
|ColumnValueDistributionProfile|Colonne di `char` tipo|  
|ColumnPatternProfile|Colonne di `char` tipo|  
|CandidateKeyProfile|Colonne di `integer` , digitare `char` tipo, e `datetime` tipo|  
|FunctionalDependencyProfile|Colonne di `integer` , digitare `char` tipo, e `datetime` tipo|  
|InclusionProfile|Colonne di `integer` , digitare `char` tipo, e `datetime` tipo|  
  
 \* Nella tabella precedente di tipi di dati valido, il `integer`, `char`, `datetime`, e `numeric` includono i tipi di dati specifici seguenti:  
  
 I tipi integer includono `bit`, `tinyint`, `smallint`, `int` e `bigint`.  
  
 I tipi carattere includono `char`, `nchar`, `varchar` e `nvarchar,`, ma non `varchar(max)` e `nvarchar(max)`.  
  
 I tipi di data e ora includono `datetime`, `smalldatetime` e `timestamp`.  
  
 I tipi numerici includono `integer` tipi (eccetto `bit`), `money`, `smallmoney`, `decimal`, `float`, `real`, e `numeric`.  
  
 \*\* `image`, `text`, `XML`, `udt`, e `variant` tipi non sono supportati per profili diversi dal profilo rapporto di colonna Null.  
  
### <a name="valid-tables-and-columns"></a>Tabelle e colonne valide  
 Se la tabella o la colonna è vuota, l'attività Profiling dati esegue le seguenti azioni:  
  
-   Quando la tabella o la vista selezionata è vuota, l'attività Profiling dati non calcola i profili.  
  
-   Quando tutti i valori nella colonna selezionata sono Null, l'attività Profiling dati calcola solo il profilo del rapporto di valori di colonna Null. L'attività non calcola il profilo della distribuzione della lunghezza di colonna, il profilo criteri di ricerca colonna, il profilo di statistiche di colonna o il profilo di distribuzione dei valori di colonna.  
  
## <a name="features-of-the-data-profiling-task"></a>Caratteristiche dell'attività Profiling dati  
 L'attività Profiling dati presenta le seguenti opzioni di configurazione di facile utilizzo:  
  
-   **Colonne jolly** Quando si configura una richiesta di profilo, l'attività accetta il carattere jolly **(\*)** al posto del nome di colonna. In questo modo viene semplificata la configurazione e diventa più facile individuare le caratteristiche dei dati non noti. Quando viene eseguita l'attività, è possibile analizzare ciascuna colonna che presenta un tipo di dati adatto.  
  
-   **Profilo rapido** You can select Profilo rapido to configure the task quickly. Un profilo rapido analizza una tabella o una vista utilizzando tutti i profili e le impostazioni predefiniti.  
  
## <a name="custom-logging-messages-available-on-the-data-profililng-task"></a>Messaggi di registrazione personalizzati disponibili nell'attività Profiling dati  
 Nella tabella seguente sono elencate le voci di log personalizzate disponibili per l'attività Profiling dati. Per altre informazioni, vedere [Registrazione di Integration Services &#40;SSIS&#41;](../performance/integration-services-ssis-logging.md) e [Messaggi personalizzati per la registrazione](../custom-messages-for-logging.md).  
  
|Voce di log|Description|  
|---------------|-----------------|  
|**DataProfilingTaskTrace**|Fornisce informazioni descrittive sullo stato dell'attività. I messaggi includono le informazioni seguenti:<br /><br /> Avvio elaborazione richieste<br /><br /> Inizio query<br /><br /> Query End<br /><br /> Fine calcolo richiesta|  
  
## <a name="output-and-its-schema"></a>Output e relativo schema  
 L'attività Profiling dati restituisce i profili selezionati in un formato XML strutturato in base allo schema DataProfile.xsd. È possibile specificare se questo output XML è salvato in un file o in una variabile del pacchetto. È possibile visualizzare questo schema online all'indirizzo [http://schemas.microsoft.com/sqlserver/2008/DataDebugger/](http://schemas.microsoft.com/sqlserver/2008/DataDebugger/). Nella pagina Web è possibile salvare una copia locale dello schema. È quindi possibile visualizzare la copia locale dello schema in Microsoft [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] o in un altro editor di schemi, in un editor XML o in un editor di testo come Blocco note.  
  
 Questo schema per informazioni sulla qualità dei dati può essere utile per:  
  
-   Scambio delle informazioni sulla qualità di dati all'interno delle organizzazioni e tra organizzazioni diverse.  
  
-   Compilazione di strumenti personalizzati da utilizzare con le informazioni sulla qualità dei dati.  
  
 Lo spazio dei nomi di destinazione viene identificato nello schema come [http://schemas.microsoft.com/sqlserver/2008/DataDebugger/](http://schemas.microsoft.com/sqlserver/2008/DataDebugger/).  
  
## <a name="output-in-the-conditional-workflow-of-a-package"></a>Output nel flusso di lavoro condizionale di un pacchetto  
 I componenti di profiling dei dati non includono la funzionalità predefinita per implementare la logica condizionale nel flusso di lavoro del pacchetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] basata sull'output dell'attività Profiling dati. È tuttavia facile aggiungere questa logica con una programmazione minima in un'attività Script. Con questo codice verrebbe eseguita una query XPath sull'output XML e quindi il risultato verrebbe salvato in una variabile del pacchetto. I vincoli di precedenza che collegano l'attività Script alle attività successive possono utilizzare un'espressione per determinare il flusso di lavoro. Ad esempio, l'attività Script rileva che la percentuale di valori Null in una colonna supera una determinata soglia. Quando questa condizione è vera, potrebbe essere necessario interrompere il pacchetto e risolvere il problema prima di continuare.  
  
## <a name="configuration-of-the-data-profiling-task"></a>Configurazione dell'attività Profiling dati  
 Configurare l'attività Profiling dati utilizzando **Editor attività Profiling dati**. L'editor è composto da due pagine:  
  
 [Pagina Generale](../general-page-of-integration-services-designers-options.md)  
 Nella pagina **Generale** viene specificato il file di output o la variabile. È inoltre possibile selezionare **Profilo rapido** per configurare rapidamente l'attività per il calcolo dei profili utilizzando le impostazioni predefinite. Per altre informazioni, vedere [Single Table Quick Profile Form &#40;Data Profiling Task&#41;](data-profiling-task.md).  
  
 [Pagina richieste del profilo](data-profiling-task-editor-profile-requests-page.md)  
 Nella pagina **Richieste profilo** specificare l'origine dati e quindi selezionare e configurare i profili dei dati che si vogliono calcolare. Per ulteriori informazioni sui diversi profili che è possibile configurare, vedere gli argomenti seguenti:  
  
-   [Opzioni di richiesta profilo chiave candidata &#40;attività Profiling dati&#41;](candidate-key-profile-request-options-data-profiling-task.md)  
  
-   [Opzioni di richiesta profilo distribuzione lunghezze di colonna &#40;attività Profiling dati&#41;](column-length-distribution-profile-request-options-data-profiling-task.md)  
  
-   [Opzioni di richiesta profilo rapporto di valori Null di colonna &#40;attività Profiling dati&#41;](column-null-ratio-profile-request-options-data-profiling-task.md)  
  
-   [Opzioni di richiesta profilo criteri di ricerca colonna &#40;attività Profiling dati&#41;](column-pattern-profile-request-options-data-profiling-task.md)  
  
-   [Opzioni di richiesta profilo statistiche di colonna &#40;attività Profiling dati&#41;](column-statistics-profile-request-options-data-profiling-task.md)  
  
-   [Opzioni di richiesta profilo distribuzione valori di colonna &#40;attività Profiling dati&#41;](column-value-distribution-profile-request-options-data-profiling-task.md)  
  
-   [Opzioni di richiesta profilo dipendenza funzionale &#40;attività Profiling dati&#41;](functional-dependency-profile-request-options-data-profiling-task.md)  
  
-   [Opzioni di richiesta profilo inclusione valore &#40;attività Profiling dati&#41;](value-inclusion-profile-request-options-data-profiling-task.md)  
  
  

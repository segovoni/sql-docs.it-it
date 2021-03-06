---
title: Esportazione in Microsoft Word (Generatore report e SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 0cd8ae26-4682-4473-8f15-af084951defd
caps.latest.revision: 20
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 9aa5b777f8e05b9a3bd8784c15ae8294e9caa8bb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37264277"
---
# <a name="exporting-to-microsoft-word-report-builder-and-ssrs"></a>Esportazione in Microsoft Word (Generatore report e SSRS)
  Estensione per il rendering Word esegue il rendering dei report nel formato nativo di [!INCLUDE[ofprword](../../includes/ofprword-md.md)] 2007-2010. Il formato è Office Open XML.  
  
 Il rendering di Word è compatibile con [!INCLUDE[ofprword](../../includes/ofprword-md.md)] 2007-2010 e con [!INCLUDE[ofprword](../../includes/ofprword-md.md)] 2003 grazie a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Compatibility Pack per i formati di file Word, Excel e PowerPoint. Per altre informazioni su Compatibility Pack, vedere [Microsoft Office Compatibility Pack per i formati di file Word, Excel e PowerPoint](http://go.microsoft.com/fwlink/?LinkID=205622).  
  
 Il tipo di contenuto di file generati da questo renderer è **application/vnd.openxmlformats-officedocument.wordprocessingml.document** mentre l'estensione del nome dei file è docx.  
  
 La versione precedente dell'estensione per il rendering di Word, compatibile con [!INCLUDE[ofprword](../../includes/ofprword-md.md)] 2003, è rinominata Word 2003. Per impostazione predefinita, è disponibile solo l'estensione per il rendering di Word. È necessario aggiornare i file di configurazione di Reporting Services per rendere disponibile l'estensione per il rendering di Word 2003. Il tipo di contenuto di file generati dal renderer di Word 2003 è **application/vnd.ms-word** mentre l'estensione di file è doc.  
  
> [!IMPORTANT]  
>  Il [!INCLUDE[ofprword](../../includes/ofprword-md.md)] estensione per il rendering 2003 è deprecata. Per altre informazioni, vedere [Deprecated Features di SQL Server Reporting Services in SQL Server 2014](../deprecated-features-in-sql-server-reporting-services-ssrs.md).  
  
 Dopo l'esportazione del report in un documento di Word, è possibile modificarne il contenuto e progettare report in formato documento, ad esempio etichette di indirizzi, ordini di acquisto o lettere tipo.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="ReportItemsWord"></a> Elementi del report in Word  
 I report esportati in Word vengono visualizzati sotto forma di una tabella nidificata che rappresenta il corpo del report. Il rendering di un'area dati Tablix viene eseguito come tabella nidificata che riflette la struttura dell'area dati nel report, mentre quello di caselle di testo e rettangoli viene eseguito come celle all'interno della tabella. Il valore della casella di testo viene visualizzato all'interno della cella.  
  
 Il rendering di immagini, grafici, barre di dati, grafici sparkline, mappe, indicatori e misuratori viene eseguito come immagini statiche all'interno delle celle della tabella. Vengono sottoposti a rendering i collegamenti ipertestuali e i collegamenti drill-through presenti in questi elementi del report. Le mappe e le aree su cui è possibile fare clic all'interno di un grafico non sono supportate.  
  
 I report a colonne in formato newsletter non vengono sottoposti a rendering in Word. Il rendering di colori e immagini di sfondo delle pagine e del corpo del report non viene eseguito.  
  
##  <a name="Pagination"></a> Paginazione  
 Dopo l'apertura in Word, l'intero report viene rimpaginato in base alle dimensioni della pagina. La rimpaginazione può causare l'inserimento di interruzioni di pagina in posizioni non previste e, in alcuni casi, la presenza nel report esportato di due interruzioni di pagina consecutive in una riga o l'aggiunta di pagine vuote. È possibile tentare di modificare la paginazione di Word regolando i margini della pagina.  
  
 Questo renderer supporta solo interruzioni di pagina logiche.  
  
### <a name="page-sizing"></a>Ridimensionamento della pagina  
 Per il rendering del report, l'altezza e la larghezza della pagina in Word vengono impostate in base alle seguenti proprietà RDL: altezza e larghezza delle dimensioni della pagina, margini sinistro e destro della pagina e margini superiore e inferiore della pagina.  
  
### <a name="page-width"></a>Larghezza della pagina  
 Word supporta una larghezza di pagina massima di 56 centimetri. Se la larghezza del report è maggiore di 56 centimetri, il rendering del report verrà comunque eseguito, ma il contenuto del report non verrà visualizzato in visualizzazione Layout di stampa o Layout lettura di Word. Per visualizzare i dati, passare alla visualizzazione Normale o Layout Web. Poiché in queste visualizzazioni di Word la quantità di spazi vuoti viene ridotta, è possibile visualizzare un'area maggiore del contenuto del report.  
  
 Dopo il rendering, la larghezza del report aumenta se necessario fino a un massimo di 56 centimetri, per consentire la visualizzazione del contenuto. La larghezza minima del report è basata sulla proprietà RDL Width nel riquadro Proprietà.  
  
##  <a name="DocumentProperties"></a> Proprietà del documento  
 Il renderer di Word consente di scrivere i metadati seguenti nel file DOCX.  
  
|Proprietà degli elementi del report|Description|  
|-------------------------------|-----------------|  
|Report Title (titolo del report)|Title|  
|Report.Author|Autore|  
|Report.Description|Commenti|  
  
##  <a name="ReportHeadersFooters"></a> Intestazioni di pagina e piè di pagina  
 Per le intestazioni e i piè di pagina il rendering viene eseguito come aree di intestazione e piè di pagina in Word. Se nell'intestazione o nel piè di pagina è visualizzato un numero di pagina o un'espressione che indica il numero complessivo di pagine del report, questi valori vengono convertiti in un campo di Word. In questo modo, nel report visualizzabile appare il numero di pagina preciso. L'eventuale impostazione nel report dell'altezza dell'intestazione o del piè di pagina non è supportata in Word. In alcune circostanze, la proprietà PrintOnFirstPage può specificare se il testo di un'intestazione e di un piè di pagina viene stampato nella prima pagina di un report. Se il report visualizzabile è costituito da più pagine e in ognuna di esse è presente un'unica sezione, la proprietà PrintOnFirstPage può essere impostata su False in modo che il testo venga eliminato dalla prima pagina; in caso contrario, il testo viene stampato indipendentemente dal valore della proprietà PrintOnFirstPage.  
  
 Tramite il renderer di Word viene tentata l'analisi di tutte le espressioni delle intestazioni e dei piè di pagina quando i report vengono esportati in Word. Molte forme di espressioni vengono analizzate correttamente e i valori previsti vengono visualizzati nei piè di pagina e nelle intestazioni di tutte le pagine dei report.  
  
 Tuttavia, se in un'intestazione o piè di pagina è presente un'espressione complessa mediante la quale vengono restituiti valori diversi in pagine differenti di un report, in tutte le pagine del report potrebbe essere visualizzato lo stesso valore. I numeri di pagina nelle due espressioni seguenti non vengono incrementati nel report esportato. Il numero viene convertito nello stesso valore in tutte le pagine del report.  
  
-   `="Page: " + Globals!PageNumber.ToString + " of " + Globals!TotalPages.ToString`  
  
-   `=Avg(Fields!YTDPurchase.Value, "Sales") & " Page Number " & Globals!PageNumber`  
  
 Questa situazione si verifica in quanto tramite il renderer di Word nel report viene eseguita l'analisi dei campi correlati alla paginazione, ad esempio **PageNumber** e **TotalPages** , e viene gestito solo un riferimento semplice, non le chiamate a una funzione. In questo caso, tramite l'espressione viene chiamata la funzione **ToString** . Le due espressioni seguenti sono equivalenti ed entrambe consentono di eseguire correttamente il rendering quando il report viene visualizzato in anteprima in Generatore report o Progettazione report o viene eseguito il rendering del report pubblicato in Gestione report o in una raccolta di SharePoint. Tuttavia, il renderer di Word consente di analizzare correttamente solo la seconda espressione ed eseguire il rendering dei numeri di pagina corretti.  
  
-   **Espressione complessa:**  l'espressione è `="Average Sales " & Avg(Fields!YTDPurchase.Value, "Sales") & " Page Number " & Globals!PageNumber`  
  
-   **Espressione con sequenze di testo:** testo, **Average Sales**, espressione,  `=Avg(Fields!YTDPurchase.Value, "Sales)`, testo, **Page Number**ed espressione `=Globals!PageNumber`  
  
 Per evitare questo problema, usare più sequenze di testo invece di una sola espressione complessa quando si usano espressioni nei piè di pagina e nelle intestazioni. Le due espressioni seguenti sono equivalenti. La prima è un'espressione complessa, mentre nella seconda vengono utilizzate sequenze di testo. Il renderer di Word consente di analizzare correttamente solo la seconda espressione.  
  
##  <a name="Interactivity"></a> Interattività  
 Alcuni elementi interattivi sono supportati in Word. Di seguito è riportata una descrizione di comportamenti specifici.  
  
### <a name="show-and-hide"></a>Elementi visualizzati e nascosti  
 Il renderer di Word esegue il rendering degli elementi del report in base al relativo stato corrente. Se un elemento del report ha lo stato impostato come nascosto, tale elemento non verrà sottoposto a rendering nel documento di Word. Un elemento del report il cui stato è impostato come visualizzato verrà sottoposto a rendering nel documento di Word. La funzionalità di attivazione e disattivazione della visualizzazione non è supportata in Word.  
  
### <a name="document-map"></a>Mappa documento  
 Se il report contiene etichette della mappa documento, queste verranno sottoposte a rendering come etichette di sommario di Word nei rispettivi elementi e gruppi del report. L'etichetta della mappa documento viene utilizzata come testo delle etichette di sommario. Il collegamento di destinazione viene posizionato accanto all'elemento su cui è impostata l'etichetta. Anche se nel documento di Word non viene automaticamente creato un sommario, è possibile compilarne uno utilizzando le etichette della mappa documento visualizzate nel report.  
  
### <a name="hyperlink-and-drillthrough-links"></a>Collegamenti ipertestuali e collegamenti drill-through  
 Per i collegamenti ipertestuali e i collegamenti drill-through presenti negli elementi del report di tipo casella di testo e immagine, il rendering viene eseguito come collegamenti ipertestuali nel documento di Word. Quando si fa clic sul collegamento ipertestuale, il browser Web predefinito viene aperto in corrispondenza dell'URL. Quando si fa clic sul collegamento ipertestuale drill-through, si accede al server di report di origine.  
  
### <a name="interactive-sorting"></a>Ordinamento interattivo  
 Il rendering del contenuto del report viene eseguito in base all'ordinamento corrente nell'area dati del report. L'ordinamento interattivo non è supportato in Word. Dopo il rendering del report, è possibile applicare l'ordinamento della tabella all'interno di Word.  
  
### <a name="bookmarks"></a>Segnalibri  
 Per i segnalibri del report viene eseguito il rendering come segnalibri di Word. Il rendering dei collegamenti a un segnalibro viene eseguito come collegamenti ipertestuali che consentono di accedere alle etichette di segnalibro all'interno del documento. Le etichette di segnalibro devono contenere meno di 40 caratteri. L'unico carattere speciale che è possibile utilizzare in queste etichette è il carattere di sottolineatura (_). I caratteri speciali non supportati vengono rimossi dal nome dell'etichetta di segnalibro. Il nome viene inoltre troncato se costituito da più di 40 caratteri. Se il report contiene nomi di segnalibro duplicati, il rendering dei segnalibri non verrà eseguito in Word.  
  
##  <a name="WordStyleRendering"></a> Rendering dello stile in Word  
 Di seguito è riportata una breve descrizione della modalità di rendering degli stili in Word.  
  
### <a name="color-palette"></a>Tavolozza dei colori  
 I colori visualizzati nel report vengono sottoposti a rendering nel documento di Word.  
  
### <a name="border"></a>Bordo  
 Per i bordi degli elementi del report, ad eccezione del bordo della pagina, viene eseguito il rendering come bordi di celle di tabella di Word.  
  
##  <a name="SquigglyLines"></a> Righe ondulate nei report esportati  
 Quando esportati e visualizzati in Word, costanti o dati del report potrebbero essere sottolineati con righe ondulate rosse o verdi. Con le righe ondulate rosse vengono identificati gli errori di ortografia, con quelle verdi gli errori grammaticali. Questa situazione si verifica quando nel report sono incluse parole non conformi agli strumenti di correzione (controllo ortografia e grammatica) della lingua di modifica specificata in Word. Ad esempio, i titoli in inglese di colonne del report probabilmente saranno sottolineati con righe ondulate rosse se viene eseguito il rendering del report in una versione spagnola di Word. Gli errori ortografici percepiti sono più comuni nei report rispetto a quelli grammaticali in quanto nei report sono inclusi in genere solo testi brevi, non paragrafi o frasi intere.  
  
 La presenza di righe ondulate nei report implica la presenza di errori nel report che probabilmente non esistono. È possibile rimuovere le righe ondulate cambiando la lingua degli strumenti di correzione per il report. Per cambiare la lingua degli strumenti di correzione, selezionare il contenuto del report e specificare la lingua appropriata per tale contenuto. È possibile selezionare una parte o l'intero contenuto. In Word 2010, l'opzione relativa alla lingua, **Imposta lingua di modifica**, si trova nella scheda **Rivedere** nell'area **Lingua** . Al termine dell'aggiornamento del contenuto, è necessario salvare di nuovo il documento.  
  
 A seconda della lingua della versione di Office in uso, gli strumenti di correzione (ad esempio, il dizionario) della lingua scelta sono inclusi nel programma o forniti in un Language Pack di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office acquistato.  
  
 Negli argomenti seguenti vengono fornite ulteriori informazioni sull'impostazione delle opzioni di Word e di Office.  
  
-   Cambiare la lingua di modifica nella finestra di dialogo **Preferenze di lingua di Microsoft Office 2010** o **Opzioni di Word** in Word. Per altre informazioni, vedere [Impostazione delle preferenze di lingua per la modifica, l'interfaccia utente o la Guida](http://office.microsoft.com/word-help/enable-the-use-of-other-languages-in-your-office-programs-HA010354783.aspx?CTT=1).  
  
-   Aggiungere i Language Pack di Office e cambiare la lingua di modifica. Per altre informazioni, vedere [Impostazione delle preferenze di lingua per la modifica, l'interfaccia utente o la Guida](http://office.microsoft.com/word-help/enable-the-use-of-other-languages-in-your-office-programs-HA010354783.aspx?CTT=1) e [Opzioni disponibili per Office 2010](http://office.microsoft.com/language/).  
  
> [!NOTE]  
>  Quando si cambia la lingua di modifica nella finestra di dialogo **Preferenze di lingua di Microsoft Office 2010** o **Opzioni di Word** in Word, la modifica viene applicata a tutti i programmi di Office.  
  
##  <a name="WordLimitations"></a> Limitazioni di Word  
 In [!INCLUDE[ofprword](../../includes/ofprword-md.md)]vengono applicate le limitazioni seguenti:  
  
-   Le tabelle di Word supportano un massimo di 63 colonne. Se il report contiene più di 63 colonne e si tenta di eseguirne il rendering, la tabella viene divisa in Word. Le colonne aggiuntive vengono posizionate accanto alle 63 colonne visualizzate nel corpo del report. Pertanto, è possibile che le colonne del report non siano allineate come previsto.  
  
-   Word supporta pagine di dimensioni massime pari a 56 centimetri di larghezza e 56 centimetri di altezza. Se la larghezza del contenuto è maggiore di 56 centimetri, è possibile che alcuni dati non vengano visualizzati in visualizzazione Layout di stampa.  
  
-   Le impostazioni relative all'altezza dell'intestazione e del piè di pagina vengono ignorate in Word.  
  
-   Dopo l'esportazione, il report viene rimpaginato in Word. Questo può causare l'aggiunta di altre interruzioni di pagina nel report visualizzabile.  
  
-   Word non Ripeti righe intestazione in pagina 2 e versioni successive, anche se si imposta la proprietà RepeatOnNewPage della riga di intestazione statica di una tablix (tabella, matrice o elenco) `True`. È possibile definire interruzioni di pagina esplicite nel report per forzare la visualizzazione delle righe di intestazione nelle nuove pagine. Poiché tuttavia al report visualizzabile esportato in Word viene applicata la paginazione specifica di Word, i risultati potrebbero variare e la riga di intestazione potrebbe non essere ripetuta in modo prevedibile. La riga di intestazione statica è la riga contenente le intestazioni di colonna.  
  
-   Le dimensioni delle caselle di testo aumentano quando contengono spazi unificatori.  
  
-   Quando viene esportato in Word, il testo con effetti carattere in alcuni tipi di carattere può generare glifi imprevisti o mancanti nel report visualizzabile.  
  
##  <a name="WordBenefits"></a> Vantaggi dell'utilizzo del renderer di Word  
 Oltre a rendere le funzionalità che sono nuove in [!INCLUDE[ofprword](../../includes/ofprword-md.md)] 2007-2010 disponibili per esportare i report, file *. docx di report esportati tendono a essere più piccoli. I report esportati tramite il renderer di Word sono in genere notevolmente più piccoli rispetto agli stessi report esportati usando il renderer di Word 2003.  
  
## <a name="backward-compatibility-of-exported-reports"></a>Compatibilità con le versioni precedenti di report esportati  
 È possibile selezionare una modalità di compatibilità di Word e impostare opzioni di compatibilità. Il renderer di Word consente di creare documenti con la modalità di compatibilità abilitata. L'ulteriore salvataggio di documenti con tale modalità disabilitata potrebbe influire sul layout del documento.  
  
 Se si disabilita la modalità di compatibilità e si salva di nuovo un report, il relativo layout potrebbe cambiare in modo imprevisto.  
  
##  <a name="AvailabilityWord"></a> Disponibilità del Renderer di Word 2003  
 Nelle [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], il renderer di Word predefinito è la versione che esegue il rendering nel formato nativo di [!INCLUDE[ofprword](../../includes/ofprword-md.md)] 2007-2010. Si tratta dell'opzione **Word** elencata nei menu **Esporta** in Gestione report e SharePoint. La versione precedente, compatibile solo con [!INCLUDE[ofprword](../../includes/ofprword-md.md)] 2003, è ora denominata Word 2003 ed è elencata nei menu con tale nome. L'opzione di menu **Word 2003** non è visibile per impostazione predefinita, tuttavia un amministratore può renderla tale aggiornando il file di configurazione RSReportServer. Per esportare i report da [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] usando il renderer di Word 2003, è possibile aggiornare il file di configurazione RSReportDesigner. Tuttavia, rendere visibile il renderer di Word 2003 non lo rende disponibile in tutti gli scenari. Poiché il file di configurazione RSReportServer si trova nel server di report, gli strumenti o prodotti da cui si esportano i report devono essere connessi a un server di report per la lettura del file di configurazione. Se si usano strumenti o prodotti in modalità senza connessione o locale, rendere visibile il renderer di Word 2003 non produce alcun effetto. L'opzione di menu **Word 2003** rimane non disponibile. Se si rende visibile il renderer di Word 2003 nel file di configurazione RSReportDesigner, l'opzione di menu **Word 2003** è sempre disponibile nell'anteprima report di [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] .  
  
 L'opzione di menu **Word 2003** non è mai visibile negli scenari seguenti:  
  
-   Generatore report in modalità senza connessione e anteprima di un report in Generatore report. Ciò si verifica in entrambi i [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] e nelle versioni autonome di Generatore Report.  
  
-   Web part di Visualizzatore report in modalità locale e farm di SharePoint non integrata con un server di report [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Per altre informazioni, vedere [Report in modalità locale e con connessione nel visualizzatore di report &#40;Reporting Services in modalità SharePoint&#41;](../local-vs-connected-mode-report-viewer-reporting-services-sharepoint-mode.md)  
  
 Se il renderer di **Word 2003** è configurato per essere visibile, entrambe le opzioni di menu **Word** e **Word 2003** sono disponibili negli scenari seguenti:  
  
-   Gestione report quando Reporting Services è installato in modalità nativa.  
  
-   Sito di SharePoint quando Reporting Services è installato in modalità integrata SharePoint.  
  
-   [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] e anteprima dei report.  
  
-   Generatore report connesso a un server di report. Può trattarsi di un [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] o la versione autonoma di Generatore Report.  
  
-   Web part di Visualizzatore report in modalità remota.  
  
 Nel codice XML seguente sono mostrati gli elementi delle due estensioni per il rendering di Word nei file di configurazione RSReportServer e RSReportDesigner:  
  
 `<Extension Name="WORDOPENXML" Type="Microsoft.ReportingServices.Rendering.WordRenderer.WordOpenXmlRenderer.WordOpenXmlDocumentRenderer,Microsoft.ReportingServices.WordRendering"/>`  
  
 `<Extension Name="WORD" Type="Microsoft.ReportingServices.Rendering.WordRenderer.WordDocumentRenderer,Microsoft.ReportingServices.WordRendering" Visible="false"/>`  
  
 L'estensione WORDOPENXML consente di definire il renderer di Word per [!INCLUDE[ofprword](../../includes/ofprword-md.md)] 2007-2010. L'estensione WORD consente di definire la versione [!INCLUDE[ofprword](../../includes/ofprword-md.md)] 2003. `Visible = “false”` indica che il renderer di Word 2003 è nascosto. Per altre informazioni, vedere [RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md) e [RSReportDesigner Configuration File](../report-server/rsreportdesigner-configuration-file.md).  
  
##  <a name="Differences"></a> Differenze tra le parole e i renderer di Word 2003  
 I report, visualizzabili tramite i renderer di Word o Word 2003, tendono a essere non distinguibili da un punto di vista visivo. Tuttavia, è possibile riscontrare piccole differenze tra i due tipi di formati Word o Word 2003.  
  
##  <a name="DeviceInfo"></a> Impostazioni relative alle informazioni sul dispositivo  
 Modificando le impostazioni relative alle informazioni sul dispositivo, è possibile modificare alcune impostazioni predefinite per questo renderer, ad esempio omettere collegamenti ipertestuali e collegamenti drill-through o espandere tutti gli elementi la cui visibilità può essere attivata o disattivata indipendentemente dal relativo stato originale durante il rendering. Per altre informazioni, vedere [Word Device Information Settings](../word-device-information-settings.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Paginazione in Reporting Services &#40;Generatore report e SSRS&#41;](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md)   
 [Tipi di rendering &#40;Generatore report e SSRS&#41;](../report-design/rendering-behaviors-report-builder-and-ssrs.md)   
 [Funzionalità interattiva per estensioni di Rendering del Report diversi &#40;Report e SSRS&#41;](interactive-functionality-different-report-rendering-extensions.md)   
 [Rendering degli elementi del report &#40;Generatore report e SSRS&#41;](../report-design/rendering-report-items-report-builder-and-ssrs.md)   
 [Tabelle, matrici ed elenchi &#40;Generatore report e SSRS&#41;](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)  
  
  

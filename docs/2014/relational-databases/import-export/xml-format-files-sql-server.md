---
title: File di formato XML (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: data-movement
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- format files [SQL Server], XML format files
- bulk importing [SQL Server], format files
- XML format files [SQL Server]
ms.assetid: 69024aad-eeea-4187-8fea-b49bc2359849
caps.latest.revision: 44
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 06ba4a93e79d9b2a602101b25944d251ea9c5b54
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37203551"
---
# <a name="xml-format-files-sql-server"></a>File in formato XML (SQL Server)
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] viene fornito un XML Schema che definisce la sintassi per la scrittura di *file di formato XML* da utilizzare per l'importazione bulk dei dati in una tabella di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . I file di formato XML devono essere conformi a questo schema, definito in XML Schema Definition Language (XSDL). I file di formato XML sono supportati solo quando gli strumenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono installati insieme a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
 È possibile usare un file di formato XML con un comando **bcp**, un'istruzione BULK INSERT o un'istruzione INSERT ... Istruzione SELECT \* FROM OPENROWSET(BULK...). Il comando **bcp** consente di generare automaticamente un file di formato XML per una tabella. Per ulteriori informazioni, vedere [bcp Utility](../../tools/bcp-utility.md).  
  
> [!NOTE]  
>  Sono supportati due tipi di file di formato per l'esportazione e l'importazione in blocco: *file di formato non XML* e *file di formato XML*. I file di formato XML offrono un'alternativa flessibile ed efficiente rispetto ai file di formato non XML. Per informazioni sui file di formato non XML, vedere [File in formato non XML &#40;SQL Server&#41;](xml-format-files-sql-server.md).  
  

  
##  <a name="BenefitsOfXmlFFs"></a> Vantaggi dei file di formato XML  
  
-   I file di formato XML sono autodescrittivi, semplificandone la lettura, la creazione e l'estensione. Sono inoltre leggibili, semplificando la comprensione della modalità di interpretazione dei dati durante le operazioni bulk.  
  
-   I file di formato XML contengono i tipi di dati delle colonne di destinazione.  La codifica XML descrive in modo semplice i tipi di dati e gli elementi dati del file di dati, nonché il mapping tra gli elementi dati e le colonne della tabella.  
  
     Consente la separazione tra la modalità di rappresentazione dei dati nel file di dati e il tipo di dati associato a ogni campo nel file. Ad esempio, se il file di dati include una rappresentazione dei caratteri dei dati, il tipo della colonna SQL corrispondente viene perduto.  
  
-   Un file di formato XML consente il caricamento di un campo contenente un unico tipo di dati LOB (Large Object) da un file di dati.  
  
-   È possibile apportare miglioramenti a un file di formato XML, mantenendolo tuttavia compatibile con le versioni precedenti. La semplicità della codifica XML facilita inoltre la creazione di più file di formato per un file di dati specifico, il che risulta utile nel caso sia necessario eseguire il mapping di tutti i campi dati o parte di essi a colonne di tabelle o viste diverse.  
  
-   La sintassi XML è indipendente dalla direzione dell'operazione, ovvero è identica sia per l'esportazione bulk che per l'importazione bulk.  
  
-   È possibile utilizzare i file di formato XML per l'importazione bulk dei dati in tabelle o in viste non partizionate e per l'esportazione bulk dei dati.  
  
-   È facoltativo specificare una tabella di destinazione per la funzione OPENROWSET(BULK...), poiché la funzione si basa su un file di formato XML per la lettura dei dati da un file di dati.  
  
    > [!NOTE]  
    >  Una tabella di destinazione è necessaria con il comando **bcp** e l'istruzione BULK INSERT in cui le colonne della tabella di destinazione vengono usate per eseguire la conversione dei tipi.  
  
##  <a name="StructureOfXmlFFs"></a> Struttura dei file di formato XML  
 Analogamente a un file di formato non XML, un file di formato XML definisce il formato e la struttura dei campi dati di un file di dati ed esegue il mapping di tali campi alle colonne di una singola tabella di destinazione.  
  
 Un file di formato XML include due componenti principali, \<RECORD> e \<ROW>:  
  
-   \<RECORD> descrive i dati archiviati nel file di dati.  
  
     Ogni elemento \<RECORD> include un set contenente uno o più elementi \<FIELD>. Questi elementi corrispondono ai campi del file di dati. La sintassi di base è la seguente:  
  
     \<RECORD>  
  
     \<FIELD .../> [ ...*n* ]  
  
     \</RECORD>  
  
     Ogni elemento \<FIELD> descrive il contenuto di un campo dati specifico. È possibile eseguire il mapping di un campo unicamente a una colonna della tabella. Non è tuttavia necessario eseguire il mapping di tutti i campi a colonne.  
  
     Un campo di un file di dati può essere a lunghezza fissa o variabile oppure può terminare con un carattere. Un *valore del campo* può essere rappresentato da un carattere (rappresentazione a un byte), da un carattere wide (rappresentazione Unicode a due byte), da un formato nativo del database o da un nome file. Se un valore del campo è rappresentato da un nome di file, tale nome punta al file contenente il valore di una colonna BLOB della tabella di destinazione.  
  
-   \<ROW> descrive come creare righe di dati da un file di dati quando i dati del file vengono importati in una tabella di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     Un elemento \<ROW> include un set di elementi \<COLUMN>. Questi elementi corrispondono alle colonne della tabella. La sintassi di base è la seguente:  
  
     \<ROW>  
  
     \<COLUMN .../> [ ...*n* ]  
  
     \</ROW>  
  
     È possibile eseguire il mapping di ogni elemento \<COLUMN> a un solo campo nel file di dati. L'ordine degli elementi \<COLUMN> nell'elemento \<ROW> definisce l'ordine in cui tali elementi vengono restituiti dall'operazione in blocco. Il file di formato XML assegna ogni elemento \<COLUMN> a un nome locale senza alcuna relazione con la colonna nella tabella di destinazione di un'operazione di importazione in blocco.  
  
##  <a name="SchemaSyntax"></a> Sintassi dello schema per i file di formato XML  
 In questa sezione è incluso un riepilogo degli elementi e degli attributi di XML Schema per i file di formato XML. La sintassi di un file di formato è indipendente dalla direzione dell'operazione, ovvero è identica sia per l'esportazione bulk che per l'importazione bulk. Questa sezione descrive anche in che modo l'importazione in blocco usa gli elementi \<ROW> e \<COLUMN> e come inserire il valore xsi:type di un elemento in un set di dati.  
  
 Per informazioni sulla corrispondenza tra la sintassi e i file di formato XML effettivi, vedere [File di formato XML di esempio](#SampleXmlFFs), più avanti in questo argomento.  
  
> [!NOTE]  
>  È possibile modificare un file di formato per eseguire l'importazione bulk da un file di dati in cui il numero e/o l'ordine dei campi differisce dal numero e/o dall'ordine delle colonne della tabella. Per altre informazioni, vedere [File di formato per l'importazione o l'esportazione di dati &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md).  
  
  
  
###  <a name="BasicSyntax"></a> Sintassi di base di XML Schema  
 Le istruzioni della sintassi seguenti mostrano solo gli elementi (\<BCPFORMAT>, \<RECORD>, \<FIELD>, \<ROW> e \<COLUMN>) e i relativi attributi di base.  
  
 \<BCPFORMAT ...>  
  
 \<RECORD>  
  
 \<FIELD ID = "*fieldID*" xsi:type = "*fieldType*" [...]  
  
 />  
  
 \</RECORD>  
  
 \<ROW>  
  
 \<COLUMN SOURCE = "*fieldID*" NAME = "*columnName*" xsi:type = "*columnType*" [...]  
  
 />  
  
 \</ROW>  
  
 \</BCPFORMAT>  
  
> [!NOTE]  
>  Gli altri attributi associati al valore di xsi:type in un elemento \<FIELD> o \<COLUMN> sono descritti più avanti in questo argomento.  
  

  
####  <a name="SchemaElements"></a> Elementi dello schema  
 In questa sezione viene riepilogato lo scopo di ciascun elemento definito da XML Schema per i file di formato XML. Gli attributi sono descritti in apposite sezioni più avanti in questo argomento.  
  
 \<BCPFORMAT>  
 Corrisponde all'elemento del file di formato che definisce la struttura del record di un file di dati specifico e la relativa corrispondenza con le colonne di una riga della tabella.  
  
 \<RECORD .../>  
 Definisce un elemento complesso contenente uno o più elementi \<FIELD>. L'ordine con cui i campi vengono dichiarati nel file di formato corrisponde a quello con cui tali campi sono riportati nel file di dati.  
  
 \<FIELD .../>  
 Definisce un campo, contenente dati, nel file di dati.  
  
 Gli attributi di questo elemento vengono discussi in [Attributi dell'elemento \<FIELD>](#AttrOfFieldElement) più avanti in questo argomento.  
  
 \<ROW .../>  
 Definisce un elemento complesso contenente uno o più elementi \<COLUMN>. L'ordine degli elementi \<COLUMN> è indipendente da quello degli elementi \<FIELD> in una definizione RECORD. L'ordine degli elementi \<COLUMN> in un file di formato determina invece l'ordine delle colonne del set di righe risultante. I campi di dati vengono caricati nell'ordine in cui vengono dichiarati gli elementi \<COLUMN> corrispondenti nell'elemento \<COLUMN>.  
  
 Per altre informazioni, vedere [Uso dell'elemento \<ROW> nell'importazione in blocco](#HowUsesROW) più avanti in questo argomento.  
  
 \<COLUMN>  
 Definisce una colonna come elemento (\<COLUMN>). Ogni elemento \<COLUMN> corrisponde a un elemento \<FIELD>, il cui ID viene specificato nell'attributo SOURCE dell'elemento \<COLUMN>.  
  
 Gli attributi di questo elemento vengono discussi in [Attributi dell'elemento \<COLUMN>](#AttrOfColumnElement) più avanti in questo argomento. Vedere anche [Uso dell'elemento \<COLUMN> nell'importazione in blocco](#HowUsesColumn) più avanti in questo argomento.  
  
 \</BCPFORMAT>  
 Richiesto per terminare il file di formato.  
  
####  <a name="AttrOfFieldElement"></a> Attributi dell'elemento \<FIELD>  
 Questa sezione descrive gli attributi dell'elemento \<FIELD>, riepilogati nella sintassi dello schema seguente:  
  
 Valori xsi:type di <FIELD  
  
 ID **= "*`fieldID`*"**  
  
 xsi **:** tipo **= "*`fieldType`*"**  
  
 [ LENGTH **="*`n`*"** ]  
  
 [PREFIX_LENGTH **= "*`p`*"** ]  
  
 [MAX_LENGTH **= "*`m`*"** ]  
  
 [REGOLE DI CONFRONTO **= "*`collationName`*"** ]  
  
 [CARATTERE DI TERMINAZIONE **= "*`terminator`*"** ]  
  
 />  
  
 Ogni elemento \<FIELD> è indipendente dagli altri. Per la descrizione di un campo vengono utilizzati gli attributi seguenti:  
  
|Attributo FIELD|Descrizione|Facoltativo /<br /><br /> Obbligatorio|  
|---------------------|-----------------|------------------------------|  
|ID **= "*`fieldID`*"**|Specifica il nome logico del campo nel file di dati. L'ID di un campo rappresenta la chiave utilizzata per fare riferimento al campo.<br /><br /> < FIELD ID **= "*`fieldID`*"**/ > esegue il mapping a < COLUMN SOURCE **= "*`fieldID`*"**/>|Obbligatorio|  
|xsi: Type **= "*`fieldType`*"**|Costrutto XML, utilizzato in modo simile a un attributo, che identifica il tipo dell'istanza dell'elemento. Il valore di *fieldType* determina gli attributi opzionali, riportati di seguito, necessari in un'istanza specifica.|Obbligatorio, a seconda del tipo di dati|  
|LENGTH **="*`n`*"**|Definisce la lunghezza per un'istanza di un tipo di dati a lunghezza fissa.<br /><br /> Il valore di *n* deve essere un numero intero positivo.|Facoltativo, a meno che non richiesto dal valore xsi:type|  
|PREFIX_LENGTH **= "*`p`*"**|Definisce la lunghezza del prefisso per una rappresentazione di dati binary. Il valore PREFIX_LENGTH *p*deve essere uno dei seguenti: 1, 2, 4 o 8.|Facoltativo, a meno che non richiesto dal valore xsi:type|  
|MAX_LENGTH **= "*`m`*"**|Corrisponde al numero massimo di byte archiviabile in un campo specifico. In assenza di una tabella di destinazione, la lunghezza massima della colonna non è nota. L'attributo MAX_LENGTH limita la lunghezza massima di una colonna di testo di output e di conseguenza anche lo spazio di archiviazione allocato al valore della colonna. Tale limitazione risulta particolarmente comoda quando si utilizza l'opzione BULK della funzione OPENROWSET in una clausola SELECT FROM.<br /><br /> Il valore di *m* deve essere un numero intero positivo. Per impostazione predefinita, la lunghezza massima è pari a 8000 caratteri per una colonna **char** e a 4000 caratteri per una colonna **nchar** .|Facoltativo|  
|LE REGOLE DI CONFRONTO **= "*`collationName`*"**|Questo attributo è consentito solo per i campi di tipo carattere. Per un elenco dei nomi delle regole di confronto SQL, vedere [Nome delle regole di confronto di SQL Server &#40;Transact-SQL&#41;](/sql/t-sql/statements/sql-server-collation-name-transact-sql).|Facoltativo|  
|CARATTERE DI TERMINAZIONE **= "*`terminator`*"**|Specifica il carattere di terminazione di un campo di dati. Il carattere di terminazione può essere costituito da un carattere qualsiasi, univoco e non facente parte dei dati.<br /><br /> Per impostazione predefinita, il carattere di terminazione corrisponde al carattere di tabulazione, rappresentato come \t. Per rappresentare un segno di paragrafo, utilizzare \r\n.|Viene utilizzato solo con un valore xsi:type di dati di tipo carattere, per il quale è necessario specificare questo attributo.|  
  
#####  <a name="XsiTypeValuesOfFIELD"></a> Valori Xsi:type dell'elemento \<FIELD>  
 Il valore xsi:type è un costrutto XML, utilizzato in modo simile a un attributo, che identifica il tipo di dati di un'istanza di un elemento. Per informazioni sull'utilizzo di questo valore, vedere "Inserimento del valore xsi:type in un set di dati", più avanti in questa sezione.  
  
 Il valore xsi:type dell'elemento \<FIELD> supporta i tipi di dati seguenti.  
  
|Valori xsi:type di \<FIELD>|Attributi XML obbligatori<br /><br /> per il tipo di dati|Attributi XML facoltativi<br /><br /> per il tipo di dati|  
|-------------------------------|---------------------------------------------------|---------------------------------------------------|  
|**NativeFixed**|`LENGTH`|Nessuna.|  
|**NativePrefix**|`PREFIX_LENGTH`|MAX_LENGTH|  
|**CharFixed**|`LENGTH`|COLLATION|  
|**NCharFixed**|`LENGTH`|COLLATION|  
|**CharPrefix**|`PREFIX_LENGTH`|MAX_LENGTH, COLLATION|  
|**NCharPrefix**|`PREFIX_LENGTH`|MAX_LENGTH, COLLATION|  
|**CharTerm**|`TERMINATOR`|MAX_LENGTH, COLLATION|  
|**NCharTerm**|`TERMINATOR`|MAX_LENGTH, COLLATION|  
  
 Per altre informazioni sui tipi di dati di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vedere [Tipi di dati &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).  
  
####  <a name="AttrOfColumnElement"></a> Attributi dell'elemento \<COLUMN>  
 Questa sezione descrive gli attributi dell'elemento \<COLUMN>, riepilogati nella sintassi dello schema seguente:  
  
 \<COLUMN  
  
 SOURCE = "*fieldID*"  
  
 NAME = "*columnName*"  
  
 xsi:type = "*columnType*"  
  
 [ LENGTH = "*n*" ]  
  
 [ PRECISION = "*n*" ]  
  
 [ SCALE = "*value*" ]  
  
 [ NULLABLE = { "YES"  
  
 "NO" } ]  
  
 />  
  
 Per eseguire il mapping di un campo a una colonna nella tabella di destinazione vengono utilizzati gli attributi seguenti:  
  
|Attributo COLUMN|Description|Facoltativo /<br /><br /> Obbligatorio|  
|----------------------|-----------------|------------------------------|  
|ORIGINE **= "*`fieldID`*"**|Specifica l'ID del campo di cui eseguire il mapping alla colonna.<br /><br /> < COLUMN SOURCE **= "*`fieldID`*"**/ > esegue il mapping a < FIELD ID **= "*`fieldID`*"**/>|Obbligatorio|  
|NAME = "*columnName*"|Specifica il nome della colonna del set di righe rappresentato dal file di formato. Viene utilizzato per identificare la colonna nel set dei risultati e non corrisponde necessariamente al nome di colonna utilizzato nella tabella di destinazione.|Obbligatorio|  
|xsi **:** tipo **= "*`ColumnType`*"**|Costrutto XML, utilizzato in modo simile a un attributo, che identifica il tipo di dati dell'istanza dell'elemento. Il valore di *ColumnType* determina gli attributi opzionali, riportati di seguito, necessari in un'istanza specifica.<br /><br /> Nota: I possibili valori della *ColumnType* e i relativi attributi associati sono elencati nella tabella seguente.|Facoltativo|  
|LENGTH **="*`n`*"**|Definisce la lunghezza per un'istanza di un tipo di dati a lunghezza fissa. Viene utilizzato solo quanto il valore xsi:type corrisponde a un tipo di dati string.<br /><br /> Il valore di *n* deve essere un numero intero positivo.|Facoltativo (disponibile solo se il valore xsi:type corrisponde a un tipo di dati string)|  
|PRECISION **="*`n`*"**|Indica il numero di cifre in un numero. Il numero 123,45, ad esempio, ha una precisione di 5.<br /><br /> Il valore deve essere un numero intero positivo.|Facoltativo (disponibile solo se il valore xsi:type corrisponde a un tipo di dati numerico variabile)|  
|SCALA **= "*`int`*"**|Indica il numero di cifre a destra della virgola decimale in un numero. Il numero 123,45, ad esempio, ha una scala di 2.<br /><br /> Il valore deve essere un numero intero.|Facoltativo (disponibile solo se il valore xsi:type corrisponde a un tipo di dati numerico variabile)|  
|NULLABLE **=** { **"** YES **"**<br /><br /> **"** NO **"** }|Indica se una colonna supporta o meno valori NULL. Questo attributo è completamente indipendente da FIELDS. Se, tuttavia, una colonna non ammette valori Null e il valore del campo è NULL, ovvero non è stato specificato alcun valore, verrà restituito un errore di run-time.<br /><br /> L'attributo NULLABLE viene utilizzato solo per un'istruzione SELECT FROM OPENROWSET(BULK...) semplice.|Facoltativo (disponibile per qualsiasi tipo di dati)|  
  
#####  <a name="XsiTypeValuesOfCOLUMN"></a> Valori Xsi:type dell'elemento \<COLUMN>  
 Il valore xsi:type è un costrutto XML, utilizzato in modo simile a un attributo, che identifica il tipo di dati di un'istanza di un elemento. Per informazioni sull'utilizzo di questo valore, vedere "Inserimento del valore xsi:type in un set di dati", più avanti in questa sezione.  
  
 L'elemento \<COLUMN> supporta i tipi di dati SQL nativi, come descritto di seguito:  
  
|Categoria del tipo|Tipi di dati di \<COLUMN>|Attributi XML obbligatori<br /><br /> per il tipo di dati|Attributi XML facoltativi<br /><br /> per il tipo di dati|  
|-------------------|---------------------------|---------------------------------------------------|---------------------------------------------------|  
|Fisso|`SQLBIT`, `SQLTINYINT`, `SQLSMALLINT`, `SQLINT`, `SQLBIGINT`, `SQLFLT4`, `SQLFLT8`, `SQLDATETIME`, `SQLDATETIM4`, `SQLDATETIM8`, `SQLMONEY`, `SQLMONEY4`, `SQLVARIANT`, e `SQLUNIQUEID`|Nessuna.|NULLABLE|  
|Numero variabile|`SQLDECIMAL` e `SQLNUMERIC`|Nessuna.|NULLABLE, PRECISION, SCALE|  
|LOB|`SQLIMAGE`, `CharLOB`, `SQLTEXT` e `SQLUDT`|Nessuna.|NULLABLE|  
|Character LOB|`SQLNTEXT`|Nessuna.|NULLABLE|  
|Stringa binaria|`SQLBINARY` e `SQLVARYBIN`|Nessuna.|NULLABLE, LENGTH|  
|Stringa di caratteri|`SQLCHAR`, `SQLVARYCHAR`, `SQLNCHAR` e `SQLNVARCHAR`|Nessuna.|NULLABLE, LENGTH|  
  
> [!IMPORTANT]  
>  Per eseguire l'esportazione o l'importazione bulk dei dati SQLXML, utilizzare uno dei tipi di dati seguenti nel file di formato: SQLCHAR o SQLVARYCHAR (i dati vengono inviati nella tabella codici del client o nella tabella codici implicita nelle regole di confronto), SQLNCHAR o SQLNVARCHAR (i dati vengono inviati come Unicode) oppure SQLBINARY o SQLVARYBIN (i dati vengono inviati senza conversione).  
  
 Per altre informazioni sui tipi di dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vedere [Tipi di dati &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).  
  
###  <a name="HowUsesROW"></a> Uso dell'elemento \<ROW> nell'importazione in blocco  
 L'elemento \<ROW> viene ignorato in alcuni contesti. L'elemento \<ROW> può influire su un'operazione di importazione in blocco a seconda della modalità con cui viene eseguita l'operazione:  
  
-   Comando **bcp**   
  
     Quando i dati vengono caricati in una tabella di destinazione, **bcp** ignora il componente \<ROW>. e **bcp** carica i dati in base ai tipi di colonna della tabella di destinazione.  
  
-   [!INCLUDE[tsql](../../../includes/tsql-md.md)] Istruzioni (provider bulk per set di righe di BULK INSERT e OPENROWSET)  
  
     Durante l'importazione in blocco dei dati in una tabella, le istruzioni [!INCLUDE[tsql](../../../includes/tsql-md.md)] usano il componente \<ROW> per generare il set di righe di input. Le istruzioni [!INCLUDE[tsql](../../../includes/tsql-md.md)] eseguono anche le conversioni appropriate dei tipi sulla base dei tipi di colonna specificati in \<ROW> e della colonna corrispondente nella tabella di destinazione. Se i tipi di colonna specificati nel file di formato e quelli della tabella di destinazione non corrispondono, verrà eseguita un'ulteriore conversione dei tipi. Questa conversione supplementare può comportare alcune discrepanze, ovvero mancanza di precisione, nel comportamento del provider bulk per set di righe di BULK INSERT o OPENROWSET rispetto a **bcp**.  
  
     Le informazioni presenti nell'elemento \<ROW> consentono di costruire una riga senza richiedere altre informazioni. È quindi possibile generare un set di righe usando un'istruzione SELECT (SELECT \* FROM OPENROWSET(BULK *datafile* FORMATFILE=*xmlformatfile*).  
  
    > [!NOTE]  
    >  La clausola OPENROWSET BULK richiede un file di formato. Si noti che la conversione da un tipo di dati del campo al tipo di dati di una colonna è disponibile solo con un file di formato XML.  
  
###  <a name="HowUsesColumn"></a> Uso dell'elemento \<COLUMN> nell'importazione in blocco  
 Per consentire l'importazione in blocco dei dati in una tabella, gli elementi \<COLUMN> di un file di formato eseguono il mapping di un campo del file di dati alle colonne della tabella specificando:  
  
-   La posizione di ogni campo all'interno di una riga del file di dati.  
  
-   Il tipo di colonna utilizzata per la conversione del tipo di dati del campo nel tipo di dati della colonna desiderato.  
  
 In caso di assenza di mapping delle colonne a un campo, quest'ultimo non verrà copiato nella riga o nelle righe generate. Questo comportamento consente a un file di dati di generare righe con diverse colonne e in diverse tabelle.  
  
 Analogamente, per consentire l'esportazione in blocco dei dati di una tabella, ogni \<COLUMN> del file di formato esegue il mapping della colonna dalla riga della tabella di input al campo corrispondente del file di dati di output.  
  
###  <a name="PutXsiTypeValueIntoDataSet"></a> Inserimento del valore xsi:type in un set di dati  
 Quando per la convalida di un documento XML si utilizza il linguaggio XML Schema Definition (XSD), il valore xsi:type non viene inserito nel set di dati. Per inserire le informazioni relative al valore xsi:type nel set di dati, è tuttavia possibile caricare il file di formato XML in un documento XML, ad esempio `myDoc`, come illustrato nel frammento di codice seguente:  
  
```  
...;  
myDoc.LoadXml(xmlFormat);  
XmlNodeList ColumnList = myDoc.GetElementsByTagName("COLUMN");  
for(int i=0;i<ColumnList.Count;i++)  
{  
   Console.Write("COLUMN: xsi:type=" +ColumnList[i].Attributes["type",  
      "http://www.w3.org/2001/XMLSchema-instance"].Value+"\n");  
}  
```  
  
##  <a name="SampleXmlFFs"></a> File di formato XML di esempio  
 In questa sezione sono vengono fornite informazioni sull'utilizzo dei file di formato XML in una vasta gamma di situazioni, incluso un esempio relativo a [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] .  
  
> [!NOTE]  
>  Nei file di dati degli esempi seguenti `<tab>` indica un carattere di tabulazione e `<return>` indica un ritorno a capo.  
  

  
> [!NOTE]  
>  Per informazioni su come creare file di formato, vedere [Creare un file di formato &#40;SQL Server&#41;](create-a-format-file-sql-server.md).  
  
###  <a name="OrderCharFieldsSameAsCols"></a> A. Ordinamento dei campi dati di tipo carattere identico a quello delle colonne della tabella  
 Nell'esempio seguente viene illustrato un file di formato XML che descrive un file di dati contenente tre campi dati di tipo carattere. Il file di formato esegue il mapping tra il file di dati e una tabella che contiene tre colonne. Tra i campi dati e le colonne della tabella esiste una corrispondenza di tipo uno-a-uno.  
  
 **Tabella (riga):** Person (Age int, FirstName varchar(20), LastName varchar(30))  
  
 **File di dati (record):** Age\<tab>Firstname\<tab>Lastname\<return>  
  
 Il file di formato XML seguente legge il file di dati e quindi la tabella.  
  
 Nell'elemento `<RECORD>` il file di formato rappresenta i valori dei dati di tutti e tre i campi come dati di tipo carattere. Per ogni campo, l'attributo `TERMINATOR` indica il carattere di terminazione che segue il valore dei dati.  
  
 Tra i campi dati e le colonne della tabella esiste una corrispondenza di tipo uno-a-uno. Nell'elemento `<ROW>` il file di formato esegue il mapping tra la colonna `Age` e il primo campo, la colonna `FirstName` e il secondo campo e la colonna `LastName` e il terzo campo.  
  
```  
<?xml version="1.0"?>  
<BCPFORMAT   
xmlns="http://schemas.microsoft.com/sqlserver/2004/bulkload/format"   
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <RECORD>  
    <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="\t"   
      MAX_LENGTH="12"/>   
    <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="\t"   
      MAX_LENGTH="20" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
    <FIELD ID="3" xsi:type="CharTerm" TERMINATOR="\r\n"   
      MAX_LENGTH="30"   
      COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  </RECORD>  
  <ROW>  
    <COLUMN SOURCE="1" NAME="age" xsi:type="SQLINT"/>  
    <COLUMN SOURCE="2" NAME="firstname" xsi:type="SQLVARYCHAR"/>  
    <COLUMN SOURCE="3" NAME="lastname" xsi:type="SQLVARYCHAR"/>  
  </ROW>  
</BCPFORMAT>  
```  
  
> [!NOTE]  
>  Per un esempio equivalente di [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] , vedere [Creare un file di formato &#40;SQL Server&#41;](create-a-format-file-sql-server.md).  
  
###  <a name="OrderFieldsAndColsDifferently"></a> B. Ordinamento dei campi dati diverso da quello delle colonne della tabella  
 Nell'esempio seguente viene illustrato un file di formato XML che descrive un file di dati contenente tre campi dati di tipo carattere. Il file di formato esegue il mapping tra il file di dati e una tabella che contiene tre colonne ordinate in modo diverso rispetto ai campi del file di dati.  
  
 **Tabella (riga):** Person (Age int, FirstName varchar(20), LastName varchar(30))  
  
 **File di dati** (record): Age\<tab>Lastname\<tab>Firstname\<return>  
  
 Nell'elemento `<RECORD>` il file di formato rappresenta i valori dei dati di tutti e tre i campi come dati di tipo carattere.  
  
 Nell'elemento `<ROW>` il file di formato esegue il mapping tra la colonna `Age` e il primo campo, la colonna `FirstName` e il terzo campo e la colonna `LastName` e il secondo campo.  
  
```  
<?xml version="1.0"?>  
<BCPFORMAT   
xmlns="http://schemas.microsoft.com/sqlserver/2004/bulkload/format"   
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <RECORD>  
    <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="\t"   
      MAX_LENGTH="12"/>  
    <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="\t" MAX_LENGTH="20"   
      COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
    <FIELD ID="3" xsi:type="CharTerm" TERMINATOR="\r\n"   
      MAX_LENGTH="30" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  </RECORD>  
  <ROW>  
    <COLUMN SOURCE="1" NAME="age" xsi:type="SQLINT"/>  
    <COLUMN SOURCE="3" NAME="firstname" xsi:type="SQLVARYCHAR"/>  
    <COLUMN SOURCE="2" NAME="lastname" xsi:type="SQLVARYCHAR"/>  
  </ROW>  
</BCPFORMAT>  
```  
  
> [!NOTE]  
>  Per un esempio equivalente di [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)], vedere [Usare un file di formato per eseguire il mapping tra le colonne della tabella e i campi del file di dati &#40;SQL Server&#41;](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md).  
  
### <a name="c-omitting-a-data-field"></a>C. Omissione di un campo dati  
 Nell'esempio seguente viene illustrato un file di formato XML che descrive un file di dati contenente quattro campi dati di tipo carattere. Il file di formato esegue il mapping tra il file di dati e una tabella che contiene tre colonne. Il secondo campo dati non corrisponde a nessuna colonna della tabella.  
  
 **Tabella (riga):** Person (Age int, FirstName Varchar(20), LastName Varchar(30))  
  
 **File di dati (record):** Age\<tab>employeeID\<tab>Firstname\<tab>Lastname\<return>  
  
 Nell'elemento `<RECORD>` il file di formato rappresenta i valori dei dati di tutti e quattro i campi come dati di tipo carattere. Per ogni campo, l'attributo TERMINATOR indica il carattere di terminazione che segue il valore dei dati.  
  
 Nell'elemento `<ROW>` il file di formato esegue il mapping tra la colonna `Age` e il primo campo, la colonna `FirstName` e il terzo campo e la colonna `LastName` e il quarto campo.  
  
```  
<BCPFORMAT   
xmlns="http://schemas.microsoft.com/sqlserver/2004/bulkload/format"   
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <RECORD>  
    <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="\t"   
      MAX_LENGTH="12"/>  
    <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="\t"   
      MAX_LENGTH="10"   
      COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
    <FIELD ID="3" xsi:type="CharTerm" TERMINATOR="\t"   
      MAX_LENGTH="20"   
      COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
    <FIELD ID="4" xsi:type="CharTerm" TERMINATOR="\r\n"   
      MAX_LENGTH="30"   
      COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  </RECORD>  
  <ROW>  
    <COLUMN SOURCE="1" NAME="age" xsi:type="SQLINT"/>  
    <COLUMN SOURCE="3" NAME="firstname" xsi:type="SQLVARYCHAR"/>  
    <COLUMN SOURCE="4" NAME="lastname" xsi:type="SQLVARYCHAR"/>  
  </ROW>  
</BCPFORMAT>  
```  
  
> [!NOTE]  
>  Per un esempio equivalente di [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] , vedere [Usare un file di formato per escludere un campo di dati &#40;SQL Server&#41;](use-a-format-file-to-skip-a-data-field-sql-server.md).  
  
###  <a name="MapXSItype"></a> D. Mapping tra il valore xsi:type dell'elemento \<FIELD> e il valore xsi:type dell'elemento \<COLUMN>  
 Nell'esempio seguente vengono illustrati tipi diversi di campi e i relativi mapping alle colonne.  
  
```  
<?xml version = "1.0"?>  
<BCPFORMAT  
xmlns="http://schemas.microsoft.com/sqlserver/2004/bulkload/format"   
   xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
   <RECORD>  
      <FIELD xsi:type="CharTerm" ID="C1" TERMINATOR="\t"   
            MAX_LENGTH="4"/>  
      <FIELD xsi:type="CharFixed" ID="C2" LENGTH="10"   
         COLLATION="SQL_LATIN1_GENERAL_CP1_CI_AS"/>  
      <FIELD xsi:type="CharPrefix" ID="C3" PREFIX_LENGTH="2"   
         MAX_LENGTH="32" COLLATION="SQL_LATIN1_GENERAL_CP1_CI_AS"/>  
      <FIELD xsi:type="NCharTerm" ID="C4" TERMINATOR="\t"   
         MAX_LENGTH="4"/>  
      <FIELD xsi:type="NCharFixed" ID="C5" LENGTH="10"   
         COLLATION="SQL_LATIN1_GENERAL_CP1_CI_AS"/>  
      <FIELD xsi:type="NCharPrefix" ID="C6" PREFIX_LENGTH="2"   
         MAX_LENGTH="32" COLLATION="SQL_LATIN1_GENERAL_CP1_CI_AS"/>  
      <FIELD xsi:type="NativeFixed" ID="C7" LENGTH="4"/>  
   </RECORD>  
   <ROW>  
      <COLUMN SOURCE="C1" NAME="Age" xsi:type="SQLTINYINT"/>  
      <COLUMN SOURCE="C2" NAME="FirstName" xsi:type="SQLVARYCHAR"   
      LENGTH="16" NULLABLE="NO"/>  
      <COLUMN SOURCE="C3" NAME="LastName" />  
      <COLUMN SOURCE="C4" NAME="Salary" xsi:type="SQLMONEY"/>  
      <COLUMN SOURCE="C5" NAME="Picture" xsi:type="SQLIMAGE"/>  
      <COLUMN SOURCE="C6" NAME="Bio" xsi:type="SQLTEXT"/>  
      <COLUMN SOURCE="C7" NAME="Interest"xsi:type="SQLDECIMAL"   
      PRECISION="5" SCALE="3"/>  
   </ROW>  
</BCPFORMAT>  
```  
  
###  <a name="MapXMLDataToTbl"></a> E. Mapping tra i dati XML e una tabella  
 Nell'esempio seguente viene creata una tabella vuota a due colonne denominata`t_xml`in cui viene eseguito il mapping tra la prima colonna e il tipo di dati `int` e tra la seconda colonna e il tipo di dati `xml` .  
  
```  
CREATE TABLE t_xml (c1 int, c2 xml)  
```  
  
 Il file di formato XML seguente carica un file di dati nella tabella `t_xml`.  
  
```  
<?xml version="1.0"?>  
<BCPFORMAT xmlns="http://schemas.microsoft.com/sqlserver/2004/bulkload/format"   
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
 <RECORD>  
  <FIELD ID="1" xsi:type="NativePrefix" PREFIX_LENGTH="1"/>  
  <FIELD ID="2" xsi:type="NCharPrefix" PREFIX_LENGTH="8"/>  
 </RECORD>  
 <ROW>  
  <COLUMN SOURCE="1" NAME="c1" xsi:type="SQLINT"/>  
  <COLUMN SOURCE="2" NAME="c2" xsi:type="SQLNCHAR"/>  
 </ROW>  
</BCPFORMAT>  
```  
  
###  <a name="ImportFixedFields"></a> F. Importazione di campi a lunghezza fissa o a larghezza fissa  
 Nell'esempio seguente vengono descritti campi fissi di `10` o `6` caratteri ognuno. Il file di formato rappresenta queste lunghezze o larghezze dei campi rispettivamente come `LENGTH="10"` e `LENGTH="6"`. Ogni riga dei file di dati termina con una combinazione di ritorno a capo e avanzamento riga, {CR}{LF}, rappresentata nel file di formato come `TERMINATOR="\r\n"`.  
  
```  
<?xml version="1.0"?>  
<BCPFORMAT  
       xmlns="http://schemas.microsoft.com/sqlserver/2004/bulkload/format"  
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <RECORD>  
    <FIELD ID="1" xsi:type="CharFixed" LENGTH="10"/>  
    <FIELD ID="2" xsi:type="CharFixed" LENGTH="6"/>  
    <FIELD ID="3" xsi:type="CharTerm" TERMINATOR="\r\n"  
  </RECORD>  
  <ROW>  
    <COLUMN SOURCE="1" NAME="C1" xsi:type="SQLINT" />  
    <COLUMN SOURCE="2" NAME="C2" xsi:type="SQLINT" />  
  </ROW>  
</BCPFORMAT>  
```  
  
###  <a name="AdditionalExamples"></a> Esempi aggiuntivi  
 Per ulteriori esempi di file di formato XML e non XML, vedere gli argomenti seguenti:  
  
-   [Usare un file di formato per ignorare una colonna di una tabella &#40;SQL Server&#41;](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
-   [Usare un file di formato per escludere un campo di dati &#40;SQL Server&#41;](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [Utilizzo di un file di formato per eseguire il mapping tra le colonne della tabella e i campi del file di dati &#40;SQL Server&#41;](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
##  <a name="RelatedTasks"></a> Attività correlate  
  
-   [Creazione di un file di formato &#40;SQL Server&#41;](create-a-format-file-sql-server.md)  
  
-   [Usare un file di formato per l'importazione in blocco dei dati &#40;SQL Server&#41;](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [Utilizzo di un file di formato per ignorare una colonna di una tabella &#40;SQL Server&#41;](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
-   [Usare un file di formato per escludere un campo di dati &#40;SQL Server&#41;](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [Utilizzo di un file di formato per eseguire il mapping tra le colonne della tabella e i campi del file di dati &#40;SQL Server&#41;](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
##  <a name="RelatedContent"></a> Contenuto correlato  
 Nessuna.  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sull'importazione ed esportazione in blocco di dati &#40;SQL Server&#41;](bulk-import-and-export-of-data-sql-server.md)   
 [Tipi di dati &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)   
 [File in formato non XML &#40;SQL Server&#41;](xml-format-files-sql-server.md)   
 [File di formato per l'importazione o l'esportazione di dati &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md)  
  
  

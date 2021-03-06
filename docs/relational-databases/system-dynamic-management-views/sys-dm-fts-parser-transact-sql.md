---
title: sys.dm_fts_parser (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_fts_parser_TSQL
- dm_fts_parser
- dm_fts_parser_TSQL
- sys.dm_fts_parser
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_fts_parser dynamic management function
- troubleshooting [SQL Server], full-text search
ms.assetid: 2736d376-fb9d-4b28-93ef-472b7a27623a
caps.latest.revision: 37
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 717e97ca38fdc68b0ba807f546a253793234375b
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/23/2018
---
# <a name="sysdmftsparser-transact-sql"></a>sys.dm_fts_parser (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce il risultato della Tokenizzazione finale dopo aver applicato una determinata [componente word breaker](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md), [thesaurus](../../relational-databases/search/configure-and-manage-thesaurus-files-for-full-text-search.md), e [stoplist](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md) combinazione in una stringa di query di input. Il risultato della tokenizzazione è equivalente all'output del motore di ricerca full-text per la stringa di query specificata.  
  
 sys.dm_fts_parser è una funzione a gestione dinamica.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sys.dm_fts_parser('query_string', lcid, stoplist_id, accent_sensitivity)  
```  
  
## <a name="arguments"></a>Argomenti  
 *query_string*  
 Query da analizzare. *stringa_query* può essere una catena di stringhe che [CONTAINS](../../t-sql/queries/contains-transact-sql.md) supportano la sintassi. È possibile ad esempio includere forme flessive, un thesaurus e operatori logici.  
  
 *lcid*  
 Identificatore delle impostazioni locali (LCID) del word breaker da utilizzare per l'analisi *stringa_query*.  
  
 *stoplist_id*  
 ID di parole non significative, se presente, da utilizzare il word breaker identificato da *lcid*. *stoplist_id* viene **int**. Se si specifica NULL, non viene utilizzato alcun elenco di parole non significative. Se si specifica 0, viene utilizzato l'elemento STOPLIST di sistema.  
  
 L'ID di un elenco di parole non significative è univoco all'interno di un database. Per ottenere l'ID di parole non significative per un indice full-text in un tabella specifica, utilizzare il [fulltext_indexes](../../relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql.md) vista del catalogo.  
  
 *accent_sensitivity*  
 Valore booleano che controlla se la ricerca full-text supporta o meno la distinzione relativa ai segni diacritici. *accent_sensitivity* viene **bit**, con uno dei valori seguenti:  
  
|Value|Distinzione caratteri accentati/non accentati|  
|-----------|----------------------------|  
|0|Non attiva<br /><br /> Parole del tipo "café" e "cafe" vengono considerate in modo identico.|  
|1|Sensibile<br /><br /> Parole del tipo "café" e "cafe" vengono considerate in modo diverso.|  
  
> [!NOTE]  
>  Per visualizzare l'impostazione corrente di questo valore per un catalogo full-text, eseguire il comando seguente [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzione: `SELECT fulltextcatalogproperty('` *catalog_name*`', 'AccentSensitivity');`.  
  
## <a name="table-returned"></a>Tabella restituita  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|parola chiave|**varbinary(128)**|Rappresentazione esadecimale di una parola chiave specificata restituita da un word breaker. Tale rappresentazione viene utilizzata per archiviare la parola chiave nell'indice full-text. Questo valore non è leggibile, ma è utile per relative a una determinata parola chiave per l'output restituito da altre viste a gestione dinamica che restituiscono il contenuto di un indice full-text, ad esempio [Sys.dm fts_index_keywords](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-transact-sql.md) e [ Sys.dm fts_index_keywords_by_document](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql.md).<br /><br /> **Nota:** OxFF rappresenta il carattere speciale che indica la fine di un file o set di dati.|  
|group_id|**int**|Contiene un valore integer utile per differenziare il gruppo logico dal quale è stato generato un termine specifico. '`Server AND DB OR FORMSOF(THESAURUS, DB)"`' produce ad esempio i seguenti valori di group_id in inglese:<br /><br /> 1: server<br />2: DB<br />3: DB|  
|phrase_id|**int**|Contiene un valore integer utile per differenziare i casi in cui il word breaker invia forme alternative di parole composte, come full-text. In presenza di parole composte, ad esempio "multi-million", a volte il word breaker invia forme alternative. In alcuni casi tali forme alternative (frasi) devono essere differenziate.<br /><br /> '`multi-million`' produce ad esempio i seguenti valori di phrase_id in inglese:<br /><br /> 1 per `multi`<br />1 per `million`<br />2 per `multimillion`|  
|occurrence|**int**|Indica l'ordine di ogni termine nel risultato dell'analisi. Per la frase "`SQL Server query processor`", ad esempio, in occurrence sarebbero presenti i seguenti valori di occorrenza per i termini, in inglese:<br /><br /> 1 per `SQL`<br />2 per `Server`<br />3 per `query`<br />4 per `processor`|  
|special_term|**nvarchar(4000)**|Contiene informazioni sulle caratteristiche del termine inviato dal word breaker, tra cui:<br /><br /> Corrispondenza esatta<br /><br /> Parola non significativa<br /><br /> Fine di frase<br /><br /> Fine di paragrafo<br /><br /> Fine di capitolo|  
|display_term|**nvarchar(4000)**|Contiene la forma leggibile della parola chiave. Analogamente alle funzioni progettate per accedere al contenuto dell'indice full-text, il termine visualizzato potrebbe non essere identico al termine originale a causa della limitazione della denormalizzazione, ma dovrebbe essere tuttavia abbastanza preciso per consentire di identificarlo partendo dall'input originale.|  
|expansion_type|**int**|Contiene informazioni sulla natura dell'espansione di un termine specificato. I valori possono essere i seguenti:<br /><br /> 0 = singola parola<br /><br /> 2 = espansione flessiva<br /><br /> 4 = espansione/sostituzione del thesaurus<br /><br /> Si consideri ad esempio un caso in cui il thesaurus definisce il termine "run" come un'espansione di `jog`:<br /><br /> `<expansion>`<br /><br /> `<sub>run</sub>`<br /><br /> `<sub>jog</sub>`<br /><br /> `</expansion>`<br /><br /> Il termine `FORMSOF (FREETEXT, run)` genera l'output seguente:<br /><br /> `run` con expansion_type = 0<br /><br /> `runs` con expansion_type = 2<br /><br /> `running` con expansion_type = 2<br /><br /> `ran` con expansion_type = 2<br /><br /> `jog` con expansion_type = 4|  
|source_term|**nvarchar(4000)**|Termine o frase da cui viene generato o analizzato un termine specifico. Una query eseguita su '"`word breakers" AND stemmers'` produce ad esempio i seguenti valori di source_term in inglese:<br /><br /> `word breakers` per il display_term`word`<br />`word breakers` per il display_term`breakers`<br />`stemmers` per il display_term`stemmers`|  
  
## <a name="remarks"></a>Osservazioni  
 **fts_parser** supporta la sintassi e le funzionalità di predicati full-text, ad esempio [CONTAINS](../../t-sql/queries/contains-transact-sql.md) e [FREETEXT](../../t-sql/queries/freetext-transact-sql.md)e le funzioni, ad esempio [CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md)e [FREETEXTTABLE](../../relational-databases/system-functions/freetexttable-transact-sql.md).  
  
## <a name="using-unicode-for-parsing-special-characters"></a>Utilizzo di Unicode per l'analisi di caratteri speciali  
 Quando si analizza una stringa di query, **Sys.dm fts_parser** utilizza le regole di confronto del database a cui si è connessi, a meno che non si specifica la stringa di query in formato Unicode. Pertanto, per una stringa non Unicode che contiene i caratteri speciali, ad esempio ü oppure ç, l'output potrebbe essere imprevisto, a seconda delle regole di confronto del database. Per elaborare una stringa di query indipendentemente dalle regole di confronto del database, la stringa di prefisso `N`, vale a dire `N'` *stringa_query*`'`.  
  
 Per ulteriori informazioni, vedere "C. Visualizzazione dell'output di una stringa che contiene caratteri speciali" più avanti in questo argomento.  
  
## <a name="when-to-use-sysdmftsparser"></a>Utilizzo di sys.dm_fts_parser  
 **fts_parser** può risultare molto potente per scopi di debug. Di seguito vengono riportati alcuni dei principali scenari di utilizzo:  
  
-   Comprensione del modo in cui un word breaker considera un input specificato  
  
     La restituzione di risultati imprevisti da parte di una query può essere probabilmente provocata dal modo in cui il word breaker analizza e divide i dati. Se si utilizza sys.dm_fts_parser è possibile individuare il risultato che un word breaker passa all'indice full-text. È inoltre possibile visualizzare quali termini sono parole non significative che non vengono ricercate nell'indice full-text. Se un termine è una parola non significativa per una determinata lingua variano a seconda che si tratti di parole non significative specificato da di *stoplist_id* valore dichiarato nella funzione.  
  
     Si noti inoltre il flag relativo alla distinzione tra caratteri accentati e non accentati, che consentirà all'utente di visualizzare il modo in cui il word breaker analizzerà l'input in base alle informazioni relative alla distinzione tra caratteri accentati e non accentati di cui dispone.  
  
-   Comprensione del funzionamento dello stemmer su un input specificato  
  
     Per individuare il modo in cui il word breaker e lo stemmer analizzano un termine della query e le relative forme di stemming, è possibile specificare una query CONTAINS o CONTAINSTABLE che contiene la clausola FORMSOF seguente:  
  
    ```  
    FORMSOF( INFLECTIONAL, query_term )  
    ```  
  
     I risultati indicano i termini che vengono passati all'indice full-text.  
  
-   Comprensione del modo in cui il thesaurus espande o sostituisce tutto o parte dell'input  
  
     È inoltre possibile specificare:  
  
    ```  
    FORMSOF( THESAURUS, query_term )  
    ```  
  
     I risultati di questa query indicano il modo in cui il word breaker e il thesaurus interagiscono per il termine della query. È possibile visualizzare l'espansione o le sostituzioni eseguite dal thesaurus e identificare la query risultante effettivamente inviata all'indice full-text.  
  
     Si noti che se l'utente invia:  
  
    ```  
    FORMSOF( FREETEXT, query_term )  
    ```  
  
     Le funzionalità flessive e del thesaurus verranno eseguite automaticamente.  
  
 Oltre agli scenari di utilizzo precedenti, sys.dm_fts_parser può risultare estremamente utile nella comprensione e nella risoluzione di molti altri problemi relativi alla query full-text.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza di **sysadmin** fissa diritti di accesso e ruolo del server per l'elenco di parole non significative specificato.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-displaying-the-output-of-a-given-word-breaker-for-a-keyword-or-phrase"></a>A. Visualizzazione dell'output di un word breaker specifico per una parola chiave o una frase  
 Nell'esempio seguente viene restituito l'output relativo all'utilizzo del word breaker inglese, il cui LCID è 1033, e di nessun elenco di parole non significative sulla stringa di query seguente:  
  
 `The Microsoft business analysis`  
  
 La distinzione tra caratteri accentati e non accentati è disabilitata.  
  
```  
SELECT * FROM sys.dm_fts_parser (' "The Microsoft business analysis" ', 1033, 0, 0);  
```  
  
### <a name="b-displaying-the-output-of-a-given-word-breaker-in-the-context-of-stoplist-filtering"></a>B. Visualizzazione dell'output di un word breaker specifico nel contesto di applicazione di filtri dell'elenco di parole non significative  
 Nell'esempio seguente viene restituito l'output relativo all'utilizzo del word breaker inglese, il cui LCID è 1033, e di un elenco di parole non significative, il cui ID è 77, sulla stringa di query seguente:  
  
 `"The Microsoft business analysis" OR "MS revenue"`  
  
 La distinzione tra caratteri accentati e non accentati è disabilitata.  
  
```  
SELECT * FROM sys.dm_fts_parser (' "The Microsoft business analysis"  OR " MS revenue" ', 1033, 77, 0);  
```  
  
### <a name="c-displaying-the-output-of-a-string-that-contains-special-characters"></a>C. Visualizzazione dell'output di una stringa che contiene caratteri speciali  
 Nell'esempio seguente viene utilizzato Unicode per analizzare la stringa in lingua francese seguente:  
  
 `français`  
  
 Nell'esempio viene specificato l'identificatore LCID per la lingua francese, `1036`, e l'ID di un elenco di parole non significative definito dall'utente, `5` La distinzione tra caratteri accentati e non accentati è abilitata.  
  
```  
SELECT * FROM sys.dm_fts_parser(N'français', 1036, 5, 1);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni e viste a gestione dinamica ricerca semantica e ricerca full-Text &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)   
 [Ricerca full-Text](../../relational-databases/search/full-text-search.md)   
 [Configurazione e gestione di word breaker e stemmer per la ricerca](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md)   
 [Configurare e gestire i file del Thesaurus per la ricerca Full-Text](../../relational-databases/search/configure-and-manage-thesaurus-files-for-full-text-search.md)   
 [Configurare e gestire parole non significative ed elenchi per la ricerca Full-Text](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)   
 [Eseguire query con ricerca full-text](../../relational-databases/search/query-with-full-text-search.md)   
 [Eseguire query con ricerca full-text](../../relational-databases/search/query-with-full-text-search.md)   
 [Entità a protezione diretta](../../relational-databases/security/securables.md)  
  
  

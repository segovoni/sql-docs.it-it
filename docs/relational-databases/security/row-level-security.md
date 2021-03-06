---
title: Sicurezza a livello di riga | Microsoft Docs
ms.custom: ''
ms.date: 03/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: security
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- access control predicates
- row level security
- security [SQL Server], predicate based access control
- row level security described
- predicate based security
ms.assetid: 7221fa4e-ca4a-4d5c-9f93-1b8a4af7b9e8
caps.latest.revision: 47
author: CarlRabeler
ms.author: carlraba
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: d66ca1a1b7c76d70f97d3bc4e769403c8ef939a6
ms.sourcegitcommit: 00ffbc085c5a4b792646ec8657495c83e6b851b5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/26/2018
ms.locfileid: "36943127"
---
# <a name="row-level-security"></a>Sicurezza a livello di riga
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  ![Immagine della sicurezza a livello di riga](../../relational-databases/security/media/row-level-security-graphic.png "Immagine della sicurezza a livello di riga")  
  
 La sicurezza a livello di consente ai clienti di controllare l'accesso alle righe in una tabella del database in base alle caratteristiche dell'utente che esegue una query (ad esempio, l'appartenenza al gruppo o il contesto di esecuzione).  
  
 La sicurezza a livello di riga semplifica la progettazione e la codifica della sicurezza nell'applicazione e consente di implementare delle restrizioni di accesso alle righe di dati. Ad esempio, assicura che i dipendenti possano accedere solo alle righe di dati relative al proprio reparto o limita l'accesso ai dati di un cliente in modo che possa visualizzare solo i dati rilevanti per la propria azienda.  
  
 La logica di restrizione dell'accesso si trova sul livello del database e non su un altro livello applicazione lontano dai dati. Il sistema del database applica le restrizioni di accesso a ogni tentativo di accesso ai dati da qualsiasi livello. La riduzione della superficie di attacco del sistema di sicurezza lo rende più affidabile e solido.  
  
 Implementare la sicurezza a livello di riga tramite l'istruzione [CREATE SECURITY POLICY](../../t-sql/statements/create-security-policy-transact-sql.md)[!INCLUDE[tsql](../../includes/tsql-md.md)] e i predicati creati come [funzioni inline con valori di tabella](../../relational-databases/user-defined-functions/create-user-defined-functions-database-engine.md).  
  
**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] alla [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)), [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] ([fare clic qui per ottenerlo](http://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/?WT.mc_id=TSQL_GetItTag)).  
  

##  <a name="Description"></a> Descrizione  
 La sicurezza a livello di riga supporta due tipi di predicati di sicurezza.  
  
-   I predicati del filtro filtrano automaticamente le righe disponibili per le operazioni di lettura (SELECT, UPDATE e DELETE).  
  
-   I predicati di blocco bloccano esplicitamente le operazioni di scrittura (AFTER INSERT, AFTER UPDATE, BEFORE UPDATE e BEFORE DELETE) che violano il predicato.  
  
 L'accesso ai dati a livello di riga in una tabella è limitato da un predicato di sicurezza definito come una funzione inline con valori di tabella. La funzione viene quindi richiamata e applicata dai criteri di sicurezza. Nel caso dei predicati del filtro non sono presenti indicazioni per l'applicazione che le righe sono state filtrate dal set di risultati. Se vengono filtrate tutte le righe, viene restituito un set Null. Per i predicati di blocco, qualsiasi operazione che violi il predicato non verrà completata e genererà un errore.  
  
 I predicati di filtro vengono applicati durante la lettura dei dati dalla tabella di base. Questa azione influisce su tutte le operazioni Get: **SELECT**, **DELETE** (l'utente non può eliminare le righe filtrate) e **UPDATE** (l'utente non può aggiornare le righe filtrate, sebbene sia possibile aggiornare le righe in modo che vengano filtrate successivamente). I predicati di blocco influiscono su tutte le operazioni di scrittura.  
  
-   I predicati AFTER INSERT e AFTER UPDATE possono impedire agli utenti di aggiornare le righe con valori che violano il predicato.  
  
-   I predicati BEFORE UPDATE possono impedire agli utenti di aggiornare le righe che attualmente violano il predicato.  
  
-   I predicati BEFORE DELETE possono bloccare le operazioni di eliminazione.  
  
 I predicati del filtro e di blocco e i criteri di sicurezza si comportano nel modo seguente:  
  
-   È possibile definire una funzione di predicato che si unisca a un'altra tabella e/o chiami una funzione. Se i criteri di sicurezza vengono creati con `SCHEMABINDING = ON`, il join o la funzione è accessibile dalla query e funziona come previsto senza controlli aggiuntivi delle autorizzazioni. Se i criteri di sicurezza vengono creati con `SCHEMABINDING = OFF`, gli utenti dovranno avere autorizzazioni **SELECT** o **EXECUTE** su queste tabelle e funzioni aggiuntive per eseguire query sulla tabella di destinazione.
  
-   È possibile inviare una query in una tabella con un predicato di sicurezza definito ma disabilitato. Le righe filtrate o bloccate non sono interessate.  
  
-   Se l'utente dbo, un membro del ruolo **db_owner** o il proprietario della tabella esegue query su una tabella con criteri di sicurezza definiti e abilitati, le righe vengono filtrate o bloccate in base a quanto definito nei criteri di sicurezza.  
  
-   I tentativi di modificare lo schema di una tabella tramite un criterio di sicurezza associato allo schema generano un errore. Le colonne a cui non fa riferimento il predicato possono tuttavia essere modificate.  
  
-   I tentativi di aggiunta di un predicato in una tabella in cui è già presente un predicato definito per l'operazione specificata, indipendentemente dal fatto che sia abilitato o disabilitato, generano un errore.  
  
-   Per quanto riguarda i criteri di sicurezza associati allo schema, i tentativi di modifica di una funzione usata come predicato in una tabella inclusa nei risultati di un criterio di sicurezza generano un errore.  
  
-   La definizione di più criteri di sicurezza attivi contenenti predicati non sovrapposti riesce correttamente.  
  
 I predicati del filtro si comportano nel modo seguente:  
  
-   Definire i criteri di sicurezza per filtrare le righe di una tabella. L'applicazione non rileva righe filtrate per le operazioni **SELECT**, **UPDATE**e **DELETE** , incluse le situazioni in cui sono state escluse tutte le righe. L'applicazione può eseguire **INSERT** su qualsiasi riga, a prescindere se sarà filtrata durante altre operazioni.  
  
 I predicati di blocco si comportano nel modo seguente:  
  
-   I predicati di blocco di UPDATE vengono suddivisi in operazioni distinte BEFORE e AFTER. Di conseguenza non è possibile, ad esempio, impedire agli utenti di aggiornare una riga con un valore superiore a quello corrente. Se si deve applicare una logica di questo tipo, occorre usare i trigger con le tabelle intermedie DELETED e INSERTED per rimandare ai valori precedenti e nuovi insieme.  
  
-   L'ottimizzatore non controllerà il predicato di blocco AFTER e UPDATE se non è stata modificata nessuna delle colonne usate dalla funzione del predicato. Ad esempio, Alice non deve essere in grado di modificare uno stipendio in modo che superi 100.000, ma deve essere in grado di modificare l'indirizzo di un dipendente il cui stipendio è già maggiore di 100.000 e pertanto viola già il predicato.  
  
-   Non sono state modificate le API in blocco, compresa l'API BULK INSERT. Questo significa che i predicati di blocco AFTER INSERT verranno applicati alle operazioni di inserimento in blocco come se fossero operazioni di inserimento regolari.  
  
  
##  <a name="UseCases"></a> Modalità di utilizzo comuni  
 Di seguito sono riportati degli esempi di progettazione relativi alle modalità di utilizzo della sicurezza a livello di riga:  
  
-   Un ospedale può creare criteri di sicurezza che consentono agli infermieri di visualizzare le righe di dati solo per i propri pazienti.  
  
-   Una banca può creare dei criteri per limitare l'accesso alle righe di dati finanziari in base alla divisione aziendale del dipendente o al suo ruolo nell'azienda.  
  
-   Un'applicazione multi-tenant può creare dei criteri per applicare una separazione logica delle righe di dati di ciascun tenant da qualsiasi altra riga del tenant. L'efficienza viene raggiunta archiviando i dati per diversi tenant in un'unica tabella. Naturalmente, ogni tenant può visualizzar solo le proprie righe di dati.  
  
 I predicati di filtro della sicurezza a livello di riga sono funzionalmente equivalenti all'aggiunta di una clausola **WHERE** . Il predicato può essere sofisticato, se lo richiedono le procedure aziendali, oppure è possibile usare una clausola semplice, ad esempio `WHERE TenantId = 42`.  
  
 In termini più formali, la sicurezza a livello di riga introduce il controllo degli accessi basato su predicato. Comprende una valutazione basata su predicato flessibile e centralizzata che può prendere in considerazione i metadati o altri criteri ritenuti appropriati dall'amministratore. Il predicato viene usato come criterio per determinare se l'utente dispone o meno dell'accesso appropriato ai dati in base agli attributi utente. Il controllo degli accessi basato su etichetta può essere implementato usando un controllo degli accessi basato su predicato.  
  
  
##  <a name="Permissions"></a> Permissions  
 La creazione, la modifica o l'eliminazione dei criteri di sicurezza richiede l'autorizzazione **ALTER ANY SECURITY POLICY** . La creazione o l'eliminazione dei criteri di sicurezza richiede l'autorizzazione **ALTER** nello schema.  
  
 Inoltre, per ogni predicato che viene aggiunto sono richieste le autorizzazioni seguenti:  
  
-   Le autorizzazioni**SELECT** e **REFERENCES** per la funzione usata come predicato.  
  
-   L'autorizzazione**REFERENCES** per la tabella di destinazione associata ai criteri.  
  
-   L'autorizzazione**REFERENCES** per ogni colonna della tabella di destinazione usata come argomento.  
  
 I criteri di sicurezza sono applicati a tutti gli utenti, inclusi gli utenti dbo nel database. Gli utenti dbo possono modificare o eliminare i criteri di sicurezza, tuttavia tali modifiche ai criteri di sicurezza possono essere controllate. Se un utente con privilegi elevati, ad esempio sysadmin o db_owner, deve visualizzare tutte le righe per risolvere i problemi o convalidare i dati, il criterio di sicurezza deve essere scritto in modo da consentire tale operazione.  
  
 Se i criteri di sicurezza vengono creati con `SCHEMABINDING = OFF`, per eseguire query sulla tabella di destinazione gli utenti devono avere l'autorizzazione  **SELECT** o **EXECUTE** sulla funzione di predicato e su qualsiasi tabella, vista o funzione aggiuntiva usata nella funzione di predicato. Se i criteri di sicurezza vengono creati con `SCHEMABINDING = ON` (impostazione predefinita), questi controlli delle autorizzazioni vengono ignorati quando gli utenti eseguono query sulla tabella di destinazione.  
  
  
##  <a name="Best"></a> Procedure consigliate  
  
-   Si consiglia di creare uno schema separato per gli oggetti della sicurezza a livello di riga (funzione di predicato e criteri di sicurezza).  
  
-   L'autorizzazione **ALTER ANY SECURITY POLICY** è destinata agli utenti con privilegi elevati (ad esempio, il gestore dei criteri di sicurezza). Il gestore dei criteri di sicurezza non richiede l'autorizzazione **SELECT** nelle tabella che protegge.  
  
-   Non usare le conversioni del tipo nelle funzioni di predicato per evitare potenziali errori di run-time.  
  
-   Se possibile, evitare la ricorsione nelle funzioni di predicato per evitare un calo delle prestazioni. Query Optimizer tenta di rilevare le ricorsioni dirette, ma non garantisce il rilevamento delle ricorsioni indirette (ossia, quando una seconda funzione chiama la funzione di predicato).  
  
-   Evitare di usare un numero eccessivo di join di tabella nelle funzioni di predicato per ottimizzare le prestazioni.  
  
 Evitare una logica di predicato dipendente da [opzioni SET](../../t-sql/statements/set-statements-transact-sql.md)specifiche della sessione. Nonostante sia improbabile che vengano usate in applicazioni pratiche, le funzioni di predicato la cui logica dipende da determinate opzioni **SET** specifiche della sessione possono causare perdite di informazioni se gli utenti possono eseguire query arbitrarie. Ad esempio, una funzione di predicato che converte implicitamente una stringa in **datetime** potrebbe filtrare righe diverse in base all'opzione **SET DATEFORMAT** per la sessione corrente. In generale le funzioni di predicato devono rispettare le regole seguenti:  
  
-   Le funzioni di predicato non devono convertire implicitamente stringhe di caratteri in **date**, **smalldatetime**, **datetime**, **datetime2** o **datetimeoffset** né viceversa, perché queste conversioni sono influenzate dalle opzioni [SET DATEFORMAT &#40;Transact-SQL&#41;](../../t-sql/statements/set-dateformat-transact-sql.md) e [SET LANGUAGE &#40;Transact-SQL&#41;](../../t-sql/statements/set-language-transact-sql.md). Utilizzare invece la funzione **CONVERT** e specificare esplicitamente il parametro di stile.  
  
-   Le funzioni di predicato non devono basarsi sul valore del primo giorno della settimana, perché questo valore è influenzato dall'opzione [SET DATEFIRST &#40;Transact-SQL&#41;](../../t-sql/statements/set-datefirst-transact-sql.md).  
  
-   Le funzioni di predicato non devono basarsi su espressioni aritmetiche o di aggregazione che restituiscono **NULL** in caso di errore, come overflow o divisione per zero, perché questo comportamento è influenzato dalle opzioni [SET ANSI_WARNINGS &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-warnings-transact-sql.md), [SET NUMERIC_ROUNDABORT &#40;Transact-SQL&#41;](../../t-sql/statements/set-numeric-roundabort-transact-sql.md) e [SET ARITHABORT &#40;Transact-SQL&#41;](../../t-sql/statements/set-arithabort-transact-sql.md).  
  
-   Le funzioni di predicato non devono confrontare stringhe concatenate con **NULL**, perché questo comportamento è influenzato dall'opzione [SET CONCAT_NULL_YIELDS_NULL &#40;Transact-SQL&#41;](../../t-sql/statements/set-concat-null-yields-null-transact-sql.md).  
   
  
##  <a name="SecNote"></a> Nota sulla sicurezza: attacchi al canale laterale  
 **Gestore dei criteri di sicurezza malintenzionato:** è importante osservare che un gestore dei criteri di sicurezza malintenzionato, con autorizzazioni sufficienti per creare criteri di sicurezza per una colonna sensibile e per creare o modificare le funzioni inline con valori di tabella, può agire in collusione con un altro utente con autorizzazioni Select su una tabella al fine di estrarre dolosamente i dati creando funzioni inline con valori di tabella progettate per usare attacchi al canale laterale per estrapolare i dati. Questi attacchi richiedono la collusione con altre persone (o autorizzazioni eccessive concesse a un utente malintenzionato) e richiedono probabilmente diversi tentativi di modifica dei criteri (che richiede autorizzazioni per rimuovere il predicato per interrompere l'associazione allo schema), la modifica delle funzioni inline con valori di tabella e diverse esecuzioni delle istruzioni Select nella tabella di destinazione. Si consiglia di limitare le autorizzazioni concedendo solo quelle necessarie e di monitorare le attività sospette, ad esempio la modifica frequente dei criteri e delle funzioni inline con valori di tabella relativi alla sicurezza a livello di riga.  
  
 **Query create appositamente:** è possibile causare perdite di informazioni mediante l'utilizzo di query create appositamente. Ad esempio, `SELECT 1/(SALARY-100000) FROM PAYROLL WHERE NAME='John Doe'` consentirebbe a un utente malintenzionato di sapere che lo stipendio di John Doe ammonta a 100.000 dollari. Anche se è disponibile un predicato di sicurezza per impedire le query dirette di un utente malintenzionato relative allo stipendio degli altri dipendenti, l'utente può determinare quando la query restituisce un'eccezione di divisione per zero.  
   
  
##  <a name="Limitations"></a> Compatibilità tra funzionalità  
 In generale la sicurezza a livello di riga funziona tra varie funzionalità nel modo previsto. Esistono tuttavia alcune eccezioni a questa regola. Questa sezione contiene diverse note e avvertenze per l'uso della sicurezza a livello di riga con altre funzionalità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   **DBCC SHOW_STATISTICS** genera statistiche sui dati non filtrati e potrebbero quindi verificarsi perdite di informazioni altrimenti protette da criteri di sicurezza. Per questo motivo, per visualizzare un oggetto statistiche per una tabella con criteri di sicurezza a livello di riga, l'utente deve essere il proprietario della tabella oppure un membro del ruolo predefinito del server sysadmin o del ruolo predefinito del database db_owner o db_ddladmin.  
  
-   La sicurezza a livello di riga**Filestream** non è compatibile con Filestream.  
  
-   La sicurezza a livello di riga**Polybase** non è compatibile con Polybase.  
  
-   **tabelle ottimizzate per la memoria**. La funzione inline con valori di tabella usata come predicato di sicurezza in una tabella ottimizzata per la memoria deve essere definita con l'opzione `WITH NATIVE_COMPILATION`. Con questa opzione le funzionalità del linguaggio non supportate dalle tabelle ottimizzate per la memoria verranno escluse e verrà generato l'errore appropriato al momento della creazione. Per altre informazioni, vedere la sezione relativa alla **sicurezza a livello di riga nelle tabelle con ottimizzazione per la memoria** in [Introduzione alle tabelle con ottimizzazione per la memoria](../../relational-databases/in-memory-oltp/introduction-to-memory-optimized-tables.md).  
  
-   **Viste indicizzate** In generale è possibile creare criteri di sicurezza nelle viste ed è possibile creare viste nelle tabelle associate a criteri di sicurezza. Non è possibile tuttavia creare viste indicizzate in tabelle con un criterio di sicurezza, poiché le ricerche di righe tramite l'indice potrebbero ignorare il criterio.  
  
-   **Change Data Capture** . Change Data Capture può causare la perdita di intere righe che devono essere filtrate per i membri di **db_owner** o gli utenti membri del ruolo di "controllo" specificato quando Change Data Capture viene abilitato per una tabella (si noti che è possibile impostare esplicitamente **NULL** per consentire a tutti gli utenti di accedere ai dati di modifica). I membri di questo ruolo di controllo e **db_owner** possono infatti visualizzare tutte le modifiche dei dati in una tabella anche se per la tabella esistono criteri di sicurezza.  
  
-   **Rilevamento delle modifiche** Il rilevamento delle modifiche può provocare la perdita della chiave primaria delle righe che devono essere filtrate per gli utenti con autorizzazioni **SELECT** e **VIEW CHANGE TRACKING** . I valori dei dati effettivi non vengono perduti, ma va perduto solo il fatto che la colonna A è stata aggiornata/inserita/eliminata per la riga con la chiave primaria B. Questo rappresenta un problema se la chiave primaria contiene un elemento riservato, ad esempio un codice fiscale. In pratica però **CHANGETABLE** è quasi sempre unito alla tabella originale per ottenere i dati più recenti.  
  
-   **Ricerca full-text** . A causa di un join aggiuntivo introdotto per applicare la sicurezza a livello di riga ed evitare la perdita di chiavi primarie delle righe che devono essere filtrate, è previsto un calo di prestazioni per le query che usano le funzioni di ricerca semantica e ricerca full-text seguenti: **CONTAINSTABLE**, **FREETEXTTABLE**, semantickeyphrasetable, semanticsimilaritydetailstable e semanticsimilaritytable.  
  
-   **Indici columnstore** . La sicurezza a livello di riga è compatibile con indici columnstore sia cluster che non cluster. Dato però che la sicurezza a livello di riga applica una funzione, l'ottimizzatore può modificare il piano di query in modo che non usi la modalità batch.  
  
-   **Viste partizionate** Non è possibile definire predicati di blocco nelle viste partizionate e non è possibile creare viste partizionate in tabelle che usano predicati di blocco. I predicati di filtro sono compatibili con le viste partizionate.  
  
-   **Le tabelle temporali** sono compatibili con la sicurezza a livello di riga. I predicati di sicurezza nella tabella corrente non vengono tuttavia replicati automaticamente nella tabella di cronologia. Per applicare un criterio di sicurezza alla tabella della cronologia e alla tabella corrente, è necessario aggiungere singolarmente un predicato di sicurezza in ogni tabella.  
  
  
##  <a name="CodeExamples"></a> Esempi  
  
###  <a name="Typical"></a> A. Scenari per gli utenti che eseguono l'autenticazione nel database  
 Questo breve esempio crea tre utenti, crea e popola una tabella con sei righe, quindi crea una funzione inline con valori di tabella e i criteri di sicurezza per la tabella. L'esempio mostra in che modo le istruzioni Select vengono filtrate per i diversi utenti.  
  
 Creare tre account utente per mostrare le diverse capacità di accesso.  
  
```sql  
CREATE USER Manager WITHOUT LOGIN;  
CREATE USER Sales1 WITHOUT LOGIN;  
CREATE USER Sales2 WITHOUT LOGIN;  
```  
  
 Creare una tabella semplice per conservare i dati.  
  
```  
CREATE TABLE Sales  
    (  
    OrderID int,  
    SalesRep sysname,  
    Product varchar(10),  
    Qty int  
    );  
```  
  
 Popolare la tabella con sei righe di dati che mostrano tre ordini per ciascun rappresentante.  
  
```  
INSERT Sales VALUES   
(1, 'Sales1', 'Valve', 5),   
(2, 'Sales1', 'Wheel', 2),   
(3, 'Sales1', 'Valve', 4),  
(4, 'Sales2', 'Bracket', 2),   
(5, 'Sales2', 'Wheel', 5),   
(6, 'Sales2', 'Seat', 5);  
-- View the 6 rows in the table  
SELECT * FROM Sales;  
```  
  
 Concedere l'accesso in lettura alla tabella a ciascuno degli utenti.  
  
```  
GRANT SELECT ON Sales TO Manager;  
GRANT SELECT ON Sales TO Sales1;  
GRANT SELECT ON Sales TO Sales2;  
```  
  
 Creare un nuovo schema e una funzione inline con valori di tabella. La funzione restituisce 1 quando una riga nella colonna SalesRep è uguale all'utente che esegue la query (`@SalesRep = USER_NAME()`) o se l'utente che esegue la query è l'utente gestore (`USER_NAME() = 'Manager'`).  
  
```  
CREATE SCHEMA Security;  
GO  
  
CREATE FUNCTION Security.fn_securitypredicate(@SalesRep AS sysname)  
    RETURNS TABLE  
WITH SCHEMABINDING  
AS  
    RETURN SELECT 1 AS fn_securitypredicate_result   
WHERE @SalesRep = USER_NAME() OR USER_NAME() = 'Manager';  
```  
  
 Creare i criteri di sicurezza aggiungendo la funzione come predicato di filtro. Lo stato deve essere impostato su ON per abilitare i criteri.  
  
```  
CREATE SECURITY POLICY SalesFilter  
ADD FILTER PREDICATE Security.fn_securitypredicate(SalesRep)   
ON dbo.Sales  
WITH (STATE = ON);  
```  
  
 Testare il predicato di filtro mediante la selezione dalla tabella Sales per ciascun utente.  
  
```  
EXECUTE AS USER = 'Sales1';  
SELECT * FROM Sales;   
REVERT;  
  
EXECUTE AS USER = 'Sales2';  
SELECT * FROM Sales;   
REVERT;  
  
EXECUTE AS USER = 'Manager';  
SELECT * FROM Sales;   
REVERT;  
```  
  
 Il gestore dovrebbe visualizzare tutte e sei le righe. Gli utenti Sales1 e Sales2 dovrebbero visualizzare solo le proprie vendite.  
  
 Modificare i criteri di sicurezza per disabilitarli.  
  
```  
ALTER SECURITY POLICY SalesFilter  
WITH (STATE = OFF);  
```  
  
 Ora gli utenti Sales1 e Sales2 possono visualizzare tutte e sei le righe.  
  
  
###  <a name="MidTier"></a> B. Scenari per gli utenti che si connettono al database tramite un'applicazione di livello intermedio  
 Questo esempio mostra in che modo un'applicazione di livello intermedio può implementare il filtro della connessione, in cui gli utenti dell'applicazione (o i tenant) condividono lo stesso utente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (l'applicazione). L'applicazione imposta l'ID utente dell'applicazione corrente in [SESSION_CONTEXT &#40;Transact-SQL&#41;](../../t-sql/functions/session-context-transact-sql.md) dopo la connessione al database, quindi i criteri di sicurezza filtrano in modo trasparente le righe che non devono essere visibili a tale ID e impediscono all'utente di inserire righe per l'ID utente errato. Non sono necessarie altre modifiche all'applicazione.  
  
 Creare una tabella semplice per conservare i dati.  
  
```  
CREATE TABLE Sales (  
    OrderId int,  
    AppUserId int,  
    Product varchar(10),  
    Qty int  
);  
```  
  
 Popolare la tabella con sei righe di dati che mostrano tre ordini per ciascun utente dell'applicazione.  
  
```  
INSERT Sales VALUES   
    (1, 1, 'Valve', 5),   
    (2, 1, 'Wheel', 2),   
    (3, 1, 'Valve', 4),  
    (4, 2, 'Bracket', 2),   
    (5, 2, 'Wheel', 5),   
    (6, 2, 'Seat', 5);  
```  
  
 Creare un utente con privilegi limitati che l'applicazione userà per connettersi.  
  
```  
-- Without login only for demo  
CREATE USER AppUser WITHOUT LOGIN;   
GRANT SELECT, INSERT, UPDATE, DELETE ON Sales TO AppUser;  
  
-- Never allow updates on this column  
DENY UPDATE ON Sales(AppUserId) TO AppUser;  
```  
  
 Creare un nuovo schema e una nuova funzione di predicato con cui usare l'ID utente dell'applicazione archiviato in **SESSION_CONTEXT** per filtrare le righe.  
  
```  
CREATE SCHEMA Security;  
GO  
  
CREATE FUNCTION Security.fn_securitypredicate(@AppUserId int)  
    RETURNS TABLE  
    WITH SCHEMABINDING  
AS  
    RETURN SELECT 1 AS fn_securitypredicate_result  
    WHERE  
        DATABASE_PRINCIPAL_ID() = DATABASE_PRINCIPAL_ID('AppUser')    
        AND CAST(SESSION_CONTEXT(N'UserId') AS int) = @AppUserId;   
GO  
```  
  
 Creare un criterio di sicurezza che aggiunga questa funzione come predicato di filtro e predicato di blocco in `Sales`. Nel predicato di blocco è necessario solo **AFTER INSERT**, perché **BEFORE UPDATE** e **BEFORE DELETE** sono già filtrati e **AFTER UPDATE** non è necessario perché la colonna `AppUserId` non può essere aggiornata con altri valori a causa dell'autorizzazione per la colonna impostata in precedenza.  
  
```  
CREATE SECURITY POLICY Security.SalesFilter  
    ADD FILTER PREDICATE Security.fn_securitypredicate(AppUserId)   
        ON dbo.Sales,  
    ADD BLOCK PREDICATE Security.fn_securitypredicate(AppUserId)   
        ON dbo.Sales AFTER INSERT   
    WITH (STATE = ON);  
```  
  
 Ora è possibile simulare il filtro della connessione con la selezione dalla tabella `Sales` dopo l'impostazione di ID utente diversi in **SESSION_CONTEXT**. In pratica, l'applicazione è responsabile dell'impostazione dell'ID utente corrente in **SESSION_CONTEXT** dopo l'apertura di una connessione.  
  
```  
EXECUTE AS USER = 'AppUser';  
EXEC sp_set_session_context @key=N'UserId', @value=1;  
SELECT * FROM Sales;  
GO  
  
--  Note: @read_only prevents the value from changing again   
--  until the connection is closed (returned to the connection pool)  
EXEC sp_set_session_context @key=N'UserId', @value=2, @read_only=1;   
  
SELECT * FROM Sales;  
GO  
  
INSERT INTO Sales VALUES (7, 1, 'Seat', 12); -- error: blocked from inserting row for the wrong user ID  
GO  
  
REVERT;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE SECURITY POLICY &#40;Transact-SQL&#41;](../../t-sql/statements/create-security-policy-transact-sql.md)   
 [ALTER SECURITY POLICY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-security-policy-transact-sql.md)   
 [DROP SECURITY POLICY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-security-policy-transact-sql.md)   
 [CREATE FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/create-function-transact-sql.md)   
 [SESSION_CONTEXT &#40;Transact-SQL&#41;](../../t-sql/functions/session-context-transact-sql.md)   
 [sp_set_session_context &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-set-session-context-transact-sql.md)   
 [sys.security_policies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-security-policies-transact-sql.md)   
 [sys.security_predicates &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-security-predicates-transact-sql.md)   
 [Creare funzioni definite dall'utente &#40;Motore di database&#41;](../../relational-databases/user-defined-functions/create-user-defined-functions-database-engine.md)  
  
  

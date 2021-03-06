---
title: CHANGETABLE (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 08/08/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CHANGETABLE_TSQL
- CHANGETABLE
dev_langs:
- TSQL
helpviewer_keywords:
- CHANGETABLE
- change tracking [SQL Server], CHANGETABLE
ms.assetid: d405fb8d-3b02-4327-8d45-f643df7f501a
caps.latest.revision: 34
author: rothja
ms.author: jroth
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 8b0062a473b403a62f2805f28f84d5e0d9651dcb
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33239904"
---
# <a name="changetable-transact-sql"></a>CHANGETABLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Vengono restituite informazioni sul rilevamento delle modifiche per una tabella. È possibile utilizzare questa istruzione per restituire tutte le modifiche per una tabella o informazioni sul rilevamento delle modifiche per una riga specifica.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
CHANGETABLE (  
    { CHANGES table , last_sync_version  
    | VERSION table , <primary_key_values> } )  
[AS] table_alias [ ( column_alias [ ,...n ] )  
  
<primary_key_values> ::=  
( column_name [ , ...n ] ) , ( value [ , ...n ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 Le modifiche *tabella* , *last_sync_version*  
 Restituisce informazioni di rilevamento per tutte le modifiche a una tabella che si sono verificate a partire dalla versione specificato da *last_sync_version*.  
  
 *table*  
 Tabella definita dall'utente di cui ottenere le modifiche rilevate. Il rilevamento delle modifiche deve essere abilitato per la tabella. È possibile utilizzare un nome di tabella composto da una, due, tre o quattro parti. Il nome della tabella può esserne un sinonimo.  
  
 *last_sync_version*  
 Quando ottiene modifiche, l'applicazione chiamante deve specificare il punto dal quale sono richieste le modifiche. Tale punto viene specificato da last_sync_version. La funzione restituisce informazioni per tutte le righe modificate a partire dalla versione indicata. L'applicazione esegue una query per ricevere modifiche con una versione successiva a quella restituita da last_sync_version.  
  
 In genere, prima di ottenere le modifiche, l'applicazione chiama **change_tracking_current_version ()** per ottenere la versione che verrà utilizzata il successive ora è necessario apportare modifiche. Non è pertanto necessario che l'applicazione interpreti o conosca il valore effettivo.  
  
 Poiché last_sync_version viene ottenuto dall'applicazione chiamante, il relativo valore dovrà essere salvato in modo permanente in tale applicazione. In caso di perdita del valore, sarà necessario reinizializzare i dati.  
  
 *last_sync_version* viene **bigint**. Il valore deve essere scalare. Un'espressione provocherà un errore di sintassi.  
  
 Se il valore è NULL, vengono restituite tutte le modifiche rilevate.  
  
 *last_sync_version* devono essere convalidati per assicurarsi che non sia troppo vecchio, in quanto alcune o tutte le informazioni sulle modifiche potrebbero essere state eliminate in base al periodo di memorizzazione configurato per il database. Per altre informazioni, vedere [CHANGE_TRACKING_MIN_VALID_VERSION &#40;Transact-SQL&#41; ](../../relational-databases/system-functions/change-tracking-min-valid-version-transact-sql.md) e [opzioni ALTER DATABASE SET &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md).  
  
 VERSIONE *tabella*, {< primary_key_values >}  
 Restituisce le informazioni più recenti sul rilevamento delle modifiche per una riga specificata. I valori della chiave primaria devono consentire di identificare la riga. <primary_key_values> consente di identificare le colonne chiave primarie e di specificare i valori. I nomi delle colonne chiave primaria possono essere specificati in qualsiasi ordine.  
  
 *Tabella*  
 Tabella definita dall'utente di cui ottenere le informazioni sul rilevamento delle modifiche. Il rilevamento delle modifiche deve essere abilitato per la tabella. È possibile utilizzare un nome di tabella composto da una, due, tre o quattro parti. Il nome della tabella può esserne un sinonimo.  
  
 *column_name*  
 Specifica il nome della colonna o delle colonne chiave primaria. È possibile specificare in qualsiasi ordine più nomi di colonna.  
  
 *Valore*  
 Il valore della chiave primaria. Se sono presenti più colonne chiave primaria, i valori devono essere specificati nello stesso ordine come le colonne vengono visualizzate nel *column_name* elenco.  
  
 [COME] *table_alias* [(*column_alias* [,... *n* ])]  
 Fornisce nomi per i risultati restituiti da CHANGETABLE.  
  
 *table_alias*  
 Nome alias della tabella restituito da CHANGETABLE. *table_alias* è obbligatorio e deve essere un valore valido [identificatore](../../relational-databases/databases/database-identifiers.md).  
  
 *column_alias*  
 Alias di colonna facoltativo o elenco di alias di colonna per le colonne restituite da CHANGETABLE. Consente la personalizzazione dei nomi di colonna in caso di nomi duplicati nei risultati.  
  
## <a name="return-types"></a>Tipi restituiti  
 **table**  
  
## <a name="return-values"></a>Valori restituiti  
  
### <a name="changetable-changes"></a>CHANGETABLE CHANGES  
 Specificando CHANGES, vengono restituite zero o più righe che presentano le colonne seguenti.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|SYS_CHANGE_VERSION|**bigint**|Valore della versione associato all'ultima modifica alla riga|  
|SYS_CHANGE_CREATION_VERSION|**bigint**|Valori della versione associati all'ultima operazione di inserimento.|  
|SYS_CHANGE_OPERATION|**nchar(1)**|Specifica il tipo di modifica:<br /><br /> **U** = aggiornamento<br /><br /> **È possibile** = inserimento<br /><br /> **1!d** = eliminazione|  
|SYS_CHANGE_COLUMNS|**varbinary(4100)**|Vengono elencate le colonne modificate a partire da last_sync_version (versione di riferimento). Si noti che le colonne calcolate non vengono mai elencate come modificata.<br /><br /> Il valore è NULL quando viene soddisfatta una o più delle condizioni seguenti:<br /><br /> Il rilevamento delle modifiche per le colonne non è abilitato.<br /><br /> L'operazione è di inserimento o di eliminazione.<br /><br /> Tutte le colonne chiave non primaria sono state aggiornate in un'unica operazione. Questo valore binario non deve essere interpretato direttamente. Per interpretarlo, utilizzare invece [change_tracking_is_column_in_mask ()](../../relational-databases/system-functions/change-tracking-is-column-in-mask-transact-sql.md).|  
|SYS_CHANGE_CONTEXT|**varbinary(128)**|Modificare le informazioni di contesto che è possibile specificare facoltativamente utilizzando il [WITH](../../relational-databases/system-functions/with-change-tracking-context-transact-sql.md) clausola come parte di un'istruzione INSERT, UPDATE o DELETE.|  
|\<valore della colonna chiave primaria >|Come per le colonne della tabella utente|Valori della chiave primaria per la tabella rilevata. Questi valori identificano in modo univoco ogni riga nella tabella utente.|  
  
### <a name="changetable-version"></a>CHANGETABLE VERSION  
 Quando si specifica VERSION, viene restituita una riga con le colonne seguenti.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|SYS_CHANGE_VERSION|**bigint**|Il valore della versione corrente associato alla riga.<br /><br /> Il valore è NULL se non è stata effettuata alcuna modifica per un periodo superiore a quello di memorizzazione del rilevamento delle modifiche, oppure se la riga non è stata modificata a partire dall'abilitazione del rilevamento delle modifiche.|  
|SYS_CHANGE_CONTEXT|**varbinary(128)**|Modificare le informazioni di contesto specificabili liberamente utilizzando la clausola WITH come parte di un'istruzione INSERT, UPDATE o DELETE.|  
|\<valore della colonna chiave primaria >|Come per le colonne della tabella utente|Valori della chiave primaria per la tabella rilevata. Questi valori identificano in modo univoco ogni riga nella tabella utente.|  
  
## <a name="remarks"></a>Osservazioni  
 La funzione CHANGETABLE è in genere utilizzata nella clausola FROM di una query come se si trattasse di una tabella.  
  
## <a name="changetablechanges"></a>CHANGETABLE(CHANGES...)  
 Per ottenere i dati delle righe per le righe nuove o modificate, unire il set di risultati alla tabella utente utilizzando le colonne chiave primaria. Viene restituita solo una riga per ogni riga nella tabella utente che è stata modificata, anche se sono state apportate più modifiche alla stessa riga dopo il *last_sync_version* valore.  
  
 Le modifiche alla colonna chiave primaria non vengono mai contrassegnate come aggiornamenti. Se il valore della chiave primaria cambia, ciò viene considerato come un'eliminazione del valore obsoleto e un inserimento del nuovo valore.  
  
 Se si elimina una riga per poi inserire una riga con la chiave primaria obsoleta, la modifica viene considerata come un aggiornamento per tutte le colonne nella riga.  
  
 I valori restituiti per le colonne SYS_CHANGE_OPERATION e SYS_CHANGE_COLUMNS sono relativi riferimento (last_sync_version) specificata. Ad esempio, se un'operazione di inserimento viene effettuata alla versione 10 e un'operazione di aggiornamento alla versione 15 e se la linea di base *last_sync_version* è 12, verrà riportato un aggiornamento. Se il *last_sync_version* valore è 8, verrà riportato un inserimento. I valori SYS_CHANGE_COLUMNS non riporteranno mai colonne calcolate come aggiornate.  
  
 Generalmente, vengono rilevate tutte le operazioni che consentono di inserire, aggiornare o eliminare i dati nelle tabelle utente, inclusa l'istruzione MERGE.  
  
 Le operazioni seguenti che influiscono sui dati delle tabelle utente non vengono rilevate:  
  
-   Esecuzione dell'istruzione UPDATETEXT.  
  
     Questa istruzione è deprecata e verrà rimossa in una versione futura di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Vengono tuttavia rilevate le modifiche apportate utilizzando la clausola .WRITE dell'istruzione UPDATE.  
  
-   Eliminazione di righe utilizzando TRUNCATE TABLE  
  
     Quando una tabella viene troncata, le informazioni sulla versione del rilevamento delle modifiche associata alla tabella vengono reimpostate, come se il rilevamento delle modifiche fosse stato appena abilitato nella tabella. Un'applicazione client deve sempre convalidare l'ultima versione sincronizzata. La convalida non riesce se la tabella è stata troncata.  
  
## <a name="changetableversion"></a>CHANGETABLE(VERSION...)  
 Se viene specificata una chiave primaria inesistente, viene restituito un set di risultati vuoto.  
  
 Il valore di SYS_CHANGE_VERSION potrebbe essere NULL se non sono state apportate modifiche per un periodo superiore a quello di memorizzazione, ad esempio se la pulizia ha eliminato le informazioni sulle modifiche, o se la riga non è mai stata modificata dal momento dell'abilitazione del rilevamento delle modifiche per la tabella.  
  
## <a name="permissions"></a>Autorizzazioni  
 Richiede le autorizzazioni seguenti per la tabella specificata per il *tabella* valore per ottenere informazioni sul rilevamento delle modifiche:  
  
-   Autorizzazione SELECT per le colonne chiave primaria  
  
-   VIEW CHANGE TRACKING  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-returning-rows-for-an-initial-synchronization-of-data"></a>A. Restituzione delle righe per una sincronizzazione iniziale dei dati  
 Nell'esempio seguente viene illustrato come ottenere i dati per una sincronizzazione iniziale dei dati della tabella. La query restituisce tutti i dati delle righe e le relative versioni associate. Sarà quindi possibile inserire o aggiungere tali dati al sistema che conterrà i dati sincronizzati.  
  
```sql  
-- Get all current rows with associated version  
SELECT e.[Emp ID], e.SSN, e.FirstName, e.LastName,  
    c.SYS_CHANGE_VERSION, c.SYS_CHANGE_CONTEXT  
FROM Employees AS e  
CROSS APPLY CHANGETABLE   
    (VERSION Employees, ([Emp ID], SSN), (e.[Emp ID], e.SSN)) AS c;  
```  
  
### <a name="b-listing-all-changes-that-were-made-since-a-specific-version"></a>B. Elenco di tutte le modifiche effettuate a partire da una versione specifica  
 Nell'esempio seguente viene illustrato come elencare tutte le modifiche effettuate in una tabella a partire dalla versione specificata (`@last_sync_version)`. [Emp ID] e SSN sono colonne in una chiave primaria composta.  
  
```sql  
DECLARE @last_sync_version bigint;  
SET @last_sync_version = <value obtained from query>;  
SELECT [Emp ID], SSN,  
    SYS_CHANGE_VERSION, SYS_CHANGE_OPERATION,  
    SYS_CHANGE_COLUMNS, SYS_CHANGE_CONTEXT   
FROM CHANGETABLE (CHANGES Employees, @last_sync_version) AS C;  
```  
  
### <a name="c-obtaining-all-changed-data-for-a-synchronization"></a>C. Acquisizione di tutti i dati modificati per una sincronizzazione  
 Nell'esempio seguente viene illustrato come ottenere tutti i dati modificati. La query unisce le informazioni sul rilevamento delle modifiche alla tabella utente, in modo da restituire le informazioni sulla tabella utente. Utilizzando un `LEFT OUTER JOIN` viene restituita una riga per le righe eliminate.  
  
```sql  
-- Get all changes (inserts, updates, deletes)  
DECLARE @last_sync_version bigint;  
SET @last_sync_version = <value obtained from query>;  
SELECT e.FirstName, e.LastName, c.[Emp ID], c.SSN,  
    c.SYS_CHANGE_VERSION, c.SYS_CHANGE_OPERATION,  
    c.SYS_CHANGE_COLUMNS, c.SYS_CHANGE_CONTEXT   
FROM CHANGETABLE (CHANGES Employees, @last_sync_version) AS c  
    LEFT OUTER JOIN Employees AS e  
        ON e.[Emp ID] = c.[Emp ID] AND e.SSN = c.SSN;  
```  
  
### <a name="d-detecting-conflicts-by-using-changetableversion"></a>D. Rilevamento di conflitti utilizzando CHANGETABLE(VERSION...)  
 Nell'esempio seguente viene illustrato come aggiornare una riga che non ha subito modifiche dall'ultima sincronizzazione. Il numero di versione della riga specifica si ottiene utilizzando `CHANGETABLE`. Se la riga è stata aggiornata, le modifiche non vengono effettuate e la query restituisce informazioni sulla sua modifica più recente.  
  
```sql  
-- @last_sync_version must be set to a valid value  
UPDATE  
    SalesLT.Product  
SET  
    ListPrice = @new_listprice  
FROM  
    SalesLT.Product AS P  
WHERE  
    ProductID = @product_id AND  
    @last_sync_version >= ISNULL (  
        (SELECT CT.SYS_CHANGE_VERSION FROM   
            CHANGETABLE(VERSION SalesLT.Product,  
            (ProductID), (P.ProductID)) AS CT),  
        0);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni di rilevamento delle modifiche &#40;Transact-SQL&#41;](../../relational-databases/system-functions/change-tracking-functions-transact-sql.md)   
 [Rilevare le modifiche ai dati &#40;SQL Server&#41;](../../relational-databases/track-changes/track-data-changes-sql-server.md)   
 [CHANGE_TRACKING_IS_COLUMN_IN_MASK &#40;Transact-SQL&#41;](../../relational-databases/system-functions/change-tracking-is-column-in-mask-transact-sql.md)   
 [CHANGE_TRACKING_CURRENT_VERSION &#40;Transact-SQL&#41;](../../relational-databases/system-functions/change-tracking-current-version-transact-sql.md)   
 [CHANGE_TRACKING_MIN_VALID_VERSION &#40;Transact-SQL&#41;](../../relational-databases/system-functions/change-tracking-min-valid-version-transact-sql.md)  
  
  

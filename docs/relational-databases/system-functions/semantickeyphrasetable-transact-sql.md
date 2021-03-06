---
title: semantickeyphrasetable (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- semantickeyphrasetable
- semantickeyphrasetable_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- semantickeyphrasetable function
ms.assetid: d33b973a-2724-4d4b-aaf7-67675929c392
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 98d837abe05cf99051230e24fd0d418e1263aa4f
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33236065"
---
# <a name="semantickeyphrasetable-transact-sql"></a>semantickeyphrasetable (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Restituisce una tabella con zero, una o più righe per le frasi chiave associate alle colonne indicate nella tabella specificata.  
  
 A questa funzione per i set di righe è possibile fare riferimento nella clausola FROM di un'istruzione SELECT come se fosse un normale nome di tabella.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```sql  
SEMANTICKEYPHRASETABLE  
    (  
    table,  
    { column | (column_list) | * }  
     [ , source_key ]  
    )  
```  
  
##  <a name="Arguments"></a> Argomenti  
 **table**  
 Nome di una tabella per cui è abilitata l'indicizzazione full-text e semantica.  
  
 Questo nome può essere costituito da una a quattro parti, ma non è consentito un nome di server remoto.  
  
 **column**  
 Nome della colonna indicizzata per cui restituire risultati. Per la colonna deve essere abilitata l'indicizzazione semantica.  
  
 **column_list**  
 Indica diverse colonne, separate da una virgola e racchiuse tra parentesi. Per tutte le colonne deve essere abilitata l'indicizzazione semantica.  
  
 **\***  
 Indica che tutte le colonne per cui l'indicizzazione semantica è abilitata sono incluse.  
  
 **source_key**  
 Chiave univoca per la riga per richiedere risultati per una riga specifica.  
  
 Laddove possibile, la chiave viene convertita in modo implicito nel tipo della chiave univoca full-text nella tabella di origine. La chiave può essere specificata come costante o variabile, ma non può essere un'espressione o il risultato di una sottoquery scalare. Se si omette source_key, vengono restituiti risultati per tutte le righe.  
  
## <a name="table-returned"></a>Tabella restituita  
 Nella tabella seguente vengono descritte le informazioni sulle frasi chiave restituite da questa funzione per i set di righe.  
  
|Nome della colonna|Tipo|Description|  
|------------------|----------|-----------------|  
|**column_id**|**int**|ID della colonna da cui è stata estratta e indicizzata la frase chiave corrente.<br /><br /> Vedere le funzioni COL_NAME e COLUMNPROPERTY per informazioni dettagliate su come recuperare il nome di colonna da column_id e viceversa.|  
|**document_key**|**\***<br /><br /> Questa chiave corrisponde al tipo della chiave univoca nella tabella di origine.|Valore della chiave univoca del documento o della riga da cui è stata indicizzata la frase chiave corrente.|  
|**frasi chiave**|**NVARCHAR**|Frase chiave trovata nella colonna identificata da column_id e associato con il documento specificato da document_key.|  
|**Punteggio**|**REAL**|Valore relativo per la frase chiave nella sua relazione con tutte le altre frasi chiave nello stesso documento presente nella colonna indicizzata.<br /><br /> Il valore è un valore decimale frazionario compreso nell'intervallo [0.0, 1.0], dove un punteggio maggiore rappresenta un peso maggiore e 1.0 costituisce il punteggio perfetto.|  
  
## <a name="general-remarks"></a>Osservazioni generali  
 Per ulteriori informazioni, vedere [trovare frasi chiave nei documenti mediante ricerca semantica](../../relational-databases/search/find-key-phrases-in-documents-with-semantic-search.md).  
  
## <a name="metadata"></a>Metadati  
 Per informazioni generali e sullo stato relative all'estrazione e al popolamento semantici di frasi chiave, eseguire una query sulle DMV seguenti:  
  
-   [sys.dm_db_fts_index_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-fts-index-physical-stats-transact-sql.md)  
  
-   [sys.dm_fts_index_population &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql.md)  
  
## <a name="security"></a>Sicurezza  
  
### <a name="permissions"></a>Autorizzazioni  
 Sono necessarie autorizzazioni SELECT per la tabella di base in cui sono stati creati gli indici full-text e semantico.  
  
## <a name="examples"></a>Esempi  
  
###  <a name="HowToTopPhrases"></a>Esempio 1: Trovare le principali frasi chiave in un documento specifico  
 L'esempio seguente recupera le prime 10 frasi chiave dal documento specificato tramite la variabile @DocumentId nella colonna Document della tabella Production.Document del database di esempio AdventureWorks. La variabile @DocumentId rappresenta un valore della colonna chiave dell'indice full-text. La funzione **SEMANTICKEYPHRASETABLE** recupera in modo efficiente questi risultati tramite una ricerca nell'indice anziché un'analisi della tabella. In questo esempio si presuppone che la colonna venga configurata per l'indicizzazione full-text e semantica.  
  
```sql  
SELECT TOP(10) KEYP_TBL.keyphrase  
FROM SEMANTICKEYPHRASETABLE  
    (  
    Production.Document,  
    Document,  
    @DocumentId  
    ) AS KEYP_TBL  
ORDER BY KEYP_TBL.score DESC;  
  
```  
  
###  <a name="HowToTopDocuments"></a>Esempio 2: Trovare i documenti principali che contengono una frase chiave specifica  
 Nell'esempio seguente vengono recuperati i primi 25 documenti che contengono la frase chiave "supporto" dalla colonna Documento della tabella Production.Document del database di esempio AdventureWorks. In questo esempio si presuppone che la colonna venga configurata per l'indicizzazione full-text e semantica.  
  
```sql  
SELECT TOP (25) DOC_TBL.DocumentID, DOC_TBL.DocumentSummary  
FROM Production.Document AS DOC_TBL  
    INNER JOIN SEMANTICKEYPHRASETABLE  
    (  
    Production.Document,  
    Document  
    ) AS KEYP_TBL  
ON DOC_TBL.DocumentID = KEYP_TBL.document_key  
WHERE KEYP_TBL.keyphrase = 'Bracket'  
ORDER BY KEYP_TBL.Score DESC;  
  
```  
  
  

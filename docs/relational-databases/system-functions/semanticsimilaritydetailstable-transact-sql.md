---
title: semanticsimilaritydetailstable (Transact-SQL) | Documenti Microsoft
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
- semanticsimilaritydetailstable
- semanticsimilaritydetailstable_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- semanticsimilaritydetailstable function
ms.assetid: 038d751a-fca5-4b4c-9129-cba741a4e173
caps.latest.revision: 16
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 31e23931b0b4b22df06cde0981209c28aecef373
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33236633"
---
# <a name="semanticsimilaritydetailstable-transact-sql"></a>semanticsimilaritydetailstable (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Restituisce una tabella di zero, una o più righe di frasi chiave comuni in due documenti (un documento di origine e un documento corrispondente) il cui contenuto è semanticamente simile.  
  
 Questa funzione di set di righe può fare riferimento nella clausola FROM di un'istruzione SELECT 
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```sql  
SEMANTICSIMILARITYDETAILSTABLE  
    (  
    table,  
    source_column,  
    source_key,  
    matched_column,  
    matched_key  
    )  
```  
  
##  <a name="Arguments"></a> Argomenti  
 **table**  
 Nome di una tabella per cui è abilitata l'indicizzazione full-text e semantica.  
  
 Questo nome può essere costituito da una a quattro parti, ma non è consentito un nome di server remoto.  
  
 **source_column**  
 Nome della colonna nella riga di origine in cui è presente il contenuto da confrontare per la somiglianza.  
  
 **source_key**  
 Chiave univoca che rappresenta la riga del documento di origine.  
  
 Quando possibile, questa chiave viene convertita in modo implicito nel tipo della chiave univoca full-text nella tabella di origine. La chiave può essere specificata come costante o variabile, ma non può essere un'espressione o il risultato di una sottoquery scalare. Se si specifica una chiave non valida, non viene restituita alcuna riga.  
  
 **matched_column**  
 Nome della colonna nella riga corrispondente in cui è presente il contenuto da confrontare per la somiglianza.  
  
 **matched_key**  
 Chiave univoca che rappresenta la riga del documento corrispondente.  
  
 Quando possibile, questa chiave viene convertita in modo implicito nel tipo della chiave univoca full-text nella tabella di origine. La chiave può essere specificata come costante o variabile, ma non può essere un'espressione o il risultato di una sottoquery scalare.  
  
## <a name="table-returned"></a>Tabella restituita  
 Nella tabella seguente vengono descritte le informazioni sulle frasi chiave restituite da questa funzione per i set di righe.  
  
|Nome della colonna|Tipo|Description|  
|------------------|----------|-----------------|  
|**frasi chiave**|**NVARCHAR**|Frase chiave che contribuisce alla somiglianza tra documento di origine e il documento corrispondente.|  
|**Punteggio**|**REAL**|Valore relativo per la frase chiave nella relazione con tutte le altre frasi chiave analoghe nei due documenti.<br /><br /> Il valore è un valore decimale frazionario compreso nell'intervallo [0.0, 1.0], dove un punteggio maggiore rappresenta un peso maggiore e 1.0 costituisce il punteggio perfetto.|  
  
## <a name="general-remarks"></a>Osservazioni generali  
 Per ulteriori informazioni, vedere [trovare documenti simili e correlati tramite la ricerca semantica](../../relational-databases/search/find-similar-and-related-documents-with-semantic-search.md).  
  
## <a name="metadata"></a>Metadati  
 Per informazioni generali e sullo stato relative all'estrazione e al popolamento della somiglianza semantica, eseguire una query sulle DMV seguenti:  
  
-   [sys.dm_db_fts_index_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-fts-index-physical-stats-transact-sql.md)  
  
-   [sys.dm_fts_semantic_similarity_population &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-semantic-similarity-population-transact-sql.md)  
  
## <a name="security"></a>Sicurezza  
  
### <a name="permissions"></a>Autorizzazioni  
 Sono necessarie autorizzazioni SELECT per la tabella di base in cui sono stati creati gli indici full-text e semantico.  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente recupera le 5 frasi chiave che al punteggio di somiglianza più elevato tra i candidati specificati nella **Jobcandidate** tabella del database di esempio AdventureWorks2012. Il @CandidateId e @MatchedID le variabili rappresentano i valori della colonna chiave dell'indice full-text.  
  
```sql  
SELECT TOP(5) KEY_TBL.keyphrase, KEY_TBL.score  
FROMSEMANTICSIMILARITYDETAILSTABLE  
    (  
    HumanResources.JobCandidate,  
    Resume, @CandidateID,  
    Resume, @MatchedID  
    ) AS KEY_TBL  
ORDER BY KEY_TBL.score DESC;  
  
```  
  
  

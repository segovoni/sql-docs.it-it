---
title: Proprietà indice full-Text (pagina generale) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: search
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.fulltextindexproperties.general.f1
ms.assetid: f4dff61c-8c2f-4ff9-abe4-70a34421448f
caps.latest.revision: 27
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 825b7e357d5904108b9dd4cbdec9533e89313c83
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37149932"
---
# <a name="full-text-index-properties-general-page"></a>Proprietà indice full-text (pagina Generale)
  **Per visualizzare o modificare le proprietà modificabili di un indice full-text**  
  
-   [Gestire indici full-text](../relational-databases/indexes/indexes.md)  
  
## <a name="uielement-list"></a>Elenco degli elementi di interfaccia  
 **Catalogo full-Text**  
 Visualizza il nome del catalogo full-text a cui è associato l'indice full-text.  
  
 **Database**  
 Visualizza il nome del database in cui risiede l'indice full-text.  
  
 **Tabella**  
 Visualizza il nome della tabella utilizzata per la definizione dell'indice full-text.  
  
 **Chiave di indice full-Text**  
 Visualizza il nome della chiave per l'indice full-text, ovvero un indice univoco presente in una singola colonna della tabella.  
  
 **Stato popolamento Full-Text tabella**  
 Visualizza lo stato di popolamento della tabella con indicizzazione full-text.  
  
 I valori possibili sono i seguenti:  
  
 0 = Inattivo  
  
 1 = Popolamento completo in corso.  
  
 2 = Popolamento incrementale in corso.  
  
 3 = Propagazione delle modifiche rilevate in corso.  
  
 4 = Operazione in corso per l'indice ad aggiornamento in background, ad esempio il rilevamento automatico delle modifiche.  
  
 5 = Indicizzazione full-text rallentata o sospesa.  
  
 **Indice Full-Text attivo**  
 Indica se la tabella include un indice full-text attivo.  
  
 1 = True  
  
 0 = False  
  
 **Filegroup indice full-Text**  
 Filegroup cui appartiene l'indice full-text.  
  
 **Elenco di parole non significative indice full-text**  
 Elenco di parole non significative associate all'indice full-text. Un elenco di parole non significative è un elenco delle [parole non significative](../relational-databases/search/full-text-search.md). eventualmente associato a un indice full-text viene applicato alle query full-text su tale indice. È possibile rimuovere l'elenco di parole non significative dall'indice selezionando  **\<OFF >** dall'elenco, oppure è possibile selezionare un elenco diverso;  **\<Sistema >** indica l'elenco di parole non significative di sistema.  
  
 **Per creare un elenco di parole non significative**  
  
-   [Configurare e gestire parole non significative ed elenchi di parole non significative per la ricerca full-text](../relational-databases/search/full-text-search.md)  
  
 **Elenco delle proprietà di ricerca**  
 Elenco delle proprietà di ricerca, se presente, attualmente associato all'indice full-text. Un elenco delle proprietà di ricerca specifica un set di proprietà del documento incluse nell'indice full-text associato al momento del popolamento. Per altre informazioni, vedere [Eseguire ricerche nelle proprietà dei documenti con elenchi delle proprietà di ricerca](../relational-databases/search/search-document-properties-with-search-property-lists.md).  
  
 **\<Off >** indica che non è attualmente alcun elenco di proprietà di ricerca associato all'indice. È possibile rimuovere l'elenco di proprietà di ricerca corrente dall'indice selezionando  **\<Off >** dall'elenco, oppure è possibile selezionare un elenco di proprietà di ricerca diverso nell'elenco. Questo elenco contiene solo gli elenchi delle proprietà di ricerca inclusi nel database corrente.  
  
> [!NOTE]  
>  È possibile associare un elenco delle proprietà di ricerca specificato a più indici full-text nello stesso database.  
  
 **Per creare un elenco di proprietà di ricerca**  
  
-   [Eseguire ricerche nelle proprietà dei documenti con elenchi delle proprietà di ricerca](../relational-databases/search/search-document-properties-with-search-property-lists.md)  
  
 **Conteggio elementi Full-Text tabella**  
 Indica il numero di righe sottoposte correttamente a indicizzazione full-text.  
  
 Questa proprietà corrisponde al `TableFulltextItemCount` proprietà restituita da OBJECTPROPERTYEX [!INCLUDE[tsql](../includes/tsql-md.md)] (funzione).  
  
 **Documenti Full-Text della tabella elaborati**  
 Visualizza il numero di righe che sono state elaborate dopo l'avvio dell'indicizzazione full-text. In una tabella sottoposta a indicizzazione ai fini della ricerca full-text tutte le colonne di una riga vengono considerate come appartenenti a un unico documento da indicizzare. Le righe eliminate non vengono conteggiate.  
  
|||  
|-|-|  
|0|Indica che l'indicizzazione full-text è stata completata e non è presente alcun popolamento attivo.|  
|> 0|Per un popolamento attivo, indica il numero di documenti elaborati da operazioni di inserimento o aggiornamento dopo una delle operazioni seguenti: popolamento, abilitazione del rilevamento delle modifiche con popolamento dell'indice ad aggiornamento in background (ad esempio il rilevamento automatico delle modifiche), modifica dello schema dell'indice full-text, ricompilazione del catalogo full-text, riavvio dell'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] e così via.|  
  
 **Full-Text tabella delle modifiche in sospeso**  
 Numero di voci in sospeso del rilevamento delle modifiche da elaborare.  
  
 0 = Il rilevamento delle modifiche non è abilitato.  
  
 NULL = La tabella non include un indice full-text.  
  
 **Conteggio errori Full-Text tabella**  
 Numero di righe non indicizzate dalla ricerca full-text.  
  
 0 = Popolamento completato.  
  
 \>0 = possibili valori sono i seguenti:  
  
-   Numero di documenti non indicizzati dopo l'avvio del popolamento con rilevamento delle modifiche ad aggiornamento completo, incrementale e manuale.  
  
-   Per il rilevamento delle modifiche con un indice ad aggiornamento in background, numero di righe non indicizzate dopo l'avvio o il riavvio del popolamento. La mancata indicizzazione potrebbe essere dovuta a una modifica dello schema, alla ricompilazione del catalogo, al riavvio del server e così via.  
  
 **Indicizzazione full-text abilitata**  
 Specifica se l'indicizzazione full-text è abilitata.  
  
|||  
|-|-|  
|**True**|Abilitata|  
|**False**|Disabilitata|  
  
 **Rilevamento delle modifiche**  
 Specifica se per la tabella è abilitato il rilevamento delle modifiche full-text e, in caso affermativo, di quale tipo. Con il rilevamento delle modifiche full-text viene mantenuto un record delle righe modificate in una tabella o in una vista indicizzata configurata per l'indicizzazione full-text. Tali modifiche possono essere propagate nell'indice full-text.  
  
 I valori di **Rilevamento modifiche** sono i seguenti:  
  
|||  
|-|-|  
|**Off**|L'indice full-text non viene aggiornato con le modifiche apportate ai dati sottostanti.|  
|**Manuale**|L'indice full-text non viene aggiornato automaticamente con le modifiche apportate ai dati sottostanti. Tuttavia, le modifiche apportate ai dati sottostanti vengono mantenute ed è possibile propagarle all'indice full-text in base a una pianificazione utilizzando SQL Server Agent o manualmente.|  
|**Automatico**|L'indice full-text viene aggiornato automaticamente con le modifiche apportate ai dati sottostanti nella tabella di base.|  
  
 **Ripopolamento indice**  
 Fare clic per avviare un popolamento sull'indice full-text alla chiusura della finestra di dialogo. Selezionare uno dei tipi di popolamento seguenti:  
  
|||  
|-|-|  
|**Full**|Durante il popolamento di una tabella, vengono create voci di indice per tutte le righe.|  
|**Incrementale**|Il popolamento incrementale aggiorna l'indice full-text relativamente alle righe aggiunte, eliminate o modificate dopo l'ultimo popolamento o durante la sua esecuzione. Eseguire un popolamento incrementale, è necessario che la tabella di base contenga una colonna del `timestamp` tipo di dati.|  
|**Update**|L'indice full-text viene aggiornato ogni qual volta i dati della tabella di base vengono modificati.|  
  
## <a name="see-also"></a>Vedere anche  
 [Introduzione alla ricerca full-text](../relational-databases/search/get-started-with-full-text-search.md)  
  
  

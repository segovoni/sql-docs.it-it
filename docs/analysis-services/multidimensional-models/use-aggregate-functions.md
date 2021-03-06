---
title: Utilizzare le funzioni di aggregazione | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d4e30b5670e7a9a02fdfa9f3bbfad6889e83b562
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34026038"
---
# <a name="use-aggregate-functions"></a>Utilizzare le funzioni di aggregazione
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Quando una dimensione viene usata per sezionare una misura, la misura viene riepilogata in base alle gerarchie contenute in tale dimensione. Il comportamento della somma dipende dalla funzione di aggregazione specificata per la misura. Per la maggior parte delle misure contenenti dati numerici, la funzione di aggregazione è **Sum**. Il valore della misura sarà la somma di quantità diverse a seconda di quale sarà il livello della gerarchia attivo.  
  
 In Analysis Services, ogni misura creata è supportata da una funzione di aggregazione che determina l'operazione della misura. I tipi di aggregazione predefiniti sono **Sum**, **Min**, **Max**, **Count**, **Distinct Count**oltre a diverse altre funzioni più specialistiche. In alternativa, se sono necessarie aggregazioni basate su formule complesse o personalizzate, è possibile creare un calcolo MDX anziché una funzione di aggregazione predefinita. Se ad esempio si vuole definire una misura per un valore percentuale, si procede in MDX, usando una misura calcolata. Vedere [Istruzione CREATE MEMBER &#40;MDX&#41;](../../mdx/mdx-data-definition-create-member.md).  
  
 Le misure create tramite la Creazione guidata cubo vengono assegnate a un tipo di aggregazione come parte della definizione della misura. Il tipo di aggregazione è sempre **Sum**, supponendo che la colonna di origine contenga dati numerici. **Sum** viene assegnato a prescindere dal tipo di dati della colonna di origine. Se ad esempio si usa la Creazione guidata cubo per creare misure e si inseriscono tutte le colonne di una tabella dei fatti, si noterà che tutte le misure risultanti presentano un'aggregazione di **Sum**, anche se l'origine è una colonna data e ora. Controllare sempre i metodi di aggregazione pre-assegnati per le misure create tramite la procedura guidata, per assicurarsi che la funzione di aggregazione sia adatta.  
  
 È possibile assegnare o modificare il metodo di aggregazione sia nella definizione del cubo, tramite [!INCLUDE[ss_dtbi](../../includes/ss-dtbi-md.md)], sia tramite MDX. Per altre istruzioni, vedere [Creare misure e gruppi di misure nei modelli multidimensionali](../../analysis-services/multidimensional-models/create-measures-and-measure-groups-in-multidimensional-models.md) o [Aggregate &#40;MDX&#41;](../../mdx/aggregate-mdx.md).  
  
##  <a name="AggFunction"></a> Funzioni di aggregazione  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] fornisce funzioni per aggregare misure insieme alle dimensioni contenute in gruppi di misure. L' *additività* di una funzione di aggregazione determina la modalità di aggregazione della misura in tutte le dimensioni del cubo. Le funzioni di aggregazione presentano tre livelli di additività:  
  
 Additive  
 Una misura additiva, definita anche misura completamente additiva, può essere aggregata in tutte le dimensioni incluse nel gruppo di misure contenente la misura, senza restrizioni.  
  
 Semiadditive  
 Una misura semiadditiva può essere aggregata in alcune ma non in tutte le dimensioni incluse nel gruppo contenente la misura. Una misura che rappresenta ad esempio la quantità disponibile di scorte può essere aggregata in una dimensione di tipo Geografia per produrre una quantità totale disponibile per tutti i magazzini, ma non può essere aggregata in una dimensione temporale perché rappresenta uno snapshot periodico di quantità disponibili. L'aggregazione di tale misura in una dimensione temporale genererebbe risultati non corretti. Per informazioni dettagliate, vedere [Definire una funzione semiadditiva](../../analysis-services/multidimensional-models/define-semiadditive-behavior.md) .  
  
 Nonadditive  
 Una misura non additiva non può essere aggregata in alcuna dimensione inclusa nel gruppo contenente la misura. La misura deve essere invece calcolata singolarmente per ogni cella inclusa nel cubo che rappresenta la misura. Una misura calcolata che restituisce una percentuale, quale un margine di profitto, non può ad esempio essere aggregata dai valori della percentuale dei membri figlio in alcuna dimensione.  
  
 Nella tabella seguente vengono elencate le funzioni di aggregazione disponibili in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]e vengono descritti sia il livello di additività che l'output previsto della funzione.  
  
|Funzione di aggregazione|additività|Valore restituito|  
|--------------------------|----------------|--------------------|  
|**Sum**|Additive|Calcola la somma dei valori per tutti i membri figlio. Si tratta della funzione di aggregazione predefinita.|  
|**Count**|Additive|Recupera il numero di tutti i membri figlio.|  
|**Min**|Semiadditive|Recupera il valore minimo per tutti i membri figlio.|  
|**Max**|Semiadditive|Recupera il valore massimo per tutti i membri figlio.|  
|**DistinctCount**|Nonadditive|Recupera il numero di tutti i membri figlio univoci. Per altri dettagli, vedere [Informazioni sulle misure Distinct Count](../../analysis-services/multidimensional-models/use-aggregate-functions.md#bkmk_distinct) nella sezione successiva.|  
|**Nessuno**|Nonadditive|Non viene eseguita alcuna aggregazione e tutti i valori per i membri foglia e non foglia in una dimensione vengono specificati direttamente dalla tabella dei fatti per il gruppo di misure contenente la misura. Se non è possibile leggere alcun valore dalla tabella dei fatti per un membro, il valore per il membro è impostato su Null.|  
|**ByAccount**|Semiadditive|Calcola l'aggregazione in base alla funzione di aggregazione assegnata al tipo di conto per un membro in una dimensione di tipo Conti. Se nel gruppo di misure non è presente alcuna dimensione di tipo Conti, deve essere considerata come la funzione di aggregazione **None** .<br /><br /> Per altre informazioni sulle dimensioni di tipo Conti, vedere [Creare un conto finanziario della dimensione di tipo padre-figlio](../../analysis-services/multidimensional-models/database-dimensions-finance-account-of-parent-child-type.md).|  
|**AverageOfChildren**|Semiadditive|Calcola la media dei valori per tutti i membri figlio non vuoti.|  
|**FirstChild**|Semiadditive|Recupera il valore del primo membro figlio.|  
|**LastChild**|Semiadditive|Recupera il valore dell'ultimo membro figlio.|  
|**FirstNonEmpty**|Semiadditive|Recupera il valore del primo membro figlio non vuoto.|  
|**LastNonEmpty**|Semiadditive|Recupera il valore dell'ultimo membro figlio non vuoto.|  
  
##  <a name="bkmk_distinct"></a> Informazioni sulle misure Distinct Count  
 Una misura con il valore della proprietà **Funzione di aggregazione** impostato su **Distinct Count** viene denominata misura Distinct Count. Una misura Distinct Count può essere usata per conteggiare le occorrenze dei membri di livello più basso di una dimensione nella tabella dei fatti. Poiché si tratta di un conteggio di valori distinti, un membro con più occorrenze viene conteggiato una sola volta. Una misura Distinct Count viene sempre inserita in un gruppo di misure dedicato. L'inserimento di una misura Distinct Count nel proprio gruppo di misure è una procedura consigliata che è stata creata nella finestra di progettazione come tecnica di ottimizzazione delle prestazioni.  
  
 Le misure Distinct Count vengono in genere usate per determinare per ogni membro di una dimensione il numero dei membri distinti di livello più basso di un'altra dimensione che condividono righe nella tabella dei fatti. In un cubo Sales, ad esempio, è possibile determinare il numero di prodotti distinti acquistati per ogni cliente e gruppo di clienti, individuando per ogni membro della dimensione Customers il numero di membri distinti di livello più basso della dimensione Products che condividono righe nella tabella dei fatti. In un cubo Internet Site Visits, invece, è ad esempio possibile determinare il numero di pagine distinte visitate nel sito Internet, individuando per ogni membro della dimensione Site Visitors il numero di membri distinti di livello più basso della dimensione Pages che condividono righe nella tabella dei fatti. In ognuno di questi esempi, i membri di livello più basso della seconda dimensione vengono conteggiati mediante una misura Distinct Count.  
  
 Questo tipo di analisi non deve necessariamente essere limitata a due dimensioni. Una misura Distinct Count può infatti essere separata e sezionata con qualsiasi combinazione di dimensioni del cubo, inclusa la dimensione contenente i membri conteggiati.  
  
 Una misura Distinct Count con conteggio dei membri è basata su una colonna chiave esterna nella tabella dei fatti, identificata dalla proprietà **Colonna di origine** della misura. Questa colonna viene unita in join alla colonna della tabella della dimensione che identifica i membri conteggiati mediante la misura Distinct Count.  
  
## <a name="see-also"></a>Vedere anche  
 [Le misure e gruppi di misure](../../analysis-services/multidimensional-models/measures-and-measure-groups.md)   
 [Riferimento alla funzione MDX & #40; MDX & #41;](../../mdx/mdx-function-reference-mdx.md)   
 [Definisci funzioni semiadditive](../../analysis-services/multidimensional-models/define-semiadditive-behavior.md)  
  
  

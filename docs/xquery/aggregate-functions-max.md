---
title: max (funzione) (XQuery) | Documenti Microsoft
ms.custom: 
ms.date: 03/09/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- max function [XQuery]
- fn:max function
ms.assetid: 5ee625c0-044a-4cda-b210-02b64e619d65
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1c3a2ac9b8831fa97843f8de69efca887a2f8437
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="aggregate-functions---max"></a>Funzioni di aggregazione - max
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Restituisce da una sequenza di valori atomici, *$arg*, l'unico elemento il cui valore è maggiore di quello di tutti gli altri.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
fn:max($arg as xdt:anyAtomicType*) as xdt:anyAtomicType?  
```  
  
## <a name="arguments"></a>Argomenti  
 *$arg*  
 Sequenza di valori atomici dalla quale deve essere restituito il valore massimo.  
  
## <a name="remarks"></a>Osservazioni  
 Tutti i tipi di valori atomizzati passati a **max ()** devono essere sottotipi dello stesso tipo di base. Tipi di base accettati sono i tipi che supportano il **gt** operazione. Tra questi tipi sono inclusi i tre tipi di base numerici predefiniti, ovvero i tipi di base di data/ora xs:string, xs:boolean e xdt:untypedAtomic. Per i valori di tipo xdt:untypedAtomic viene eseguito il cast a xs:double. Se è presente una combinazione di questi tipi, o se vengono passati altri valori di altri tipi, viene generato un errore statico.  
  
 Il risultato di **max ()** riceve il tipo di base dei tipi passati, ad esempio xs: double nel caso di xdt: untypedAtomic. Se l'input è una sequenza vuota calcolata in modo statico, la sequenza vuota è implicita e viene restituito un errore statico.  
  
 Il **max ()** funzione restituisce un valore nella sequenza che è maggiore di qualsiasi altro valore della sequenza di input. Per i valori xs:string, vengono utilizzate le regole di confronto predefinite dei punti di codice Unicode. Se non è possibile eseguire il cast di un valore xdt: untypedAtomic a xs: Double, il valore viene ignorato nella sequenza di input, *$arg*. Se l'input è una sequenza vuota calcolata in modo dinamico, viene restituita la sequenza vuota.  
  
## <a name="examples"></a>Esempi  
 In questo argomento vengono forniti esempi di XQuery sulle istanze XML archiviate in diverse **xml** colonne di tipo di [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database.  
  
### <a name="a-using-the-max-xquery-function-to-find-work-center-locations-in-the-manufacturing-process-that-have-the-most-labor-hours"></a>A. Utilizzo della funzione XQuery max() per trovare i centri di lavorazione del processo di produzione che hanno il maggior numero di ore di manodopera  
 La query fornita [funzione min (XQuery)](../xquery/aggregate-functions-min.md) può essere riscritto per utilizzare il **max ()** (funzione).  
  
## <a name="implementation-limitations"></a>Limitazioni di implementazione  
 Limitazioni:  
  
-   Il **max (**) funzione esegue il mapping di tutti i valori interi a xs: decimal.  
  
-   Il **max ()** funzione con valori di tipo xs: Duration non è supportata.  
  
-   Non sono supportate le sequenze con combinazioni di tipi che non rispettano i limiti del tipo di base.  
  
-   Non è supportata l'opzione sintattica che fornisce le regole di confronto.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni XQuery per il tipo di dati XML](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
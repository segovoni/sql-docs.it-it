---
title: Funzione Count (Generatore report e SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 7b50b101-daf8-4fb0-ae04-57384755779f
caps.latest.revision: 7
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 3fc2b74413f2ecb7f0a1f72684494f85ecf82ca9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37152172"
---
# <a name="count-function-report-builder-and-ssrs"></a>Funzione Count (Generatore report e SSRS)
  Restituisce il conteggio dei valori non Null specificati dall'espressione, valutato nel contesto dell'ambito specificato.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Count(expression, scope, recursive)  
```  
  
#### <a name="parameters"></a>Parametri  
 *expression*  
 (`Variant` oppure `Binary`) espressione su cui eseguire l'aggregazione, ad esempio, `=Fields!FieldName.Value`.  
  
 *ambito*  
 (`String`) Nome di un set di dati, gruppo o area dati che contiene il report elementi a cui applicare la funzione di aggregazione. Se si omette *scope* , viene usato l'ambito corrente.  
  
 *ricorsivi*  
 (**Enumerated Type**) Facoltativo. `Simple` (impostazione predefinita) o `RdlRecursive`. Specifica se eseguire l'aggregazione in modo ricorsivo.  
  
## <a name="return-type"></a>Tipo restituito  
 Restituisce un `Integer`.  
  
## <a name="remarks"></a>Note  
 Il valore di *scope* deve essere una costante di tipo stringa e non può essere un'espressione. Per aggregazioni o aggregazioni esterne che non specificano altre aggregazioni, *scope* deve fare riferimento all'ambito corrente o a un ambito contenitore. Per le aggregazioni di aggregazioni, le aggregazioni nidificate possono specificare un ambito figlio.  
  
 *Expression* può contenere chiamate alle funzioni di aggregazione nidificate con le eccezioni e le condizioni seguenti:  
  
-   *Scope* per le aggregazioni nidificate deve corrispondere o essere contenuto nell'ambito dell'aggregazione esterna. Per tutti gli ambiti distinti nell'espressione, un ambito deve essere in una relazione figlio con tutti gli altri ambiti.  
  
-   *Scope* per le aggregazioni nidificate non può essere il nome di un set di dati.  
  
-   *Espressione* non deve contenere `First`, `Last`, `Previous`, o `RunningValue` funzioni.  
  
-   *Expression* non deve contenere aggregazioni nidificate che specificano *recursive*.  
  
 Per altre informazioni, vedere [Riferimento a funzioni di aggregazione &#40;Generatore report e SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) e [Ambito di espressioni per totali, aggregazioni e raccolte predefinite &#40;Generatore report e SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
 Per altre informazioni sulle aggregazioni ricorsive, vedere [Creazione di gruppi di gerarchie ricorsive &#40;Generatore report e SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).  
  
 Esempio  
  
## <a name="description"></a>Description  
 Nell'esempio di codice seguente è illustrata un'espressione che calcola il numero di valori non Null di `Size` per l'ambito predefinito e per un ambito di gruppo padre. L'espressione viene aggiunta in una riga di una cella che appartiene al gruppo figlio `GroupbySubcategory`. Il gruppo padre è `GroupbyCategory`. L'espressione visualizza i risultati per `GroupbySubcategory` (ambito predefinito) e quindi per `GroupbyCategory` (ambito del gruppo padre).  
  
> [!NOTE]  
>  Le espressioni non devono contenere ritorni a capo e interruzioni di riga, che sono inclusi nell'esempio per supportare i renderer della documentazione. Se si copia l'esempio seguente, rimuovere i ritorni a capo da ogni riga.  
  
## <a name="code"></a>codice  
  
```  
="Count (Subcategory): " & Count(Fields!Size.Value) &   
"Count (Category): " & Count(Fields!Size.Value,"GroupbyCategory")  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Uso delle espressioni nei report di &#40;Report e SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Esempi di espressioni &#40;Generatore report e SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [Tipi di dati nelle espressioni &#40;Generatore report e SSRS&#41;](expressions-report-builder-and-ssrs.md)   
 [Ambito di espressioni per totali, aggregazioni e raccolte predefinite &#40;Report e SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  

---
title: DrilldownMember (MDX) | Documenti Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7991ec4b9f1e4968060774825c08a7cb82fb49b7
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740490"
---
# <a name="drilldownmember-mdx"></a>DrilldownMember (MDX)


  Esegue il drill-down dei membri di un set specificato presenti in un secondo set specificato.  
  
 La funzione esegue in alternativa il drill-down su un set di tuple utilizzando la prima gerarchia di tuple o la gerarchia specificata facoltativamente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DrillDownMember(<Set_Expression1>, <Set_Expression2> [,[<Target_Hierarchy>]] [,[RECURSIVE][,INCLUDE_CALC_MEMBERS]])  
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression1*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Set_Expression2*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Target_Hierarchy*  
 Espressione MDX (Multidimensional Expression) valida che restituisce una gerarchia.  
  
 *Ricorsivo*  
 Una parola chiave che indica il confronto ricorsivo tra set.  
  
 *Include_Calc_Members*  
 Una parola chiave per consentire l'inclusione dei membri calcolati nei risultati del drill-down.  
  
## <a name="remarks"></a>Remarks  
 Questa funzione restituisce un set di membri figlio ordinati in base alla gerarchia e comprende i membri specificati nel primo set che sono presenti anche nel secondo set. Il drill-down non verrà eseguito sui membri padre se il primo set contiene il membro padre e uno o più figli. Il primo set può avere qualsiasi dimensionalità, mentre il secondo deve contenere un set unidimensionale. L'ordine originale dei membri nel primo set viene mantenuto, con la sola differenza che nel set di risultati della funzione tutti i membri figlio vengono indicati immediatamente sotto il membro padre corrispondente. La funzione ottiene il set di risultati recuperando il membro figlio di ogni membro del primo set presente anche nel secondo set. Se **RICORSIVA** è specificato, la funzione continua in modo ricorsivo i membri del set di risultati con il secondo set, recuperare gli elementi figlio per ogni membro nel risultato set che di confronto presente anche nel secondo set fino a quando non più membri del set di risultati sono reperibile nel secondo set.  
  
 Query sulla proprietà XMLA **MdpropMdxDrillFunctions** consente di verificare il livello di supporto che il server garantisce per le funzioni di drill; vedere [proprietà XMLA supportate &#40;XMLA&#41; ](../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md)per informazioni dettagliate.  
  
 Il primo set può contenere tuple anziché membri. La funzione per il drill-down di tuple è un'estensione di OLE DB e restituisce un set di tuple anziché di membri.  
  
> [!IMPORTANT]  
>  Il drill-down di un membro non verrà eseguito se tale membro è immediatamente seguito da uno dei relativi figli. L'ordine dei membri nel set è rilevante per * drill-down e drill-up\* famiglie di funzioni.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene eseguito il drill-down nel membro Australia del primo set, presente anche nel secondo set.  
  
```  
SELECT DrilldownMember   
   ( [Geography].[Geography].Children,  
      {[Geography].[Geography].[Country].[Australia],  
        [Geography].[Geography].[State-Province].[New South Wales]}  
   )  
   ON 0  
   FROM [Adventure Works]  
```  
  
 Nell'esempio seguente viene eseguito il drill-down nel membro Australia del primo set, presente anche nel secondo set. Poiché tuttavia è specificato l'argomento RECURSIVE, la funzione confronta ricorsivamente i membri del set di risultati, ovvero i membri del livello State-Province, con i membri del secondo set e recupera il membro figlio di ogni membro del set di risultati (i membri del livello City) presente anche nel secondo set fino a quando nel secondo set non viene individuato alcun membro del set di risultati.  
  
```  
SELECT DrilldownMember   
   ( [Geography].[Geography].Children,  
      {[Geography].[Geography].[Country].[Australia],  
        [Geography].[Geography].[State-Province].[New South Wales]}  
   ,RECURSIVE)  
   ON 0  
   FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

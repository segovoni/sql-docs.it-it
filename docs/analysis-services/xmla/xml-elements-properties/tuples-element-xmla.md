---
title: Elemento tuples (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c0578c541c39bdaceede6bff8afdea3d642abcef
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38062545"
---
# <a name="tuples-element-xmla"></a>Elemento Tuples (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contiene un set di [tupla](../../../analysis-services/xmla/xml-elements-properties/tuple-element-xmla.md) degli oggetti per un' [asse](../../../analysis-services/xmla/xml-elements-properties/axis-element-xmla.md) elemento che utilizza il [MDDataSet](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md) tipo di dati restituito dal [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) (metodo).  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Axis>  
   ...  
   <Tuples>  
      <Tuple>...</Tuple>  
   </Tuples>  
   ...  
</Axis>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche di elementi  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Elementi-relazioni  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Axis](../../../analysis-services/xmla/xml-elements-properties/axis-element-xmla.md)|  
|Elementi figlio|[Tupla](../../../analysis-services/xmla/xml-elements-properties/tuple-element-xmla.md)|  
  
## <a name="remarks"></a>Note  
 Quando un'applicazione client imposta la proprietà **AxisFormat** su *TupleFormat*, un’asse viene rappresentata come un set di tuple. Ogni elemento **Axis** contiene un elemento **Tuples** che rappresenta il set di tuple su quell’asse. Ogni tupla viene rappresentata usando un elemento **Tuple** che contiene elementi [Member](../../../analysis-services/xmla/xml-elements-properties/member-element-xmla.md) di ogni gerarchia sull'asse.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrata la struttura del **Tuple** elemento quando un client specifica *TupleFormat* oppure *CustomFormat* per il **AxisFormat**  XML per la proprietà Analysis (XMLA), presupponendo i membri seguenti per l'asse:  
  
|||||  
|-|-|-|-|  
|Gerarchia **Time**|1999|1999|2000|  
|Gerarchia **Category**|Valore effettivo|Budget|Budget|  
  
```  
<Axes>  
   <Axis name="Axis0">  
      <Tuples>  
         <Tuple>  
            <Member Hierarchy="Time">  
               <UName>[Time].[1999]</UName>  
               ...  
            </Member>  
            <Member Hierarchy="Category">  
               <UName>[Scenario].[Actual]</UName>  
               ...  
            </Member>  
         </Tuple>  
         <Tuple>  
            <Member Hierarchy="Time">  
               <UName>[Time].[1999]</UName>  
               ...  
            </Member>  
            <Member Hierarchy="Category">  
               <UName>[Scenario].[Budget]</UName>  
               ...  
            </Member>  
         </Tuple>  
         <Tuple>  
            <Member Hierarchy="Time">  
               <UName>[Time].[2000]</UName>  
               ...  
            </Member>  
            <Member Hierarchy="Category">  
               <UName>[Scenario].[Budget]</UName>  
               ...  
            </Member>  
         </Tuple>  
      </Tuples>  
   </Axis>  
   ...  
</Axes>  
```  
  
## <a name="see-also"></a>Vedere anche
 [Proprietà &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

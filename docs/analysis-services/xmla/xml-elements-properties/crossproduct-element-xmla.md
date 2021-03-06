---
title: Elemento CrossProduct (XMLA) | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2b2c5b195e2bc95d95a555557accd481aa9836f7
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34574763"
---
# <a name="crossproduct-element-xmla"></a>Elemento CrossProduct (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contiene un prodotto incrociato tra set ordinati di membri di ogni gerarchia per un [asse](../../../analysis-services/xmla/xml-elements-properties/axis-element-xmla.md) elemento che utilizza il [MDDataSet](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md) tipo di dati restituito dal [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) metodo.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Axis>  
   ...  
   <CrossProduct Size="integer">  
      <Members>...</Members>  
   </CrossProduct>  
   ...  
</Axis>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Axis](../../../analysis-services/xmla/xml-elements-properties/axis-element-xmla.md)|  
|Elementi figlio|[Membri](../../../analysis-services/xmla/xml-elements-properties/members-element-xmla.md)|  
  
## <a name="attributes"></a>Attributi  
  
|attribute|Description|  
|---------------|-----------------|  
|Dimensione|Richiesto **intero** attributo. Indica il numero di tuple contenuto nel prodotto-incrociato rappresentato dal **CrossProduct** elemento.|  
  
## <a name="remarks"></a>Remarks  
 Quando un'applicazione client imposta il **AxisFormat** proprietà *ClusterFormat*, i membri su ogni asse sono divisi in cluster in cui ogni cluster rappresenta un prodotto incrociato tra set ordinati di membri di ogni gerarchia. Ogni cluster è rappresentato da un **CrossProduct** elemento. Ogni **CrossProduct** elemento contiene un **membri** elemento per ogni gerarchia sull'asse. Oggetto **CrossProduct** elemento può contenere membri di una singola gerarchia.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrata la struttura del **CrossProduct** elemento quando un client specifica *ClusterFormat* per il **AxisFormat** proprietà XMLA, dato il membri seguenti per l'asse:  
  
||||||  
|-|-|-|-|-|  
|Gerarchia **Time**|1999|1999|2000|2001|  
|Gerarchia **Category**|Valore effettivo|Budget|Budget|Budget|  
|Clusters|Cluster 1|Cluster 1|Cluster 1|Cluster 2|  
  
```  
<Axes>  
   <Axis name="Axis0">  
      <CrossProduct Size="4">  
         <Members Hierarchy="Time">  
            <Member>  
               <UName>[Time].[1999]</UName>  
               ...  
            </Member>  
            <Member>  
               <UName>[Time].[2000]</UName>  
               ...  
            </Member>  
         </Members>  
         <Members Hierarchy="Category">  
            <Member>  
               <UName>[Scenario].[Actual]</UName>  
               ...  
            </Member>  
            <Member>  
               <UName>[Scenario].[Budget]</UName>  
               ...  
            </Member>  
         </Members>  
      </CrossProduct>  
      <CrossProduct Size="1">  
         <Members Hierarchy="Time">  
            <Member>  
               <UName>[Time].[2001]</UName>  
               ...  
            </Member>  
         </Members>  
         <Members Hierarchy="Category">  
            <Member>  
               <UName>[Scenario].[Budget]</UName>  
               ...  
            </Member>  
         </Members>  
      </CrossProduct>  
   </Axis>  
   ...  
</Axes>  
```  
  
## <a name="see-also"></a>Vedere anche
 [Proprietà &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

---
title: Il livello di elemento (CSDLBI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: fdf75c47-77dc-4bdb-9931-8eca198fdb88
caps.latest.revision: 10
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3fd89aaa69e8dc2b29b80ca82f89d1453dc44017
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37211481"
---
# <a name="level-element-csdlbi"></a>Elemento Level (CSDLBI)
  L'elemento Level è un tipo complesso che definisce un solo livello in una gerarchia.  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Nella tabella seguente vengono elencati gli attributi e gli elementi che definiscono l'elemento Level.  
  
|nome|Obbligatorio|Description|  
|----------|-----------------|-----------------|  
|Origine|Sì|Contenitore per il riferimento alla proprietà.|  
|PropertyRef|Sì|Riferimento a una proprietà dell'istanza. Altri attributi del livello, ad esempio didascalie, nome e nome del riferimento, possono essere prese dalla proprietà dell'istanza a cui si fa riferimento. In tal caso, non è necessario specificarli nell'elemento Level.|  
  
## <a name="remarks"></a>Note  
 Per altre informazioni sulle gerarchie nei modelli tabulari, vedere [Elemento Hierarchy &#40;CSDLBI&#41;](hierarchy-element-csdlbi.md).  
  
## <a name="example"></a>Esempio  
 **Tabella**  
  
 Nell'esempio seguente, in CSDLBI versione 1.1, viene mostrata la definizione di più livelli in una gerarchia del modello tabulare di esempio di AdventureWorks.  
  
```  
  
<bi:Hierarchy Name="Category">  
   <bi:Level Name="CategoryName">  
     <bi:Source>  
       <bi:PropertyRef Name="CategoryName" />  
     </bi:Source>  
   </bi:Level>  
   <bi:Level Name="ProductName">  
     <bi:Source>  
       <bi:PropertyRef Name="ProductName" />  
     </bi:Source>  
   </bi:Level>  
</bi:Hierarchy>  
```  
  
## <a name="example"></a>Esempio  
 **Multidimensionale**  
  
 Nell'esempio seguente, in CSDLBI versione 1.1, è riportato una gerarchia con più livelli del cubo Operations di Contoso.  
  
```  
<bi:Hierarchy   
   Name="Product_Hierarchy"   
   Caption="Product Hierarchy"   
   ReferenceName="Product Hierarchy">  
     <bi:Documentation>  
        <bi:Summary>DESCRIPTION_ProductModelCateg_Hierarchies</bi:Summary>  
     </bi:Documentation>  
  
     <bi:Level Name="ProductLine">  
        <bi:Source>  
        <bi:PropertyRef Name="ProductLine" />  
        </bi:Source>  
     </bi:Level>  
  
     <bi:Level Name="ModelName">  
        <bi:Source>  
        <bi:PropertyRef Name="ModelName" />  
        </bi:Source>  
     </bi:Level>  
</bi:Hierarchy>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Comprendere il modello a oggetti tabulare](../representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)   
 [Informazioni sulle funzioni per gerarchie padre-figlio in DAX](https://msdn.microsoft.com/library/gg492192(v=sql.120).aspx)   
 [Configurare il &#40;tutti&#41; livello per le gerarchie di attributi](../../multidimensional-models/database-dimensions-configure-the-all-level-for-attribute-hierarchies.md)  
  
  

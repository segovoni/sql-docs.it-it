---
title: Elemento NavigationProperty (CSDLBI) | Documenti Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9db2facd93380fa3d0e011104bb95950e43340fb
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34038735"
---
# <a name="navigationproperty-element-csdlbi"></a>Elemento NavigationProperty (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  L'elemento NavigationProperty è un tipo complesso che estende il tipo Member di CSDL per supportare la navigazione nei modelli di dati di Business Intelligence.  
  
> [!WARNING]  
>  Questo elemento è destinato alla creazione di report e non può essere modificato.  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Nella tabella seguente vengono elencati gli attributi e gli elementi che definiscono l'elemento NavigationProperty.  
  
|Nome|Obbligatorio|Description|  
|----------|-----------------|-----------------|  
|CollectionCaption|No|Nome plurale per fare riferimento a un set di istanze della proprietà di navigazione.<br /><br /> Se questo attributo viene omesso, viene utilizzato l'attributo Caption dell'elemento Member di base.|  
  
## <a name="example"></a>Esempio  
 **Tabulare**  
  
 L'esempio seguente mostra una proprietà di navigazione in CSDLBI versione 1.1 che descrive il collegamento tra la tabella Product SubCategory e la tabella Product in un modello tabulare.  
  
```  
  
<NavigationProperty   
    Name="Product_Sub_Category_ProductSubcategoryKey"      
    Relationship="Sandbox.Product_Product_Sub_Category_Product_Sub_Category_ProductSubcategoryKey"  
     FromRole="Product_ProductSubcategoryKey"   
    ToRole="Product_Sub_Category_ProductSubcategoryKey">  
<bi:NavigationProperty   
     ReferenceName="Product Sub-Category_ProductSubcategoryKey" />  
</NavigationProperty>  
```  
  
## <a name="example"></a>Esempio  
 **Multidimensionale**  
  
 Nell'esempio seguente, in CSDLBI versione 1.1, viene illustrata una proprietà di navigazione che descrive la relazione tra due tabelle nel cubo Operations di Contoso. La relazione connette la tabella Bike Category con la tabella Product Subcategory.  
  
```  
  
<NavigationProperty   
     Name="BikeSubcategory_ProductSubcategoryKey"   
     Relationship="Sandbox.Bike_BikeSubcategory_BikeSubcategory_ProductSubcategoryKey"   
     FromRole="Bike_ProductSubcategoryKey"   
     ToRole="BikeSubcategory_ProductSubcategoryKey">  
   <bi:NavigationProperty />  
</NavigationProperty>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sul modello a oggetti tabulare alla compatibilità 1050 1103 tramite i livelli](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
  

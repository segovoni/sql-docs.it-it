---
title: Filtri di uso comune (Generatore report e SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- multivalued parameters [Reporting Services]
- single-valued parameters [Reporting Services]
- parameters [Reporting Services], multivalued
- valid values [Reporting Services]
ms.assetid: cb70d0cd-707b-4de5-b39f-e4eb57d316aa
caps.latest.revision: 36
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: e0c10880dd8557ed7d1a0902b33397e37bd6483c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37185756"
---
# <a name="commonly-used-filters-report-builder-and-ssrs"></a>Filtri di uso comune (Generatore report e SSRS)
  Per creare un filtro è necessario specificare una o più equazioni di filtro. Un'equazione di filtro include un'espressione, un tipo di dati, un operatore e un valore. In questo argomento vengono forniti esempi di filtri di uso comune.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="filter-examples"></a>Esempi di filtri  
 Nella tabella seguente sono riportati esempi di equazioni di filtro che utilizzano tipi di dati e operatori differenti. L'ambito per il confronto è determinato dall'elemento del report per il quale è definito il filtro. Per un filtro definito in un set di dati, ad esempio, **TOP% 10** si riferisce al primo 10 percento di valori nel set di dati. Per un filtro definito in un gruppo, **TOP% 10** rappresenta il primo 10 percento di valori nel gruppo.  
  
|Espressione semplice|Tipo di dati|Operatore|valore|Description|  
|-----------------------|---------------|--------------|-----------|-----------------|  
|`[SUM(Quantity)]`|`Integer`|`>`|`7`|Sono inclusi valori di dati maggiori di 7.|  
|`[SUM(Quantity)]`|`Integer`|`TOP N`|`10`|Include i primi 10 valori di dati.|  
|`[SUM(Quantity)]`|`Integer`|`TOP %`|`20`|Include il primo 20% di valori di dati.|  
|`[Sales]`|`Text`|`>`|`=CDec(100)`|Include tutti i valori di tipo System.Decimal (tipi di dati "money" in SQL) maggiori di 100 dollari.|  
|`[OrderDate]`|`DateTime`|`>`|`2088-01-01`|Include tutte le date dal 1 gennaio 2008 alla data corrente.|  
|`[OrderDate]`|`DateTime`|`BETWEEN`|`2008-01-01`<br /><br /> `2008-02-01`|Include le date dal 1 gennaio 2008 al 1 febbraio 2008 compreso.|  
|`[Territory]`|`Text`|`LIKE`|`*east`|Tutti i nomi di territorio che terminano in "east".|  
|`[Territory]`|`Text`|`LIKE`|`%o%th*`|Tutti i nomi di territorio che iniziano con North e South.|  
|`=LEFT(Fields!Subcat.Value,1)`|`Text`|`IN`|`B, C, T`|Tutti i valori di sottocategoria che iniziano con la lettera B, C o T.|  
  
## <a name="examples-with-report-parameters"></a>Esempi con parametri report  
 Nella tabella seguente sono forniti esempi di espressioni di filtro contenenti un riferimento a un parametro a valore singolo o multivalore.  
  
|Tipo di parametro|Espressione (filtro)|Operatore|valore|Tipo di dati|  
|--------------------|---------------------------|--------------|-----------|---------------|  
|Valore singolo|`[EmployeeID]`|=|`[@EmployeeID]`|Valore intero|  
|Multivalore|`[EmployeeID]`|IN|`[@EmployeeID]`|Valore intero|  
  
## <a name="see-also"></a>Vedere anche  
 [Parametri report &#40;Generatore report e Progettazione report&#41;](report-parameters-report-builder-and-report-designer.md)   
 [Aggiungere filtri per set di dati, aree dati e gruppi &#40;Generatore report e SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md)   
 [Uso delle espressioni nei report di &#40;Report e SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Esempi di espressioni &#40;Generatore report e SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [I tipi di dati nelle espressioni di &#40;Report e SSRS&#41;](expressions-report-builder-and-ssrs.md)  
  
  

---
title: Preparare i dati per la visualizzazione in un'area dati Tablix (Generatore report e SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: report-design
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: fbb00dc6-7887-480c-b771-cab6fecb8dcc
caps.latest.revision: 5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e6b8f3672b21a43c87eb1dec7008593a93f3b850
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33023968"
---
# <a name="preparing-data-for-display-in-a-tablix-data-region-report-builder-and-ssrs"></a>Preparare i dati per la visualizzazione in un'area dati Tablix (Generatore report e SSRS)
  In un'area dati Tablix vengono visualizzati i dati di un set di dati. È possibile visualizzare tutti i dati recuperati per il set di dati o creare filtri in modo da visualizzare solo un subset dei dati. È inoltre possibile aggiungere espressioni condizionali per inserire valori Null o modificare la query affinché un set di dati includa colonne che definiscono il tipo di ordinamento per una colonna esistente.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="working-with-nulls-and-blanks-in-field-values"></a>Utilizzo di valori Null e spazi vuoti nei valori dei campi  
 Nei dati relativi alla raccolta di campi di un set di dati sono compresi tutti i valori recuperati in fase di esecuzione dall'origine dati, inclusi i valori Null e gli spazi vuoti. In genere, i valori Null e gli spazi vuoti non sono distinguibili. Nella maggior parte dei casi questo è il comportamento desiderato. Funzioni di aggregazione numeriche come [Sum](../../reporting-services/report-design/report-builder-functions-sum-function.md) e [Avg](../../reporting-services/report-design/report-builder-functions-avg-function.md) ignorano ad esempio i valori Null. Per altre informazioni, vedere [Riferimento a funzioni di aggregazione &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/report-builder-functions-aggregate-functions-reference.md).  
  
 Se si desidera gestire in modo diverso i valori Null, è possibile utilizzare espressioni condizionali o codice personalizzato per sostituire un valore personalizzato al valore Null. Nell'espressione seguente ad esempio il testo `Null` viene sostituito ogni volta che si rileva un valore Null nel campo `[Size]`.  
  
```  
=IIF(Fields!Size.Value IS NOTHING,"Null",Fields!Size.Value)  
```  
  
 Per altre informazioni sull'eliminazione di valori Null nei dati prima del recupero dei dati da un'origine dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tramite query [!INCLUDE[tsql](../../includes/tsql-md.md)] , vedere le sezioni relative a valori Null e valori Null e join nella documentazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] inclusa nella [documentazione online di SQL Server](http://go.microsoft.com/fwlink/?linkid=120955).  
  
## <a name="handling-null-field-names"></a>Gestione dei nomi dei campi con valori Null  
 Il testing dei valori Null in un'espressione risulta appropriato fino a quando il campo stesso è presente nel set di risultati della query. Partendo dal codice personalizzato è possibile eseguire il testing per verificare la presenza del campo tra i campi della raccolta restituiti in fase di esecuzione dall'origine dati. Per altre informazioni, vedere [Riferimenti alla raccolta di campi del set di dati &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/built-in-collections-dataset-fields-collection-references-report-builder.md).  
  
## <a name="adding-a-sort-order-column"></a>Aggiunta di una colonna per il tipo di ordinamento  
 Per impostazione predefinita, è possibile disporre in ordine alfabetico i valori di un campo del set di dati. Per impostare un ordine diverso, è possibile aggiungere una nuova colonna al set di dati che definisce il tipo di ordinamento desiderato in un'area dati. Per eseguire l'ordinamento in base al campo `[Color]` , disponendo per primi gli elementi bianchi e neri, è possibile aggiungere una colonna `[ColorSortOrder]`, come mostrato nella query seguente:  
  
```  
SELECT ProductID, p.Name, Color,  
   CASE  
      WHEN p.Color = 'White' THEN 1  
      WHEN p.Color = 'Black' THEN 2  
      WHEN p.Color = 'Blue' THEN 3  
      WHEN p.Color = 'Yellow' THEN 4  
      ELSE 5  
   END As ColorSortOrder  
FROM Production.Product p  
```  
  
 Per configurare un'area dati della tabella in base a questo tipo di ordinamento, impostare l'espressione di ordinamento nel gruppo dettagli su `=Fields!ColorSortOrder.Value`. Per altre informazioni, vedere [Ordinare i dati in un'area dati &#40;Generatore report e SSRS& #41;](../../reporting-services/report-design/sort-data-in-a-data-region-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Raccolta di campi del set di dati &#40;Generatore report e SSRS&#41;](../../reporting-services/report-data/dataset-fields-collection-report-builder-and-ssrs.md)   
 [Espressioni &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)   
 [Filtrare, raggruppare e ordinare i dati &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)  
  
  

---
title: Ordinare i dati in una tabella | Documenti Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ef0a5de0958fbea806063c17dd5f9f1912449be4
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34039634"
---
# <a name="sort-data-in-a-table"></a>Ordinare i dati di una tabella 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  È possibile ordinare i dati per testo (da A a Z o da Z ad A) e numeri (dal più piccolo al più grande o dal più grande al più piccolo) in una o più colonne.  
  
### <a name="to-sort-the-data-in-a-table-based-on-a-text-column"></a>Per ordinare i dati in una tabella basata su una colonna di testo  
  
1.  In Progettazione modelli selezionare una colonna di dati alfanumerici, un intervallo di celle in una colonna oppure assicurarsi che la cella attiva si trovi in una colonna di una tabella contenente dati alfanumerici, quindi fare clic sulla freccia nell'intestazione della colonna in base alla quale filtrare i dati.  
  
2.  Nel menu Filtro automatico effettuare uno dei passaggi seguenti:  
  
    -   Per ordinare in ordine alfanumerico crescente, fare clic su **Ordina da A a Z**.  
  
    -   Per ordinare in ordine alfanumerico decrescente, fare clic su **Ordina da Z a A**.  
  
    > [!NOTE]  
    >  In alcuni casi, dati importati da un'altra applicazione potrebbero presentare spazi iniziali inseriti prima dei dati stessi. È necessario rimuovere gli spazi iniziali per ordinare correttamente i dati.  
  
### <a name="to-sort-the-data-in-a-table-based-on-a-numeric-column"></a>Per ordinare i dati in una tabella basata su una colonna numerica  
  
1.  In Progettazione modelli selezionare una colonna di dati alfanumerici, un intervallo di celle in una colonna oppure assicurarsi che la cella attiva si trovi in una colonna di una tabella contenente dati alfanumerici, quindi fare clic sulla freccia nell'intestazione della colonna in base alla quale filtrare i dati.  
  
2.  Nel menu Filtro automatico effettuare uno dei passaggi seguenti:  
  
    -   Per l'ordinamento ascendente fare clic su **Ordina dal più piccolo al più grande**.  
  
    -   Per l'ordinamento discendente fare clic su **Ordina dal più grande al più piccolo**.  
  
    > [!NOTE]  
    >  Se i risultati non sono quelli previsti, la colonna potrebbe contenere numeri archiviati come testo e non come numeri. Ad esempio numeri negativi importati da alcuni sistemi di contabilità o un numero immesso con carattere apostrofo (') iniziale, vengono archiviati come testo.  
  
## <a name="see-also"></a>Vedere anche  
 [Filtrare e ordinare dati](http://msdn.microsoft.com/library/55ebd7a6-2458-4398-911f-fcfeb2413f1b)   
 [Prospettive](../../analysis-services/tabular-models/perspectives-ssas-tabular.md)   
 [Roles](../../analysis-services/tabular-models/roles-ssas-tabular.md)  
  
  

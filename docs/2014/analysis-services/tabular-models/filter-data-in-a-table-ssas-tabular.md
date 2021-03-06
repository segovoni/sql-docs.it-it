---
title: Filtrare i dati in una tabella (SSAS tabulare) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.customfilterdb.f1
- sql12.asvs.bidtoolset.autofiltermenu.f1
- sql12.asvs.bidtoolset.notallitemsshowing.f1
ms.assetid: 3223059d-f525-4835-bf88-ebc195d9dbdc
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5232c34c8fdb8a76d24a623103d30863e7e9c21c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37306411"
---
# <a name="filter-data-in-a-table-ssas-tabular"></a>Filtrare i dati di una tabella (SSAS tabulare)
  È possibile applicare filtri quando si importano dati per controllare le righe caricate in una tabella. Dopo aver importato i dati, non è possibile eliminare righe singole. Tuttavia, è possibile applicare filtri personalizzati per controllare la modalità in cui visualizzare tali righe. Le righe che non soddisfano i criteri di filtro sono nascoste. È possibile filtrare i dati in base a una o più colonne. I filtri sono additivi, pertanto ciascun filtro aggiuntivo è basato sul filtro corrente e consente di ridurre ulteriormente il subset di dati.  
  
> [!NOTE]  
>  La finestra di anteprima del filtro consente di limitare il numero di valori diversi visualizzati. Se il limite viene superato, viene visualizzato un messaggio.  
  
### <a name="to-filter-data-based-on-column-values"></a>Per filtrare dati in base ai valori della colonna  
  
1.  In Progettazione modelli selezionare una tabella, quindi fare clic sulla freccia nell'intestazione della colonna in base alla quale filtrare i dati.  
  
2.  Nel menu Filtro automatico effettuare uno dei passaggi seguenti:  
  
    -   Nell'elenco di valori delle colonne selezionare o deselezionare uno o più valori da utilizzare come filtri, quindi fare clic su **OK**.  
  
         Se il numero di valori è estremamente elevato, singoli elementi potrebbero non essere visualizzati nell'elenco. Verrà invece visualizzato il messaggio, "Troppi elementi da visualizzare".  
  
    -   Fare clic su **Filtri per numeri** o su **Filtri per testo** (a seconda del tipo di colonna) e quindi fare clic su uno dei comandi di operatore di confronto (ad esempio **Uguale a**) o su **Filtro personalizzato**. Nella finestra di dialogo **Filtro personalizzato** creare il filtro, quindi fare clic su **OK**.  
  
### <a name="to-clear-a-filter-for-a-column"></a>Per cancellare un filtro per una colonna  
  
1.  Fare clic sulla freccia nell'intestazione della colonna per la quale si desidera cancellare un filtro.  
  
2.  Fare clic su **Cancella filtro da \<nome colonna >**.  
  
### <a name="to-clear-all-filters-for-a-table"></a>Per cancellare tutti i filtri per una tabella  
  
1.  In Progettazione modelli selezionare la tabella per la quale si desidera cancellare i filtri.  
  
2.  Fare clic sul menu **Colonna** , quindi scegliere **Cancella tutti i filtri**.  
  
## <a name="see-also"></a>Vedere anche  
 [Filtrare e ordinare i dati &#40;tabulare di SSAS&#41;](../filter-and-sort-data-ssas-tabular.md)   
 [Le prospettive &#40;tabulare di SSAS&#41;](perspectives-ssas-tabular.md)   
 [I ruoli &#40;tabulare di SSAS&#41;](roles-ssas-tabular.md)  
  
  

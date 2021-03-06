---
title: Filtrare il cubo di origine per una struttura di Data Mining | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- slice cubes [Analysis Services]
- mining structures [Analysis Services], filtering source cube
- cubes [Analysis Services], slicing
- filtering data [Analysis Services]
ms.assetid: 05dce7e1-2fe5-4500-bacf-c1a8a76e1424
caps.latest.revision: 15
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 10ad6c295f61de1f50688bb8f52b12268756860a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37226651"
---
# <a name="filter-the-source-cube-for-a-mining-structure"></a>Filtrare il cubo di origine per una struttura di data mining
  Quando si crea una struttura di data mining che si basa sui dati in un modello multidimensionale (cubo OLAP), è possibile *slice* del cubo che dipende dalla struttura di data mining. Il sezionamento consente di creare subset di dati, come un filtro da applicare ai dati utilizzati per il training del modello di data mining.  
  
### <a name="to-slice-a-cube"></a>Per sezionare un cubo  
  
1.  Progettazione modelli di Data Mining in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], selezionare il **struttura di Data Mining** scheda o il **modelli di Data Mining** scheda.  
  
2.  Nel **modello di Data Mining** dal menu **Definisci sezione del cubo struttura di Data Mining**.  
  
     Il **seziona cubo** verrà visualizzata la finestra di dialogo.  
  
3.  Nel **dimensione** della colonna della **seziona cubo** finestra di dialogo, selezionare la dimensione che si desidera filtrare.  
  
4.  Selezionare un livello di una gerarchia, tramite l'elenco nella **gerarchia** colonna.  
  
5.  Selezionare un operatore dall'elenco nella **operatore** colonna, da utilizzare nella compilazione della condizione di filtro.  
  
6.  Fare clic sulla casella di **filtro** colonna.  
  
     Verrà visualizzata una finestra di dialogo contenente tutti i membri al livello specificato della gerarchia.  
  
7.  Selezionare uno o più membri a cui si desidera applicare il filtro.  
  
8.  Fare clic su **OK** nella finestra di dialogo di membro.  
  
9. Fare clic su **OK** nel **seziona cubo** nella finestra di dialogo.  
  
     A questo punto, il cubo di origine è filtrato come definito dalla sezione del cubo.  
  
## <a name="see-also"></a>Vedere anche  
 [Data mining struttura attività e procedure](data-mining/mining-structure-tasks-and-how-tos.md)   
 [Creare una nuova struttura di data mining OLAP](data-mining/create-a-new-olap-mining-structure.md)  
  
  

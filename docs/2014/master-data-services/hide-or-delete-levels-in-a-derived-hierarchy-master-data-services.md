---
title: Nascondere o eliminare i livelli di una gerarchia derivata (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- derived hierarchies, hiding levels
- derived hierarchies, deleting levels
ms.assetid: e00582b9-9415-4b66-b4a7-9f590d83875f
caps.latest.revision: 4
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: da74b0ff57f6bb5488903730351dcacacf92b2f8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37300421"
---
# <a name="hide-or-delete-levels-in-a-derived-hierarchy-master-data-services"></a>Nascondere o eliminare livelli di una gerarchia derivata (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]è possibile nascondere un livello di una gerarchia derivata quando è necessario per il raggruppamento ma non si vuole visualizzarlo. Eliminare un livello quando non si desidera utilizzarlo per il raggruppamento.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per eseguire questa procedura:  
  
-   È necessario disporre di autorizzazione per accedere all'area funzionale **Amministrazione sistema** .  
  
-   È necessario essere un amministratore del modello. Per altre informazioni, vedere [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
### <a name="to-hide-or-delete-levels-in-a-derived-hierarchy"></a>Per nascondere o eliminare i livelli di una gerarchia derivata  
  
1.  In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], fare clic su **Amministrazione sistema**.  
  
2.  Nel **Vista modelli** pagina, dalla barra dei menu scegliere **Gestisci** e fare clic su **gerarchie derivate**.  
  
3.  Nella pagina **Gestione gerarchia derivata** selezionare un modello dall'elenco **Modello** .  
  
4.  Selezionare la riga relativa alla gerarchia derivata da modificare.  
  
5.  Fare clic su **selezionato Modifica gerarchia derivata**.  
  
6.  Nel riquadro **Livelli correnti** :  
  
    -   Per nascondere un livello, fare clic su un livello diverso quello superiore o inferiore. Nell'elenco **Visibile** selezionare **No**. Quindi fare clic su **Salva elemento gerarchia selezionato**.  
  
    -   Per eliminare il livello superiore, fare clic su **Elimina elemento gerarchia selezionato**. Nella finestra di dialogo di conferma fare clic su **OK**. È possibile eliminare solo il livello superiore.  
  
## <a name="see-also"></a>Vedere anche  
 [Spostare membri all'interno di una gerarchia di &#40;Master Data Services&#41;](../../2014/master-data-services/move-members-within-a-hierarchy-master-data-services.md)   
 [Gerarchie derivate &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md)  
  
  

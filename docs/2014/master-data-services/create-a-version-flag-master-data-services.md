---
title: Creare un flag di versione (Master Data Services) | Microsoft Docs
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
- creating version flags [Master Data Services]
- version flags [Master Data Services], creating
- versions [Master Data Services], creating flags
ms.assetid: 3067e1e3-05b7-4f11-9206-c612ef4e7e42
caps.latest.revision: 5
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 8e749d7e0be27ec7ea749073f89f192972a354f2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37287547"
---
# <a name="create-a-version-flag-master-data-services"></a>Creare un flag di versione (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]creare un flag di versione da assegnare a una versione. Il flag può indicare la versione che utenti o sistemi di sottoscrizione devono usare.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per eseguire questa procedura:  
  
-   È necessario avere l'autorizzazione per accedere all'area funzionale **Gestione versioni** .  
  
-   È necessario essere un amministratore del modello. Per altre informazioni, vedere [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
### <a name="to-create-a-version-flag"></a>Per creare un flag di versione  
  
1.  In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], fare clic su **Gestione versioni**.  
  
2.  Nella pagina **Gestisci versioni** scegliere **Gestisci** dalla barra dei menu, quindi fare clic su **Flag**.  
  
3.  Nella pagina **Gestisci flag di versione** nel campo **Modello** selezionare il modello per il quale si vuole creare un flag.  
  
4.  Scegliere **Aggiungi**.  
  
5.  Nella casella **Nome** digitare un nome.  
  
6.  Nella casella **Descrizione** digitare una descrizione.  
  
7.  Nel campo **Solo versioni con commit** selezionare **True** per indicare che il flag può essere assegnato solo alle versioni con stato **Commit completato** . Selezionare **False** per indicare che il flag può essere assegnato alle versioni con qualsiasi stato.  
  
8.  Fare clic su **Salva**.  
  
## <a name="next-steps"></a>Passaggi successivi  
  
-   [Assegnare un Flag a una versione &#40;Master Data Services&#41;](../../2014/master-data-services/assign-a-flag-to-a-version-master-data-services.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Le versioni &#40;Master Data Services&#41;](../../2014/master-data-services/versions-master-data-services.md)   
 [Modificare il nome di un Flag di versione &#40;Master Data Services&#41;](../../2014/master-data-services/change-a-version-flag-name-master-data-services.md)  
  
  

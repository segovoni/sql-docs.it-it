---
title: Creare membri consolidati (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 04/01/2016
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- creating consolidated members [Master Data Services]
- members [Master Data Services], creating consolidated members
- consolidated members [Master Data Services], creating
ms.assetid: 431ab2d2-5517-4372-9980-142b05427c08
caps.latest.revision: 12
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 16b0bedcee527d7f5acf4d43149e745df8052df5
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2018
ms.locfileid: "35400283"
---
# <a name="create-a-consolidated-member-master-data-services"></a>Create a Consolidated Member (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]creare un membro consolidato quando si desidera un nodo padre per una gerarchia esplicita. Per aggiungere i dati in blocco, usare invece le tabelle di staging. Per altre informazioni, vedere [Importare dati dalle tabelle &#40;Master Data Services&#41;](../master-data-services/import-data-from-tables-master-data-services.md).  
  
## <a name="prerequisites"></a>Prerequisites  
 Per eseguire questa procedura:  
  
-   È necessario disporre dell'autorizzazione per accedere all'area funzionale **Esplora** .  
  
-   È necessaria almeno l'autorizzazione **Update** per l'oggetto modello consolidato dell'entità a cui si sta aggiungendo un membro e l'autorizzazione **Create permission** per il tipo consolidato contenuto nell'entità.  
  
### <a name="to-create-a-consolidated-member"></a>Per creare un membro consolidato  
  
1.  Nella home page di [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] selezionare un modello nell'elenco **Modello** .  
  
2.  Selezionare una versione dall'elenco **Versione** .  
  
3.  Fare clic su **Esplora**.  
  
4.  Dalla barra dei menu scegliere **Gerarchie** , quindi fare clic sul nome della gerarchia alla quale si desidera aggiungere un membro consolidato.  
  
5.  Sopra la griglia, selezionare l'opzione **Membri consolidati** o **Tutti i membri consolidati nella gerarchia** .  
  
6.  Nel riquadro a sinistra selezionare un nodo radice o un membro consolidato in cui creare un membro consolidato.  
  
7.  Scegliere **Aggiungi**.  
  
8.  Nel riquadro sulla destra, completare i campi.  
  
9. Facoltativo. Nella casella **Annotazioni** , digitare un commento indicando il perché è stato aggiunto il membro. Tutti gli utenti che dispongono di accesso al membro possono visualizzare l'annotazione.  
  
10. Fare clic su **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Creare una gerarchia esplicita &#40;Master Data Services&#41;](../master-data-services/create-an-explicit-hierarchy-master-data-services.md)   
 [Creare un membro foglia &#40;Master Data Services&#41;](../master-data-services/create-a-leaf-member-master-data-services.md)   
 [Membri &#40;Master Data Services&#41;](../master-data-services/members-master-data-services.md)   
 [Gerarchie esplicite &#40;Master Data Services&#41;](../master-data-services/explicit-hierarchies-master-data-services.md)  
  
  

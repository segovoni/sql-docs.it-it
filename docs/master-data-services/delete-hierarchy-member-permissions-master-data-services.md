---
title: Eliminare le autorizzazioni dei membri della gerarchia (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.component: non-specific
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- deleting member permissions [Master Data Services]
- members [Master Data Services], deleting permissions
- permissions [Master Data Services], deleting member permissions
ms.assetid: 7f22d5e2-70c1-422c-99c2-e995a47d812a
caps.latest.revision: 6
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: b85c88e1db4545274309b9897f1392436f90d689
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="delete-hierarchy-member-permissions-master-data-services"></a>Eliminare le autorizzazioni membri gerarchia (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]eliminare le autorizzazioni dell'oggetto modello per rimuovere qualsiasi assegnazione attribuita.  
  
## <a name="prerequisites"></a>Prerequisites  
 Per eseguire questa procedura:  
  
-   È necessario disporre di autorizzazione per accedere all'area funzionale **Autorizzazioni utenti e gruppi** .  
  
-   È necessario essere un amministratore del modello. Per altre informazioni, vedere [Amministratori &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-delete-hierarchy-member-permissions"></a>Per eliminare le autorizzazioni membri gerarchia  
  
1.  In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], fare clic su **Autorizzazioni utenti e gruppi**.  
  
2.  Nella pagina **Utenti** o **Gruppi** selezionare la riga relativa all'utente o al gruppo che si desidera modificare.  
  
3.  Fare clic su **Modifica utente selezionato**.  
  
4.  Fare clic sulla scheda **Membri gerarchia** .  
  
5.  Selezionare un modello dall'elenco **Modello** .  
  
6.  Selezionare una versione dall'elenco **Versione** .  
  
7.  Fare clic su **Modifica**.  
  
8.  Individuare il nodo dell'albero con l'autorizzazione nel panello **Autorizzazioni membri gerarchia** .  
  
9. Fare clic sul nodo dell'albero e quindi scegliere **Nessuno** dal menu di scelta rapida.  
  
    > [!NOTE]  
    >  Se l'autorizzazione viene ereditata da un gruppo, non sarà possibile rimuoverla da un utente. È necessario invece rimuovere l'autorizzazione dal gruppo.  
  
10. Fare clic su **Salva**.  
  
## <a name="see-also"></a>Vedere anche  
 [Autorizzazioni membri gerarchie &#40;Master Data Services&#41;](../master-data-services/hierarchy-member-permissions-master-data-services.md)   
 [Assegnare autorizzazioni membri gerarchia &#40;Master Data Services&#41;](../master-data-services/assign-hierarchy-member-permissions-master-data-services.md)  
  
  

---
title: Gestire gli insiemi di modifiche (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: cc74d46d-7566-45d8-9b51-2cfc262f6abe
caps.latest.revision: 11
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: ed310d84295b7437ac345b8a047054c2fb99803c
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2018
ms.locfileid: "35407233"
---
# <a name="manage-changesets-master-data-services"></a>Gestire gli insiemi di modifiche (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] è possibile gestire tutte le modifiche in base a modello e versione.  
  
## <a name="prerequisites"></a>Prerequisites  
  
-   È necessario disporre dell'autorizzazione per accedere all'area funzionale **Esplora** . Per altre informazioni, vedere [Autorizzazioni per aree funzionali &#40;Master Data Services&#41;](../master-data-services/functional-area-permissions-master-data-services.md).  
  
-   È necessario almeno l'accesso con diritti di lettura sull'entità o su uno dei relativi attributi.  
  
-   Gli amministratori dell'entità possono gestire gli insiemi di modifiche che hanno creato o quelli in sospeso per l'approvazione.  
  
-   Se non si è un amministratore dell'entità, è possibile gestire solo gli insiemi di modifiche creati personalmente.  
  
## <a name="to-manage-the-changesets"></a>Per gestire gli insiemi di modifiche  
  
1.  In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]selezionare il modello e la versione e fare clic su **Visualizzatore**.  
  
2.  Fare clic su **Insiemi di modifiche**. Sono visualizzati tutti gli insiemi di modifiche che è possibile gestire per il modello e la versione selezionati.  
  
3.  Fare clic su **Applica** per visualizzare i dettagli dell'insieme di modifiche.  
  
4.  Fare clic su **Elimina** per eliminare un insieme di modifiche. È possibile eliminare solo un insieme di modifiche che non è in stato in sospeso o approvato.  
  
5.  Fare clic su **Aggiungi** per aggiungere un insieme di modifiche.  
  
6.  Fare clic su **Modifica** per modificare un insieme di modifiche.  
  
  

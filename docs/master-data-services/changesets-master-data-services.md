---
title: Insiemi di modifiche (Master Data Services) | Microsoft Docs
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
ms.assetid: f227c49a-ed46-4e0f-8992-83093456cf94
caps.latest.revision: 13
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 455f8c4c409a5314fb24f4f41c75641c0128cfa7
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2018
ms.locfileid: "35404664"
---
# <a name="changesets-master-data-services"></a>Insiemi di modifiche (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] supporta ora la funzionalità di salvataggio delle modifiche in sospeso per un'entità come insiemi di modifiche. Esistono due scenari di utilizzo per questa funzionalità.  
  
-   **Modifiche apportate quando viene attivata l'opzione "Approvazione necessaria" dall'amministratore di entità**  
  
     Se l'amministratore di entità specifica che le modifiche per una determinata entità devono essere prima approvate per poterne eseguire il commit, sarà necessario salvare eventuali modifiche all'entità in un insieme di modifiche nuovo o esistente per poterle inviare per l'approvazione.  Per altre informazioni, vedere [Approvazione necessaria &#40;Master Data Services&#41;](../master-data-services/approval-required-master-data-services.md)  
  
     Seguire il flusso di lavoro seguente.  
  
    1.  Creare un insieme di modifiche. Lo stato dell'insieme di modifiche è Aperto. Vedere [Creare un insieme di modifiche &#40;Master Data Services&#41;](../master-data-services/create-a-changeset-master-data-services.md)  
  
    2.  Applicare l'insieme di modifiche e aggiungere alcune modifiche all'insieme. Vedere [Apply and Update a Changeset &#40;Master Data Services&#41;](../master-data-services/apply-and-update-a-changeset-master-data-services.md)  
  
    3.  Inviare l'insieme di modifiche all'amministratore di entità per l'approvazione. Lo stato dell'insieme di modifiche è In sospeso. Vedere [Eseguire il commit o inviare un insieme di modifiche &#40;Master Data Services&#41;](../master-data-services/commit-or-submit-a-changeset-master-data-services.md)  
  
    4.  L'amministratore di entità riceve una notifica di posta elettronica che segnala che un insieme di modifiche è in attesa di approvazione. Se l'amministratore di entità approva l'insieme di modifiche, lo stato dell'insieme diventa Approvato. Vedere [Applicare e rifiutare un insieme di modifiche &#40;Master Data Services&#41;](../master-data-services/approve-or-reject-a-changeset-master-data-services.md)  
  
    5.  Verrà eseguito automaticamente il commit dell'insieme di modifiche approvato. Se il commit della modifica viene eseguito correttamente, lo stato dell'insieme di modifiche è Commit eseguito.  
  
-   **Modifiche dell'utente locali**  
  
     Per limitarsi a salvare le modifiche locali per poterle usare o recuperare in seguito, è possibile usare gli insiemi di modifiche.  
  
     Seguire il flusso di lavoro seguente.  
  
    1.  Creare un insieme di modifiche. Lo stato dell'insieme di modifiche è Aperto. Vedere [Creare un insieme di modifiche &#40;Master Data Services&#41;](../master-data-services/create-a-changeset-master-data-services.md)  
  
    2.  Applicare l'insieme di modifiche e aggiungere alcune modifiche all'insieme. Vedere [Applicare e aggiornare un insieme di modifiche &#40;Master Data Services&#41;](../master-data-services/apply-and-update-a-changeset-master-data-services.md)  
  
    3.  Quando si è pronti, eseguire il commit dell'insieme di modifiche. Vedere [Eseguire il commit o inviare un insieme di modifiche &#40;Master Data Services&#41;](../master-data-services/commit-or-submit-a-changeset-master-data-services.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Creare un insieme di modifiche &#40;Master Data Services&#41;](../master-data-services/create-a-changeset-master-data-services.md)   
 [Applicare e aggiornare un insieme di modifiche &#40;Master Data Services&#41;](../master-data-services/apply-and-update-a-changeset-master-data-services.md)   
 [Eseguire il commit o inviare un insieme di modifiche &#40;Master Data Services&#41;](../master-data-services/commit-or-submit-a-changeset-master-data-services.md)   
 [Applicare o rifiutare un insieme di modifiche &#40;Master Data Services&#41;](../master-data-services/approve-or-reject-a-changeset-master-data-services.md)   
 [Gestire gli insiemi di modifiche &#40;Master Data Services&#41;](../master-data-services/manage-changesets-master-data-services.md)  
  
  

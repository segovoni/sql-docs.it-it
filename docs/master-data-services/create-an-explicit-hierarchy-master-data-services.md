---
title: Creare una gerarchia esplicita (Master Data Services) | Microsoft Docs
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
- creating explicit hierarchies [Master Data Services]
- explicit hierarchies, creating
ms.assetid: ba768393-6990-4eda-8cb0-d58cb3cfc2e2
caps.latest.revision: 10
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 38f0658b634d6267e7c3c9a5c79d084026b8b7ed
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2018
ms.locfileid: "35400233"
---
# <a name="create-an-explicit-hierarchy-master-data-services"></a>Creare una gerarchia esplicita (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]creare una gerarchia esplicita quando è necessaria una gerarchia incompleta nella quale possono esistere membri a qualsiasi livello. Nelle gerarchie esplicite sono inclusi membri da una singola entità.  
  
 Dopo aver creato una gerarchia esplicita, è possibile aggiungervi membri nell'area funzionale **Esplora** .  
  
## <a name="prerequisites"></a>Prerequisites  
 Per eseguire questa procedura:  
  
-   È necessario disporre di autorizzazione per accedere all'area funzionale **Amministrazione sistema** .  
  
-   È necessario essere un amministratore del modello. Per altre informazioni, vedere [Amministratori &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
-   È necessario abilitare l'entità per le gerarchie esplicite e le raccolte.  
  
### <a name="to-create-an-explicit-hierarchy"></a>Per creare una gerarchia esplicita  
  
1.  In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], fare clic su **Amministrazione sistema**.  
  
2.  Nella pagina **Gestisci modelli** selezionare un modello dalla griglia, quindi fare clic su **Entità**.  
  
3.  Dalla griglia della pagina **Gestisci entità** selezionare la riga per l'entità per cui si vuole creare una gerarchia esplicita.  
  
4.  Fare clic su **Gerarchie esplicite**.  
  
5.  Nella pagina **Gestisci gerarchie esplicite** fare clic su **Aggiungi**.  
  
6.  Nella casella **Nome** digitare un nome per la gerarchia.  
  
7.  Facoltativamente, deselezionare la casella di controllo **Gerarchia obbligatoria** per creare una gerarchia come non obbligatoria. Per altre informazioni sui tipi di gerarchia, vedere [Gerarchie esplicite &#40;Master Data Services&#41;](../master-data-services/explicit-hierarchies-master-data-services.md).  
  
8.  Fare clic su **Salva**.  
  
## <a name="grid-columns"></a>Colonne della griglia  
 Per ogni gerarchia esplicita creata, viene aggiunta una riga con sette colonne alla griglia. Di seguito sono descritte le colonne.  
  
|nome|Descrizione|  
|----------|-----------------|  
|Stato|Stato dell'entità. Quando si fa clic su **Salva** , viene visualizzata l'immagine seguente che indica che l'entità è in fase di aggiornamento.<br /><br /> ![Icona di aggiornamento dello stato](../master-data-services/media/mds-statusicon-updating.png "Icona di aggiornamento dello stato")<br /><br /> Se si verificano errori durante la creazione o la modifica di un'entità, viene visualizzata l'immagine seguente.<br /><br /> ![Icona di errore](../master-data-services/media/mds-statusicon-error.png "Icona di errore")<br /><br /> Se lo stato è OK, viene visualizzata l'immagine seguente.<br /><br /> ![Icona dello stato OK](../master-data-services/media/mds-statusicon-ok.png "Icona dello stato OK")|  
|nome|Il nome della gerarchia esplicita.|  
|Obbligatorio|Specifica se la gerarchia esplicita è obbligatoria.|  
|Creato da|Nome utente dell'utente che ha creato la gerarchia esplicita.|  
|Data creazione|Data e ora di creazione della gerarchia esplicita.|  
|Aggiornato da|Nome utente dell'ultimo utente che ha aggiornato la gerarchia esplicita.|  
|Data aggiornamento|Data e ora dell'ultimo aggiornamento della gerarchia esplicita.|  
  
## <a name="next-steps"></a>Next Steps  
  
-   [Creare membri consolidati &#40;Master Data Services&#41;](../master-data-services/create-a-consolidated-member-master-data-services.md)  
  
  
  
## <a name="see-also"></a>Vedere anche  
 [Gerarchie esplicite &#40;Master Data Services&#41;](../master-data-services/explicit-hierarchies-master-data-services.md)   
 [Gerarchie derivate con estremità esplicite &#40;Master Data Services&#41;](../master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md)   
 [Modificare il nome di una gerarchia esplicita &#40;Master Data Services&#41;](../master-data-services/change-an-explicit-hierarchy-name-master-data-services.md)  
  
  


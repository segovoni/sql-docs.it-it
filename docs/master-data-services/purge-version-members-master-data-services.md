---
title: Ripulire i membri di versione (Master Data Services) | Microsoft Docs
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
ms.assetid: adecce2d-46bb-49ff-8be9-0b31b8dd3cb6
caps.latest.revision: 7
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: ad4a9d41b4ba46ef4d83269712ee624d23d2d97b
ms.sourcegitcommit: de5e726db2f287bb32b7910831a0c4649ccf3c4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2018
ms.locfileid: "35335035"
---
# <a name="purge-version-members-master-data-services"></a>Ripulire i membri di versione (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]l'eliminazione di un membro comporta solo la disattivazione o l'eliminazione temporanea. I dati rimangono nel database. Questo argomento descrive come ripulire (eliminare definitivamente) tutti i membri eliminati temporaneamente nella versione di un modello.  
  
## <a name="prerequisites"></a>Prerequisites  
 Per eseguire questa procedura.  
  
-   È necessario avere l'autorizzazione per accedere all'area funzionale Gestione versioni.  
  
-   È necessario essere un amministratore del modello. Per altre informazioni, vedere [Amministratori &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
## <a name="to-purge-soft-deleted-members"></a>Per ripulire i membri eliminati temporaneamente  
  
1.  In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], fare clic su **Gestione versioni**.  
  
2.  Nella pagina **Gestisci versioni** selezionare il modello con la versione da ripulire. Viene visualizzato l'elenco di versioni del modello.  
  
3.  Selezionare la riga relativa alla versione da ripulire.  
  
4.  Fare clic su **Ripulisci membri**.  
  
5.  Fare clic su "OK" alla richiesta di conferma.  
  
## <a name="additional-methods-to-purge-members"></a>Metodi aggiuntivi per ripulire i membri  
 La ripulitura definitiva dei membri della versione elimina i membri eliminati temporaneamente in tutte le entità relative alla versione selezionata. Un'alternativa con una maggiore granularità consiste nell'usare lo staging di base dell'entità per eliminare definitivamente solo membri specifici di un'entità. Inoltre, gli amministratori dell'entità con l'autorizzazione funzionale Esplora possono ripulire una versione dell'entità nella pagina Esplora entità.  
  
 Per altre informazioni, vedere [Tabella di gestione temporanea dei membri foglia &#40;Master Data Services&#41;](../master-data-services/leaf-member-staging-table-master-data-services.md)  
  
  

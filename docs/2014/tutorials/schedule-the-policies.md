---
title: Pianificare i criteri | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 59417a54-55f1-4468-ba41-368aa852c2d4
caps.latest.revision: 5
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: c328073f25c27ff05b8b6edbd79a56ad1fda85ab
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37315131"
---
# <a name="schedule-the-policies"></a>Pianificazione criteri
  In questa attività verrà eseguita la pianificazione dei criteri per procedure consigliate importati nell'attività precedente.  
  
### <a name="to-schedule-the-best-practices-policies"></a>Per pianificare i criteri per procedure consigliate  
  
1.  In Esplora oggetti, espandere **Management**, espandere **gestione dei criteri**, espandere **criteri**, fare doppio clic su un criterio di procedure ottimo e quindi fare clic su  **Proprietà**.  
  
    > [!NOTE]  
    >  In alternativa, per vedere facilmente quali criteri sono associati alle procedure consigliate e ordinare le categorie delle procedure consigliate, espandere **Management**, espandere **gestione dei criteri**, quindi fare clic su **i criteri**. Scegliere **Dettagli Esplora oggetti** dal menu **Visualizza**. Nel **dettagli Esplora oggetti** riquadro, fare clic sui **categoria** intestazione per ordinare i criteri in base alla categoria. I criteri per procedure consigliate migliori hanno il prefisso **procedure consigliate Microsoft**. Fare doppio clic sui criteri che si desidera configurare e quindi fare clic su **proprietà**.  
  
2.  Nel **generali** pagina della **Apri criteri** nella finestra di dialogo il **modalità di valutazione** elenco, fare clic su **su pianificazione**.  
  
3.  Accanto al **pianificazione** fare clic su **Scegli** per specificare una pianificazione esistente oppure fare clic su **New** per creare una nuova pianificazione.  
  
4.  Dopo aver configurato una pianificazione, è possibile selezionare i **abilitato** casella di controllo nella parte superiore della pagina per abilitare i criteri pianificati.  
  
5.  Ripetere i passaggi da 1 a 4 per tutti i criteri che si desidera pianificare.  
  
    > [!NOTE]  
    >  Per visualizzare i risultati di valutazione dopo l'esecuzione di criteri pianificati, aprire il log Cronologia criteri nell'istanza di destinazione. Per aprire il log, fare doppio clic su **criteri di gestione**, quindi fare clic su **Visualizza cronologia**.  
  
## <a name="summary"></a>Riepilogo  
 I criteri pianificati sono stati configurati per essere eseguiti in un'istanza singola di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Se si desidera distribuire i criteri pianificati in più istanze, continuare con la prossima attività in questa esercitazione.  
  
## <a name="next-steps"></a>Passaggi successivi  
 [Distribuzione di criteri pianificati in istanze multiple](../../2014/tutorials/deploy-scheduled-policies-to-multiple-instances.md)  
  
  

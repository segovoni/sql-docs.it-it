---
title: Pagina Stato (procedure guidate gruppi di disponibilità Always On) | Microsoft Docs
ms.custom: ''
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.swb.failoverwizard.progress.f1
- sql13.swb.adddatabasewizard.progress.f1
- sql13.swb.addreplicawizard.progress.f1
- sql13.swb.newagwizard.progress.f1
ms.assetid: bd3b0306-8384-4120-a1c9-03825f0ae26a
caps.latest.revision: 13
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1fe9313834f9e6cc4f3af9364c9e1aecebe6cbdc
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34768567"
---
# <a name="progress-page-always-on-availability-group-wizards"></a>Pagina Stato (procedure guidate gruppi di disponibilità Always On)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Utilizzare questa finestra di dialogo per visualizzare lo stato di avanzamento di una procedura guidata [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] eseguita in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. L'indicatore di stato segnala lo stato di avanzamento relativo dei passaggi eseguiti dalla procedura guidata.  
  
## <a name="uielement-list"></a>Elenco degli elementi di interfaccia  
 **Altri dettagli**  
 Fare clic sulla freccia GIÙ per visualizzare una griglia dello stato di avanzamento in cui sono elencati i passaggi completati, seguiti dall'attuale operazione in corso. La griglia include le colonne seguenti:  
  
 **Nome**  
 Visualizza una frase che descrive un passaggio specifico.  
  
 **Stato**  
 Indica il risultato dei passaggi completati e la percentuale di completamento del passaggio corrente, come segue:  
  
|Risultato|Descrizione|  
|------------|-----------------|  
|**Errore**|Indica che si è verificato un errore nell'operazione relativa a questo passaggio. Fare clic sul collegamento per visualizzare una finestra di dialogo del messaggio in cui viene descritto l'errore.|  
|**In corso (** *percentuale di completamento* **)**|Indica che l'operazione è in corso e stima la percentuale di completamento di questo passaggio.|  
|**Esito positivo**|Indica che l'operazione per questo passaggio è stata completata.|  
  
 **Meno dettagli**  
 Fare clic per nascondere la griglia dello stato di avanzamento.  
  
 **Annulla**  
 Fare clic per ignorare eventuali operazioni rimanenti e uscire dalla procedura guidata.  
  
##  <a name="RelatedTasks"></a> Attività correlate  
  
-   [Utilizzare la finestra di dialogo Nuovo gruppo di disponibilità &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [Usare la procedura guidata Aggiungi replica a gruppo di disponibilità &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Usare la procedura guidata Aggiungi database a gruppo di disponibilità &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/availability-group-add-database-to-group-wizard.md)  
  
-   [Usare la Procedura guidata Failover del gruppo di disponibilità &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-fail-over-availability-group-wizard-sql-server-management-studio.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica di Gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)  
  
  

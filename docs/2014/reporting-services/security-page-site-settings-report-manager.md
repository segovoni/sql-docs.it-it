---
title: Pagina sicurezza (Impostazioni sito. Gestione report) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: acc9a905-90f8-4544-aec6-b2ab3a1b0015
caps.latest.revision: 26
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: a613f3d2cadae9913f14759ca3c59252d62cd14f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37294101"
---
# <a name="security-page-site-settings-report-manager"></a>Pagina sicurezza (Impostazioni sito. Gestione report)
  La pagina Sicurezza consente di visualizzare le assegnazioni di ruolo a livello di sistema che regolano l'accesso al sito del server di report. Le assegnazioni di ruolo a livello di sistema sono esterne all'ambito dello spazio dei nomi o della gerarchia di cartelle del server di report. Le assegnazioni di ruolo a livello di sistema sono globali e non possono variare per elementi specifici. Le operazioni supportate tramite le assegnazioni di ruolo a livello di sistema includono la creazione di pianificazioni condivise, l'utilizzo di Generatore report e l'impostazione di valori predefiniti per alcune caratteristiche del server.  
  
 Durante l'installazione del server di report viene creata un'assegnazione di ruolo a livello di sistema predefinita. Questa assegnazione di ruolo concede agli amministratori di sistema locali le autorizzazioni per la gestione dell'ambiente del server di report. Un amministratore di sistema locale ha sempre la possibilità di impostare la sicurezza per un server di report locale, anche se vengono eliminate le assegnazioni di ruolo a livello di sistema.  
  
 A tutti gli altri utenti che necessitano di accedere a Generatore report o a pianificazioni condivise, è necessario assegnare un'assegnazione di ruolo a livello di sistema.  
  
## <a name="navigation"></a>Navigazione  
 Utilizzare la procedura riportata di seguito per navigare fino a questo percorso nell'interfaccia utente.  
  
###### <a name="to-open-the-security-page-for-site-settings"></a>Per aprire la pagina Sicurezza per Impostazioni sito  
  
1.  Aprire Gestione report.  
  
2.  Nella parte superiore della pagina fare clic su **Impostazioni sito**. Viene visualizzata la pagina delle proprietà Generale del sito.  
  
3.  Fare clic sulla scheda **Sicurezza** .  
  
## <a name="options"></a>Opzioni  
 **Elimina**  
 Fare clic per eliminare un'assegnazione di ruolo esistente. Prima di fare clic su **Elimina**, selezionare la casella di controllo accanto al nome del gruppo o dell'utente che si desidera rimuovere. Non è possibile eliminare un'assegnazione di ruolo se è l'unica rimanente. L'eliminazione di un'assegnazione di ruolo non comporta l'eliminazione di account utente, account di gruppo o definizioni di ruolo.  
  
 **Nuova assegnazione ruolo**  
 Fare clic per visualizzare la pagina Nuova assegnazione ruolo a livello di sistema, nella quale è possibile creare assegnazioni di ruolo di sistema aggiuntive per il sito del server di report. Per altre informazioni, vedere [nuove assegnazioni di ruolo di sistema: modifica pagina assegnazioni di ruolo del sistema &#40;gestione Report&#41;](../../2014/reporting-services/new-system-role-assignments-edit-system-role-assignments-page-report-manager.md).  
  
 **Modifica**  
 Fare clic per visualizzare la pagina Nuova assegnazione ruolo a livello di sistema, nella quale è possibile modificare assegnazioni di ruolo di sistema singole per il sito del server di report. Per altre informazioni, vedere [nuove assegnazioni di ruolo di sistema: modifica pagina assegnazioni di ruolo del sistema &#40;gestione Report&#41;](../../2014/reporting-services/new-system-role-assignments-edit-system-role-assignments-page-report-manager.md).  
  
 **Gruppo o utente**  
 Consente di visualizzare l'elenco di gruppi e utenti che fanno parte di un'assegnazione di ruolo esistente. Le assegnazioni di ruolo esistenti per la cartella corrente sono definite per i gruppi e gli utenti visualizzati in questa colonna. Fare clic su **Modifica** accanto a un gruppo o un nome utente per visualizzare o modificare i dettagli dell'assegnazione di ruolo.  
  
 **Roles**  
 Visualizza un elenco di una o più definizioni di ruolo che fanno parte di un'assegnazione di ruolo esistente. Se a un account utente o di gruppo vengono assegnati più ruoli, tale gruppo o utente potrà eseguire tutte le attività incluse in tutti i ruoli. Per visualizzare il set di attività supportate da ogni ruolo, usare [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]. Non è possibile visualizzare, creare, modificare o eliminare ruoli in Gestione report. Per istruzioni, vedere [creare, eliminare o modificare un ruolo &#40;Management Studio&#41;](security/role-definitions-create-delete-or-modify.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Guida F1 di gestione report](../../2014/reporting-services/report-manager-f1-help.md)   
 [Concessione di autorizzazioni in un server di report in modalità nativa](security/granting-permissions-on-a-native-mode-report-server.md)  
  
  

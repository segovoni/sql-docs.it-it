---
title: 'Nuova assegnazione di ruolo di sistema: Modifica pagina Assegnazioni ruolo di sistema (gestione Report) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 62a22ab9-1eb4-4ce5-8dd7-06b5ed2d9a2a
caps.latest.revision: 26
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 6b580fc8ab1a2558d8c356372d6ccbd4f40ebb95
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37331271"
---
# <a name="new-system-role-assignments-edit-system-role-assignments-page-report-manager"></a>Pagina Nuova assegnazione ruolo a livello di sistema: Modifica assegnazioni ruolo a livello di sistema (Gestione report)
  La pagina Nuova assegnazione ruolo a livello di sistema o Modifica assegnazioni ruolo a livello di sistema consente di impostare la sicurezza per il server di report. Il sistema di sicurezza è interamente basato sulle assegnazioni di ruolo, tramite le quali utenti o gruppi specifici vengono mappati alle attività che possono eseguire. L'elenco di attività è rappresentato in forma di definizione di ruolo selezionabile per la creazione dell'assegnazione di ruolo.  
  
 A livello di sistema, le assegnazioni di ruolo create o modificate vengono applicate al server di report nel suo complesso. Ad esempio, la possibilità di creare pianificazioni condivise viene impostata a livello di sistema perché le pianificazioni condivise vengono utilizzate in tutto il sistema.  
  
 Per impostazione predefinita, Reporting Services fornisce due ruoli a livello di sistema predefiniti:  
  
-   Utente sistema include attività che consentono agli utenti di visualizzare le proprietà del server di report e le pianificazioni condivise e di eseguire definizioni di report che consentono di visualizzare report click-through pubblicati nel server di report. La maggior parte degli utenti deve essere assegnata a questo ruolo.  
  
-   Amministratore sistema include attività per la creazione e la gestione di pianificazioni condivise, l'impostazione di proprietà del server e la creazione di assegnazioni di ruolo a livello di sistema per altri utenti. Le autorizzazioni a questo livello sono necessarie per un numero limitato di utenti.  
  
## <a name="navigation"></a>Navigazione  
 Utilizzare la procedura riportata di seguito per navigare fino a questo percorso nell'interfaccia utente.  
  
###### <a name="to-open-the-new-system-role-assignments-or-edit-system-role-assignments-page"></a>Per aprire la pagina Nuova assegnazione ruolo a livello di sistema o Modifica assegnazioni ruolo a livello di sistema  
  
1.  Aprire Gestione report.  
  
2.  Fare clic su **Impostazioni sito**nell'angolo superiore destro della pagina. Viene visualizzata la pagina delle proprietà Generale per il sito.  
  
3.  Fare clic sulla scheda **Sicurezza** . Per accedere a questa pagina, è necessario disporre delle autorizzazioni Gestione contenuto e Amministratore sistema.  
  
4.  Per creare una nuova assegnazione di ruolo, nella barra degli strumenti fare clic su **Nuova assegnazione ruolo** . Per modificare un'assegnazione di ruolo esistente, fare clic su **Modifica** accanto a un gruppo o un utente nella pagina delle proprietà Sicurezza.  
  
## <a name="options"></a>Opzioni  
 **Gruppo o utente**  
 Consente di digitare il nome di un account di gruppo o di un account utente del dominio. Se il server di report viene eseguito nel contesto di un account locale, è necessario specificare gruppi o utenti locali. Se il server di report viene eseguito nel contesto di un account di dominio, è necessario specificare gruppi o utenti del dominio. Immettere l'account nel formato seguente: \<dominio >\\< account\>.  
  
> [!NOTE]  
>  Questa casella è disponibile solo nella pagina Nuova assegnazione ruolo.  
  
 **Roles**  
 Fornisce un elenco di ruoli a livello di sistema che è possibile assegnare agli altri utenti. È possibile specificare più ruoli per una singola assegnazione di ruolo.  
  
 Gestione report non consente di visualizzare le attività incluse in ogni ruolo né di aggiungere o modificare le attività. I ruoli devono essere utilizzati come sono definiti. Per creare, modificare o eliminare ruoli, usare [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]. Per altre informazioni, vedere [creare, eliminare o modificare un ruolo &#40;Management Studio&#41;](security/role-definitions-create-delete-or-modify.md).  
  
 Si noti che se si usa [!INCLUDE[ssExpressEd2005](../includes/ssexpressed2005-md.md)] with Advanced Services, è necessario usare i ruoli predefiniti forniti.  
  
 **Descrizioni**  
 Visualizza informazioni aggiuntive sul ruolo. La descrizione di un ruolo predefinito, ad esempio Utente sistema o Amministratore sistema, contiene un riassunto delle attività supportate da ciascun ruolo.  
  
 **Elimina assegnazione ruolo**  
 Fare clic per eliminare l'assegnazione ruolo esistente per un utente o un gruppo. Non è possibile eliminare l'ultima assegnazione di ruolo rimasta (a ogni elemento deve essere associata almeno una assegnazione di ruolo).  
  
> [!NOTE]  
>  Questo pulsante è disponibile solo nella pagina Modifica assegnazione ruolo.  
  
## <a name="see-also"></a>Vedere anche  
 [Guida F1 di gestione report](../../2014/reporting-services/report-manager-f1-help.md)   
 [Assegnazioni di ruolo](security/role-assignments.md)   
 [Definizioni di ruolo](security/role-definitions.md)  
  
  

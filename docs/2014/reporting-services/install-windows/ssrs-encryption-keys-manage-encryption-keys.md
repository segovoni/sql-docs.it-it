---
title: Configurare e gestire chiavi di crittografia (Gestione configurazione SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- encryption keys [Reporting Services]
- private keys [Reporting Services]
- cryptography [Reporting Services]
- symmetric keys [Reporting Services]
- encryption [Reporting Services]
- public keys [Reporting Services]
ms.assetid: 58e61636-88a2-4338-ae5f-3dd210aee887
caps.latest.revision: 7
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 95ba14d23db8c606e66db48b5be5b865879de7c3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37187978"
---
# <a name="configure-and-manage-encryption-keys-ssrs-configuration-manager"></a>Configurare e gestire chiavi di crittografia (Gestione configurazione SSRS)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] usa le chiavi di crittografia per proteggere le credenziali e le informazioni di connessione archiviate in un database del server di report. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]supporta la crittografia tramite una combinazione di chiavi pubbliche, private e simmetriche utilizzate per proteggere dati sensibili. La chiave simmetrica viene creata durante l'inizializzazione del server di report al momento dell'installazione o della configurazione dello stesso e viene utilizzata dal server di report per crittografare dati sensibili archiviati in tale server. Le chiavi pubblica e privata vengono create dal sistema operativo e sono utilizzate per proteggere la chiave simmetrica. Per ogni istanza del server di report che contiene dati sensibili in un database del server di report viene creata una coppia di chiavi pubblica e privata.  
  
 La gestione delle chiavi di crittografia consiste nel creare una copia di backup della chiave simmetrica e nell'individuare il momento corretto in cui ripristinare, eliminare o modificare le chiavi, nonché la modalità appropriata per eseguire tali operazioni. Se si esegue la migrazione di un'installazione del server di report o si configura una distribuzione con scalabilità orizzontale, è necessario disporre di una copia di backup della chiave simmetrica per applicarla alla nuova installazione.  
  
> [!IMPORTANT]  
>  La modifica periodica della chiave di crittografia di Reporting Services è una procedura consigliata ai fini della sicurezza. È consigliabile modificare la chiave immediatamente dopo un aggiornamento della versione principale di Reporting Services. Modificando la chiave di crittografia di Reporting Services dopo un aggiornamento si riduce il rischio di ulteriori interruzioni del servizio rispetto invece all'eseguire questa operazione all'esterno del ciclo di aggiornamento.  
  
 Per gestire le chiavi simmetriche è possibile usare lo strumento di configurazione di Reporting Services o l'utilità **rskeymgmt** . Gli strumenti inclusi in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] consentono di gestire solo la chiave simmetrica, mentre le chiavi pubbliche e private vengono gestite dal sistema operativo. Sia lo strumento Gestione configurazione Reporting Services sia l'utilità **rskeymgmt** supportano le attività seguenti:  
  
-   Backup di una copia della chiave simmetrica per poterla utilizzare per il recupero dell'installazione di un server di report o come parte di una migrazione pianificata.  
  
-   Ripristino di una chiave simmetrica salvata in precedenza in un database del server di report, per consentire a una nuova istanza del server di report di accedere ai dati esistenti che originariamente non erano stati crittografati.  
  
-   Eliminazione dei dati crittografati in un database del server di report nel caso molto improbabile in cui non sia più possibile accedere a tali dati.  
  
-   Ricreazione delle chiavi simmetriche e riesecuzione della crittografia dei dati nel caso molto improbabile in cui la chiave simmetrica risulti compromessa. Come procedura di sicurezza consigliata, ricreare la chiave simmetrica periodicamente, ad esempio ogni pochi mesi, per proteggere il database del server di report da attacchi informatici mirati alla decrittazione della chiave.  
  
-   Aggiunta o rimozione di un'istanza del server di report da una distribuzione del server di report con scalabilità orizzontale in cui più server di report condividono sia un unico database del server di report sia la chiave simmetrica che consente la crittografia reversibile per quel database.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 [Inizializzare un Server di Report &#40;Gestione configurazione SSRS&#41;](ssrs-encryption-keys-initialize-a-report-server.md)  
 Illustra come vengono create le chiavi di crittografia.  
  
 [Eseguire il backup e il ripristino delle chiavi di crittografia di Reporting Services](ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)  
 Illustra come eseguire il backup delle chiavi di crittografia e ripristinarle per eseguire il recupero o la migrazione di un'installazione del server di report.  
  
 [Store dati crittografati di Report Server &#40;Gestione configurazione SSRS&#41;](ssrs-encryption-keys-store-encrypted-report-server-data.md)  
 Descrive la crittografia in un server di report.  
  
 [Eliminare e ricreare chiavi di crittografia &#40;Gestione configurazione SSRS&#41;](ssrs-encryption-keys-delete-and-re-create-encryption-keys.md)  
 Illustra come sostituire una chiave simmetrica con una nuova versione e come iniziare nuovamente nel caso in cui non sia possibile convalidare le chiavi simmetriche.  
  
 [Aggiungere e rimuovere le chiavi di crittografia per la distribuzione con scalabilità orizzontale &#40;Gestione configurazione SSRS&#41;](add-and-remove-encryption-keys-for-scale-out-deployment.md)  
 Illustra come aggiungere e rimuovere le chiavi di crittografia per controllare quali server di report fanno parte di una distribuzione con scalabilità orizzontale.  
  
## <a name="see-also"></a>Vedere anche  
 [Store dati crittografati di Report Server &#40;Gestione configurazione SSRS&#41;](ssrs-encryption-keys-store-encrypted-report-server-data.md)  
  
  

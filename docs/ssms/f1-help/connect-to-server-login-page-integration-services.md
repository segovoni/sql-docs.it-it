---
title: Connetti al server (pagina Nome account di accesso) - Integration Services | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.connecttodts.login.f1
- sql13.swb.connecttodtsserver.login.f1
ms.assetid: 402c2de4-f4ea-40b0-909f-3ddf3bd59950
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 18699131b8268dedfb0e47f05ec4032d81b498ef
ms.lasthandoff: 04/11/2017

---
# <a name="connect-to-server-login-page-integration-services"></a>Connetti al server (pagina Nome account di accesso) - Integration Services
Usare questa scheda per visualizzare o specificare le opzioni seguenti per la connessione a [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion_md.md)].  
  
## <a name="options"></a>Opzioni  
**Tipo server**  
Per la registrazione di un server da Esplora oggetti, selezionare il tipo di server a cui connettersi, ovvero [!INCLUDE[ssDE](../../includes/ssde_md.md)], Analysis Services, Reporting Services o Integration Services. Nelle altre parti della finestra di dialogo vengono visualizzate solo le opzioni applicabili al tipo di server selezionato. Durante la registrazione di un server da Server registrati, la casella **Tipo server** è di sola lettura e corrisponde al tipo di server visualizzato nel componente Server registrati. Per registrare un tipo diverso di server, selezionare [!INCLUDE[ssDE](../../includes/ssde_md.md)], Analysis Services, Reporting Services o Integration Services nella barra degli strumenti Server registrati prima di avviare la registrazione di un nuovo server.  
  
**Nome server**  
Consente di selezionare il server a cui connettersi. Per impostazione predefinita verrà visualizzata l'ultima istanza del server a cui è stata effettuata la connessione.  
  
> [!NOTE]  
> Non usare *<servername>*\\*<instancename>*, perché [!INCLUDE[ssIS](../../includes/ssis_md.md)] non supporta più di un'istanza in un computer.  
  
**Autenticazione**  
Solo l'autenticazione di [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows è disponibile per [!INCLUDE[ssIS](../../includes/ssis_md.md)]. Tale modalità consente di connettersi tramite un account utente di Windows.  
  
**Nome utente**  
Questa opzione non è disponibile in quanto per [!INCLUDE[ssIS](../../includes/ssis_md.md)]è possibile utilizzare solo l'autenticazione di Windows.  
  
**Password**  
Questa opzione non è disponibile in quanto per [!INCLUDE[ssIS](../../includes/ssis_md.md)]è possibile utilizzare solo l'autenticazione di Windows.  
  
**Memorizza password**  
Questa opzione non è disponibile in quanto per [!INCLUDE[ssIS](../../includes/ssis_md.md)]è possibile utilizzare solo l'autenticazione di Windows.  
  
**Connetti**  
Consente di connettersi al server selezionato.  
  
**Opzioni**  
Fare clic su questo pulsante per modificare la finestra di dialogo e nascondere le opzioni aggiuntive per la connessione al server, ad esempio le opzioni per la memorizzazione della password.  
  

---
title: Finestra di dialogo Seleziona origine | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: performance-monitor
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.swb.dmf.selectsource.f1
ms.assetid: d664c2e5-dd0c-4da8-b27d-aa4ee4fc0ffd
caps.latest.revision: 16
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: f5138982829e14779632ddbb60aad34c63ac1b54
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32955386"
---
# <a name="select-source-dialog-box"></a>Finestra di dialogo Seleziona origine
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Utilizzare questa finestra di dialogo per selezionare l'origine dei criteri da eseguire. Per selezionare uno o più file XML che contengono criteri, selezionare **File**. Per eseguire i criteri individuati nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], selezionare **Server**.  
  
 È possibile aprire questa finestra di dialogo in diversi modi.  
  
 **Per aprire la finestra di dialogo**  
  
-   In Server registrati fare clic con il pulsante destro del mouse su **Gruppi di server locali** , su qualsiasi server in **Gruppi di server locali**o su qualsiasi server in **Server di gestione centrale**, quindi scegliere **Valuta criteri**. Nella pagina **Selezione criteri** della finestra di dialogo **Valuta criteri** fare clic sul pulsante Sfoglia (**...**).  
  
-   In Esplora oggetti espandere **Gestione**, espandere **Gestione criteri**, fare clic con il pulsante destro del mouse su **Criteri**, quindi scegliere **Importa criteri**. Nella finestra di dialogo **Importa** fare clic sul pulsante Sfoglia (**...**).  
  
-   In Esplora oggetti fare clic con il pulsante destro del mouse su un server, un database o un oggetto di database, scegliere **Criteri**, quindi fare clic su **Valuta**. Nella pagina **Selezione criteri** della finestra di dialogo **Valuta criteri** fare clic sul pulsante Sfoglia (**...**).  
  
## <a name="options"></a>Opzioni  
 **File**  
 Selezionare uno o più file XML che contengono criteri.  
  
 **Server**  
 Consente di selezionare un server contenente i criteri che si desidera eseguire.  
  
 **Tipo server**  
 Solo i server del [!INCLUDE[ssDE](../../includes/ssde-md.md)] contengono criteri. Il contenuto di questa casella è di sola lettura.  
  
 **Nome server**  
 Consente di selezionare l'istanza del server a cui connettersi. Per impostazione predefinita, viene visualizzata l'istanza del server a cui è stata effettuata l'ultima connessione.  
  
 **Autenticazione**  
 Sono disponibili due modalità di autenticazione per la connessione a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
 **Modalità di autenticazione di Windows (Autenticazione di Windows)**  
 La modalità di autenticazione di Windows modalità consente di connettersi tramite un account utente di Windows.  
  
 **autenticazione di SQL Server**  
 Quando un utente si connette con un nome di accesso e una password da una connessione di tipo non trusted, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] esegue l'autenticazione verificando che sia impostato un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e che la password specificata corrisponda a quella registrata in precedenza. Se non è stato impostato alcun account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , l'autenticazione non viene completata e viene segnalato un errore all'utente.  
  
> [!IMPORTANT]  
>  Se possibile, usare l'autenticazione di Windows.  
  
 **User name**  
 Immettere il nome utente da utilizzare per la connessione. Questa opzione è disponibile solo si è scelto di utilizzare l'autenticazione di Windows per la connessione.  
  
 **Account di accesso**  
 Immettere l'account di accesso da utilizzare per la connessione. Questa opzione è disponibile solo se si è scelto di utilizzare l'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per la connessione.  
  
 **Password**  
 Immettere la password per l'account di accesso. Questa opzione è modificabile solo se si è scelto di utilizzare l'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per la connessione.  
  
## <a name="see-also"></a>Vedere anche  
 [Nodo Gestione criteri &#40;Esplora oggetti&#41;](../../relational-databases/policy-based-management/policy-management-node-object-explorer.md)   
 [Amministrazione di server tramite la gestione basata su criteri](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  

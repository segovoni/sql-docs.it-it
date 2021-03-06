---
title: Associare un'applicazione Web e un database Master Data Services | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.suite: sql
ms.technology: install
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ccb25672-f71d-4135-b548-f50eb45d8fa5
caps.latest.revision: 9
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: c7604c76f50a9f9a05a91c877398b6f47e300629
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32893090"
---
# <a name="associate-a-master-data-services-database-and-web-application"></a>Associare un'applicazione Web e un database Master Data Services

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Associare l'applicazione Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] a un database [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] per specificare il database da usare per le operazioni Web.  
  
## <a name="prerequisites"></a>Prerequisites  
  
-   [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] deve essere installato nel computer locale. Per altre informazioni, vedere [Install Master Data Services](../../master-data-services/install-windows/install-master-data-services.md)(Installare Master Data Services).  
  
-   È necessario che sia disponibile un'applicazione Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] locale. Per altre informazioni, vedere [Creare un'applicazione Web Gestione dati master &#40;Master Data Services&#41;](../../master-data-services/install-windows/create-a-master-data-manager-web-application-master-data-services.md).  
  
-   È necessario che sia disponibile un database [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] locale o remoto. Per altre informazioni, vedere [Creare un database Master Data Services](../../master-data-services/install-windows/create-a-master-data-services-database.md).  
  
### <a name="to-associate-a-master-data-services-database-and-web-application"></a>Per associare un'applicazione Web e un database Master Data Services  
  
1.  Aprire [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].  
  
2.  Nel riquadro sinistro fare clic su **Configurazione Web**.  
  
3.  Nell'elenco **Sito Web** della pagina **Configurazione Web**, in **Applicazione Web** selezionare il sito Web in cui è inclusa l'applicazione Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] .  
  
4.  Nella casella **Applicazione Web** selezionare l'applicazione Web in cui è ospitato [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)].  
  
5.  In **Associare l'applicazione al database**fare clic su **Seleziona**. Verrà visualizzata la finestra di dialogo **Connetti al database** .  
  
6.  Specificare le informazioni di connessione per l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che ospita il database [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] e fare clic su **Connetti**.  
  
7.  Nell'elenco **Database Master Data Services** selezionare il database che si desidera associare all'applicazione Web, quindi scegliere **OK**.  
  
8.  In **Associare l'applicazione al database**verificare che l'istanza e le informazioni del database siano corrette, quindi fare clic su **Applica**.  
  
## <a name="next-steps"></a>Next Steps  
  
-   L'accesso a livello di programmazione ai servizi Web [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] , viene abilitato automaticamente durante la creazione dell'applicazione Web. Per consentire agli sviluppatori di accedere ai metadati del servizio al fine di generare in modo semplice classi proxy per l'accesso a livello di codice, abilitare la pubblicazione dei metadati. Per altre informazioni, vedere [Creare le classi proxy del servizio Web Gestione dati master](../../master-data-services/develop/create-master-data-manager-web-service-proxy-classes.md).  
  
-   Aggiungere utenti e gruppi a [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]. Se a nessun utente o gruppo è stato concesso l'accesso a [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)], è necessario aprire [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] utilizzando le credenziali di amministratore del sistema [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]. Per altre informazioni, vedere [Amministratori &#40;Master Data Services&#41;](../../master-data-services/administrators-master-data-services.md) e [Utenti e gruppi &#40;Master Data Services&#41;](../../master-data-services/users-and-groups-master-data-services.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Install Master Data Services](../../master-data-services/install-windows/install-master-data-services.md)   
 [Pagina Configurazione Web &#40;Gestione configurazione Master Data Services&#41;](../../master-data-services/web-configuration-page-master-data-services-configuration-manager.md)  
  
  

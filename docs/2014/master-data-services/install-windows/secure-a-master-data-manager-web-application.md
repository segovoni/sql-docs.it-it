---
title: Rendere sicura un'applicazione Web Gestione dati master | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e360ba3a-e96b-4f85-b588-ed1f767fa973
caps.latest.revision: 8
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 3316a5469e6b5420178ae34a40ae4e2f9f0abd70
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37231341"
---
# <a name="secure-a-master-data-manager-web-application"></a>Rendere sicura un'applicazione Web Gestione dati master
  È possibile rendere sicura l'applicazione Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] con HTTPS.  
  
> [!NOTE]  
>  L'applicazione Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] consente di utilizzare HTTP o HTTPS, ma non entrambi.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per eseguire la procedura:  
  
-   È necessario essere un amministratore nel server Web in cui è installato [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] .  
  
-   È necessario che MDS sia installato nel server Web e che sia presente un'applicazione Web. Per altre informazioni, vedere [Installazione di Master Data Services](install-master-data-services.md) e [Create a Master Data Manager Web Application &#40;Master Data Services&#41;](create-a-master-data-manager-web-application-master-data-services.md).  
  
### <a name="to-secure-the-master-data-manager-web-application-with-https"></a>Per rendere sicura l'applicazione Web Gestione dati master con HTTPS  
  
1.  Dopo avere verificato che l'applicazione Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] sia configurata correttamente con HTTP, creare un certificato in IIS. Per altre informazioni, vedere [Configuring Server Certificates in IIS 7](http://technet.microsoft.com/library/cc732230\(WS.10\).aspx)(Configurazione dei certificati del server in IIS 7).  
  
2.  Nel riquadro **Connessioni** , in **Siti**, fare clic sul sito che ospita l'applicazione Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] .  
  
3.  Nel riquadro **Azioni** fare clic su **Binding**.  
  
4.  Scegliere **Aggiungi**.  
  
5.  Nell'elenco selezionare **https**.  
  
6.  Selezionare il certificato SSL.  
  
7.  Fare clic su **OK**.  
  
8.  Facoltativo. Per rimuovere HTTP in modo che gli utenti possano accedere al sito solo tramite HTTPS, fare clic sulla riga con **http**. Fare clic su **Rimuovi** e nella finestra di dialogo di conferma fare clic su **Sì**.  
  
    > [!IMPORTANT]  
    >  È necessario modificare le configurazioni di basicHttp e wsHttpBinding dopo la rimozione di HTTP.  
  
9. Fare clic su **Chiudi** per chiudere la finestra di dialogo **Binding sito**.  
  
10. Aprire il file Web. config da *unità*: \Programmi\Microsoft SQL Server\120\Master Data services\webapplication.  
  
11. Individuare la stringa `<security mode="Message">` e impostarla su `<security mode="Transport">`.  
  
12. Salvare e chiudere il file. Se si verifica un errore, il Controllo dell'account utente potrebbe essere abilitato. Per altre informazioni, vedere [Turn off User Account Control](http://technet.microsoft.com/library/cc709691\(WS.10\).aspx)(Disattivare il controllo dell'account utente). A questo punto, gli utenti dovrebbero poter utilizzare HTTPS per accedere al sito.  
  
## <a name="see-also"></a>Vedere anche  
 [Creare un'applicazione Web Gestione dati master &#40;Master Data Services&#41;](create-a-master-data-manager-web-application-master-data-services.md)  
  
  

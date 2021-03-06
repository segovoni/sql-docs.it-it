---
title: Visualizza pacchetti in SQL Server Management Studio (servizio SSIS) di Integration Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- viewing packages
- connections [Integration Services], packages
ms.assetid: 783e653c-0f1f-45ed-b3ef-5ba07b019f27
caps.latest.revision: 23
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 57d7a86bea2082875139c84c2f3759e40f92341e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37290869"
---
# <a name="view-integration-services-packages-in-sql-server-management-studio-ssis-service"></a>Visualizzare pacchetti di Integration Services in SQL Server Management Studio (servizio SSIS)
    
> [!IMPORTANT]  
>  In questo argomento viene illustrato il servizio [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , un servizio Windows per la gestione dei pacchetti di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] supporta il servizio per la compatibilità con le versioni precedenti di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. A partire da [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], è possibile gestire oggetti come i pacchetti del server Integration Services.  
  
 In questo argomento viene descritta la procedura per la connessione a [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] e la visualizzazione di un elenco dei pacchetti gestiti dal servizio [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
### <a name="to-connect-to-integration-services"></a>Per connettersi a Integration Services  
  
1.  Fare clic sul pulsante **Start**, scegliere **Tutti i programmi**, **Microsoft SQL Server**, quindi **SQL Server Management Studio**.  
  
2.  Nella finestra di dialogo **Connetti al server** selezionare **Integration Services** dall'elenco **Tipo server** , specificare il nome del server nella finestra di dialogo **Nome server** e quindi fare clic su **Connetti**.  
  
    > [!IMPORTANT]  
    >  Se non è possibile stabilire la connessione con [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], è probabile che il servizio [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] non sia in esecuzione. Per informazioni sullo stato del servizio, fare clic sul pulsante **Start**, scegliere **Tutti i programmi**, **Microsoft SQL Server**, **Strumenti di configurazione**, quindi fare clic su **Gestione configurazione SQL Server**. Nel riquadro di sinistra fare clic su **Servizi di SQL Server**. Nel riquadro di destra cercare il servizio [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Se non è già in esecuzione, avviare il servizio.  
  
     [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] si apre. Per impostazione predefinita, la finestra Esplora oggetti viene aperta e posizionata nell'angolo inferiore sinistro del programma. Se Esplora oggetti non viene visualizzato, scegliere **Esplora oggetti** dal menu **Visualizza** .  
  
### <a name="to-view-the-packages-that-integration-services-service-manages"></a>Per visualizzare i pacchetti gestiti da Integration Services  
  
1.  In Esplora oggetti espandere la cartella Pacchetti archiviati.  
  
2.  Espandere le sottocartelle di Pacchetti archiviati per visualizzare i pacchetti.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione dei pacchetti &#40;servizio SSIS&#41;](service/package-management-ssis-service.md)   
 [Utilizzo di SQL Server Management Studio](../database-engine/use-sql-server-management-studio.md)  
  
  

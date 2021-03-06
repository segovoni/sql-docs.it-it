---
title: Visualizzare i facet della gestione basata su criteri in un oggetto di SQL Server | Microsoft Docs
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
helpviewer_keywords:
- Policy-Based Management, view facets
ms.assetid: 5f423b9f-a6c4-41a7-9d8d-8f4926ce1fb4
caps.latest.revision: 7
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 860ffb36a0a4a51f5f4a3076abcabc193f56e081
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32953196"
---
# <a name="view-the-policy-based-management-facets-on-a-sql-server-object"></a>Visualizzare i facet della gestione basata su criteri in un oggetto di SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  In questo argomento verrà descritto come visualizzare tutti i facet della gestione basata su criteri applicati a un oggetto specifico di SQL Server in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Security](#Security)  
  
-   **Per visualizzare tutti i facet in un oggetto tramite:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
 È necessaria l'appartenenza al ruolo PolicyAdministratorRole nel database msdb.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-view-all-of-the-facets-in-an-object"></a>Per visualizzare tutti i facet in un oggetto  
  
1.  In Esplora oggetti fare clic con il pulsante destro del mouse su un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], su un oggetto istanza, su un database o su un oggetto di database, quindi scegliere **Facet**.  
  
2.  Nella finestra di dialogo **Visualizza facet -**nome_oggetto* selezionare un facet nell'elenco **Facet** per visualizzarne le proprietà. Per ulteriori informazioni sulle opzioni disponibili in questa finestra di dialogo, vedere [View Facets Dialog Box](../../relational-databases/policy-based-management/view-facets-dialog-box.md).  
  
3.  Al termine, fare clic su **OK**.  
  
  

---
title: Finestra di dialogo Versioni progetto | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.isprojectprop.versions.f1
ms.assetid: a48a387c-2e70-45bc-be2e-26e57a9bb2c4
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 47a5330398b0a29731376a6387695b220bcb4b93
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37197521"
---
# <a name="project-versions-dialog-box"></a>Finestra di dialogo Versioni progetto
  Utilizzare la finestra di dialogo **Versioni di progetto** per visualizzare le versioni di un progetto e per ripristinare una versione precedente.  
  
 È anche possibile visualizzare le versioni precedenti nella vista [catalog.object_versions &#40;database SSISDB&#41;](/sql/integration-services/system-views/catalog-object-versions-ssisdb-database) e usare la stored procedure [catalog.restore_project &#40;database SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-restore-project-ssisdb-database) per ripristinare le versioni precedenti.  
  
 **Per saperne di più**  
  
-   [Aprire la finestra di dialogo Versioni di progetto](#open_dialog)  
  
-   [Ripristinare una versione Progetto](#restore)  
  
##  <a name="open_dialog"></a> Aprire la finestra di dialogo Versioni di progetto  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]connettersi al server [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] .  
  
     cioè connettersi all'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] in cui è ospitato il database di [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] .  
  
2.  In Esplora oggetti espandere l'albero per visualizzare il nodo dei **cataloghi di Integration Services** .  
  
3.  Espandere il nodo **Cataloghi di Integration Services** per visualizzare il nodo **SSISDB** .  
  
4.  Nel nodo **SSISDB** sono contenute una o più cartelle in cui sono inclusi uno o più progetti. Espandere la cartella contenente il progetto a cui si è interessati.  
  
5.  Fare clic con il pulsante destro del mouse sul progetto e quindi scegliere **Versioni**.  
  
 Nella tabella **Versioni** della finestra di dialogo **Versioni progetto** viene visualizzato l'elenco di versioni del progetto che sono state distribuite nel server, con la data e l'ora di distribuzione della versione, la data e l'ora di ripristino della versione (se questa operazione è stata effettuata), la descrizione della versione e un identificatore di versione. La versione attualmente attiva viene indicata con un segno di spunta nella colonna **Corrente** della tabella.  
  
##  <a name="restore"></a> Ripristinare una versione Progetto  
 Per ripristinare una versione precedente di un progetto, selezionare la versione nella tabella **Versioni** , quindi fare clic su **Ripristina versione selezionata**. Il progetto viene ripristinato alla versione selezionata e quella versione viene indicata con un segno di spunta nella colonna **Corrente** della tabella **Versioni** .  
  
  

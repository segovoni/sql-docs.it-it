---
title: Importare i criteri della gestione basata su criteri | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, import policy
ms.assetid: 850b7ef9-d2b7-4754-bf04-7cb419ffb776
caps.latest.revision: 10
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 40c9e6e32cebd7811a57ae1b8154fb446d8f90e4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37302311"
---
# <a name="import-a-policy-based-management-policy"></a>Importare i criteri della gestione basata su criteri
  In questo argomento verrà descritto come importare un'istanza dei criteri della gestione basata su criteri in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
     [Security](#Security)  
  
-   **Per importare un'istanza dei criteri tramite:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sono inclusi criteri che possono essere utilizzati per monitorare un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per impostazione predefinita, questi criteri non vengono installati nel [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], ma possono essere importati dal percorso predefinito C:\Programmi\Microsoft SQL Server\120\Tools\Policies\DatabaseEngine\1033.  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
 È necessaria l'appartenenza al ruolo PolicyAdministratorRole nel database msdb.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-import-a-policy-instance"></a>Per importare un'istanza dei criteri  
  
1.  In **Esplora oggetti**fare clic sul segno più per espandere il server in cui si troverà l'istanza dei criteri appena importata.  
  
2.  Fare clic sul segno più per espandere la cartella **Gestione** .  
  
3.  Fare clic sul segno più per espandere la cartella **Gestione criteri**.  
  
4.  Fare clic con il pulsante destro del mouse sulla cartella **Criteri** e selezionare **Importa criteri**.  
  
5.  Nella finestra di dialogo **Importa** digitare il percorso e il nome del file oppure usare il pulsante Sfoglia (**...**) per trovare il file XML che contiene i criteri, quindi selezionare il file. Per ulteriori informazioni sulle opzioni disponibili nella finestra di dialogo **Importa** , vedere [Import Policies Dialog Box](import-policies-dialog-box.md).  
  
6.  Al termine, fare clic su **OK**.  
  
  

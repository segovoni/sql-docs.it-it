---
title: Concedere le autorizzazioni al servizio Integration Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 0c2caa68-7834-4ea0-bd77-4f3a7c86d634
caps.latest.revision: 7
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4de544925778a159fd16deb54833b1d94cf5d232
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37158612"
---
# <a name="grant-permissions-to-integration-services-service"></a>Concessione di autorizzazioni al servizio Integration Services
  Nelle versioni precedenti di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], per impostazione predefinita quando si installa [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] tutti gli utenti nel gruppo Utenti dispongono di accesso al servizio [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Quando si installa la versione corrente di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], gli utenti non dispongono di accesso al servizio [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Il servizio è protetto per impostazione predefinita. Dopo avere installato [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , l'amministratore deve concedere l'accesso al servizio.  
  
### <a name="to-grant-access-to-the-integration-services-service"></a>Per concedere l'accesso al servizio Integration Services  
  
1.  Eseguire Dcomcnfg.exe. Dcomcnfg.exe fornisce un'interfaccia utente per la modifica di determinate impostazioni del Registro di sistema.  
  
2.  Nella finestra di dialogo **Servizi componenti** espandere il nodo > Computer > Risorse del computer > Config DCOM.  
  
3.  Fare doppio clic su **Microsoft SQL Server Integration Services 12.0**, quindi fare clic su **proprietà**.  
  
4.  Nella scheda **Sicurezza** della finestra **Autorizzazioni di esecuzione e attivazione** fare clic su **Modifica** .  
  
5.  Aggiungere utenti e assegnare le autorizzazioni appropriate, quindi scegliere OK.  
  
6.  Ripetere i passaggi 4 e 5 per le autorizzazioni di accesso.  
  
7.  Riavviare SQL Server Management Studio.  
  
8.  Riavviare il servizio [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
  

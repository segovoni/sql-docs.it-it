---
title: Procedura di gestione di un servizio CDC locale | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 7f9be649-cd93-40c1-bc48-0480106f207c
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 1d913d41b9a94e0dbc407b64f23c382bdbded6c1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37187174"
---
# <a name="how-to-manage-a-local-cdc-service"></a>Procedura di gestione di un servizio CDC locale
  In questa procedura viene illustrato come utilizzare CDC Service Configuration Console per gestire servizi CDC specifici.  
  
### <a name="to-manage-a-specific-cdc-service"></a>Per gestire un servizio CDC specifico  
  
1.  Dal menu **Start** , selezionare **CDC Service Configuration for Oracle**.  
  
2.  Dal riquadro sinistro di CDC Service Configuration Console, espandere **Local CDC Services**.  
  
3.  Selezionare il servizio CDC che si desidera utilizzare.  
  
     È inoltre possibile fare clic con il pulsante destro del mouse sul servizio CDC da utilizzare e selezionare l'azione desiderata.  
  
     **OPPURE**  
  
     Selezionare **Local CDC Services** dal riquadro sinistro di CDC Service Configuration Console, quindi selezionare quindi il servizio che si desidera utilizzare dalla sezione centrale della console di configurazione del servizio CDC.  
  
     È inoltre possibile fare clic con il pulsante destro del mouse sul servizio CDC da utilizzare e selezionare l'azione desiderata.  
  
4.  Quando si utilizza un servizio CDC è possibile eseguire le attività seguenti:  
  
    -   **Eliminare il servizio**  
  
         Dal riquadro **Actions** sul lato destro di CDC Service Configuration Console, fare clic su **Delete** per eliminare il servizio.  
  
         È inoltre possibile fare clic con il pulsante destro del mouse sul servizio CDC da eliminare e scegliere **Delete**.  
  
         **Nota**: se il servizio è in esecuzione al momento dell'eliminazione, il servizio viene arrestato prima di essere eliminato.  
  
         Per eliminare una definizione del servizio Windows di Oracle CDC, è necessario aggiornare l'accesso al database MSXDBCDC nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] associata. Quando si fa clic su **OK** per eliminare il servizio, viene effettuato un tentativo di eliminare la registrazione del servizio Oracle CDC nel database MSXDBCDC. Se l'operazione ha esito negativo a causa della mancanza di autorizzazioni, verrà visualizzata una finestra di dialogo in cui viene richiesto all'utente di immettere un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con un accesso di aggiornamento al database MSXDBCDC.  
  
         Per informazioni sui dati da immettere nella finestra di dialogo Connect to SQL Server, vedere [Manage an Oracle CDC Service](manage-an-oracle-cdc-service.md) e [Connection to SQL Server for Delete](connection-to-sql-server-for-delete.md).  
  
    -   **Modificare le proprietà del servizio CDC**  
  
         Dal riquadro **Actions** sul lato destro di CDC Service Configuration Console, fare clic su **Properties**.  
  
         È inoltre possibile fare clic con il pulsante destro del mouse sul servizio CDC in cui si desidera modificare le proprietà e scegliere **Properties**.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestire un servizio Oracle CDC](manage-an-oracle-cdc-service.md)  
  
  

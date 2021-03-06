---
title: Requisiti del database (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: fe731839-c5c4-4884-bb6a-644eca28bb30
caps.latest.revision: 13
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 8ae9989f2ca04e0d0beb2d246fbea4d47fcf3a6b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37193398"
---
# <a name="database-requirements-master-data-services"></a>Requisiti del database (Master Data Services)
  Tutti i dati master vengono archiviati in un database [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] . Nel computer che ospita questo database deve essere eseguita un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
 Utilizzare [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] per creare e configurare il database [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] in un computer locale o remoto. Se si sposta il database da un ambiente a un altro, è possibile gestire le informazioni in un nuovo ambiente associando il servizio Web [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] e [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] al database nella nuova posizione.  
  
> [!NOTE]  
>  Tutti i computer in cui si installano componenti di [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] devono essere dotati di licenza appropriata. Per ulteriori informazioni, fare riferimento al Contratto di licenza.  
  
## <a name="requirements"></a>Requisiti  
 Prima di creare un database [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] , assicurarsi che vengano soddisfatti i requisiti seguenti.  
  
### <a name="sql-server-edition"></a>Edizione di SQL Server  
 Il database [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] può essere ospitato nelle seguenti edizioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence (64-bit) x64  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise (64-bit) x64  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Developer (64-bit) x64  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Business Intelligence (64-bit) x64  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Enterprise (64 bit) x64 - Aggiornamento solo da [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Enterprise  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Developer (64-bit) x64  
  
-   Microsoft SQL Server 2008 R2 Enterprise (64 bit) x64  
  
-   Microsoft SQL Server 2008 R2 Developer (64 bit) x64  
  
 Per un elenco delle funzionalità supportate dalle edizioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
### <a name="operating-system"></a>Sistema operativo  
 Per informazioni sui sistemi operativi Windows supportati e altri requisiti per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)], vedere [Hardware and Software Requirements for Installing SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).  
  
### <a name="accounts-and-permissions"></a>Account e autorizzazioni  
  
|Tipo|Description|  
|----------|-----------------|  
|Account utente|Per ospitare il database [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)], in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è possibile usare un account di Windows o un account di [!INCLUDE[ssDE](../../includes/ssde-md.md)] per connettersi all'istanza del [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] . È necessario che l'account utente appartenga al ruolo server **sysadmin** nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Per altre informazioni sul ruolo **sysadmin** , vedere [Ruoli a livello di server](../../relational-databases/security/authentication-access/server-level-roles.md).|  
|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] account amministratore|Quando si crea un database [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] , è necessario specificare un account utente di dominio con il ruolo di amministratore di sistema di [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] . Per tutte le applicazioni Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] associate a questo database, tale utente può aggiornare i modelli e i dati in tutte le aree funzionali. Per altre informazioni, vedere [Administrators &#40;Master Data Services&#41;](../administrators-master-data-services.md).|  
  
### <a name="database-backup"></a>Backup del database  
 In base alla procedura consigliata, eseguire il backup dell'intero database quotidianamente in un momento di bassa attività ed eseguire il backup dei log delle transazioni con maggiore frequenza a seconda delle necessità dell'ambiente. Per altre informazioni sui backup di database, vedere [Panoramica del backup &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-overview-sql-server.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Installare Master Data Services](install-master-data-services.md)   
 [Creare un database Master Data Services](create-a-master-data-services-database.md)   
 [Master Data Services Database](../master-data-services-database.md)   
 [Finestra di dialogo Connessione a un database Master Data Services](../connect-to-a-master-data-services-database-dialog-box.md)   
 [Procedura guidata Crea database &#40;Gestione configurazione Master Data Services&#41;](../create-database-wizard-master-data-services-configuration-manager.md)  
  
  

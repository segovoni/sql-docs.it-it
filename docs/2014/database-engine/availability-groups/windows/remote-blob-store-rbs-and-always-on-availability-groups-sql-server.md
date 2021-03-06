---
title: Store Blob remoti (RBS) e i gruppi di disponibilità AlwaysOn (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 01a70258-d4fd-40bc-bc44-c490b5d6c420
caps.latest.revision: 13
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 55f604d9c85cd93baa564a0bd5a99a483f310fdb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37169329"
---
# <a name="remote-blob-store-rbs-and-alwayson-availability-groups-sql-server"></a>Archivio BLOB remoti (RBS) e gruppi di disponibilità AlwaysOn (SQL Server)
  [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] offre una soluzione di disponibilità elevata e di ripristino di emergenza per gli oggetti BLOB dell'[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][archivio BLOB remoto](../../../relational-databases/blob/remote-blob-store-rbs-sql-server.md) (RBS, Remote Blob Store). [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] protegge tutti i metadati e gli schemi di RBS archiviati in un database di disponibilità replicandoli nelle repliche secondarie. Questo è il database del contenuto di SharePoint. In generale, tramite [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] questi metadati di RBS vengono archiviati in modo indipendente dal BLOB.  
  
 La protezione dei dati BLOB di RBS dipende dal percorso dell'archivio BLOB, come riportato di seguito:  
  
|Percorso dell'archivio BLOB|Possibilità di protezione dei dati BLOB tramite i gruppi di disponibilità|  
|-------------------------|-----------------------------------------------------|  
|Stesso database in cui sono contenuti i metadati di RBS (archiviato utilizzando un provider FILESTREAM remoto di RBS)|Sì|  
|Database diverso nella stessa istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (archiviato utilizzando un provider FILESTREAM remoto di RBS)|Sì<br /><br /> È consigliabile inserire questo database nello stesso gruppo di disponibilità del database in cui sono contenuti i metadati di RBS.|  
|Database diverso in un'istanza differente di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (archiviato utilizzando un provider FILESTREAM remoto di RBS)|Sì<br /><br /> Questo database deve trovarsi in un gruppo di disponibilità separato.|  
|Archivio BLOB di terze parti|no<br /><br /> Per proteggere questi dati BLOB, utilizzare i meccanismi di disponibilità elevata del provider dell'archivio BLOB.|  
  
##  <a name="Limitations"></a> Limitazioni  
  
-   I gestori RBS devono essere indirizzati alla replica primaria.  
  
##  <a name="Recommendations"></a> Indicazioni  
  
-   Utilizzare un listener del gruppo di disponibilità. Per altre informazioni, vedere [Listener del gruppo di disponibilità, connettività client e failover dell'applicazione &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md).  
  
##  <a name="RelatedContent"></a> Contenuto correlato  
  
-   [Maintaining Remote BLOB Store](http://msdn.microsoft.com/library/gg316773\(SQL.105\).aspx) (Gestione dell'archivio BLOB remoti) in [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] Documentazione online  
  
-   [Running RBS Maintainer](http://blogs.msdn.com/b/sqlrbs/archive/2010/03/19/running-rbs-maintainer.aspx) (Esecuzione di Gestore RBS) (blog)  
  
-   [Configure Remote BLOB Storage (RBS) with the FILESTREAM provider (SharePoint 2010)](http://blogs.msdn.com/b/mvpawardprogram/archive/2012/04/02/configure-remote-blob-storage-rbs-with-the-filestream-provider-sharepoint-2010.aspx) (Configurare l'archivio BLOB remoti (RBS) con il provider FILESTREAM (SharePoint 2010)) (blog)  
  
## <a name="see-also"></a>Vedere anche  
 [Connettività Client AlwaysOn &#40;SQL Server&#41;](always-on-client-connectivity-sql-server.md)   
 [Archivio BLOB remoto &#40;RBS&#41; &#40;SQL Server&#41;](../../../relational-databases/blob/remote-blob-store-rbs-sql-server.md)  
  
  

---
title: Combinazioni supportate di SharePoint e server Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 07/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SharePoint mode
- add-in for sharepoint
- rsSharePoint
ms.assetid: dc6a3372-db26-43f0-b7aa-f725acc635c2
caps.latest.revision: 39
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 006841648398b5d0da8343decdfbfe7b094a8bdf
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35322770"
---
# <a name="supported-combinations-of-sharepoint-and-reporting-services-server"></a>Combinazioni supportate di SharePoint e server Reporting Services

[!INCLUDE [ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE [ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE [ssrs-appliesto-not-2017](../../includes/ssrs-appliesto-not-2017.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE [ssrs-appliesto-not-pbirs](../../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

Un server di report SQL Server Reporting Services installato in modalità SharePoint richiede una versione di SharePoint e il componente aggiuntivo SQL Server Reporting Services (rsSharePoint.msi) per prodotti SharePoint, da installare nei server SharePoint. In questo argomento vengono riepilogate le combinazioni supportate.

> [!NOTE]
> L'integrazione di Reporting Services con SharePoint non è più disponibile nelle versioni successive a SQL Server 2016.

## <a name="supported-combinations-of-sharepoint-and-reporting-services-components"></a>Combinazioni supportate di SharePoint e componenti Reporting Services

 Nella tabella seguente sono riepilogate le combinazioni supportate di server di report, componente aggiuntivo Reporting Services per prodotti SharePoint e prodotti SharePoint. Le combinazioni non elencate nella tabella seguente non sono supportate.

### <a name="supported-combinations"></a>Combinazioni supportate

||Server di report|Componente aggiuntivo|Versione di SharePoint|
|-|-------------------|-------------|------------------------|
|1|SQL Server 2016|SQL Server 2016|SharePoint 2016|
|2|SQL Server 2016|SQL Server 2016|SharePoint 2013|
|3|SQL Server 2014|SQL Server 2014|SharePoint 2013|
|4|SQL Server 2014|SQL Server 2014|SharePoint 2010|
|5|SQL Server 2012 SP3|SQL Server 2014 e SQL Server 2012 SP3|SharePoint 2013|
|6|SQL Server 2012 SP2|SQL Server 2014 e SQL Server 2012 SP2|SharePoint 2013|
|7|SQL Server 2012 SP1|SQL Server 2014 e SQL Server 2012 SP1|SharePoint 2013|
|8|SQL Server 2012 e SQL Server 2012 SP1*|SQL Server 2014|SharePoint 2010|
|9|SQL Server 2012|SQL Server 2012|SharePoint 2010|
|10|SQL Server 2008 R2|SQL Server 2014|SharePoint 2010|
|11|SQL Server 2008 R2|SQL Server 2012 e SQL Server 2012 SP1 o versione successiva|SharePoint 2010|
|12|SQL Server 2008 R2|SQL Server 2008 R2|SharePoint 2010|
|13|SQL Server 2008 R2|SQL Server 2008 SP2|SharePoint 2007|
|14|SQL Server 2008 SP2|SQL Server 2008 R2|SharePoint 2010|
|15|SQL Server 2008 SP2|SQL Server 2008 e SQL Server 2008 SP2|SharePoint 2007|

 *Eccezione: l'integrazione di Power View non è supportata.

 Per i collegamenti alle pagine di download del componente aggiuntivo, vedere [Posizione in cui trovare il componente aggiuntivo Reporting Services per prodotti SharePoint](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).  

 **Altre considerazioni:**

- Assicurarsi di aggiornare tutti i server SharePoint all'interno della farm. Sono inclusi i server front-end Web e i server applicazioni.

- Per il supporto di SharePoint 2016, inclusa l'integrazione di Power View, sono necessari il server di report di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] e la versione del componente aggiuntivo [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] di SQL Server 2016 o versione successiva.

- Per il supporto di SharePoint 2013, inclusa l'integrazione di Power View, sono necessari il server di report di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] e la versione del componente aggiuntivo [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] di SQL Server 2012 SP1 o versione successiva.

- Power View è stato introdotto in SQL Server 2012. L'integrazione di Power View con SharePoint 2010 richiede pertanto la versione SQL Server 2012 o successiva del componente aggiuntivo.

- Il componente aggiuntivo di SQL Server 2008 R2 non è supportato dai server di report SQL Server 2012 o versione successiva. Tramite il programma di installazione essenziale di SharePoint 2010 viene installato automaticamente il componente aggiuntivo di SQL Server 2008 R2. È necessario disinstallarlo prima di installare le versioni più recenti del componente aggiuntivo. L'aggiornamento sul posto del componente aggiuntivo non è supportato.

- **Aggiornamento:** non è possibile eseguire l'aggiornamento sul posto di SharePoint 2010 con il componente aggiuntivo [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] a SharePoint 2013. SharePoint 2013 richiede la versione SQL Server 2012 SP1 o successiva del componente aggiuntivo e del server di report di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Per altre informazioni sull'aggiornamento, vedere [Eseguire l'aggiornamento e la migrazione di Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md).

## <a name="next-steps"></a>Passaggi successivi

 [Posizione in cui trovare il componente aggiuntivo Reporting Services per prodotti SharePoint](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)   
 [Funzionalità supportate dalle edizioni di SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md)   
 [Requisiti hardware e software per l'installazione di SQL Server 2016](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)  

Altre domande? [Visitare il forum su Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)

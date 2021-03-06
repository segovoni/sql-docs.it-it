---
title: Introduzione alla gestione delle eccezioni in Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Web service [Reporting Services], exception handling
- errors [Reporting Services]
- exceptions [Reporting Services]
- Report Server Web service, exception handling
- XML Web service [Reporting Services], exception handling
ms.assetid: 54381870-ce67-482b-aa83-6a838cdbf9b9
caps.latest.revision: 28
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 3c4ff1e27ada53361879335d90daeac5fc4f21be
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37185838"
---
# <a name="introducing-exception-handling-in-reporting-services"></a>Introduzione alla gestione delle eccezioni in Reporting Services
  Se l'applicazione [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] invia al servizio Web ReportServer una richiesta che non può essere elaborata, viene restituita al client un'eccezione SOAP. La gestione delle eccezioni generate dal servizio Web ReportServer costituisce una parte importante dello sviluppo delle applicazioni, in quanto quando si verificano gli errori è possibile restituire agli utenti informazioni utili.  
  
 In questa sezione sono incluse informazioni specifiche sulla gestione delle eccezioni, su come impedire agli utenti di immettere input non valido e su come restituire agli utenti informazioni significative sugli errori. Per informazioni generali sulla gestione delle eccezioni, vedere "Gestione e generazione di eccezioni" nella documentazione di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Gestione delle eccezioni in Reporting Services](handling-exceptions-in-reporting-services.md)|Viene fornita una panoramica delle eccezioni in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] e del ruolo di SOAP nel restituire errori da un servizio Web.|  
|[Procedure consigliate per gestione delle eccezioni in Reporting Services](best-practices/best-practices-for-reporting-services-exception-handling.md)|Vengono forniti consigli sulla gestione delle eccezioni in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].|  
|[Classe SoapException di Reporting Services](soapexception-class/reporting-services-soapexception-class.md)|Descrive la classe **SoapException** in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].|  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di applicazioni mediante il servizio Web e .NET Framework](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
  
  

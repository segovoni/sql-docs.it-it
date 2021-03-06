---
title: Filtri ISAPI rilevati sul sito del server di report (Upgrade Advisor) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ISAPI filters
- report servers [Reporting Services], upgrade issues
ms.assetid: dd30560d-9e16-47c7-ba68-a9743a657e4e
caps.latest.revision: 12
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 448f334fc5a82dea623a12e2ad143725ec11f711
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37268137"
---
# <a name="isapi-filters-detected-on-the-report-server-site-upgrade-advisor"></a>Filtri ISAPI rilevati sul sito del server di report (Upgrade Advisor)
  Sono stati rilevati uno o più filtri ISAPI per il sito Web che ospita le directory virtuali del server di report e di Gestione report. Filtri ISAPI non sono supportati in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Nativo.|  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Description  
 Prima di eseguire l'aggiornamento, verificare se i filtri ISAPI per il sito Web sono utilizzati da applicazioni [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Se il filtro ISAPI non è necessario, è possibile aggiornare il server di report. Verranno creati gli URL predefiniti, senza il supporto per il filtro ISAPI in esecuzione in IIS. Se il filtro ISAPI è necessario, non eseguire l'aggiornamento finché non sarà stata trovata un'alternativa per l'hosting del filtro ISAPI, ad esempio utilizzando ISA Server o continuando a ospitare il filtro ISAPI in IIS. Il server di report supporta ASP.NET HTTPModules come sostituzione per i filtri ISAPI in scenari specifici. Per ulteriori informazioni, vedere la documentazione di ASP.NET in MSDN.  
  
## <a name="corrective-action"></a>Azione correttiva  
 Valutare e utilizzare una soluzione distinta per ospitare i filtri ISAPI richiesti per l'attività di sviluppo.  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento di Reporting Services &#40;Preparazione aggiornamento&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  

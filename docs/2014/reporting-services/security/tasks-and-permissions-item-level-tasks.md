---
title: Attività a livello di elemento | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- item-level tasks [Reporting Services]
ms.assetid: fdeb7bc3-167a-4342-84e3-32e3faa1fa39
caps.latest.revision: 36
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 43da85b3e7435bb3685090ae1f2e80830793b3f8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37150142"
---
# <a name="item-level-tasks"></a>Attività a livello di elemento
  Un'attività a livello di elemento è una raccolta di autorizzazioni correlate a un report, una cartella, un modello di report, una risorsa o un'origine dati condivisa. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] include anche attività a livello di sistema applicabili all'intero sito del server di report. Per altre informazioni, vedere [Attività a livello di sistema](tasks-and-permissions-system-level-tasks.md). Per altre informazioni sulle attività e le autorizzazioni in generale, vedere [attività e autorizzazioni](tasks-and-permissions.md).  
  
> [!NOTE]  
>  Se si gestiscono queste attività a livello di programmazione, è necessario utilizzare metodi che supportano attività a livello di elemento. Per altre informazioni, vedere <xref:ReportService2010.ReportingService2010.ListTasks%2A> e <xref:ReportService2010.ReportingService2010.ListRoles%2A>.  
  
## <a name="permissions-in-item-level-tasks"></a>Autorizzazioni delle attività a livello di elemento  
 Nella tabella seguente vengono elencate le attività a livello di elemento e le relative autorizzazioni e gli elementi ai quali si applicano tali autorizzazioni. L'elenco delle autorizzazioni è puramente informativo e ha lo scopo di offrire una descrizione più precisa delle funzionalità disponibili tramite ogni attività.  
  
 I set di dati condivisi utilizzano lo stesso set di autorizzazioni dei report. Le parti del report utilizzano lo stesso set di autorizzazioni delle risorse.  
  
|Attività|Applicabile all'elemento|Autorizzazioni|  
|----------|---------------------|-----------------|  
|Utilizzo di report|Report|Lettura di contenuto<br /><br /> Lettura delle definizioni dei report<br /><br /> Lettura di proprietà|  
|Utilizzo di report|Set di dati condivisi|Lettura di contenuto<br /><br /> Lettura delle definizioni dei report<br /><br /> Lettura di proprietà|  
|Creazione di report collegati|Report|Creazione di collegamenti<br /><br /> Lettura di proprietà|  
|Gestione di tutte le sottoscrizioni|Report|Lettura di proprietà<br /><br /> Lettura di qualsiasi sottoscrizione<br /><br /> Creazione di qualsiasi sottoscrizione<br /><br /> Eliminazione di qualsiasi sottoscrizione<br /><br /> Aggiornamento di qualsiasi sottoscrizione|  
|Gestione di origini dei dati|Cartelle|Creazione di origini dei dati|  
|Gestione di origini dei dati|Origini dati|Aggiornamento di proprietà<br /><br /> Eliminazione del contenuto di aggiornamento<br /><br /> Lettura di proprietà|  
|Gestione di cartelle|Cartelle|Creazione di cartelle<br /><br /> Eliminazione delle proprietà di aggiornamento<br /><br /> Lettura di proprietà|  
|Gestione di sottoscrizioni individuali|Report|Lettura di proprietà<br /><br /> Creazione di sottoscrizioni<br /><br /> Eliminazione di sottoscrizioni<br /><br /> Lettura di sottoscrizioni<br /><br /> Aggiornamento di sottoscrizioni|  
|Gestione di modelli|Cartelle|Creazione di un modello|  
|Gestione di modelli|Modelli|Lettura di proprietà<br /><br /> Lettura di contenuto<br /><br /> Eliminazione del contenuto di aggiornamento<br /><br /> Lettura di origini dei dati<br /><br /> Aggiornamento di origini dei dati<br /><br /> Lettura dei criteri di autorizzazione degli elementi del modello<br /><br /> Aggiornamento dei criteri di autorizzazione degli elementi del modello<br /><br /> Eliminazione delle proprietà di aggiornamento|  
|Gestione della cronologia dei report|Report|Lettura di proprietà<br /><br /> Creazione della cronologia dei report<br /><br /> Eliminazione della cronologia dei report<br /><br /> Esecuzione dei criteri di lettura<br /><br /> Aggiornamento di criteri<br /><br /> Visualizzazione della cronologia dei report|  
|Gestione di report|Cartelle|Creazione di report<br /><br /> applicabile anche alla creazione di set di dati condivisi|  
|Gestione di report|Report|Lettura di proprietà<br /><br /> Eliminazione delle proprietà di aggiornamento<br /><br /> Aggiornamento di parametri<br /><br /> Lettura di origini dei dati<br /><br /> Aggiornamento di origini dei dati<br /><br /> Lettura delle definizioni dei report<br /><br /> Aggiornamento delle definizioni dei report<br /><br /> Esecuzione dei criteri di lettura<br /><br /> Aggiornamento di criteri|  
|Gestione di report|Set di dati condivisi|Lettura di proprietà<br /><br /> Eliminazione delle proprietà di aggiornamento<br /><br /> Aggiornamento di parametri<br /><br /> Lettura di origini dei dati<br /><br /> Aggiornamento di origini dei dati<br /><br /> Lettura delle definizioni dei report<br /><br /> Aggiornamento delle definizioni dei report<br /><br /> Esecuzione dei criteri di lettura<br /><br /> Aggiornamento di criteri|  
|Gestione di risorse|Cartelle|Creazione di risorse|  
|Gestione di risorse|Risorse|Aggiornamento di proprietà<br /><br /> Eliminazione del contenuto di aggiornamento<br /><br /> Lettura di proprietà|  
|Gestione di risorse|Parti del report|Aggiornamento di proprietà<br /><br /> Eliminazione del contenuto di aggiornamento<br /><br /> Lettura di proprietà|  
|Impostazione della sicurezza per singoli elementi|Report, risorse, origini dei dati, set di dati condivisi, cartelle|Lettura di criteri di sicurezza - Aggiornamento di criteri di sicurezza|  
|Visualizzazione di origini dei dati|Origini dei dati|Lettura di contenuto<br /><br /> Lettura di proprietà|  
|Visualizzazione di cartelle|Cartelle|Lettura di proprietà<br /><br /> Esecuzione e visualizzazione<br /><br /> Visualizzazione della cronologia dei report|  
|Visualizzazione di modelli|Modelli di report|Lettura di proprietà<br /><br /> Lettura di contenuto<br /><br /> Lettura di origini dei dati|  
|Visualizzazione di report|Report|Lettura di contenuto<br /><br /> Lettura di proprietà|  
|Visualizzazione di report|Set di dati condivisi|Lettura di contenuto<br /><br /> Lettura di proprietà|  
|Visualizzazione di risorse|Risorse|Lettura di contenuto<br /><br /> Lettura di proprietà|  
|Visualizzazione di risorse|Parti del report|Lettura di contenuto<br /><br /> Lettura di proprietà|  
  
## <a name="see-also"></a>Vedere anche  
 [Concessione di autorizzazioni in un server di report in modalità nativa](granting-permissions-on-a-native-mode-report-server.md)  
  
  

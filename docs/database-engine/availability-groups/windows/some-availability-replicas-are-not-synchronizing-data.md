---
title: Alcune repliche di disponibilità non stanno sincronizzando i dati | Microsoft Docs
ms.custom: ''
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.swb.agdashboard.agp4synchronizing.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 3db6a569-e942-4321-a0dd-c4ab002087c8
caps.latest.revision: 12
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 12815cbc8cf2734698236aa094307afd4c8f042b
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34769393"
---
# <a name="some-availability-replicas-are-not-synchronizing-data"></a>Alcune repliche di disponibilità non stanno sincronizzando i dati.
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="introduction"></a>Introduzione  
  
|||  
|-|-|  
|**Nome criteri**|Stato di sincronizzazione dei dati delle repliche di disponibilità|  
|**Problema**|Alcune repliche di disponibilità non prevedono la sincronizzazione dei dati.|  
|**Category**|**Avviso**|  
|**Facet**|gruppo di disponibilità|  
  
## <a name="description"></a>Descrizione  
 Questi criteri consentono di eseguire il rollup dello stato di sincronizzazione dei dati di tutte le repliche di disponibilità nel gruppo di disponibilità e di verificare se la sincronizzazione di una qualsiasi replica di disponibilità non funzioni. I criteri si trovano in uno stato non integro se uno degli stati di sincronizzazione dei dati della replica di disponibilità è NON IN SINCRONIZZAZIONE.  
  
 Questi criteri sono in uno stato integro se nessuno degli stati di sincronizzazione dei dati della replica di disponibilità è NON IN SINCRONIZZAZIONE.  
  
> [!NOTE]  
>  Per questa versione di [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], le informazioni sulle possibili cause e le soluzioni sono disponibili in [Alcune repliche di disponibilità non stanno sincronizzando i dati](http://go.microsoft.com/fwlink/p/?LinkId=220852) nella Wiki di TechNet.  
  
## <a name="possible-causes"></a>Possibili cause  
 In questo gruppo di disponibilità, almeno una replica secondaria non si trova nello stato di sincronizzazione NON IN SINCRONIZZAZIONE e non riceve dati dalla replica primaria.  
  
## <a name="possible-solution"></a>Possibile soluzione  
 Utilizzare lo stato dei criteri della replica di disponibilità per trovare la replica di disponibilità con uno stato NON IN SINCRONIZZAZIONE e risolvere il relativo problema.  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica di Gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Usare il dashboard Always On &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  

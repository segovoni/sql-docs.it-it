---
title: Proprietà funzionalità | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQMSupportEnabled property
- ComUdfEnabled property
- LinkToOtherInstanceEnabled property
- ManagedCodeEnabled property
- ConnStringEncryptionEnabled property
- LinkFromOtherInstanceEnabled property
- LinkInsideInstanceEnabled property
- UseCachedPageAllocators property
ms.assetid: a34d046a-6562-4d98-b827-37cebc6d77b4
caps.latest.revision: 20
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2ae26995283bcfa50a33f78ab55536f8aac75453
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37188958"
---
# <a name="feature-properties"></a>Proprietà di funzionalità
  Tramite le proprietà di funzionalità è possibile controllare le funzionalità di un prodotto e, nella maggior parte dei casi, si tratta di proprietà avanzate, comprese le proprietà mediante le quali vengono controllati i collegamenti tra istanze di server.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] supporta le proprietà del server elencate nella tabella seguente. Per altre informazioni sulle proprietà aggiuntive del server e sulla relativa impostazione, vedere [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).  
  
 **Si applica a:** solo in modalità server multidimensionale  
  
## <a name="properties"></a>Proprietà  
  
|Proprietà|Default|Description|  
|--------------|-------------|-----------------|  
|`ManagedCodeEnabled`|1|Proprietà booleana che indica se le procedure di archiviazione CLR sono abilitate.|  
|`LinkInsideInstanceEnabled`|1|Proprietà booleana che indica se è possibile creare un oggetto collegato all'interno della medesima istanza di server.|  
|`LinkToOtherInstanceEnabled`|0|Proprietà booleana che indica se è possibile creare collegamenti a oggetti situati su server remoti.|  
|`LinkFromOtherInstanceEnabled`|0|Proprietà booleana che indica se è possibile stabilire collegamenti ad oggetti da altre istanze di server.|  
|`ConnStringEncryptionEnabled`|1|Proprietà booleana che indica se la stringa di connessione è crittografata nel file di configurazione del server.|  
|`UseCachedPageAllocators`|0|Proprietà booleana che indica se gli allocatori di pagine memorizzati nella cache sono abilitati.|  
|`ComUdfEnabled`|0|Proprietà booleana che indica se le funzioni definite dall'utente come oggetti COM sono abilitate.|  
|`SQMSupportEnabled`|1|Proprietà booleana che indica se le segnalazioni sugli errori e sull'uso delle funzionalità vengono inviate automaticamente a [!INCLUDE[msCoName](../../includes/msconame-md.md)] .|  
|`ResourceMonitoringEnabled`|1|Proprietà booleana che indica se i contatori di monitoraggio delle risorse interne sono abilitati. Questa proprietà è attivata per impostazione predefinita. Quando è abilitata, la proprietà contente ai contatori di raccogliere dati di utilizzo relativi a CPU, memoria e attività di I/O.<br /><br /> I contatori di monitoraggio delle risorse interne vengono utilizzati dalle DMV (viste a gestione dinamica) per la creazione di report sull'utilizzo delle risorse. Se si disabilita questa proprietà, le query DMV continueranno a essere eseguite, tuttavia il set di risultati non sarà valido. Tra le DMV che dipendono da questa proprietà sono incluse le seguenti:<br />**DISCOVER_OBJECT_ACTIVITY**<br />**DISCOVER_COMMAND_OBJECTS**<br />**DISCOVER_SESSIONS** (per SESSION_READS, SESSION_WRITES, SESSION_CPU_TIME_MS)<br /><br /> <br /><br /> Su un sistema multicore che utilizza l'architettura NUMA, la disabilitazione di questa proprietà può migliorare le prestazioni di esecuzione delle query, specialmente per carichi di lavoro multiutente elevati. Sarà necessario eseguire test di confronto per determinare se le prestazioni di esecuzione delle query vengono migliorate a seguito della modifica di questa proprietà. Per le procedure consigliate su come eseguire test di confronto, inclusi la cancellazione della cache e il modo di evitare errori comuni, vedere la pagina relativa alla [Guida operativa di SQL Server 2008 R2 Analysis Services](http://go.microsoft.com/fwlink/?LinkID=225539).|  
  
## <a name="see-also"></a>Vedere anche  
 [Configurare le proprietà del Server in Analysis Services](server-properties-in-analysis-services.md)   
 [Determinare la modalità Server di un'istanza di Analysis Services](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)   
 [Usare le viste a gestione dinamica &#40;viste a gestione dinamica&#41; per monitorare Analysis Services](../instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)  
  
  

---
title: Disabilitare l'opzione lightweight pooling | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: performance-monitor
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 481bb43d-6fe5-497c-9096-971fb6bf733b
caps.latest.revision: 13
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 883b864c630587282d14734b2d7000fefa6077b0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32952016"
---
# <a name="disable-lightweight-pooling"></a>Disabilitazione di lightweight pooling
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Questa regola consente di controllare che l'opzione lightweight pooling sia disabilitata nel server. Se si imposta lightweight pooling su 1, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] passerà alla pianificazione in modalità fiber. La modalità fiber deve essere utilizzata in situazioni specifiche in cui il cambio di contesto dei thread di lavoro UMS costituisce un importante collo di bottiglia per le prestazioni. Poiché questa situazione è poco frequente, la modalità fiber consente raramente di ottimizzare le prestazioni o la scalabilità in un sistema tipico.  
  
## <a name="best-practices-recommendations"></a>Procedure consigliate  
 L'opzione lightweightpooling deve essere abilitata solo in seguito a test approfonditi, dopo avere valutato tutte le altre possibilità di ottimizzazione delle prestazioni, e quando il cambio del contesto è un problema noto nell'ambiente.  
  
 È consigliabile evitare di utilizzare la pianificazione in modalità fiber per operazioni di routine, in quanto può ridurre le prestazioni impedendo i normali vantaggi derivati dal cambio del contesto e perché alcuni componenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che utilizzano TLS (Thread Local Storage) o oggetti di proprietà del thread, ad esempio i mutex (un tipo di oggetto kernel Win32), non possono funzionare correttamente in modalità fiber.  
  
 Per rimuovere l'opzione lightweight pooling, eseguire l'istruzione seguente, quindi riavviare il [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
```sql  
sp_configure 'show advanced options', 1;  
GO  
sp_configure 'lightweight pooling', 0;  
GO  
RECONFIGURE;  
GO  
```  
  
## <a name="for-more-information"></a>Ulteriori informazioni  
 [Opzione di configurazione del server lightweight pooling](../../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Monitorare e applicare le procedure consigliate tramite la gestione basata su criteri](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  

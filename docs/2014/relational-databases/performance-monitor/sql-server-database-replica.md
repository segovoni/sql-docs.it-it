---
title: SQL Server, Database Replica | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- SQLServer:Database Replica
- performance counters [SQL Server], AlwaysOn Availability Groups
- Availability Groups [SQL Server], performance counters
ms.assetid: a5f6bdce-2b13-4924-aaeb-b50b57d624d8
caps.latest.revision: 25
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: ff7159adceda1953433b2869fd5d5e05a0b91b94
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37233111"
---
# <a name="sql-server-database-replica"></a>SQL Server, replica di database
  L'oggetto prestazioni **SQLServer:Database Replica** contiene contatori delle prestazioni che forniscono informazioni sui database secondari di un gruppo di disponibilità AlwaysOn in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Questo oggetto è valido solo su un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che ospita una replica secondaria.  
  
|Nome contatore|Description|Contenuto in...|  
|------------------|-----------------|--------------|  
|**Byte file ricevuti/sec**|Quantità di dati FILESTREAM ricevuti dalla replica secondaria per il database secondario nell'ultimo secondo.|Replica secondaria|  
|**Byte log ricevuti/sec**|Quantità di record del log ricevuti dalla replica secondaria per il database nell'ultimo secondo.|Replica secondaria|  
|**Log rimanente per il rollback**|La quantità di log in KB che deve ancora completare la fase di rollback.|Replica secondaria|  
|**Coda invii log**|Quantità di record di log nei file di log del database primario che non sono stati inviati alla replica secondaria (in KB). Questo valore viene inviato alla replica secondaria dalla replica primaria. Le dimensioni della coda non includono file FILESTREAM inviati a un database secondario.|Replica secondaria|  
|**Transazioni di scrittura con mirroring/sec**|Numero di transazioni che sono state scritte nel database primario e il cui commit viene eseguito solo quando il log è stato inviato al database secondario nell'ultimo secondo.|Replica primaria|  
|**Coda di recupero**|Quantità di record del log nei file di log della replica secondaria che non sono ancora stati sottoposti a rollforward.|Replica secondaria|  
|**Blocchi rollforward/sec**|Numero di volte in cui il thread fase di rollforward viene bloccato nei blocchi utilizzati dai lettori del database.|Replica secondaria|  
|**Byte rollforward rimanenti**|Quantità di log in KB che deve essere ripetuta per completare la fase di ripristino.|Replica secondaria|  
|**Byte di cui è stato eseguito il rollforward/sec**|Quantità di record del log sottoposti a rollforward nel database secondario nell'ultimo secondo.|Replica secondaria|  
|**Totale log per cui è necessario il rollback**|Kilobyte di log totali che devono essere annullati.|Replica secondaria|  
|**Ritardo transazioni**|Periodo di attesa in millisecondi dell'acknowledgement per un commit senza terminazione.|Replica primaria|  
  
## <a name="see-also"></a>Vedere anche  
 [Monitoraggio dell'utilizzo delle risorse &#40;Monitor di sistema&#41;](monitor-resource-usage-system-monitor.md)   
 [SQL Server, replica di disponibilità](sql-server-availability-replica.md)   
 [SQL Server, oggetto di database](sql-server-databases-object.md)   
 [Gruppi di disponibilità AlwaysOn (SQL Server)](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)  
  
  

---
title: Analisi di flusso di dati | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 5654cb30-cad2-470c-97b3-59cb331033e5
caps.latest.revision: 10
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: fa09e2c86581214a1ae001c90dba640276920aba
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37209841"
---
# <a name="analysis-of-data-flow"></a>Analisi del flusso di dati
  È possibile usare la [execution_data_statistics](../relational-databases/statistics/statistics.md) `SSISDB` vista per analizzare il flusso di dati dei pacchetti di database. In questa vista viene visualizzata una riga ogni volta che un componente del flusso di dati invia dati a un componente a valle. Le informazioni possono essere utilizzate per acquisire una comprensione più approfondita delle righe inviate a ciascun componente.  
  
> [!NOTE]  
>  Il livello di registrazione deve essere impostato su **Dettagliato** per acquisire informazioni con la vista catalog.execution_data_statistics.  
  
 Nell'esempio seguente viene visualizzato il numero di righe inviate tra i componenti di un pacchetto.  
  
```  
use SSISDB  
select package_name, task_name, source_component_name, destination_component_name, rows_sent  
from catalog.execution_data_statistics  
where execution_id = 132  
order by source_component_name, destination_component_name  
  
```  
  
 Nell'esempio seguente viene calcolato il numero di righe per millisecondi inviate da ogni componente per un'esecuzione specifica. I valori calcolati sono:  
  
-   **total_rows** : somma di tutte le righe inviate dal componente  
  
-   **wall_clock_time_ms** : tempo totale di esecuzione trascorso, in millisecondi, per ogni componente  
  
-   **num_rows_per_millisecond** : numero di righe per millisecondi inviate da ogni componente  
  
 Il `HAVING` clausola viene utilizzata per impedire un errore di divisione per zero nei calcoli.  
  
```  
use SSISDB  
select source_component_name, destination_component_name,  
    sum(rows_sent) as total_rows,  
    DATEDIFF(ms,min(created_time),max(created_time)) as wall_clock_time_ms,  
    ((0.0+sum(rows_sent)) / (datediff(ms,min(created_time),max(created_time)))) as [num_rows_per_millisecond]  
from [catalog].[execution_data_statistics]  
where execution_id = 132  
group by source_component_name, destination_component_name  
having (datediff(ms,min(created_time),max(created_time))) > 0  
order by source_component_name desc  
  
```  
  
## <a name="related-tasks"></a>Related Tasks  
 [Debug di un flusso di dati](troubleshooting/debugging-data-flow.md)  
  
 [Strumenti per la risoluzione dei problemi relativi all'esecuzione dei pacchetti](troubleshooting/troubleshooting-tools-for-package-execution.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Dati nei flussi di dati](data-flow/data-in-data-flows.md)  
  
  

---
title: Procedure consigliate per chiamare stored procedure compilate in modo nativo | Microsoft Docs
ms.custom: ''
ms.date: 03/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: in-memory-oltp
ms.reviewer: ''
ms.suite: sql
ms.technology: in-memory-oltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f39fc1c7-cfec-4a95-97f6-6b95954694bb
caps.latest.revision: 8
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: d52f34dc2eea6d5b0fa09e08e20ebe1fb7704478
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2018
ms.locfileid: "34327652"
---
# <a name="best-practices-for-calling-natively-compiled-stored-procedures"></a>Procedure consigliate per chiamare stored procedure compilate in modo nativo
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Le stored procedure compilate in modo nativo:  
  
-   Vengono in genere utilizzate nelle parti critiche per le prestazioni di un'applicazione.  
  
-   Vengono eseguite di frequente.  
  
-   Devono essere molto veloci.  
  
 Il vantaggio a livello di prestazioni garantito dall'utilizzo di una stored procedure compilata in modo nativo aumenta con il numero di righe e la quantità di logica elaborata dalla procedura. Ad esempio, tramite una stored procedure compilata in modo nativo vengono garantite prestazioni migliori se si utilizzato uno o più degli elementi seguenti:  
  
-   Aggregazione.  
  
-   Join a cicli annidati.  
  
-   Operazioni di selezione, inserimento, aggiornamento ed eliminazione a più istruzioni.  
  
-   Espressioni complesse.  
  
-   Logica procedurale, ad esempio cicli e istruzioni condizionali.  
  
 Se è necessario elaborare una sola riga, l'utilizzo di una stored procedure compilata in modo nativo non può garantire un vantaggio in termini di prestazioni.  
  
 Per evitare che nel server debbano essere eseguiti il mapping dei nomi di parametro e la conversione dei tipi:  
  
-   Associare i tipi dei parametri passati alla stored procedure ai tipi nella definizione della stored procedure.  
  
-   Utilizzare i parametri ordinali (senza nome) per chiamare le stored procedure compilate in modo nativo. Per un'esecuzione ottimale, non utilizzare parametri denominati.  
  
 Le inefficienze nei parametri con stored procedure compilate in modo nativo può essere rilevato tramite l'XEvent **natively_compiled_proc_slow_parameter_passing**:
 - Tipi non corrispondenti: **reason=parameter_conversion**
 - Parametri denominati: **reason=named_parameters**
 - Valori predefiniti: **reason=default** 
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure compilate in modo nativo](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)  

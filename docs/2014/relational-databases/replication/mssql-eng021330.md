---
title: MSSQL_ENG021330 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021330 error
ms.assetid: e2bb2e21-62a7-4689-b68b-bdfba3fdd985
caps.latest.revision: 15
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7df836fad489994de9dd218e2aee9edde67a688d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37246361"
---
# <a name="mssqleng021330"></a>MSSQL_ENG021330
    
## <a name="message-details"></a>Dettagli messaggio  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|21330|  
|Origine evento|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nome simbolico||  
|Testo del messaggio|Impossibile creare una sottodirectory nella directory di lavoro della replica.(%1!)|  
  
## <a name="explanation"></a>Spiegazione  
 Questo errore si può verificare quando una sottoscrizione viene inizializzata manualmente e si riscontra un problema nella creazione della directory di archiviazione degli script di replica. L'errore può essere causato da un problema relativo alle autorizzazioni: quando una sottoscrizione viene inizializzata senza utilizzare uno snapshot, l'account con cui il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene eseguito nel server di pubblicazione deve disporre di autorizzazioni di scrittura per la cartella snapshot nel server di distribuzione.  
  
## <a name="user-action"></a>Azione dell'utente  
 Verificare che sia stato specificato il percorso corretto della cartella snapshot e che l'account con cui il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene eseguito nel server di pubblicazione disponga di autorizzazioni sufficienti.  
  
## <a name="see-also"></a>Vedere anche  
 [Specificare la posizione predefinita degli snapshot &#40;SQL Server Management Studio&#41;](specify-the-default-snapshot-location-sql-server-management-studio.md)   
 [Guida di riferimento a errori ed eventi &#40;replica&#41;](errors-and-events-reference-replication.md)   
 [Inizializzare una sottoscrizione transazionale senza uno snapshot](initialize-a-transactional-subscription-without-a-snapshot.md)  
  
  

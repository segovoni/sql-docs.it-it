---
title: Servizi Desktop remoto restituisce &quot;flusso non lettura&quot; errore | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- stream not read error in RDS [ADO]
ms.assetid: cb5a68f8-dba4-41da-bafd-04efe53706b7
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d3c1c5b3bdb64b61d6a8b8483069701c89c53252
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35274050"
---
# <a name="rds-returns-quotstream-not-readquot-error"></a>Servizi Desktop remoto restituisce &quot;flusso non lettura&quot; errore
"L'oggetto di flusso di lettura perché è vuoto o la posizione corrente si trova alla fine del flusso. Per i flussi non vuoto, impostare la posizione corrente con la proprietà posizione. Per determinare se il flusso è vuoto, controllare la proprietà di dimensione."  
  
 Se viene visualizzato questo messaggio di errore, si è tentato di utilizzare una query con parametri gerarchica su http. Servizi Desktop remoto non consente di utilizzare remote gerarchie con parametri.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="see-also"></a>Vedere anche  
 [Nozioni fondamentali su RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)



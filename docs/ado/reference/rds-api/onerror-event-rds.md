---
title: Evento onError (RDS) | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- onError event [ADO]
ms.assetid: b01cbc62-fbd7-4068-b16c-8b0f80a05887
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 470ed14f132233eb4bec6d58ac17c4d3c492b94e
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35288441"
---
# <a name="onerror-event-rds"></a>Evento onError (RDS)
Il **onError** eventi viene chiamato ogni volta che si verifica un errore durante un'operazione.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
onError SCode, Description, Source, CancelDisplay  
```  
  
#### <a name="parameters"></a>Parametri  
 *SCode*  
 Valore intero che indica il codice di stato dell'errore.  
  
 *Descrizione*  
 Oggetto **stringa** che indica una descrizione dell'errore.  
  
 *Origine*  
 Oggetto **stringa** che indica la query o un comando che ha causato l'errore.  
  
 *CancelDisplay*  
 Oggetto **booleano** valore, se impostato su **True**, che impedisce la visualizzazione in una finestra di dialogo di errore.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto DataControl (Servizi Desktop remoto)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di modello di eventi ADO (VC + +)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Riepilogo dei gestori eventi ADO](../../../ado/guide/data/ado-event-handler-summary.md)



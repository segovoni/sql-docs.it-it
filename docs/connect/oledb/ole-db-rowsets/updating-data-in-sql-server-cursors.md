---
title: L'aggiornamento dei dati nei cursori del Server SQL | Documenti Microsoft
description: L'aggiornamento dei dati nei cursori di SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- updating data [SQL Server]
- isolation levels [SQL Server]
- delayed update mode [OLE DB]
- immediate update mode [OLE DB]
- cursors [OLE DB]
- data updates [SQL Server], OLE DB
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 8cece02b19e2334246dbddc096cafbeeae705684
ms.sourcegitcommit: 03ba89937daeab08aa410eb03a52f1e0d212b44f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/16/2018
ms.locfileid: "35689504"
---
# <a name="updating-data-in-sql-server-cursors"></a>Aggiornamento dei dati nei cursori di SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Quando il recupero e l'aggiornamento dei dati tramite [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] i cursori, un Driver OLE DB per SQL Server applicazione consumer è associato mediante le stesse considerazioni e vincoli che si applicano a qualsiasi altra applicazione client.  
  
 Solo le righe dei cursori [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] partecipano al controllo di accesso ai dati simultaneo. Quando il consumer richiede un set di righe modificabile, il controllo della concorrenza viene effettuato da DBPROP_LOCKMODE. Per modificare il livello di controllo di accesso simultaneo, il consumer imposta la proprietà DBPROP_LOCKMODE prima di aprire il set di righe.  
  
 I livelli di isolamento della transazione possono provocare ritardi significativi nel posizionamento delle righe se la progettazione delle applicazioni client lascia aperte le transazioni per lunghi periodi di tempo. Per impostazione predefinita, il Driver OLE DB per SQL Server utilizza il livello di isolamento read committed specificato da DBPROPVAL_TI_READCOMMITTED. Il Driver OLE DB per SQL Server supporta l'isolamento di lettura dirty quando la concorrenza del set di righe è di sola lettura. In un set di righe modificabile il consumer può pertanto richiedere un livello di isolamento superiore ma non inferiore.  
  
## <a name="immediate-and-delayed-update-modes"></a>Modalità di aggiornamento immediato e posticipato  
 In modalità di aggiornamento immediato ogni chiamata a **IRowsetChange:: SetData** provoca un round trip al [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Se il consumer apporta più modifiche a una singola riga, risulta più efficace inviare tutte le modifiche con una singola **SetData** chiamare.  
  
 In modalità di aggiornamento posticipato viene eseguito un round trip il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] per ogni riga indicata nel *cRows* e *rghRows* parametri di **IRowsetUpdate:: Update**.  
  
 In entrambe le modalità un round trip rappresenta una transazione distinta quando per il set di righe non è aperto alcun oggetto transazione.  
  
 Quando si utilizza **IRowsetUpdate:: Update**, il Driver OLE DB per SQL Server tenta di elaborare ogni riga indicata. Un errore che si verificano a causa di valori di dati, la lunghezza o lo stato non validi per qualsiasi riga non arresta il Driver OLE DB per l'elaborazione di SQL Server. È possibile che vengano modificate tutte o nessuna delle altre righe che partecipano all'aggiornamento. Il consumer deve esaminare la *prgRowStatus* matrice per determinare l'errore per qualsiasi riga specifica quando il Driver OLE DB per SQL Server restituisce DB_S_ERRORSOCCURRED.  
  
 Un consumer non deve presupporre che le righe vengano elaborate in base a un ordine specifico. Se un consumer richiede un'elaborazione ordinata di modifica dei dati su più di una riga, deve stabilire l'ordine nella logica dell'applicazione e aprire una transazione per includere il processo.  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiornamento dei dati nei set di righe](../../oledb/ole-db-rowsets/updating-data-in-rowsets.md)  
  
  

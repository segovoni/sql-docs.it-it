---
title: MSSQLSERVER_8645 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 8645 (Database Engine error)
ms.assetid: 63d6d6d7-3850-4061-8e96-b1fa665e3180
caps.latest.revision: 17
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fde48fdc7fec84b5589c7cb157808aa9a1462e96
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37409460"
---
# <a name="mssqlserver8645"></a>MSSQLSERVER_8645
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|8645|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|MEMTIMEDOUT_ERR|  
|Testo del messaggio|Timeout durante l'attesa di risorse di memoria per l'esecuzione della query. Eseguire nuovamente la query.|  
  
## <a name="explanation"></a>Spiegazione  
 Timeout durante l'attesa di risorse di memoria per l'esecuzione della query nel pool di risorse 'predefinito'.  
  
## <a name="user-action"></a>Azione dell'utente  
 Se non si utilizza Resource Governor, si consiglia di verificare lo stato generale del server e di caricare o controllare il pool di risorse o le impostazioni del gruppo del carico di lavoro.  
  
 Nell'elenco seguente viene illustrata la procedura generale per la risoluzione degli errori di memoria:  
  
1.  Verificare se altre applicazioni o servizi utilizzano la memoria nel server specificato. Riconfigurare le applicazioni o i servizi meno critici per utilizzare una quantità di memoria inferiore.  
  
2.  Iniziare a raccogliere i dati dei contatori di monitoraggio delle prestazioni per **SQL Server: Gestione buffer** e **SQL Server: Gestione memoria**.  
  
3.  Verificare i seguenti parametri di configurazione della memoria di SQL Server:  
  
    -   **max server memory**  
  
    -   **min server memory**  
  
    -   **min memory per query**  
  
     Valutare eventuali impostazioni non comuni e, se necessario, correggerle. Considerare i requisiti di memoria aggiuntivi per [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Le impostazioni predefinite sono elencate nell'argomento "Impostazione delle opzioni di configurazione del server" nella documentazione online di SQL Server.  
  
4.  Osservare l'output di DBCC MEMORYSTATUS e il modo in cui viene modificato quando vengono visualizzati questi messaggi di errore.  
  
5.  Verificare il carico di lavoro (ad esempio, numero di sessioni simultanee, query attualmente in esecuzione).  
  
 Per aumentare la quantità di memoria disponibile per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], effettuare le operazioni seguenti:  
  
-   Se le risorse vengono utilizzate da altre applicazioni oltre a SQL Server, provare a interromperne l'esecuzione o a eseguirle in un server distinto. In questo modo sarà possibile eliminare le richieste di memoria esterne.  
  
-   Se è stata configurata l'opzione **max server memory,**, aumentarne il valore impostato.  
  
 Eseguire i comandi DBCC seguenti per liberare diverse cache in memoria di SQL Server.  
  
-   DBCC FREESYSTEMCACHE  
  
-   DBCC FREESESSIONCACHE  
  
-   DBCC FREEPROCCACHE  
  
 Se il problema persiste, sarà necessario analizzarlo in modo più dettagliato e cercare di ridurre il carico di lavoro.  
  
  
---
title: MSSQLSERVER_2533 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 2533 (Database Engine error)
ms.assetid: 0418352c-0ab2-4dc7-b8b9-5c3bad94560c
caps.latest.revision: 19
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 446206b4ce8f73e95770504150075d29ca231909
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37418240"
---
# <a name="mssqlserver2533"></a>MSSQLSERVER_2533
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|2533|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|DBCC_PAGE_WAS_NOT_SEEN|  
|Testo del messaggio|Errore di tabella: impossibile rilevare la pagina P_ID allocata all'ID di oggetto O_ID, con ID di indice I_ID, ID di partizione PN_ID, e ID di unità di allocazione A_ID (tipo TYPE). La pagina non è valida oppure l'ID di unità di allocazione contenuto nell'intestazione della pagina non è corretto.|  
  
## <a name="explanation"></a>Spiegazione  
 Una pagina viene allocata all'ID di unità di allocazione *A_ID*, che però non è contenuto nell'intestazione della pagina. L'intestazione ha un ID di unità di allocazione differente. Se l'ID di unità di allocazione contenuto nell'intestazione della pagina è relativo a un oggetto valido, la pagina può restituire un errore MSQLEngine_2534 corrispondente.  
  
## <a name="user-action"></a>Azione dell'utente  
  
### <a name="look-for-hardware-failure"></a>Individuare errori hardware  
 Eseguire gli strumenti di diagnostica hardware e risolvere eventuali problemi. Esaminare inoltre il registro di sistema di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows e il registro delle applicazioni, nonché il log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per stabilire se l'errore è dovuto a un problema hardware. Risolvere tutti i problemi relativi all'hardware indicati nei log.  
  
 In caso di problemi persistenti che provocano il danneggiamento dei dati, provare a sostituire i vari componenti hardware per isolare il problema. Verificare che nel sistema non sia abilitata la memorizzazione nella cache in scrittura sul controller del disco. Se si ritiene che il problema sia dovuto alla memorizzazione nella cache in scrittura, rivolgersi al fornitore dell'hardware.  
  
 Infine, potrebbe essere conveniente passare a un nuovo sistema hardware. A tale scopo può essere necessario riformattare le unità disco e reinstallare il sistema operativo.  
  
### <a name="restore-from-backup"></a>Eseguire un ripristino da backup  
 Se il problema non è correlato all'hardware ed è disponibile un backup valido noto, ripristinare il database dal backup.  
  
### <a name="run-dbcc-checkdb"></a>Eseguire DBCC CHECKDB  
 Se non è disponibile un backup valido, eseguire DBCC CHECKDB senza la clausola REPAIR per determinare l'entità del danno. Verrà automaticamente suggerita la clausola REPAIR da usare. Eseguire quindi DBCC CHECKDB con la clausola REPAIR appropriata per correggere il database.  
  
> [!CAUTION]  
>  Se non si è certi dell'effetto prodotto sui dati dall'esecuzione di DBCC CHECKDB con la clausola REPAIR, contattare il personale del supporto tecnico prima di eseguire l'istruzione.  
  
 Se l'esecuzione di DBCC CHECKDB con una clausola REPAIR non consente di risolvere il problema, contattare il personale del supporto tecnico.  
  
### <a name="results-of-running-repair-options"></a>Risultati dell'esecuzione delle opzioni REPAIR  
 L'istruzione REPAIR dealloca la pagina. Se la pagina è relativa a un'unità di allocazione di dati all'interno di righe, l'indice, se esistente, verrà ricompilato.  
  
> [!CAUTION]  
>  L'operazione di correzione può comportare la perdita di dati.  
  
## <a name="see-also"></a>Vedere anche  
 [MSSQLSERVER_2534](mssqlserver-2534-database-engine-error.md)  
  
  

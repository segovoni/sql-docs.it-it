---
title: MSSQLSERVER_5228 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 5228 (Database Engine error)
ms.assetid: 5e83c617-4aa2-4755-bcc5-a798c46b97e4
caps.latest.revision: 18
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f7efc73453784813847342630944ceda7a2d9592
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37416480"
---
# <a name="mssqlserver5228"></a>MSSQLSERVER_5228
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|5228|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|DBCC4_ANTIMATTER_COLUMN_DETECTED|  
|Testo del messaggio|Errore di tabella: ID di oggetto O_ID, ID di indice I_ID, ID di partizione PN_ID, ID di unità di allocazione A_ID (tipo TYPE), pagina PG_ID, riga ROW_ID. DBCC ha rilevato una pulizia incompleta causata da un'operazione di compilazione di un indice online. Valore della colonna di elenco degli elementi da eliminare VALUE.|  
  
## <a name="explanation"></a>Spiegazione  
 È stata rilevata una build di un indice online incompleta per l'oggetto *O_ID*, indice *I_ID* e partizione *PN_ID*. Tale evento è dimostrato dalla presenza di una colonna di elenco degli elementi da eliminare nella riga *R_ID*. Questa colonna viene utilizzata durante la riconciliazione di record di più origini per la compilazione di un indice online. Nel messaggio di errore viene inoltre indicato il valore della colonna di elenco degli elementi da eliminare.  
  
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
 L'esecuzione di REPAIR comporta la ricompilazione dell'indice specificato e di tutti gli indici dipendenti.  
  
## <a name="see-also"></a>Vedere anche  
 [DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)  
  
  

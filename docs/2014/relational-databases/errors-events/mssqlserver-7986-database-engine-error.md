---
title: MSSQLSERVER_7986 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 7986 (Database Engine error)
ms.assetid: ae64276c-4e1e-4ef3-9ee9-ebeb2f61e565
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 46e7ca71044b07851e2bfa5cff1883cdf62f2967
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37415840"
---
# <a name="mssqlserver7986"></a>MSSQLSERVER_7986
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|7986|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|DBCC2_PRE_CHECKS_CROSS_OBJECT_LINKAGE|  
|Testo del messaggio|Controlli preliminari su tabella di sistema: per l'ID di oggetto ID_O è definito un collegamento a catena tra oggetti. La pagina ID1_P punta a ID2_P nell'ID di unità di allocazione ID1_A (dovrebbe essere ID2_A). Istruzione di controllo interrotta a causa di un errore irreversibile.|  
  
## <a name="explanation"></a>Spiegazione  
 La prima fase dell'esecuzione di un comando DBCC CHECKDB consiste nell'eseguire controlli primitivi nelle pagine dei dati delle tabelle di sistema critiche. Non è possibile correggere eventuali errori rilevati. DBCC CHECKDB verrà pertanto terminato immediatamente. Il puntatore di pagina successiva della pagina *P_ID1* nel livello dati dell'oggetto specificato punta alla pagina *P_ID2* di un oggetto diverso.  
  
## <a name="user-action"></a>Azione dell'utente  
  
### <a name="look-for-hardware-failure"></a>Individuare errori hardware  
 Eseguire gli strumenti di diagnostica hardware e risolvere eventuali problemi. Esaminare inoltre il registro di sistema di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows e il registro delle applicazioni, nonché il log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per stabilire se l'errore è dovuto a un problema hardware. Risolvere tutti i problemi relativi all'hardware indicati nei log.  
  
 In caso di problemi persistenti che provocano il danneggiamento dei dati, provare a sostituire i vari componenti hardware per isolare il problema. Verificare che nel sistema non sia abilitata la memorizzazione nella cache in scrittura sul controller del disco. Se si ritiene che il problema sia dovuto alla memorizzazione nella cache in scrittura, rivolgersi al fornitore dell'hardware.  
  
 Infine, potrebbe essere conveniente passare a un nuovo sistema hardware. A tale scopo può essere necessario riformattare le unità disco e reinstallare il sistema operativo.  
  
### <a name="restore-from-backup"></a>Eseguire un ripristino da backup  
 Se il problema non è correlato all'hardware ed è disponibile un backup valido noto, ripristinare il database dal backup.  
  
### <a name="run-dbcc-checkdb"></a>Eseguire DBCC CHECKDB  
 Non applicabile. L'errore non può essere corretto automaticamente. Se non è possibile ripristinare il database da un backup, contattare il Servizio Supporto Tecnico Clienti [!INCLUDE[msCoName](../../includes/msconame-md.md)].  
  
  

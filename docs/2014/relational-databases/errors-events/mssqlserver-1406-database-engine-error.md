---
title: MSSQLSERVER_1406 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 1406 (Database Engine error)
ms.assetid: 915f97de-9b74-41f8-8bd5-b2d061416718
caps.latest.revision: 15
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 84f9ff97dc89092f06a960f86f0a6844a2b30a52
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37424830"
---
# <a name="mssqlserver1406"></a>MSSQLSERVER_1406
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|1406|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|DBM_BADSTATEFORFORCESERVICE|  
|Testo del messaggio|Impossibile forzare il servizio senza rischi. Per ottenere l'accesso, rimuovere il mirroring del database e recuperare il database "%.*ls".|  
  
## <a name="explanation"></a>Spiegazione  
 Il [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] non può forzare il servizio perché lo stato del mirroring non è in grado di garantire che il servizio venga forzato correttamente.  
  
## <a name="user-action"></a>Azione dell'utente  
 Rimuovere il mirroring del database. Sarà quindi possibile recuperare il database mirror per potervi accedere.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo forzato del servizio in una sessione di mirroring del database &#40;Transact-SQL&#41;](../../database-engine/database-mirroring/force-service-in-a-database-mirroring-session-transact-sql.md)   
 [Rimozione del mirroring del database &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)  
  
  

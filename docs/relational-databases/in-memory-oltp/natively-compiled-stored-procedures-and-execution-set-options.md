---
title: Stored procedure compilate in modo nativo e opzioni SET di esecuzione | Microsoft Docs
ms.custom: ''
ms.date: 10/26/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: in-memory-oltp
ms.reviewer: ''
ms.suite: sql
ms.technology: in-memory-oltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c1869cf7-9030-4d18-85d6-0e419a4e9af7
caps.latest.revision: 5
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 908b7e49c2af671773645f010435b2cc97c90afc
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2018
ms.locfileid: "34328192"
---
# <a name="natively-compiled-stored-procedures-and-execution-set-options"></a>Stored procedure compilate in modo nativo e opzioni SET di esecuzione
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Le opzioni di sessione sono fisse nei blocchi atomici, come descritto in [Blocchi atomici](atomic-blocks-in-native-procedures.md). L'esecuzione di una stored procedure non è interessata dalle opzioni SET di una sessione poiché i blocchi atomici sono obbligatori. Tuttavia, alcune opzioni SET quali SET NOEXEC e SET SHOWPLAN_XML impediscono l'esecuzione delle stored procedure, incluse quelle compilate in modo nativo.   
  
 Quando una stored procedure compilata in modo nativo viene eseguita con una qualsiasi opzione STATISTICS attivata, le statistiche vengono raccolte per la stored procedure completa e non per istruzione. Per altre informazioni, vedere [SET STATISTICS IO &#40;Transact-SQL&#41;](../../t-sql/statements/set-statistics-io-transact-sql.md), [SET STATISTICS PROFILE &#40;Transact-SQL&#41;](../../t-sql/statements/set-statistics-profile-transact-sql.md), [SET STATISTICS TIME &#40;Transact-SQL&#41;](../../t-sql/statements/set-statistics-time-transact-sql.md) e [SET STATISTICS XML &#40;Transact-SQL&#41;](../../t-sql/statements/set-statistics-xml-transact-sql.md). Per ottenere statistiche di esecuzione a livello di singola istruzione in stored procedure compilate in modo nativo, utilizzare una sessione Evento esteso in un evento sp_statement_completed, che viene attivato al completamento di ciascuna singola query nell'esecuzione di una stored procedure. Per altre informazioni sulla creazione di sessioni di evento estesi, vedere [CREATE EVENT SESSION &#40;Transact-SQL&#41;](../../t-sql/statements/create-event-session-transact-sql.md).  
  
 **SHOWPLAN_XML** è supportato per le stored procedure compilate in modo nativo. Le opzioni**SHOWPLAN_ALL** e **SHOWPLAN_TEXT** non sono supportate con le stored procedure compilate in modo nativo.  
  
 L'opzione**SET FMTONLY** non è supportata con le stored procedure compilate in modo nativo. Usare invece [sp_describe_first_result_set &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure compilate in modo nativo](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)  
  
  

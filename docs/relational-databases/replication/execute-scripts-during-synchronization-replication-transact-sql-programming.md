---
title: Eseguire script durante la sincronizzazione (programmazione Transact-SQL della replica) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- synchronization [SQL Server replication], scripts
- scripts [SQL Server replication], synchronization and
- sp_addscriptexec
ms.assetid: b58a0877-4e43-4fab-a281-24e6022d3fb1
caps.latest.revision: 34
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 5c163db9281b8a465ba99337d0574099878a2cf2
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37360244"
---
# <a name="execute-scripts-during-synchronization-replication-transact-sql-programming"></a>Esecuzione di script durante la sincronizzazione (programmazione Transact-SQL della replica)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  La replica supporta l'esecuzione di script su richiesta per i Sottoscrittori di pubblicazioni transazionali e di tipo merge. Con questa funzionalità lo script viene copiato nella directory di lavoro della replica e quindi viene applicato al Sottoscrittore tramite **sqlcmd** . Per impostazione predefinita, se si verifica un errore durante l'applicazione dello script per una sottoscrizione di una pubblicazione transazionale, l'agente di distribuzione verrà arrestato. È possibile specificare uno script [!INCLUDE[tsql](../../includes/tsql-md.md)] da eseguire a livello di programmazione tramite le stored procedure di replica.  
  
### <a name="to-specify-a-script-to-run-for-all-subscribers-to-a-snapshot-transactional-or-merge-publication"></a>Per specificare uno script da eseguire per tutti i Sottoscrittori di una pubblicazione snapshot, transazionale o di tipo merge  
  
1.  Comporre e testare lo script [!INCLUDE[tsql](../../includes/tsql-md.md)] che verrà eseguito su richiesta.  
  
2.  Salvare il file script in un percorso in cui sia accessibile all'agente snapshot per la pubblicazione.  
  
3.  Nel database di pubblicazione del server di pubblicazione eseguire [sp_addscriptexec &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addscriptexec-transact-sql.md). Specificare **@publication**, il nome del file script con il percorso UNC completo creato nel passaggio 2 per **@scriptfile**e uno dei valori seguenti per **@skiperror**:  
  
    -   **0** : l'agente arresterà l'esecuzione dello script se viene rilevato un errore.  
  
    -   **1** : l'agente registrerà gli errori e continuerà l'esecuzione dello script quando vengono rilevati errori.  
  
4.  Lo script specificato verrà eseguito in ogni Sottoscrittore la volta successiva che l'agente verrà eseguito per sincronizzare la sottoscrizione.  
  
## <a name="see-also"></a>Vedere anche  
 [Sincronizzare i dati](../../relational-databases/replication/synchronize-data.md)  
  
  

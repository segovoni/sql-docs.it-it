---
title: Eseguire un aggiornamento fittizio per un articolo di Merge (programmazione Transact-SQL della replica) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- sp_mergedummyupdate
- dummy updates [SQL Server replication]
ms.assetid: 2f339210-4d85-4843-bd94-e86f7100d3ef
caps.latest.revision: 30
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 13f72453ec5981120997d024493da2609fb2a092
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37227061"
---
# <a name="perform-a-dummy-update-for-a-merge-article-replication-transact-sql-programming"></a>Esecuzione di un aggiornamento fittizio per un articolo di merge (programmazione Transact-SQL della replica)
  La replica di tipo merge utilizza i trigger come parte del processo di replica; in caso di aggiornamento di una tabella pubblicata, viene attivato un trigger di aggiornamento. In alcuni casi, i dati possono essere aggiornati senza l'attivazione del trigger, ad esempio durante le operazioni WRITETEXT e UPDATETEXT. In questi casi, è necessario aggiungere in modo esplicito un'istruzione UPDATE fittizia per replicare la modifica. È possibile aggiungere un'istruzione UPDATE fittizia utilizzando le stored procedure di replica.  
  
### <a name="to-add-a-dummy-update-statement"></a>Per aggiungere un'istruzione UPDATE fittizia  
  
1.  Eseguire l'operazione, ad esempio UPDATETEXT, su una riga in una tabella pubblicata di merge che richiede un aggiornamento fittizio.  
  
2.  Nel database del server di pubblicazione o del Sottoscrittore nel quale è stata apportata la modifica, eseguire [sp_mergedummyupdate &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-mergedummyupdate-transact-sql). Specificare la tabella nella quale è stata apportata la modifica per **@source_object**e l'identificatore univoco della riga modificata per **@rowguid**.  
  
3.  Sincronizzare la sottoscrizione per replicare la riga modificata.  
  
  

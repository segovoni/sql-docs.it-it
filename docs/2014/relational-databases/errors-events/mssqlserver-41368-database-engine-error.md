---
title: MSSQLSERVER_41368 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 41368 (Database Engine error)
ms.assetid: abc71559-4c4d-4cce-a08f-3299dd167842
caps.latest.revision: 8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8619e3cfb8766caab9d9afbe5ed166761eeeb04f
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37409720"
---
# <a name="mssqlserver41368"></a>MSSQLSERVER_41368
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID evento|41368|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|SQL_IMPLICIT_AND_EXPLICIT_TX_NOT_SUPPORTED|  
|Testo del messaggio|L'accesso alle tabelle con ottimizzazione per la memoria utilizzando il livello di isolamento READ COMMITTED è supportato solo per transazioni in modalità autocommit. Non è invece supportato con le transazioni implicite o esplicite. Specificare un livello di isolamento supportato per la tabella con ottimizzazione per la memoria utilizzando un hint di tabella, ad esempio WITH (SNAPSHOT).|  
  
## <a name="explanation"></a>Spiegazione  
 L'accesso alle tabelle ottimizzate per la memoria utilizzando il livello di isolamento READ COMMITTED è supportato solo per transazioni in modalità autocommit. Per altre informazioni, vedere [Transaction Isolation Levels](../../database-engine/transaction-isolation-levels.md).  
  
 Quando si accede a una tabella ottimizzata per la memoria da una transazione esplicita avviata tramite un'istruzione BEGIN TRANSACTION o da una transazione implicita, se l'opzione IMPLICIT_TRANSACTIONS è impostata su ON, il livello di isolamento READ COMMITTED non è supportato.  
  
## <a name="user-action"></a>Azione dell'utente  
 Quando si accede a una tabella ottimizzata per la memoria da una transazione esplicita o implicita READ COMMITTED, utilizzare l'istruzione SNAPSHOT per accedere alla tabella. Ciò può essere ottenuta usando l'hint di tabella WITH (SNAPSHOT) (per altre informazioni, vedere [linee guida per i livelli di isolamento delle transazioni con tabelle ottimizzate per la memoria](../in-memory-oltp/memory-optimized-tables.md)) o impostare l'opzione database MEMORY_OPTIMIZED_ELEVATE_TO_ Per gli SNAPSHOT su ON (per altre informazioni, vedere [opzioni ALTER DATABASE SET &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)).  
  
## <a name="see-also"></a>Vedere anche  
 [OLTP in memoria &#40;ottimizzazione per la memoria&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  

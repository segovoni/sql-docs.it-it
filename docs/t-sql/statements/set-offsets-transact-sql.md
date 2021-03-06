---
title: SET OFFSETS (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- SET_OFFSETS_TSQL
- OFFSETS_TSQL
- SET OFFSETS
- OFFSETS
dev_langs:
- TSQL
helpviewer_keywords:
- position relative to start of statement [SQL Server]
- OFFSETS option
- offsets [SQL Server]
- SET OFFSETS statement
ms.assetid: c7bcc697-0930-4630-acae-d8ccbfa4414c
caps.latest.revision: 25
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: b40204e252142b7b72962326ccc37e2174d3a811
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/04/2018
ms.locfileid: "37783132"
---
# <a name="set-offsets-transact-sql"></a>SET OFFSETS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce il valore di offset (posizione relativa all'inizio di un'istruzione) delle parole chiave specificate in istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] alle applicazioni DB-Library.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
 
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SET OFFSETS keyword_list { ON | OFF }  
```  
  
## <a name="arguments"></a>Argomenti  
 *keyword_list*  
 Elenco delimitato da virgole di costrutti [!INCLUDE[tsql](../../includes/tsql-md.md)] che include SELECT, FROM, ORDER, TABLE, PROCEDURE, STATEMENT, PARAM ed EXECUTE.  
  
## <a name="remarks"></a>Remarks  
 L'opzione SET OFFSETS viene utilizzata solo in applicazioni DB-Library.  
  
 L'opzione SET OFFSETS viene impostata in fase di analisi, non in fase di esecuzione. Con l'impostazione in fase di analisi, se l'istruzione SET è inclusa nel batch o nella stored procedure l'impostazione diventa effettiva indipendentemente dal fatto che l'esecuzione del codice raggiunga effettivamente il punto. L'istruzione SET ha inoltre effetto prima di qualsiasi altra istruzione eseguita. Ad esempio, se l'istruzione SET è inclusa in un blocco di istruzione IF...ELSE che non viene mai raggiunto in fase di esecuzione, l'istruzione SET viene comunque eseguita perché il blocco IF...ELSE viene analizzato.  
  
 Se l'opzione SET OFFSETS viene impostata in una stored procedure, il valore dell'opzione SET OFFSETS viene ripristinato al termine della stored procedure. Un'istruzione SET OFFSETS specificata nel linguaggio SQL dinamico pertanto non ha alcun effetto sulle istruzioni successive.  
  
 SET PARSEONLY restituisce valori di offset se l'opzione OFFSETS è impostata su ON e non si verificano errori.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza al ruolo **public** .  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzioni SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET PARSEONLY &#40;Transact-SQL&#41;](../../t-sql/statements/set-parseonly-transact-sql.md)  
  
  

---
title: sp_prepexec (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_cursor_prepexec
- sp_cursor_prepexec_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_prepexec
ms.assetid: f9141850-a62b-43bf-8e46-b2f92b75ca56
caps.latest.revision: 6
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: ca8dd4639c4c2382ef17c4de89eee6fde1fdf9b9
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33250005"
---
# <a name="spprepexec-transact-sql"></a>sp_prepexec (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Prepara ed esegue un parametri [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzione. sp_prepexec combina le funzioni di sp_prepare e sp_execute. Viene richiamata specificando ID = 13 in un pacchetto del flusso TDS.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_prepexec handle OUTPUT, params , stmt  
    [ , bound param ] [ ,...n]]  
```  
  
## <a name="arguments"></a>Argomenti  
 *Handle*  
 È il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-generato *gestire* identificatore. *gestire* è un parametro obbligatorio con un **int** valore restituito.  
  
 *Params*  
 Identifica le istruzioni con parametri. Il *params* definizione delle variabili viene sostituita per i marcatori di parametro nell'istruzione. *params* è un parametro obbligatorio che richiede un **ntext**, **nchar**, o **nvarchar** valore di input. Immettere un valore NULL se l'istruzione non è con parametri.  
  
 *stmt*  
 Definisce il set di risultati del cursore. Il *stmt* parametro è obbligatorio e richiede un **ntext**, **nchar** o **nvarchar** valore di input.  
  
 *bound_param*  
 Indica l'utilizzo facoltativo di parametri aggiuntivi. *bound_param* richiede un valore di input di qualsiasi tipo di dati per definire i parametri aggiuntivi in uso.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene preparata ed eseguita un'istruzione semplice.  
  
```  
Declare @P1 int;  
EXEC sp_prepexec @P1 output,   
    N'@P1 nvarchar(128), @P2 nvarchar(100)',  
    N'SELECT database_id, name  
      FROM sys.databases  
      WHERE name=@P1 AND state_desc = @P2',   
@P1 = 'tempdb', @P2 = 'ONLINE';   
EXEC sp_unprepare @P1;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_prepare &#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sp-prepare-transact-sql.md)   
 [sp_execute &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-execute-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

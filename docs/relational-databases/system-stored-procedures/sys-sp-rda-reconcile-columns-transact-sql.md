---
title: sys.sp_rda_reconcile_columns (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: stored-procedures
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_reconcile_columns
- sys.sp_rda_reconcile_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_reconcile_columns stored procedure
ms.assetid: 60d9cc4e-1828-450b-9d88-5b8485800d73
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: fe05d88b6453bd9918b5777b3f52291ec9fefc2c
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39087943"
---
# <a name="syssprdareconcilecolumns-transact-sql"></a>sys.sp_rda_reconcile_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Risolve le differenze tra le colonne nella tabella di Azure remota per le colonne di tabella abilitata per l'estensione SQL Server.  
    
  **sp_rda_reconcile_columns** aggiunge colonne alla tabella remota presenti nella tabella abilitata per l'estensione SQL Server, ma non nella tabella remota. Queste colonne possono essere colonne accidentalmente eliminate dalla tabella remota. Tuttavia **sp_rda_reconcile_columns** non eliminare le colonne della tabella remota presenti nella tabella remota, ma non nella tabella di SQL Server.
  
  > [!IMPORTANT]
  > Quando **sp_rda_reconcile_columns** crea nuovamente le colonne accidentalmente eliminate dalla tabella remota, non ripristina i dati che erano presenti nelle colonne eliminate.
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
   
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_rda_reconcile_columns @objname = '@objname'  
  
```  
  
## <a name="arguments"></a>Argomenti  
 \@objname = '*\@objname*'  
 Il nome della tabella abilitata per l'estensione SQL Server.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o >0 (esito negativo)  
  
## <a name="permissions"></a>Permissions  
 Richiede autorizzazioni db_owner.  
   
## <a name="remarks"></a>Note  
 Se sono presenti colonne nella tabella remota di Azure che non esistono più nella tabella di SQL Server abilitata per Stretch, queste colonne aggiuntive non impediscono il normale funzionamento di Stretch Database. È possibile rimuovere le colonne aggiuntive manualmente.  
  
## <a name="example"></a>Esempio  
 Per risolvere le differenze tra le colonne nella tabella di Azure remota, eseguire l'istruzione seguente.  
  
```sql  
EXEC sp_rda_reconcile_columns @objname = N'StretchEnabledTableName';  
```  
  
  

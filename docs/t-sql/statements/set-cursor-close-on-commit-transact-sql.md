---
title: SET CURSOR_CLOSE_ON_COMMIT (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CURSOR_CLOSE_ON_COMMIT
- SET CURSOR_CLOSE_ON_COMMIT
- CURSOR_CLOSE_ON_COMMIT_TSQL
- SET_CURSOR_CLOSE_ON_COMMIT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CURSOR_CLOSE_ON_COMMIT option
- transactions [SQL Server], cursors
- closing cursors
- cursors [SQL Server], closing
- SET CURSOR_CLOSE_ON_COMMIT statement
ms.assetid: 7b976154-98ce-4a06-bbae-7e59c34211f7
caps.latest.revision: 38
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: de736d329175fe44c8bf837a2a6ef0ca966666ee
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="set-cursorcloseoncommit-transact-sql"></a>SET CURSOR_CLOSE_ON_COMMIT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Controlla il funzionamento dell'istruzione COMMIT TRANSACTION di [!INCLUDE[tsql](../../includes/tsql-md.md)]. Il valore predefinito di questa impostazione è OFF, che specifica che i cursori non verranno chiusi dal server in occasione del commit di una transazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SET CURSOR_CLOSE_ON_COMMIT { ON | OFF }  
```  
  
## <a name="remarks"></a>Osservazioni  
 Quando l'opzione SET CURSOR_CLOSE_ON_COMMIT è impostata su ON, in corrispondenza del commit o del rollback tutti i cursori aperti vengono chiusi in conformità con ISO. Quando l'opzione SET CURSOR_CLOSE_ON_COMMIT è impostata su OFF, i cursori aperti non vengono chiusi in corrispondenza del commit di una transazione.  
  
> [!NOTE]  
>  Se si imposta l'opzione SET CURSOR_CLOSE_ON_COMMIT su ON i cursori aperti non verranno chiusi in corrispondenza del rollback quando il rollback viene applicato a un savepoint_name da una istruzione SAVE TRANSACTION.  
  
 Quando l'opzione SET CURSOR_CLOSE_ON_COMMIT è impostata su OFF, in seguito all'esecuzione di un'istruzione ROLLBACK vengono chiusi solo i cursori asincroni aperti non completamente popolati. Nei cursori STATIC o INSENSITIVE che sono stati aperti dopo l'esecuzione delle modifiche non sarà più riportato lo stato dei dati se viene eseguito il rollback delle modifiche.  
  
 L'opzione SET CURSOR_CLOSE_ON_COMMIT consente di controllare la stessa funzionalità dell'opzione di database CURSOR_CLOSE_ON_COMMIT. Se l'opzione CURSOR_CLOSE_ON_COMMIT è impostata su ON o OFF, l'impostazione viene applicata alla connessione. Se non è stata specificata l'opzione SET CURSOR_CLOSE_ON_COMMIT, il valore di **is_cursor_close_on_commit_on** colonna il **Sys. Databases** vista del catalogo si applica.  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client Provider OLE DB per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client sia impostare CURSOR_CLOSE_ON_COMMIT su OFF quando si connettono. DB-Library non imposta automaticamente il valore dell'opzione CURSOR_CLOSE_ON_COMMIT.  
  
 Quando l'opzione SET ANSI_DEFAULTS è impostata su ON, l'opzione SET CURSOR_CLOSE_ON_COMMIT risulta abilitata.  
  
 L'opzione SET CURSOR_CLOSE_ON_COMMIT viene impostata in fase di esecuzione, non in fase di analisi.  
  
 Per visualizzare l'impostazione corrente per questa impostazione, eseguire la query riportata di seguito.  
  
```  
DECLARE @CURSOR_CLOSE VARCHAR(3) = 'OFF';  
IF ( (4 & @@OPTIONS) = 4 ) SET @CURSOR_CLOSE = 'ON';  
SELECT @CURSOR_CLOSE AS CURSOR_CLOSE_ON_COMMIT;  
```  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza al ruolo **public** .  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene definito un cursore in una transazione e viene tentato di utilizzarlo dopo il commit della transazione.  
  
```  
-- SET CURSOR_CLOSE_ON_COMMIT  
-------------------------------------------------------------------------------  
SET NOCOUNT ON;  
  
CREATE TABLE t1 (a INT);  
GO   
  
INSERT INTO t1   
VALUES (1), (2);  
GO  
  
PRINT '-- SET CURSOR_CLOSE_ON_COMMIT ON';  
GO  
SET CURSOR_CLOSE_ON_COMMIT ON;  
GO  
PRINT '-- BEGIN TRAN';  
BEGIN TRAN;  
PRINT '-- Declare and open cursor';  
DECLARE testcursor CURSOR FOR  
    SELECT a FROM t1;  
OPEN testcursor;  
PRINT '-- Commit tran';  
COMMIT TRAN;  
PRINT '-- Try to use cursor';  
FETCH NEXT FROM testcursor;  
CLOSE testcursor;  
DEALLOCATE testcursor;  
GO  
PRINT '-- SET CURSOR_CLOSE_ON_COMMIT OFF';  
GO  
SET CURSOR_CLOSE_ON_COMMIT OFF;  
GO  
PRINT '-- BEGIN TRAN';  
BEGIN TRAN;  
PRINT '-- Declare and open cursor';  
DECLARE testcursor CURSOR FOR  
    SELECT a FROM t1;  
OPEN testcursor;  
PRINT '-- Commit tran';  
COMMIT TRAN;  
PRINT '-- Try to use cursor';  
FETCH NEXT FROM testcursor;  
CLOSE testcursor;  
DEALLOCATE testcursor;  
GO  
DROP TABLE t1;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [BEGIN TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/begin-transaction-transact-sql.md)   
 [Chiudi &#40; Transact-SQL &#41;](../../t-sql/language-elements/close-transact-sql.md)   
 [COMMIT TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/commit-transaction-transact-sql.md)   
 [ROLLBACK TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/rollback-transaction-transact-sql.md)   
 [Istruzioni SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET ANSI_DEFAULTS &#40; Transact-SQL &#41;](../../t-sql/statements/set-ansi-defaults-transact-sql.md)  
  
  

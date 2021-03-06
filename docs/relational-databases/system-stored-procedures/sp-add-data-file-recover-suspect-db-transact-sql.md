---
title: sp_add_data_file_recover_suspect_db (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_add_data_file_recover_suspect_db
- sp_add_data_file_recover_suspect_db_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_data_file_recover_suspect_db
ms.assetid: b25262aa-a228-48b7-8739-6581c760b171
caps.latest.revision: 51
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 13c08441680744d38f870fc5b6ebd5d7a1e20c91
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33239161"
---
# <a name="spadddatafilerecoversuspectdb-transact-sql"></a>sp_add_data_file_recover_suspect_db (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Aggiunge un file di dati a un filegroup quando non è possibile completare l'operazione di recupero di un database a causa di spazio insufficiente nel filegroup (errore 1105). Dopo l'aggiunta del file, la stored procedure disabilita l'impostazione sospetta e completa il recupero del database. I parametri sono identici a quelli dell'istruzione ALTER DATABASE *database_name* ADD FILE.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_add_data_file_recover_suspect_db [ @dbName= ] 'database'   
    , [ @filegroup = ] 'filegroup_name'   
    , [ @name = ] 'logical_file_name'   
    , [ @filename= ] 'os_file_name'   
    , [ @size = ] 'size'   
    , [ @maxsize = ] 'max_size'   
    , [ @filegrowth = ] 'growth_increment'  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@dbName=** ] **' * * * database* **'**  
 Nome del database. *database* viene **sysname**, non prevede alcun valore predefinito.  
  
 [  **@filegroup=** ] **' * * * filegroup_name* **'**  
 Filegroup a cui aggiungere il file. *filegroup_name* viene **nvarchar(260)**, e il valore predefinito è NULL, che indica il file primario.  
  
 [  **@name=** ] **' * * * nome_file_logico* **'**  
 Nome utilizzato in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per fare riferimento al file. Deve essere un nome univoco nel server. *nome_file_logico* viene **nvarchar(260)**, non prevede alcun valore predefinito.  
  
 [ **@filename=** ] **'***os_file_name* **'**  
 Percorso e nome di file utilizzato dal sistema operativo per il file. Il file deve trovarsi in un'istanza di [!INCLUDE[ssDE](../../includes/ssde-md.md)]. *os_file_name* viene **nvarchar(260)**, non prevede alcun valore predefinito.  
  
 [  **@size=** ] **' * * * dimensioni* **'**  
 Dimensioni iniziali del file. *dimensioni* viene **nvarchar(20)**, con un valore predefinito è NULL. Specificare un numero intero, ovvero non includere decimali. È possibile utilizzare i suffissi MB e KB per specificare megabyte o kilobyte. Il valore predefinito è MB. Il valore minimo è 512 KB. Se *dimensioni* non viene specificato, il valore predefinito è 1 MB.  
  
 [ **@maxsize=** ] **'***max_size* **'**  
 Valore massimo fino a cui possono aumentare le dimensioni del file. *max_size* viene **nvarchar(20)**, con un valore predefinito è NULL. Specificare un numero intero, ovvero non includere decimali. È possibile utilizzare i suffissi MB e KB per specificare megabyte o kilobyte. Il valore predefinito è MB.  
  
 Se *max_size* non viene specificato, il file aumenterà finché il disco è pieno. Prima che si verifichi questa situazione, l'amministratore riceve un avviso dal registro applicazioni di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.  
  
 [  **@filegrowth=** ] **' * * * growth_increment* **'**  
 Quantità di spazio aggiunta al file ogni volta che è necessario spazio aggiuntivo. *growth_increment* viene **nvarchar(20)**, con un valore predefinito è NULL. Il valore 0 indica che le dimensioni non verranno aumentate. Specificare un numero intero, ovvero non includere decimali. È possibile specificare il valore in megabyte (MB) o in kilobyte (KB) oppure in forma di percentuale (%). Se si utilizza il suffisso %, l'incremento corrisponde alla percentuale specificata delle dimensioni del file quando si verifica l'incremento. Se si specifica un valore senza il suffisso MB, KB o %, il suffisso predefinito è MB.  
  
 Se *growth_increment* è NULL, il valore predefinito è 10% e il valore minimo è 64 KB. Le dimensioni specificate vengono arrotondate al blocco di 64 KB più prossimo.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="permissions"></a>Autorizzazioni  
 Autorizzazioni per impostazione predefinita ai membri di eseguire il **sysadmin** ruolo predefinito del server. Queste autorizzazioni non sono trasferibili.  
  
## <a name="examples"></a>Esempi  
 In questo esempio il database `db1` è stato contrassegnato come sospetto durante l'operazione di recupero a causa di spazio insufficiente (errore 1105) nel filegroup `fg1`.  
  
```  
USE master;  
GO  
EXEC sp_add_data_file_recover_suspect_db db1, fg1, file2,  
    'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data\db1_file2.mdf', '1MB';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [sp_add_log_file_recover_suspect_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-log-file-recover-suspect-db-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

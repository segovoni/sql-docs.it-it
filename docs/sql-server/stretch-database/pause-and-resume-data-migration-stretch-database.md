---
title: Sospendere e riprendere la migrazione dei dati (Stretch Database) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Stretch Database, pausing and resuming
- pausing Stretch Database
- resuming Stretch Database
ms.assetid: 65d6a990-b295-41b2-97f9-7b6bf3000e4d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e6a25d3a7039b435a10928b3ca58464f7fdccf7c
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34773217"
---
# <a name="pause-and-resume-data-migration-stretch-database"></a>Sospendere e riprendere la migrazione dei dati (Stretch Database)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md-winonly](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md-winonly.md)]


  Per sospendere o riprendere la migrazione dei dati in Azure, selezionare **Estendi** per una tabella in SQL Server Management Studio e quindi selezionare **Sospendi** o **Riprendi** per sospendere o riprendere la migrazione dei dati. È anche possibile usare Transact-SQL per sospendere o riprendere la migrazione dei dati.  
  
 Sospendere la migrazione dei dati nelle singole tabelle per risolvere i problemi nel server locale o per ottimizzare la larghezza di banda di rete disponibile.  

## <a name="pause-data-migration"></a>Sospendere la migrazione dei dati  
  
### <a name="use-sql-server-management-studio-to-pause-data-migration"></a>Usare SQL Server Management Studio per sospendere la migrazione dei dati  
  
1.  In Esplora oggetti di SQL Server Management Studio selezionare la tabella abilitata per l'estensione di cui si vuole sospendere la migrazione dei dati.  
  
2.  Fare clic con il pulsante destro del mouse e selezionare **Estendi**, quindi scegliere **Sospendi**.  
  
### <a name="use-transact-sql-to-pause-data-migration"></a>Usare Transact-SQL per sospendere la migrazione dei dati  
 Eseguire il comando seguente.  
  
```sql  
USE <Stretch-enabled database name>;
GO
ALTER TABLE <Stretch-enabled table name>  
    SET ( REMOTE_DATA_ARCHIVE ( MIGRATION_STATE = PAUSED ) ) ;  
GO 
```  
  
## <a name="resume-data-migration"></a>Riprendere la migrazione dei dati  
  
### <a name="use-sql-server-management-studio-to-resume-data-migration"></a>Usare SQL Server Management Studio per riprendere la migrazione dei dati  
  
1.  In Esplora oggetti di SQL Server Management Studio selezionare la tabella abilitata per l'estensione di cui si vuole riprendere la migrazione dei dati.  
  
2.  Fare clic con il pulsante destro del mouse e selezionare **Estendi**, quindi selezionare **Riprendi**.  
  
### <a name="use-transact-sql-to-resume-data-migration"></a>Usare Transact-SQL per riprendere la migrazione dei dati  
 Eseguire questo comando.  
  
```sql  
USE <Stretch-enabled database name>;
GO
ALTER TABLE <Stretch-enabled table name>   
    SET ( REMOTE_DATA_ARCHIVE ( MIGRATION_STATE = OUTBOUND ) ) ;  
 GO
```  

## <a name="check-whether-migration-is-active-or-paused"></a>Controllare se la migrazione è attiva o sospesa

### <a name="use-sql-server-management-studio-to-check-whether-migration-is-active-or-paused"></a>Usare SQL Server Management Studio per controllare se la migrazione è attiva o sospesa
In SQL Server Management Studio aprire **Monitoraggio di Stretch Database** e controllare il valore della colonna **Stato di migrazione**. Per altre informazioni, vedere [Monitor and troubleshoot data migration](../../sql-server/stretch-database/monitor-and-troubleshoot-data-migration-stretch-database.md)(Monitorare e risolvere i problemi relativi alla migrazione dei dati).

### <a name="use-transact-sql-to-check-whether-migration-is-active-or-paused"></a>Usare Transact-SQL per controllare se la migrazione è attiva o sospesa
Eseguire una query nella vista del catalogo **sys.remote_data_archive_tables** e controllare il valore della colonna **is_migration_paused** . Per altre informazioni, vedere [sys.remote_data_archive_tables](../../relational-databases/system-catalog-views/stretch-database-catalog-views-sys-remote-data-archive-tables.md).

## <a name="see-also"></a>Vedere anche  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
[Monitor and troubleshoot data migration](../../sql-server/stretch-database/monitor-and-troubleshoot-data-migration-stretch-database.md) 
  

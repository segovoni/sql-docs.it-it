---
title: Eseguire la migrazione di database MySQL a SQL Server - database SQL di Azure | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 8006f9a0-394d-4238-8dc5-44255134628b
caps.latest.revision: 12
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 094e74a3f4d63e46b21d74346b21132b6c616497
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/12/2018
ms.locfileid: "38985763"
---
# <a name="migrating-mysql-databases-to-sql-server---azure-sql-db-mysqltosql"></a>Migrazione di database MySQL a SQL Server - Azure SQL database (MySQLToSql)
SQL Server Migration Assistant (SSMA) per MySQL è un ambiente completo che consente di rapidamente la migrazione di database MySQL a SQL Server o SQL Azure. Tramite SSMA per MySQL, è possibile esaminare i dati e oggetti di database, valutare i database per la migrazione, eseguire la migrazione di oggetti di database a SQL Server o SQL Azure e quindi eseguire la migrazione dei dati in SQL Server o SQL Azure.  
  
## <a name="recommended-migration-process"></a>Processo di migrazione consigliato  
Per eseguire la migrazione oggetti e i dati dal database MySQL a SQL Server o SQL Azure, procedere come segue:  
  
1.  [Uso dei progetti SSMA &#40;MySQLToSQL&#41;](../../ssma/mysql/working-with-ssma-projects-mysqltosql.md).  
  
    Dopo aver creato il progetto, è possibile impostare conversione del progetto, la migrazione e le opzioni di mapping dei tipi. Per altre informazioni sulle impostazioni del progetto, vedere [impostazione delle opzioni progetto &#40;MySQLToSQL&#41;](../../ssma/mysql/setting-project-options-mysqltosql.md). Per informazioni su come personalizzare i mapping dei tipi di dati, vedere [Mapping di MySQL e SQL Server Data Types &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-and-sql-server-data-types-mysqltosql.md)  
  
2.  [La connessione a MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-mysql-mysqltosql.md)  
  
3.  [La connessione a SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-sql-server-mysqltosql.md)  
  
4.  [Mapping tra i database MySQL a schemi SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md)  
  
5.  [La connessione al database SQL di Azure &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-azure-sql-db-mysqltosql.md)  
  
6.  Facoltativamente [valutare i database di MySQL per la conversione &#40;MySQLToSQL&#41; ](../../ssma/mysql/assessing-mysql-databases-for-conversion-mysqltosql.md) valutare gli oggetti di database per la conversione e stimare il tempo di conversione.  
  
7.  [Conversione dei database MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/converting-mysql-databases-mysqltosql.md)  
  
8.  [Sincronizzazione](http://msdn.microsoft.com/ac993a6d-0283-4823-8793-6b217677dfa3)  
  
9. È possibile eseguire questa operazione in uno dei modi seguenti:  
  
    -   Salvare uno script ed eseguirlo in SQL Server o SQL Azure.  
  
    -   Sincronizzare gli oggetti di database.  
  
10. [La migrazione dei dati di MySQL in - database SQL di Azure SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/migrating-mysql-data-into-sql-server-azure-sql-db-mysqltosql.md)  
  
11. Se necessario, aggiornare le applicazioni di database.  
  
> [!NOTE]  
> È possibile eseguire la migrazione di schemi Information_schema e MySQL.  
  
## <a name="see-also"></a>Vedere anche  
[Installazione di SSMA per MySQL &#40;MySqlToSql&#41;](../../ssma/mysql/installing-ssma-for-mysql-mysqltosql.md)  
[Introduzione a SSMA per MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/getting-started-with-ssma-for-mysql-mysqltosql.md)  
  

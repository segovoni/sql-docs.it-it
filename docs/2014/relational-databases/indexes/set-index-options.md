---
title: Impostare le opzioni di indice | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: table-view-index
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ALLOW_ROW_LOCKS option
- SORT_IN_TEMPDB option
- DROP_EXISTING clause
- large data, indexes
- PAD_INDEX
- STATISTICS_NORECOMPUTE
- MAXDOP index option, setting
- index options [SQL Server]
- MAXDOP index option
- IGNORE_DUP_KEY option
- ALLOW_PAGE_LOCKS option
- ONLINE
ms.assetid: 7969af33-e94c-41f7-ab89-9d9a2747cd5c
caps.latest.revision: 44
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 4177b3a87d465781e73f5747c6797ce3d7f84211
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37331727"
---
# <a name="set-index-options"></a>Impostare le opzioni di indice
  In questo argomento si illustra come modificare le proprietà di un indice in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
     [Security](#Security)  
  
-   **Per modificare le proprietà di un indice utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   Le opzioni ALLOW_PAGE_LOCKS, ALLOW_ROW_LOCKS, IGNORE_DUP_KEY e STATISTICS_NORECOMPUTE vengono applicate immediatamente all'indice tramite la clausola SET nell'istruzione ALTER INDEX.  
  
-   Durante la ricompilazione di un indice tramite ALTER INDEX REBUILD o CREATE INDEX WITH DROP_EXISTING, è possibile impostare le opzioni PAD_INDEX, FILLFACTOR, SORT_IN_TEMPDB, IGNORE_DUP_KEY, STATISTICS_NORECOMPUTE, ONLINE, ALLOW_ROW_LOCKS, ALLOW_PAGE_LOCKS, MAXDOP e DROP_EXISTING (solo CREATE INDEX).  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
 È richiesta l'autorizzazione ALTER per la tabella o la vista.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-modify-the-properties-of-an-index-in-table-designer"></a>Per modificare le proprietà di un indice in Progettazione tabelle  
  
1.  In Esplora oggetti fare clic sul segno più per espandere il database contenente la tabella in cui si desidera modificare le proprietà di un indice.  
  
2.  Fare clic sul segno più per espandere la cartella **Tabelle** .  
  
3.  Fare clic con il pulsante destro del mouse sulla tabella in cui si vogliono modificare le proprietà di un indice e scegliere **Progetta**.  
  
4.  Scegliere **Indici/chiavi** nel menu **Progettazione tabelle**.  
  
5.  Selezionare l'indice che si desidera modificare. Le relative proprietà saranno visualizzate nella griglia principale.  
  
6.  Modificare le impostazioni di tutte le proprietà per personalizzare l'indice.  
  
7.  Scegliere **Chiudi**.  
  
8.  Nel menu **File** scegliere **Salva***nome_tabella*.  
  
#### <a name="to-modify-the-properties-of-an-index-in-object-explorer"></a>Per modificare le proprietà di un indice in Esplora oggetti  
  
1.  In Esplora oggetti fare clic sul segno più per espandere il database contenente la tabella in cui si desidera modificare le proprietà di un indice.  
  
2.  Fare clic sul segno più per espandere la cartella **Tabelle** .  
  
3.  Fare clic sul segno più per espandere la tabella nella quale modificare le proprietà di un indice.  
  
4.  Fare clic sul segno più per espandere la cartella **Indici** .  
  
5.  Fare clic con il pulsante destro del mouse sull'indice di cui si vogliono modificare le proprietà e scegliere **Proprietà**.  
  
6.  In **Selezione pagina**selezionare **Opzioni**.  
  
7.  Modificare le impostazioni di tutte le proprietà per personalizzare l'indice.  
  
8.  Per aggiungere, rimuovere o modificare la posizione di una colonna dell'indice, selezionare la pagina **Generale** della finestra di dialogo **Proprietà indice -** *nome_indice* . Per altre informazioni, vedere [Index Properties F1 Help](index-properties-f1-help.md)  
  
##  <a name="TsqlProcedure"></a> Uso di Transact-SQL  
  
#### <a name="to-see-the-properties-of-all-the-indexes-in-a-table"></a>Per visualizzare le proprietà di tutti gli indici in una tabella  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra delle query e fare clic su **Esegui**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT i.name AS index_name,   
        i.type_desc,   
        i.is_unique,   
        ds.type_desc AS filegroup_or_partition_scheme,   
        ds.name AS filegroup_or_partition_scheme_name,   
        i.ignore_dup_key,   
        i.is_primary_key,   
        i.is_unique_constraint,   
        i.fill_factor,   
        i.is_padded,   
        i.is_disabled,   
        i.allow_row_locks,   
        i.allow_page_locks,   
        i.has_filter,   
        i.filter_definition  
    FROM sys.indexes AS i  
       INNER JOIN sys.data_spaces AS ds ON i.data_space_id = ds.data_space_id  
    WHERE is_hypothetical = 0 AND i.index_id <> 0   
       AND i.object_id = OBJECT_ID('HumanResources.Employee');   
    GO  
  
    ```  
  
#### <a name="to-set-the-properties-of-an-index"></a>Per visualizzare le proprietà di un indice  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare gli esempi seguenti nella finestra Query, quindi fare clic su **Esegui**.  
  
     [!code-sql[IndexDDL#AlterIndex4](../../snippets/tsql/SQL14/tsql/indexddl/transact-sql/alterindex.sql#alterindex4)]  
  
     [!code-sql[IndexDDL#AlterIndex2](../../snippets/tsql/SQL14/tsql/indexddl/transact-sql/alterindex.sql#alterindex2)]  
  
 Per altre informazioni, vedere [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).  
  
  

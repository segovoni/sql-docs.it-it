---
title: Visualizzare proprietà di chiave esterna | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- foreign keys [SQL Server], attributes
- displaying foreign keys attributes
- viewing foreign keys attributes
ms.assetid: b0e57cb7-9b26-4b96-b76a-1f59f5f498c5
caps.latest.revision: 15
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a5266731ce16988dd9ed8dbc82d2f6c002c846ba
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37331361"
---
# <a name="view-foreign-key-properties"></a>Visualizzare Proprietà di chiave esterna
  È possibile visualizzare gli attribuiti della chiave esterna di una relazione in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Security](#Security)  
  
-   **Per visualizzare gli attributi della chiave esterna di una tabella specifica utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../security/metadata-visibility-configuration.md).  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-view-the-foreign-key-attributes-of-a-relationship-in-a-specific-table"></a>Per visualizzare gli attributi della chiave esterna di una relazione in una tabella specifica  
  
1.  Aprire Progettazione tabelle per la tabella contenente la chiave esterna che si vuole visualizzare, fare clic con il pulsante destro del mouse su Progettazione tabelle e scegliere **Relazioni** dal menu di scelta rapida.  
  
2.  Nella finestra di dialogo **Relazioni di chiave esterna** selezionare la relazione con le proprietà che si desidera visualizzare.  
  
 Se le colonne chiave esterna sono correlate a una chiave primaria, le colonne chiave primaria saranno identificate in **Progettazione tabelle** mediante un simbolo di chiave primaria nel selettore di riga.  
  
##  <a name="TsqlProcedure"></a> Uso di Transact-SQL  
  
#### <a name="to-view-the-foreign-key-attributes-of-a-relationship-in-a-specific-table"></a>Per visualizzare gli attributi della chiave esterna di una relazione in una tabella specifica  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra delle query e fare clic su **Esegui**. Nell'esempio vengono restituite tutte le chiavi esterne e le relative proprietà per tabella `HumanResources.Employee` nel database di esempio.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT   
        f.name AS foreign_key_name  
       ,OBJECT_NAME(f.parent_object_id) AS table_name  
       ,COL_NAME(fc.parent_object_id, fc.parent_column_id) AS constraint_column_name  
       ,OBJECT_NAME (f.referenced_object_id) AS referenced_object  
       ,COL_NAME(fc.referenced_object_id, fc.referenced_column_id) AS referenced_column_name  
       ,is_disabled  
       ,delete_referential_action_desc  
       ,update_referential_action_desc  
    FROM sys.foreign_keys AS f  
    INNER JOIN sys.foreign_key_columns AS fc   
       ON f.object_id = fc.constraint_object_id   
    WHERE f.parent_object_id = OBJECT_ID('HumanResources.Employee');  
    ```  
  
 Per altre informazioni, vedere [sys.foreign_keys &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-foreign-keys-transact-sql) e [sys.foreign_key_columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-foreign-key-columns-transact-sql).  
  
###  <a name="TsqlExample"></a>  

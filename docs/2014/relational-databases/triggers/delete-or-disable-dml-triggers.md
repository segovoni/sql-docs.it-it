---
title: Eliminare o disabilitare trigger DML | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- DML triggers, disabling
- removing DML triggers
- disabling DML triggers
- dropping DML triggers
- deleting DML triggers
- DML triggers, removing
ms.assetid: 0f97f953-33c5-4b26-afeb-db2a26ce38b4
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: c1e925f64b3240b4399800a3bbadb054e9f8712d
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37408292"
---
# <a name="delete-or-disable-dml-triggers"></a>Eliminare o disabilitare trigger DML
  In questo argomento viene descritto come eliminare o disabilitare un trigger DML in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Indicazioni](#Recommendations)  
  
     [Security](#Security)  
  
-   **Per eliminare o disabilitare un trigger DML tramite:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Recommendations"></a> Indicazioni  
  
-   Un trigger eliminato viene rimosso dal database corrente, ma la tabella e i dati su cui si basa il trigger non subiscono alcun impatto. L'eliminazione di una tabella comporta automaticamente l'eliminazione di tutti i trigger della tabella.  
  
-   Per impostazione predefinita, un trigger viene abilitato quando viene creato.  
  
-   La disabilitazione di un trigger non ne comporta l'eliminazione. Il trigger continua a esistere come oggetto nel database corrente Il trigger, tuttavia, non viene attivato quando viene eseguita qualsiasi istruzione INSERT, UPDATE o DELETE in cui è stato programmato. I trigger disabilitati possono essere riabilitati. L'abilitazione di un trigger non comporta la sua creazione ex-novo. Il trigger viene attivato allo stesso modo in cui è stato creato in origine.  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
 Per l'eliminazione di un trigger DML è richiesta l'autorizzazione ALTER per la tabella o la vista in cui è definito il trigger.  
  
 Per disabilitare o abilitare un trigger DML, è necessario disporre almeno dell'autorizzazione ALTER per la tabella o la vista per cui il trigger è stato creato.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-delete-a-dml-trigger"></a>Per eliminare un trigger DML  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)] , quindi espanderla.  
  
2.  Espandere il database desiderato, espandere **Tabelle**, quindi espandere la tabella che contiene il trigger da eliminare.  
  
3.  Espandere **Trigger**, fare clic con il pulsante destro del mouse sul trigger da eliminare, quindi fare clic su **Elimina**.  
  
4.  Nella finestra di dialogo **Elimina oggetto** , verificare il trigger da eliminare, quindi fare clic su **OK**.  
  
#### <a name="to-disable-and-enable-a-dml-trigger"></a>Per abilitare e disabilitare un trigger DML  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)] , quindi espanderla.  
  
2.  Espandere il database desiderato, espandere **Tabelle**, quindi espandere la tabella che contiene il trigger da disabilitare.  
  
3.  Espandere **Trigger**, fare clic con il pulsante destro del mouse sul trigger da disabilitare, quindi fare clic su **Disabilita**.  
  
4.  Per abilitare il trigger, fare clic su **Abilita**.  
  
##  <a name="TsqlProcedure"></a> Uso di Transact-SQL  
  
#### <a name="to-delete-a-dml-trigger"></a>Per eliminare un trigger DML  
  
1.  Connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare gli esempi seguenti nella finestra delle query. Per creare il trigger [, eseguire l'istruzione](/sql/t-sql/statements/create-trigger-transact-sql) CREATE TRIGGER `Sales.bonus_reminder` . Per eliminare il trigger, eseguire l'istruzione [DROP TRIGGER](/sql/t-sql/statements/drop-trigger-transact-sql) .  
  
```tsql  
--Create the trigger.  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID(N'Sales.bonus_reminder', N'TR') IS NOT NULL  
    DROP TRIGGER Sales.bonus_reminder;  
GO  
CREATE TRIGGER Sales.bonus_reminder  
ON Sales.SalesPersonQuotaHistory  
WITH ENCRYPTION  
AFTER INSERT, UPDATE   
AS RAISERROR ('Notify Compensation', 16, 10);  
GO  
  
```  
  
```tsql  
--Delete the trigger.  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ('Sales.bonus_reminder', 'TR') IS NOT NULL  
   DROP TRIGGER Sales.bonus_reminder;  
GO  
  
```  
  
#### <a name="to-disable-and-enable-a-dml-trigger"></a>Per abilitare e disabilitare un trigger DML  
  
1.  Connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare gli esempi seguenti nella finestra delle query. Per creare il trigger [, eseguire l'istruzione](/sql/t-sql/statements/create-trigger-transact-sql) CREATE TRIGGER `Sales.bonus_reminder` . Per disabilitare e abilitare il trigger, eseguire le istruzioni [DISABLE TRIGGER](/sql/t-sql/statements/disable-trigger-transact-sql) e [ENABLE TRIGGER](/sql/t-sql/statements/enable-trigger-transact-sql) , rispettivamente.  
  
```tsql  
--Create the trigger.  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID(N'Sales.bonus_reminder', N'TR') IS NOT NULL  
    DROP TRIGGER Sales.bonus_reminder;  
GO  
CREATE TRIGGER Sales.bonus_reminder  
ON Sales.SalesPersonQuotaHistory  
WITH ENCRYPTION  
AFTER INSERT, UPDATE   
AS RAISERROR ('Notify Compensation', 16, 10);  
GO  
  
```  
  
```tsql  
--Disable the trigger.  
USE AdventureWorks2012;  
GO  
DISABLE TRIGGER Sales.bonus_reminder ON Sales.SalesPersonQuotaHistory;  
GO  
  
```  
  
```tsql  
--Enable the trigger.  
USE AdventureWorks2012;  
GO  
ENABLE TRIGGER Sales.bonus_reminder ON Sales.SalesPersonQuotaHistory;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-trigger-transact-sql)   
 [CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql)   
 [DROP TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-trigger-transact-sql)   
 [ENABLE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/enable-trigger-transact-sql)   
 [DISABLE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/disable-trigger-transact-sql)   
 [EVENTDATA &#40;Transact-SQL&#41;](/sql/t-sql/functions/eventdata-transact-sql)   
 [Ottieni informazioni sui trigger DML](dml-triggers.md)   
 [sp_help &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-transact-sql)   
 [sp_helptrigger &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptrigger-transact-sql)   
 [sys.triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-triggers-transact-sql)   
 [sys.trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-trigger-events-transact-sql)   
 [sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql)   
 [sys.assembly_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-assembly-modules-transact-sql)   
 [sys.server_triggers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-triggers-transact-sql)   
 [sys.server_trigger_events &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql)   
 [sys.server_sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql)   
 [sys.server_assembly_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-assembly-modules-transact-sql)  
  
  

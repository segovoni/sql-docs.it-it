---
title: SET SHOWPLAN_TEXT (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SHOWPLAN_TEXT
- SET_SHOWPLAN_TEXT_TSQL
- SET SHOWPLAN_TEXT
- SHOWPLAN_TEXT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- statements [SQL Server], estimates
- execution information and estimates [SQL Server]
- statements [SQL Server], information without processing
- SET SHOWPLAN_TEXT statement
- canceling statement execution
- SHOWPLAN_TEXT option
- stopping statement execution
- estimated execution information [SQL Server]
ms.assetid: 2c4f3fc8-ff2c-4790-8b74-e7e8ef58f9a6
caps.latest.revision: 26
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7abd42acdcbfa4274686d3d8162e727cf36e5ee7
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="set-showplantext-transact-sql"></a>SET SHOWPLAN_TEXT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Impedisce l'esecuzione delle istruzioni [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in Microsoft [!INCLUDE[tsql](../../includes/tsql-md.md)]. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituisce invece informazioni dettagliate sulla modalità di esecuzione delle istruzioni.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SET SHOWPLAN_TEXT { ON | OFF }  
```  
  
## <a name="remarks"></a>Osservazioni  
 L'opzione SET SHOWPLAN_TEXT viene impostata in fase di esecuzione, non in fase di analisi.  
  
 Quando l'opzione SET SHOWPLAN_TEXT è impostata su ON, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituisce informazioni di esecuzione per ogni istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] senza eseguire l'istruzione. Quando l'opzione è impostata su ON, vengono restituite informazioni del piano di esecuzione su tutte le istruzioni [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] successive fino a quando l'opzione non viene reimpostata su OFF. Se, ad esempio, si esegue un'istruzione CREATE TABLE quando l'opzione SET SHOWPLAN_TEXT è impostata su ON, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituisce un messaggio di errore di una successiva istruzione SELECT che interessa la stessa tabella, per informare gli utenti che la tabella specificata non esiste. I successivi riferimenti a tale tabella pertanto hanno esito negativo. Quando l'opzione SET SHOWPLAN_TEXT è impostata su OFF, le istruzioni vengono eseguite da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] senza la generazione di un report contenente informazioni del piano di esecuzione.  
  
 SET SHOWPLAN_TEXT è destinato a restituire output leggibile per le applicazioni di Microsoft Win32 prompt dei comandi, ad esempio il **osql** utilità. L'opzione SET SHOWPLAN_ALL restituisce un output più dettagliato per l'utilizzo in programmi per la gestione di output.  
  
 Non è possibile specificare SET SHOWPLAN_TEXT e SET SHOWPLAN_ALLL all'interno di una stored procedure. Devono essere le uniche istruzioni in un batch.  
  
 L'opzione SET SHOWPLAN_TEXT restituisce informazioni sotto forma di un set di righe in un albero gerarchico che rappresenta i passaggi eseguiti da Query Processor di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per l'esecuzione delle varie istruzioni. Ogni istruzione restituita nell'output include una singola riga contenente il testo dell'istruzione seguita da alcune righe che includono i dettagli dei passaggi dell'esecuzione. Nella tabella seguente vengono illustrate le colonne incluse nell'output.  
  
|Nome colonna|Description|  
|-----------------|-----------------|  
|**StmtText**|Per righe che non sono di tipo PLAN_ROW, questa colonna include il testo dell'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)]. Per righe di tipo PLAN_ROW, include una descrizione dell'operazione. La colonna include l'operatore fisico e facoltativamente l'operatore logico. Può essere inoltre seguita da una descrizione determinata dall'operatore fisico. Per ulteriori informazioni sugli operatori fisici, vedere il **argomento** colonna [SET SHOWPLAN_ALL &#40; Transact-SQL &#41; ](../../t-sql/statements/set-showplan-all-transact-sql.md).|  
  
 Per ulteriori informazioni sugli operatori logici e fisici che possono essere visualizzati nell'output Showplan, vedere [Showplan logici e fisici riferimento a operatori](../../relational-databases/showplan-logical-and-physical-operators-reference.md)  
  
## <a name="permissions"></a>Permissions  
 Per poter utilizzare SET SHOWPLAN_TEXT, è necessario disporre delle autorizzazioni sufficienti per eseguire le istruzioni in cui SET SHOWPLAN_TEXT viene eseguito, nonché l'autorizzazione SHOWPLAN per tutti i database contenenti oggetti di riferimento.  
  
 Per SELECT, INSERT, UPDATE, DELETE, EXEC *stored_procedure*, EXEC e *user_defined_function* istruzioni, per produrre uno Showplan in cui l'utente deve:  
  
-   Autorizzazioni appropriate per l'esecuzione delle istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
-   Autorizzazione SHOWPLAN su tutti i database contenenti oggetti a cui fanno riferimento le istruzioni Transact-SQL, ad esempio tabelle, viste e così via.  
  
 Per tutte le altre istruzioni, ad esempio DDL, USE *database_name*, SET, DECLARE, SQL, dinamico e così via, solo le autorizzazioni appropriate per eseguire il [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzioni sono necessarie.  
  
## <a name="examples"></a>Esempi  
 In questo esempio viene illustrato l'utilizzo degli indici in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] durante l'elaborazione di istruzioni.  
  
 Questa query utilizza un indice:  
  
```  
USE AdventureWorks2012;  
GO  
SET SHOWPLAN_TEXT ON;  
GO  
SELECT *  
FROM Production.Product   
WHERE ProductID = 905;  
GO  
SET SHOWPLAN_TEXT OFF;  
GO  
```  
  
 Set di risultati:  
  
```  
StmtText                                             
---------------------------------------------------  
SELECT *  
FROM Production.Product   
WHERE ProductID = 905;   
  
StmtText                                                                                                                                                                                        
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------  
|--Clustered Index Seek(OBJECT:([AdventureWorks2012].[Production].[Product].[PK_Product_ProductID]), SEEK:([AdventureWorks2012].[Production].[Product].[ProductID]=CONVERT_IMPLICIT(int,[@1],0)) ORDERED FORWARD)   
```  
  
 Questa query non utilizza un indice:  
  
```  
USE AdventureWorks2012;  
GO  
SET SHOWPLAN_TEXT ON;  
GO  
SELECT *  
FROM Production.ProductCostHistory  
WHERE StandardCost < 500.00;  
GO  
SET SHOWPLAN_TEXT OFF;  
GO  
```  
  
 Set di risultati:  
  
```  
StmtText                                                                  
------------------------------------------------------------------------  
SELECT *  
FROM Production.ProductCostHistory  
WHERE StandardCost < 500.00;   
  
StmtText                                                                                                                                                                                                  
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------  
|--Clustered Index Scan(OBJECT:([AdventureWorks2012].[Production].[ProductCostHistory].[PK_ProductCostHistory_ProductCostID]), WHERE:([AdventureWorks2012].[Production].[ProductCostHistory].[StandardCost]<[@1]))  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Operatori &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [Istruzioni SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET SHOWPLAN_ALL &#40; Transact-SQL &#41;](../../t-sql/statements/set-showplan-all-transact-sql.md)  
  
  

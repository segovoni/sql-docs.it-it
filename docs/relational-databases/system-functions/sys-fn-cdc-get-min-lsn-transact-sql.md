---
title: sys.fn_cdc_get_min_lsn (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server (starting with 2008)
f1_keywords:
- sys.fn_cdc_get_min_lsn
- fn_cdc_get_min_lsn
- fn_cdc_get_min_lsn_TSQL
- sys.fn_cdc_get_min_lsn_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- fn_cdc_get_min_lsn
- sys.fn_cdc_get_min_lsn
ms.assetid: bd49e28a-128b-4f6b-8545-6a2ec3f4afb3
caps.latest.revision: 17
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 4c4c6a9bf83e83628891104f0c95a6baefa08234
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33230442"
---
# <a name="sysfncdcgetminlsn-transact-sql"></a>sys.fn_cdc_get_min_lsn (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce il valore della colonna start_lsn per l'istanza di acquisizione specificata il [change_tables](../../relational-databases/system-tables/cdc-change-tables-transact-sql.md) tabella di sistema. Questo valore rappresenta l'endpoint inferiore dell'intervallo di validità per l'istanza di acquisizione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sys.fn_cdc_get_min_lsn ( 'capture_instance_name' )  
```  
  
## <a name="arguments"></a>Argomenti  
 **'** *capture_instance_name* **'**  
 Nome dell'istanza di acquisizione. *capture_instance_name* viene **sysname**.  
  
## <a name="return-types"></a>Tipi restituiti  
 **binary(10)**  
  
## <a name="remarks"></a>Osservazioni  
 Restituisce 0x00000000000000000000 quando l'istanza di acquisizione non esiste o quando il chiamante non è autorizzato ad accedere ai dati delle modifiche associati all'istanza di acquisizione.  
  
 Questa funzione è utilizzata in genere per identificare l'endpoint inferiore della cronologia dell'acquisizione dei dati delle modifiche associati a un'istanza di acquisizione. È inoltre possibile utilizzare questa funzione per verificare che gli endpoint di una query di intervallo si trovino all'interno della cronologia dell'istanza di acquisizione prima di richiedere i dati delle modifiche. È importante eseguire tali controlli perché l'endpoint inferiore di un'istanza di acquisizione cambia quando viene eseguito il processo di pulizia sulle tabelle delle modifiche. Se il tempo tra le richieste dei dati delle modifiche è significativo, anche un endpoint inferiore impostato sull'endpoint superiore della richiesta precedente dei dati delle modifiche potrebbe cadere al di fuori della cronologia corrente.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza al ruolo predefinito del server sysadmin o al ruolo predefinito del database db_owner. Per tutti gli altri utenti, è richiesta l'autorizzazione SELECT su tutte le colonne acquisite nella tabella di origine e, se è stato definito un ruolo di controllo per l'istanza di acquisizione, l'appartenenza a tale ruolo del database.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-returning-the-minimum-lsn-value-for-a-specified-capture-instance"></a>A. Recupero del valore LSN minimo per un'istanza di acquisizione specificata  
 Nell'esempio seguente viene restituito il valore LSN minimo per l'istanza di acquisizione `HumanResources_Employee` nel database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```  
USE AdventureWorks2-12;  
GO  
SELECT sys.fn_cdc_get_min_lsn ('HumanResources_Employee')AS min_lsn;  
  
```  
  
### <a name="b-verifying-the-low-endpoint-of-a-query-range"></a>B. Verifica dell'endpoint inferiore di una query di intervallo  
 Nell'esempio seguente è utilizzato il valore LSN minimo restituito da `sys.fn_cdc_get_min_lsn` per verificare che l'endpoint inferiore proposto per una query che modifica dei dati sia valido per la cronologia corrente per l'istanza di acquisizione `HumanResources_Employee`. Questo esempio presuppone che il numero LSN dell'endpoint superiore precedente per l'istanza di acquisizione sia stato salvato e sia disponibile per impostare la variabile `@save_to_lsn`. Per gli scopi di questo esempio, `@save_to_lsn` è impostato su 0x000000000000000000 per forzare l'esecuzione della sezione della gestione degli errori.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @min_lsn binary(10), @from_lsn binary(10),@save_to_lsn binary(10), @to_lsn binary(10);  
-- Sets @save_to_lsn to the previous high endpoint saved from the last change data request.  
SET @save_to_lsn = 0x000000000000000000;  
-- Sets the upper endpoint for the query range to the current maximum LSN.  
SET @to_lsn = sys.fn_cdc_get_max_lsn();  
-- Sets the @min_lsn parameter to the current minimum LSN for the capture instance.  
SET @min_lsn = sys.fn_cdc_get_min_lsn ('HumanResources_Employee');  
-- Sets the low endpoint for the query range to the LSN that follows the previous high endpoint.  
SET @from_lsn = sys.fn_cdc_increment_lsn(@save_to_lsn);  
-- Tests to verify the low endpoint is valid for the current capture instance.  
IF (@from_lsn < @min_lsn)  
    BEGIN  
        RAISERROR('Low endpoint of the request interval is invalid.', 16, -1);  
    END  
ELSE  
-- Return the changes occurring within the query range.  
    SELECT * FROM cdc.fn_cdc_get_all_changes_HumanResources_Employee(@from_lsn, @to_lsn, 'all');  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sys.fn_cdc_get_max_lsn &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-cdc-get-max-lsn-transact-sql.md)   
 [Log delle transazioni &#40;SQL Server&#41;](../../relational-databases/logs/the-transaction-log-sql-server.md)  
  
  

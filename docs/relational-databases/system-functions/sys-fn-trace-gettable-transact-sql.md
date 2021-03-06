---
title: sys.fn_trace_gettable (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- fn_trace_gettable
- fn_trace_gettable_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- fn_trace_gettable function
- sys.fn_trace_gettable function
ms.assetid: c2590159-6ec5-4510-81ab-e935cc4216cd
caps.latest.revision: 35
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 4e8c573a9995ee8ca0d23cd89ab2e032a88c6f9e
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38014929"
---
# <a name="sysfntracegettable-transact-sql"></a>sys.fn_trace_gettable (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce il contenuto di uno o più file di traccia in formato tabulare.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] In alternativa, usare Eventi estesi.  
   
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
fn_trace_gettable ( 'filename' , number_files )  
```  
  
## <a name="arguments"></a>Argomenti  
 «*filename*»  
 Specifica il file di traccia iniziale da leggere. *nome file* viene **nvarchar(256)**, non prevede alcun valore predefinito.  
  
 *number_files*  
 Specifica il numero di file di rollover da leggere. Questo numero include il file iniziale specificato *filename*. *number_files* è un **int**.  
  
## <a name="remarks"></a>Note  
 Se *number_files* è specificato come **predefinita**, **fn_trace_gettable** legge tutti i file di rollover fino a quando non raggiunge la fine della traccia. **fn_trace_gettable** restituisce una tabella con tutte le colonne valide per la traccia specificata. Per altre informazioni, vedere [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md).  
  
 Tenere presente che la funzione fn_trace_gettable non caricherà file di rollover (quando questa opzione viene specificata tramite il *number_files* argomento) in cui il nome di file di traccia originale termina con un carattere di sottolineatura e un valore numerico. Ciò non vale per il carattere di sottolineatura e il numero che vengono aggiunti automaticamente all'esecuzione del rollover di un file. Come soluzione alternativa, è possibile rinominare i file di traccia in modo da rimuovere i caratteri di sottolineatura nel nome del file originale. Ad esempio, se il file originale è denominato **Trace_Oct_5.trc** e il file di rollover è denominato **Trace_Oct_5_1.trc**, è possibile rinominare i file da **TraceOct5.trc** e **TraceOct5_1.trc**.  
  
 Questa funzione consente di leggere una traccia ancora attiva nell'istanza in cui viene eseguita.  
  
## <a name="permissions"></a>Autorizzazioni  
 È necessario disporre dell'autorizzazione ALTER TRACE nel server.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-fntracegettable-to-import-rows-from-a-trace-file"></a>A. Utilizzo di fn_trace_gettable per importare righe da un file di traccia  
 Nell'esempio seguente viene chiamato `fn_trace_gettable` all'interno della clausola `FROM` di un'istruzione `SELECT...INTO`.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT * INTO temp_trc  
FROM fn_trace_gettable('c:\temp\mytrace.trc', default);  
GO  
```  
  
### <a name="b-using-fntracegettable-to-return-a-table-with-an-identity-column-that-can-be-loaded-into-a-sql-server-table"></a>B. Utilizzo di fn_trace_gettable per restituire una tabella con una colonna IDENTITY che può essere caricata in una tabella di SQL Server  
 Nell'esempio seguente questa funzione viene chiamata all'interno di un'istruzione `SELECT...INTO` e viene restituita una tabella con una colonna `IDENTITY` che può essere caricata nella tabella `temp_trc`.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT IDENTITY(int, 1, 1) AS RowNumber, * INTO temp_trc  
FROM fn_trace_gettable('c:\temp\mytrace.trc', default);  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_trace_generateevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [sp_trace_setfilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)   
 [sp_trace_setstatus &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)  
  
  

---
title: Estensioni specifiche SQL Server In-Process per ADO.NET | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.suite: sql
ms.technology: clr
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data access [CLR integration]
- ADO.NET [CLR integration]
- common language runtime [SQL Server], ADO.NET
- database objects [CLR integration], in-process extensions
- in-process data access providers [CLR integration]
- extensions [CLR integration]
ms.assetid: 781b812e-eb14-472a-85fa-aa4cdb929bee
caps.latest.revision: 33
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 1d7e7dd5f40be276cf9cd3308d50f1c449aa343d
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37350899"
---
# <a name="sql-server-in-process-specific-extensions-to-adonet"></a>Estensioni specifiche in-process di SQL Server ad ADO.NET
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Sono disponibili quattro estensioni funzionali principali ad ADO.NET specifiche per l'utilizzo in-process. Tali estensioni verranno analizzate dettagliatamente negli argomenti seguenti.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 [Oggetto SqlContext](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqlcontext-object.md)  
 Questa classe fornisce accesso alle altre estensioni mediante l'astrazione del contesto di un chiamante di una routine di SQL Server che esegue codice gestito in-process.  
  
 [Oggetto SqlPipe](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqlpipe-object.md)  
 Questa classe contiene routine per l'invio di risultati tabulari e messaggi al client.  
  
 [Oggetto SqlTriggerContext](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqltriggercontext-object.md)  
 Questa classe fornisce informazioni sul contesto nel quale viene eseguito un trigger.  
  
 [Oggetto SqlDataRecord](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqldatarecord-object.md)  
 La classe SqlDataRecord rappresenta una sola riga di dati, insieme ai rispettivi metadati correlati, e consente alle stored procedure di restituire set di risultati personalizzati al client.  
  
  

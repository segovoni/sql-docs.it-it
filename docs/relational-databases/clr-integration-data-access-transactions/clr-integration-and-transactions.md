---
title: Integrazione con CLR e transazioni | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: clr
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ADO.NET [CLR integration]
- common language runtime [SQL Server], ADO.NET
- managed code [SQL Server], transactions
- common language runtime [SQL Server], transactions
- System.Transactions namespace
- transactions [CLR integration]
ms.assetid: 381d206e-06e2-48d0-8206-295fcf06ac98
caps.latest.revision: 19
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: f928519eb9a94d59210c826311d187c717edf054
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37356153"
---
# <a name="clr-integration-and-transactions"></a>Integrazione con CLR e transazioni
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Il **System. Transactions** spazio dei nomi fornisce un framework per le transazioni completamente integrato con ADO.NET e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] integrazione common language runtime (CLR). **System. Transactions** e ADO.NET utilizzati congiuntamente per estendere e semplificare l'utilizzo di transazioni distribuite e locali nelle applicazioni gestite.  
  
> [!NOTE]  
>  Una procedura CLR definita dall'utente non può stabilire una connessione allo stesso server nel quale viene eseguita, ovvero una connessione loopback, ed essere integrata nella stessa transazione. Un eventuale tentativo di connessione verrà bloccato e il controllo non verrà restituito alla procedura definita dall'utente. Verrà pertanto generato un errore di timeout (messaggio 1206) nella procedura definita dall'utente.  
  
 Per ulteriori informazioni sulle transazioni e su .NET Framework, vedere gli argomenti relativi all'esecuzione e all'utilizzo di transazioni in .NET Framework SDK.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 [Promozione delle transazioni](../../relational-databases/clr-integration-data-access-transactions/transaction-promotion.md)  
 Viene illustrata la possibilità di promuovere le transazioni e viene spiegato come utilizzare tale caratteristica.  
  
 [Accesso alla transazione corrente](../../relational-databases/clr-integration-data-access-transactions/accessing-the-current-transaction.md)  
 Viene illustrato come accedere a una transazione attualmente in esecuzione in-process in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Uso di System.Transactions](../../relational-databases/clr-integration-data-access-transactions/using-system-transactions.md)  
 Viene descritto come utilizzare il **System. Transactions** API application programming interface () nell'applicazione gestita.  
  
 [Durata delle transazioni](../../relational-databases/clr-integration-data-access-transactions/transaction-lifetimes.md)  
 Viene illustrata la differenza in termini di durata tra le transazioni avviate in stored procedure [!INCLUDE[tsql](../../includes/tsql-md.md)] e quelle avviate in applicazioni CLR.  
  
## <a name="see-also"></a>Vedere anche  
 [Accesso ai dati da oggetti di database CLR](../../relational-databases/clr-integration/data-access/data-access-from-clr-database-objects.md)  
  
  

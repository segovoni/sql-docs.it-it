---
title: Collegamenti nella sicurezza dell'integrazione CLR | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-access links [CLR integration]
- security [CLR integration]
- invocation links [CLR integration]
- gated links [CLR integration]
ms.assetid: 168efd01-d12e-4bdf-a1b3-0b5c76474eaf
caps.latest.revision: 37
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 58f1d4ada74d7d64b9a5c44060f0cdd0fce8fcce
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37243101"
---
# <a name="links-in-clr-integration-security"></a>Collegamenti nella sicurezza per l'integrazione con CLR
  In questa sezione viene descritto il modo in cui frammenti di codice utente possono effettuare chiamate reciproche in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], utilizzando [!INCLUDE[tsql](../../includes/tsql-md.md)] o uno dei linguaggi gestiti. Queste relazioni tra oggetti vengono definite collegamenti.  
  
## <a name="invocation-links"></a>Collegamenti di chiamata  
 I collegamenti di chiamata corrispondono a una chiamata di codice effettuata da un utente che chiama un oggetto, ad esempio un batch [!INCLUDE[tsql](../../includes/tsql-md.md)] che chiama una stored procedure, o da una funzione o stored procedure CLR (Common Language Runtime). Tali collegamenti comportano il controllo di un'autorizzazione `EXECUTE` per il chiamato.  
  
## <a name="table-access-links"></a>Collegamenti di accesso alle tabelle  
 I collegamenti di accesso alle tabelle corrispondono al recupero o alla modifica dei valori in una tabella, una visualizzazione o una funzione con valori di tabella. Sono simili ai collegamenti di chiamata, con l'eccezione che dispongono di un controllo di accesso con granularità fine per le autorizzazioni SELECT, INSERT, UPDATE e DELETE.  
  
## <a name="gated-links"></a>Collegamenti controllati  
 I collegamenti controllati indicano che durante l'esecuzione non viene effettuato il controllo delle autorizzazioni all'interno della relazione tra gli oggetti stabilita. Quando è presente un collegamento controllato tra due oggetti (ad esempio, di oggetti **x** e l'oggetto **y**), le autorizzazioni sull'oggetto **y** e altri oggetti accessibili dall'oggetto **y** vengono controllati solo al momento della creazione dell'oggetto **x**. Al momento della creazione dell'oggetto **x**, `REFERENCE` autorizzazione viene controllata nel **y** per il proprietario di **x**. In fase di esecuzione (ad esempio, quando un utente chiama oggetto **x**), non sono disponibili autorizzazioni confrontate **y** o altri oggetti cui fa riferimento in modo statico. In fase di esecuzione, un'autorizzazione appropriata verrà controllata con l'oggetto **x** stesso.  
  
 I collegamenti controllati vengono sempre utilizzati con la dipendenza dei metadati tra due oggetti. Tale dipendenza è una relazione stabilita nei cataloghi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che impedisce che un oggetto venga eliminato finché un altro oggetto dipende da questo.  
  
 I collegamenti controllati sono utili quando non è consigliabile o possibile concedere autorizzazioni a molti oggetti dipendenti. I collegamenti controllati vengono introdotti tra oggetti che definiscono punti di ingresso [!INCLUDE[tsql](../../includes/tsql-md.md)] in assembly CLR, ad esempio procedure CLR, trigger, funzioni, tipi e aggregati, e gli assembly da cui sono definiti. La sicurezza controllata per questi oggetti implica che per poter richiamare un punto di ingresso [!INCLUDE[tsql](../../includes/tsql-md.md)] definito in un assembly CLR, il chiamante deve disporre solo di un'autorizzazione appropriata su tale punto di ingresso [!INCLUDE[tsql](../../includes/tsql-md.md)]. Non è necessario che disponga di autorizzazioni su tale assembly o su qualsiasi altro assembly a cui riferimento in modo statico. Le autorizzazioni sull'assembly vengono controllate durante la creazione del punto di ingresso [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
## <a name="sql-server-authorization-based-security"></a>Sicurezza basata sulle autorizzazioni SQL Server  
 Di seguito sono riportate le regole di base dei controlli di sicurezza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per le chiamate di e tra oggetti di database basati su CLR. Le prime tre regole definiscono le autorizzazioni controllate e l'oggetto in base al quale vengono controllate, mentre la quarta regola definisce il contesto di esecuzione in base al quale viene controllata l'autorizzazione.  
  
1.  Tutte le chiamate richiedono l'autorizzazione `EXECUTE`, a meno che non vengano effettuate all'interno dello stesso oggetto e pertanto, trattandosi di chiamate all'interno dello stesso assembly, non richiedono alcun controllo delle autorizzazioni. L'autorizzazione viene controllata in fase di esecuzione.  
  
2.  I collegamenti controllati richiedono l'autorizzazione `REFERENCE` per il chiamato quando viene creato l'oggetto chiamante. Durante la creazione dell'oggetto, viene effettuato il controllo dell'autorizzazione per il proprietario dell'oggetto chiamante.  
  
3.  I collegamenti di accesso alle tabelle richiedono l'autorizzazione `SELECT`, `INSERT`, `UPDATE` o `DELETE` corrispondente per la tabella o la visualizzazione a cui si accede.  
  
4.  Viene effettuato il controllo dell'autorizzazione per il contesto di esecuzione corrente. È possibile creare procedure e funzioni con un contesto di esecuzione diverso da quello del chiamante. Gli assembly vengono sempre creati con il contesto di esecuzione della procedura, della funzione o del trigger definito per essi.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza per l'integrazione con CLR](../../relational-databases/clr-integration/security/clr-integration-security.md)  
  
  

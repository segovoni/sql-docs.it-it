---
title: Esecuzione diretta | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ODBC applications, statements
- direct execution [ODBC]
- SQLExecDirect function
- statements [ODBC], direct execution
ms.assetid: fa36e1af-ed98-4abc-97c1-c4cc5d227b29
caps.latest.revision: 37
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4f8de566fbac1f94d3aef5cb5e63130834d728c4
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37415040"
---
# <a name="direct-execution"></a>Esecuzione diretta
  L'esecuzione diretta rappresenta la modalità più semplice di esecuzione di un'istruzione. Un'applicazione viene compilata una stringa di caratteri contenente un' [!INCLUDE[tsql](../../../includes/tsql-md.md)] istruzione che viene inviata per l'esecuzione mediante il **SQLExecDirect** (funzione). Dopo avere raggiunto il server, l'istruzione viene compilata da [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in un piano di esecuzione, che viene quindi immediatamente eseguito.  
  
 L'esecuzione diretta viene in genere utilizzata dalle applicazioni che compilano ed eseguono istruzioni in fase di esecuzione e rappresenta il metodo più efficiente per le istruzioni eseguite una sola volta. Lo svantaggio con molti database consiste nel fatto che l'istruzione SQL deve essere analizzata e compilata ogni volta che viene eseguita determinando un aumento dell'overhead se l'istruzione viene eseguita più volte.  
  
 In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vengono notevolmente migliorate le prestazioni dell'esecuzione diretta delle istruzioni utilizzate più di frequente negli ambienti multiutente e l'utilizzo di SQLExecDirect con gi marcatori di parametro per le istruzioni SQL utilizzate più di frequente si avvicina all'efficienza dell'esecuzione preparata.  
  
 Quando si è connessi a un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] driver ODBC Native Client utilizza [sp_executesql](/sql/relational-databases/system-stored-procedures/sp-executesql-transact-sql) trasmettere l'istruzione SQL o il batch specificato in **SQLExecDirect**. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ha la logica per determinare rapidamente se un'istruzione SQL o un batch eseguito con **sp_executesql** corrisponde all'istruzione o batch che ha generato un piano di esecuzione che esiste già in memoria. Se esiste una corrispondenza, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] riutilizza semplicemente il piano esistente anziché compilarne uno nuovo. Ciò significa che in genere eseguite istruzioni SQL eseguite con **SQLExecDirect** in un sistema con molti utenti trarranno vantaggio da molti dei vantaggi che erano disponibili per le stored procedure nelle versioni precedenti di soloilriutilizzodelpiano[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Il vantaggio di riutilizzare i piani di esecuzione è valido solo quando più utenti eseguono lo stesso batch o la stessa istruzione SQL. Rispettare le seguenti convenzioni di scrittura del codice per aumentare la probabilità che le istruzioni SQL eseguite da client diversi siano simili abbastanza per potere riutilizzare i piani di esecuzione:  
  
-   Non includere costanti di dati nelle istruzioni SQL; utilizzare invece i marcatori di parametro associati alle variabili di programma. Per altre informazioni, vedere [usando parametri dell'istruzione](../using-statement-parameters.md).  
  
-   Utilizzare nomi di oggetto completi. I piani di esecuzione non vengono riutilizzati se i nomi di oggetto non sono completi.  
  
-   Se possibile, utilizzare per le connessioni dell'applicazione un set comune di opzioni dell'istruzione e di connessione. I piani di esecuzione generati per una connessione con un set di opzioni, ad esempio ANSI_NULLS, non vengono riutilizzati per una connessione con un altro set di opzioni. Il driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client e il provider ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client hanno le stesse impostazioni predefinite per queste opzioni.  
  
 Se tutte le istruzioni eseguite con **SQLExecDirect** vengono codificate utilizzando tali convenzioni, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] quando qualora si possono riutilizzare i piani di esecuzione.  
  
## <a name="see-also"></a>Vedere anche  
 [L'esecuzione di istruzioni &#40;ODBC&#41;](executing-statements-odbc.md)  
  
  

---
title: SQLNumResultCols | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLNumResultCols function
ms.assetid: f79d8b3c-521e-4e50-a564-21d73ae5767b
caps.latest.revision: 33
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3c1a4825dc8d73f815f6b399c6e3a51c064d3b9b
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37424320"
---
# <a name="sqlnumresultcols"></a>SQLNumResultCols
  Per le istruzioni eseguite, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client controlla il server per segnalare il numero di colonne in un set di risultati. In questo caso, `SQLNumResultCols` genera un round trip del server. Ad esempio [SQLDescribeCol](sqldescribecol.md) e [SQLColAttribute](sqlcolattribute.md), la chiamata `SQLNumResultCols` via preparate, ma le istruzioni non eseguite genera un round trip del server.  
  
 Quando un'istruzione o un batch di istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] restituisce più set di righe di risultati, è possibile che il numero di colonne del set di risultati cambi da un set all'altro. `SQLNumResultCols` deve essere chiamato per ogni set. Quando il numero di colonne cambia, l'applicazione deve riassociare i valori dei dati prima di recuperare i risultati delle righe. Per altre informazioni sulla gestione di più risultati set restituiti, vedere [SQLMoreResults](sqlmoreresults.md).  
  
 Miglioramenti apportati al motore di database a partire da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] consentire SQLNumResultCols ottenere descrizioni più accurate dei risultati previsti. Questi risultati più accurati differiscano dai valori restituiti da SQLNumResultCols nelle versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per altre informazioni, vedere [individuazione dei metadati](../native-client/features/metadata-discovery.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione SQLNumResultCols](http://go.microsoft.com/fwlink/?LinkId=59359)   
 [Dettagli di implementazione dell'API ODBC](odbc-api-implementation-details.md)  
  
  

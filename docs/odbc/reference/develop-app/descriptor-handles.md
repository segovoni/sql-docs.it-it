---
title: Gli handle di descrittore | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- application parameter descriptor [ODBC]
- automatically allocated descriptors [ODBC]
- implementation row descriptor [ODBC]
- descriptor handles [ODBC]
- handles [ODBC], descriptor
- implementation parameter descriptor [ODBC]
- apd [ODBC]
- ard [ODBC]
- explicitly allocated descriptors [ODBC]
- ipd [ODBC]
- ird [ODBC]
- application row descriptor [ODBC]
ms.assetid: 7741035c-f3e7-4c89-901e-fe528392f67d
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 791a28ece56894c8bbe9167c8e2445da32c3e07b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32912626"
---
# <a name="descriptor-handles"></a>Handle di descrittore
Oggetto *descrittore* è una raccolta di metadati che descrivono i parametri di un'istruzione SQL o le colonne di un set di risultati, come illustrato per l'applicazione o il driver (noto anche come il *implementazione*). Di conseguenza, un descrittore può compilare uno qualsiasi dei quattro ruoli:  
  
-   **Descrittore del parametro dell'applicazione (APD).** Contiene informazioni sui buffer di applicazione associate ai parametri in un'istruzione SQL, ad esempio i relativi tipi di dati C, indirizzi e lunghezze.  
  
-   **Descrizione del parametro di implementazione (IPD).** Contiene informazioni sui parametri in un'istruzione SQL, ad esempio i tipi di dati SQL, lunghezze e supporto di valori null.  
  
-   **Descrittore della riga di applicazione (ARD).** Contiene informazioni sui buffer di applicazione associati alle colonne del set di risultati, ad esempio i relativi tipi di dati C, indirizzi e lunghezze.  
  
-   **Descrittore della riga di implementazione (IRD).** Contiene informazioni sulle colonne in un set di risultati, ad esempio i tipi di dati SQL, lunghezze e supporto di valori null.  
  
 Descrittori (un riempimento di ogni ruolo) vengono allocati automaticamente quando un'istruzione viene allocata. Questi sono conosciuti come *allocato automaticamente descrittori* e sono sempre associati a tale istruzione. Le applicazioni possono anche allocare descrittori con **SQLAllocHandle**. Questi sono conosciuti come *allocato in modo esplicito i descrittori*. Essi vengono allocate in una connessione e può essere associati a una o più istruzioni in tale connessione per soddisfare il ruolo di un APD o ARD in tali istruzioni.  
  
 La maggior parte delle operazioni in ODBC possono essere eseguite senza l'utilizzo esplicito di descrittori di dall'applicazione. Tuttavia, i descrittori forniscono un comodo collegamento per alcune operazioni. Si supponga, ad esempio, che un'applicazione si desidera inserire i dati da due diversi set di buffer. Per utilizzare il primo set di buffer, viene chiamato ripetutamente **SQLBindParameter** per associarle a parametri in un **inserire** istruzione e quindi eseguire l'istruzione. Per utilizzare il secondo set di buffer, è necessario ripetere questo processo. In alternativa, è possibile impostare le associazioni per il primo set di buffer in un descrittore e il secondo set di buffer nel descrittore di un altro. Per passare tra i set di associazioni, l'applicazione chiama semplicemente **SQLSetStmtAttr** e associare il descrittore corretto con l'istruzione come APD.  
  
 Per ulteriori informazioni sui descrittori, vedere [tipi di descrittori](../../../odbc/reference/develop-app/types-of-descriptors.md).

---
title: È il risultato creato? | Microsoft Docs
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
- result sets [ODBC], determining if created
ms.assetid: 4a83b8cb-2d57-4e64-b497-80bd587ee1f9
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0736ddcd39ce75b83dbbb4d6e0a8fc500073dd19
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32916046"
---
# <a name="was-a-result-set-created"></a>È il risultato creato?
Nella maggior parte dei casi, i programmatori di applicazioni sapere se le istruzioni in cui che viene eseguita l'applicazione crea un set di risultati. Questo è il caso se l'applicazione Usa istruzioni SQL hard-coded scritte dal programmatore. In genere si verifica quando l'applicazione crea istruzioni SQL in fase di esecuzione: il programmatore facilmente può includere codice che consente di contrassegnare se un **selezionare** istruzione o un **inserire** istruzione è in corso costruito. In alcuni casi, il programmatore non è possibile conoscere se un'istruzione crea un set di risultati. Ciò è vero se l'applicazione consente all'utente di immettere ed eseguire un'istruzione SQL. È anche true quando l'applicazione crea un'istruzione in fase di esecuzione per eseguire una stored procedure.  
  
 In questi casi, l'applicazione chiama **SQLNumResultCols** per determinare il numero di colonne nel set di risultati. Se questo è 0, l'istruzione non ha creato un set di risultati. in caso di qualsiasi altro numero, l'istruzione ha creato un set di risultati.  
  
 L'applicazione può chiamare **SQLNumResultCols** in qualsiasi momento dopo la preparazione o l'esecuzione dell'istruzione. Tuttavia, poiché alcune origini dati non sono facilmente descrive i set di risultati che verranno creati per le istruzioni preparate, le prestazioni risulteranno ridotte se **SQLNumResultCols** viene chiamato dopo che un'istruzione preparata ma prima che venga eseguito.  
  
 Alcune origini dati supportano anche il numero di righe restituito da un'istruzione SQL in un set di risultati. A tale scopo, l'applicazione chiama **SQLRowCount**. Esattamente ciò che rappresenta il conteggio delle righe è indicato dall'impostazione dell'opzione SQL_DYNAMIC_CURSOR_ATTRIBUTES2, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2, SQL_KEYSET_CURSOR_ATTRIBUTES2 o SQL_STATIC_CURSOR_ATTRIBUTES2 (a seconda del tipo di cursore) restituito da una chiamata a **SQLGetInfo**. La maschera di bit indica per ogni tipo di cursore, se il conteggio delle righe restituito è esatto, approssimativi o non è disponibile in tutti. Se il conteggio delle righe per statici o basati su keyset interessati dalle modifiche apportate tramite **SQLBulkOperations** o **SQLSetPos**, o per gli aggiornamenti posizionati o le istruzioni delete, dipende da altri bit restituito dagli stessi argomenti opzione elencati in precedenza. Per ulteriori informazioni, vedere il [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) descrizione della funzione.

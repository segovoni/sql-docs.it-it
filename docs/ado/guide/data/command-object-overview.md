---
title: Comando oggetto Panoramica | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- command object [ADO]
ms.assetid: e84a14b1-3c2a-4f7d-a966-9e08a93948df
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8d2d4eafc42e67f67b4f95c8493521f4204bc746
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35270200"
---
# <a name="command-object-overview"></a>Panoramica dell'oggetto Command
Con un **comando** dell'oggetto, è possibile eseguire le operazioni seguenti:  
  
-   Definire il testo del comando (ad esempio, un'istruzione SQL o una stored procedure) eseguibile tramite la **CommandText** proprietà.  
  
-   Definire le query con parametri o argomenti di stored procedure utilizzando **parametro** oggetti e **parametri** insieme.  
  
-   Eseguire un comando e restituire un **Recordset** oggetto, se appropriato, utilizzando il **Execute** metodo.  
  
-   Specificare il tipo di comando utilizzando il **CommandType** proprietà prima dell'esecuzione per ottimizzare le prestazioni.  
  
-   Specificare le informazioni specifiche del testo del comando utilizzando il **sottolinguaggio** proprietà del **comando** oggetto.  
  
-   Controllare se il provider Salva una versione preparata (compilata o) del comando prima dell'esecuzione utilizzando il **Prepared** proprietà.  
  
-   Impostare il numero di secondi di attesa per un comando da eseguire utilizzando un provider di **CommandTimeout** proprietà.  
  
-   Associare una connessione aperta con un **comando** oggetto impostando il relativo **ActiveConnection** proprietà.  
  
-   Impostare il **nome** proprietà per identificare il **comando** oggetto come un metodo sull'oggetto associato **connessione** oggetto.  
  
-   Passare un **comando** dell'oggetto per il **origine** proprietà di un **Recordset** per ottenere i dati.  
  
-   Passare un **flusso** oggetto che contiene un comando (ad esempio, un comando XML) a un provider che lo supporta.

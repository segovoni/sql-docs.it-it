---
title: Structured Query Language (SQL) | Microsoft Docs
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
- SQL [ODBC]
- SQL [ODBC], about SQL
- ODBC [ODBC], SQL
ms.assetid: bebfd93e-0dc0-46b3-a531-518beb7ea976
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a32983b1dd4faaa64c09f5ccc773fd4ce78f3533
ms.sourcegitcommit: 731c5aed039607a8df34c63e780d23a8fac937e1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/07/2018
ms.locfileid: "37909551"
---
# <a name="structured-query-language-sql"></a>Structured Query Language (SQL)
Un tipico DBMS consente agli utenti di archiviare, accedere e modificare i dati in modo efficiente e organizzato. Gli utenti del DBMS erano originariamente, i programmatori. L'accesso ai dati archiviati, è necessario scrivere un programma in un linguaggio di programmazione, ad esempio COBOL. Mentre questi programmi sono stati spesso scritti per presentare un'interfaccia utente semplice a un utente non tecniche, i servizi di un programmatore esperto necessario l'accesso ai dati stessi. Accesso casuale ai dati non è pratico.  
  
 Gli utenti non erano del tutto soddisfatti questa situazione. Mentre si è stato possibile accedere ai dati, spesso necessario convincere un programmatore DBMS per scrivere un software speciale. Ad esempio, se un reparto vendite desidera visualizzare le vendite totali del mese precedente da ognuno dei relativi agenti e volevo queste informazioni classificate in ordine in base alla lunghezza di ogni venditore del servizio all'interno della società, avevano due opzioni: entrambi un programma che esiste già le informazioni a cui accedere esattamente in questo modo è consentito, o il reparto era necessario chiedere a un programmatore di scrivere un programma di questo tipo. In molti casi, questo era più lavoro era la pena, ed era sempre una soluzione costosa per le richieste una tantum o ad hoc. Poiché più utenti voleva un facile accesso, questo problema sono aumentate sempre maggiori.  
  
 Consentendo agli utenti di accedere ai dati in base ad hoc, è necessario concedere loro un linguaggio per esprimere le proprie richieste. Una singola richiesta a un database viene definita come una query. un linguaggio di questo tipo viene chiamato un linguaggio di query. Molti linguaggi di query sono stati sviluppati per questo scopo, ma uno di questi è diventato più diffusi: Structured Query Language, ha inventato IBM nel 1970s. È più comunemente noto agli relativo acronimo, SQL e si pronuncia sia come "ess-cue-ell" come "aggiungere". SQL è diventato un ANSI standard in 1986 e un'immagine ISO standard nel 1987; viene utilizzato oggi in un ottimo molti sistemi di gestione di database.  
  
 Sebbene SQL consente di risolvere le esigenze degli utenti ad hoc, la necessità di accesso ai dati da programmi per computer non più visualizzata. In effetti, la maggior parte dell'accesso al database comunque (e) a livello di codice, sotto forma di report regolarmente pianificati e analisi statistiche, i programmi di immissione di dati, ad esempio quelli per la registrazione degli ordini e i dati manipolazione programmi utilizzati, come quelli usati per risolvere le differenze tra gli account e generare gli ordini di lavoro.  
  
 Questi programmi anche usano SQL, usando uno dei tre tecniche descritte di seguito:  
  
-   **Embedded SQL**, in cui SQL le istruzioni sono incorporate in un linguaggio host quale C o COBOL.  
  
-   **Moduli SQL**, nelle quali istruzioni SQL vengono compilate nel sistema DBMS e chiamati da un linguaggio host.  
  
-   **Interfaccia a livello di chiamata**, o della riga di comando, che è costituito da funzioni chiamate per passare le istruzioni SQL per il sistema DBMS e per recuperare i risultati dal sistema DBMS.  
  
> [!NOTE]  
>  Si tratta di un incidente cronologico che il termine a livello di chiamata interfaccia viene usata invece di programmazione di applicazioni di interfaccia (API), un altro termine per la stessa cosa. Nel mondo del database, API viene usata per descrivere SQL stesso: SQL è l'API per un sistema DBMS.  
  
 Di queste possibilità, embedded SQL è quello più comunemente usato, anche se la maggior parte delle principali DBMS supportare CLI di proprietari.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [L'elaborazione di un'istruzione SQL](../../odbc/reference/processing-a-sql-statement.md)  
  
-   [Embedded SQL](../../odbc/reference/embedded-sql.md)  
  
-   [Moduli SQL](../../odbc/reference/sql-modules.md)  
  
-   [Call-Level Interface](../../odbc/reference/call-level-interfaces.md)

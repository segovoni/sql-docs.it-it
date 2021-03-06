---
title: Interoperabilità | Documenti Microsoft
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
- interoperability [ODBC]
- interoperability [ODBC], about interoperability
ms.assetid: 43b7c849-9d59-4002-9977-9e2c8730b859
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 486bfc2b144e8b228197b7b813af7aaebfe5b837
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32913046"
---
# <a name="interoperability"></a>Interoperabilità
*Interoperabilità* è la capacità di una singola applicazione funzionino con molti diversi DBMS. La necessità di scrivere applicazioni interoperabili generiche è uno dei fattori principali per lo sviluppo di ODBC. Tuttavia, interoperabilità non è un semplice percorso seguito da "non interoperabile" a "tutto intercambiabili". Il percorso dispone di molti branch, e ciascuna richiede compromessi tra le funzionalità, velocità, la complessità del codice e tempi di sviluppo.  
  
 Diverse operazioni per il processo di scrittura di un'applicazione di interoperabilità:  
  
1.  Decidere se l'applicazione utilizzerà ODBC.  
  
2.  Scelta di un livello di interoperabilità e decidere quali vantaggi e svantaggi sono necessari per raggiungere tale livello.  
  
3.  Scrittura di codice di interoperabilità e il relativo test massima.  
  
 Si noti che l'interoperabilità è principalmente il dominio del writer dell'applicazione. I driver sono progettati per funzionare con un singolo DBMS e, per definizione, non sono interoperativi. Essi svolgono un ruolo nell'interoperabilità implementando correttamente e l'esposizione di ODBC in un singolo DBMS.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [La risposta è ODBC?](../../../odbc/reference/develop-app/is-odbc-the-answer.md)  
  
-   [Scelta di un livello di interoperabilità](../../../odbc/reference/develop-app/choosing-a-level-of-interoperability.md)  
  
-   [Determinazione dei DBMS e dei driver di destinazione](../../../odbc/reference/develop-app/determining-the-target-dbmss-and-drivers.md)  
  
-   [Considerazione delle funzionalità di database da usare](../../../odbc/reference/develop-app/considering-database-features-to-use.md)  
  
-   [Lunghezza del ciclo del prodotto](../../../odbc/reference/develop-app/length-of-the-product-cycle.md)  
  
-   [Scrittura di un'applicazione interoperativa](../../../odbc/reference/develop-app/writing-an-interoperable-application.md)  
  
-   [Test delle applicazioni interoperative](../../../odbc/reference/develop-app/testing-interoperable-applications.md)

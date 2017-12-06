---
title: Determinazione delle caratteristiche di un risultato di impostare (ODBC) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-results
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- result sets [ODBC], characteristics
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- SQLDescribeCol function
- metadata [ODBC]
- SQLColAttribute function
- SQLNumResultCols function
ms.assetid: 90be414c-04b3-46c0-906b-ae7537989b7d
caps.latest.revision: "32"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b38f9221a82b9d3f042045cf6aa08b16ead82fad
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="determining-the-characteristics-of-a-result-set-odbc"></a>Determinazione delle caratteristiche di un set di risultati (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  I metadati sono dati che descrivono altri dati. I metadati dei set di risultati, ad esempio, descrivono le caratteristiche di un set di risultati, ad esempio il numero di colonne nel set di risultati, i tipi di dati di tali colonne, i nomi, la precisione e il supporto di valori Null.  
  
 ODBC fornisce metadati alle applicazioni tramite le funzioni API di catalogo. Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client implementa molte delle funzioni di catalogo dell'API ODBC come chiamate a un oggetto corrispondente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] procedure del catalogo.  
  
 Le applicazioni richiedono metadati per la maggior parte delle operazioni sui set di risultati. L'applicazione, ad esempio, utilizza il tipo di dati di una colonna per determinare il tipo di variabile da associare alla colonna. L'applicazione utilizza la lunghezza in byte di una colonna di tipo carattere per determinare lo spazio necessario per visualizzare dati dalla colonna. Il modo in cui un'applicazione determina i metadati per una colonna dipende dal tipo dell'applicazione.  
  
 Le applicazioni verticali utilizzano in genere tabelle predefinite ed eseguono operazioni predefinite in tali tabelle. Poiché i metadati dei set di risultati per tali applicazioni vengono definiti persino prima che l'applicazione sia scritta e sono controllati dallo sviluppatore, possono essere specificati a livello di codice nell'applicazione. Se, ad esempio, una colonna di ID ordine viene definita come valore integer a 4 byte nell'origine dati, l'applicazione può sempre associare un valore integer a 4 byte alla colonna. Quando i metadati vengono specificati a livello di codice nell'applicazione, una modifica apportata alle tabelle utilizzate dall'applicazione comporta in genere una modifica al codice dell'applicazione.  
  
 Nelle applicazioni generiche, in particolare nelle applicazioni che supportano query ad hoc, i metadati dei set di risultati creati non sono in genere noti fino alla fase di esecuzione.  
  
 Per determinare le caratteristiche di un set di risultati, un'applicazione può chiamare le funzioni seguenti:  
  
-   [SQLNumResultCols](../../relational-databases/native-client-odbc-api/sqlnumresultcols.md) per determinare il numero di colonne una richiesta restituita.  
  
-   [SQLColAttribute](../../relational-databases/native-client-odbc-api/sqlcolattribute.md) o [SQLDescribeCol](../../relational-databases/native-client-odbc-api/sqldescribecol.md) per descrivere una colonna nel set di risultati.  
  
 Un'applicazione progettata correttamente viene scritta presupponendo che il set di risultati non sia noto e utilizza le informazioni restituite da tali funzioni per associare le colonne nel set di risultati. Un'applicazione può chiamare tali funzioni in qualsiasi momento in seguito alla preparazione o all'esecuzione di un'istruzione. Tuttavia, per ottenere prestazioni ottimali, un'applicazione deve chiamare **SQLColAttribute**, **SQLDescribeCol**, e **SQLNumResultCols** dopo l'esecuzione di un'istruzione.  
  
 È possibile disporre di più chiamate simultanee per i metadati. Le procedure di catalogo di sistema sottostanti alle implementazioni delle API di catalogo ODBC possono essere chiamate dal driver ODBC mentre utilizza cursori del server statici. In questo modo, le applicazioni possono elaborare simultaneamente più chiamate alle funzioni di catalogo ODBC.  
  
 Se un'applicazione utilizza un set specifico di metadati più volte, potrà utilizzare in modo proficuo la memorizzazione nella cache delle informazioni nelle variabili private quando tali informazioni vengono ottenute per la prima volta. In questo modo è possibile evitare chiamate alle funzioni di catalogo ODBC per le stesse informazioni, evitando in tal modo l'esecuzione di round trip al server da parte del driver.  
  
## <a name="see-also"></a>Vedere anche  
 [Elaborazione dei risultati &#40; ODBC &#41;](../../relational-databases/native-client-odbc-results/processing-results-odbc.md)  
  
  
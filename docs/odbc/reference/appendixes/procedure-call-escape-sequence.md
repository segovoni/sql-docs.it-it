---
title: Sequenza di Escape di chiamata di procedura | Documenti Microsoft
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
- escape sequences [ODBC], procedure call
- procedure call escape sequence [ODBC]
- ODBC escape sequences [ODBC], procedure call
ms.assetid: 269fbab0-e5f2-4a98-86c0-2d7b647acaae
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e5279794a7f18df2ce2d56210e3ab1373af5cde7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32908626"
---
# <a name="procedure-call-escape-sequence"></a>Sequenza di Escape di chiamata di routine
ODBC utilizza le sequenze di escape per le chiamate di procedura. La sintassi di questa sequenza di escape è come segue:  
  
 **{**[? =]**chiamare** *-nome della stored procedure*[**(**[*parametro*] [, [*parametro*]]... **)**]**}**  
  
 Nella notazione BNF, la sintassi è:  
  
 *ODBC-procedura-escape* :: =  
  
 &#124;*ODBC-esc-iniziatore* [? =] chiamare *procedure ODBC-esc-carattere di terminazione*  
  
 *stored procedure* :: = *-nome della stored procedure* &#124; *-nome della stored procedure* (*procedura-parameter-list*)  
  
 *Identificatore di stored procedure* :: = *nome definito dall'utente*  
  
 *nome della stored procedure* :: = *identificatore di procedure*  
  
 &#124;*-nome del proprietario*. *Identificatore di procedure*  
  
 &#124;*separatore di catalogo nome-catalogo* *identificatore di procedure*  
  
 &#124;*separatore di catalogo nome-catalogo* [*-nome del proprietario*]. *Identificatore di procedure*  
  
 (La terza sintassi è valida solo se l'origine dati non supporta i proprietari).  
  
 *nome del proprietario* :: = *nome definito dall'utente*  
  
 *nome del catalogo* :: = *nome definito dall'utente*  
  
 *separatore di catalogo* :: = {*definito dall'implementazione*}  
  
 (Il separatore di catalogo viene restituito tramite **SQLGetInfo** con l'opzione di informazioni SQL_CATALOG_NAME_SEPARATOR.)  
  
 *elenco di parametri di stored procedure* :: = *parametro di routine*  
  
 &#124;*parametro di routine*, *elenco di parametri di stored procedure*  
  
 *parametro di routine* :: = *parametro dinamico* &#124; *letterale* &#124; *stringa vuota*  
  
 *stringa vuota* :: =  
  
 *ODBC-esc-iniziatore* :: = {  
  
 *ODBC-esc-carattere di terminazione* :: =}  
  
 (Se un parametro di routine è una stringa vuota, la procedura Usa il valore predefinito per tale parametro).  
  
 Per determinare se l'origine dati supporta le procedure e il driver supporta la sintassi di chiamata di procedura ODBC, un'applicazione può chiamare **SQLGetInfo** con il tipo di informazioni SQL_PROCEDURES.

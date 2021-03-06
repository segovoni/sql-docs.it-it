---
title: Istruzione SELECT limitazioni | Documenti Microsoft
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
- ODBC SQL grammar, SELECT statement limitations
- SELECT statement limitations [ODBC]
ms.assetid: c6b05955-f8fd-4706-a1a7-a8dbd74870c2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 00490256cb4da90fc9384f696435419266a1a3d3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32900666"
---
# <a name="select-statement-limitations"></a>Limitazioni di istruzione SELECT
Una colonna di funzione di aggregazione non può essere combinata con una colonna non di aggregazione in un'istruzione SELECT.  
  
 Elenco di selezione di un'istruzione SELECT con una clausola GROUP BY può avere solo le espressioni della clausola GROUP BY o funzioni di set.  
  
 L'utilizzo di un asterisco (per selezionare tutte le colonne) in un'istruzione SELECT contenente una clausola GROUP BY non è supportato. Specificare i nomi delle colonne da selezionare.  
  
 L'utilizzo di una barra verticale in un'istruzione SELECT non è supportato. Se è necessario fare riferimento a un valore di dati che contiene una barra verticale, utilizzare un parametro nell'istruzione SELECT.  
  
 Quando si utilizza un alias di colonna in un'istruzione SELECT, la parola "as" deve precedere l'alias. Ad esempio, "SELECT col1 come un da b." Senza il "come", l'istruzione restituirà un errore.  
  
 Se viene immesso un nome di colonna non corretto in un'istruzione SELECT, viene restituito un errore SQLSTATE 07001, "Numero di parametri errati," anziché un errore SQLSTATE S0022, "colonna non trovato".  
  
 Quando viene utilizzato il driver di Microsoft Excel, se una stringa vuota viene inserita in una colonna, una stringa vuota verrà convertita in un valore NULL. viene eseguita un'istruzione di seleziona che viene eseguita con una stringa vuota nella clausola WHERE non verrà eseguita su tale colonna.

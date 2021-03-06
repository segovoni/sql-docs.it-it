---
title: Funzione di conversione specifica sottochiavi | Documenti Microsoft
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
- translator subkey [ODBC]
- registry entries for components [ODBC], translator specification subkeys
- translator specification subkeys [ODBC]
- subkeys [ODBC], translator specification subkeys
ms.assetid: 3c0edeee-d43a-4466-a177-bf2d2435707a
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 163add6fac863912f05378f2e799596f3ad41533
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32915996"
---
# <a name="translator-specification-subkeys"></a>Funzione di conversione specifica sottochiavi
Ogni funzione di conversione elencate nella sottochiave ODBC traduttori ha una sottochiave propri. Questa sottochiave ha lo stesso nome come valore corrispondente nella sottochiave traduttori ODBC. I valori in questa sottochiave Elenca i percorsi completi della funzione di conversione e file DLL di installazione di funzione di conversione e il conteggio di utilizzo. I formati dei valori vengono visualizzati nella tabella seguente.  
  
|Nome|Tipo di dati|data|  
|----------|---------------|----------|  
|Funzione di conversione|REG_SZ|*funzione di conversione-DLL-path*|  
|Installazione|REG_SZ|*il programma di installazione-DLL-path*|  
|UsageCount|REG_DWORD|*count*|  
  
 Per informazioni su conteggi dell'utilizzo, vedere [il conteggio di utilizzo](../../../odbc/reference/install/usage-counting.md) più indietro in questa sezione.  
  
 Applicazioni non devono impostare il conteggio di utilizzo. ODBC manterrà il conteggio.  
  
 Si supponga, ad esempio, il convertitore di tabella codici Microsoft dispone di una DLL denominata Mscpxl32, che le funzioni di conversione di programma di installazione sono nella stessa DLL, traduzione e che sia stato installato lo strumento di conversione tre volte. I valori nella sottochiave Microsoft Translator pagina di codice potrebbero essere come segue:  
  
```  
Translator : REG_SZ : C:\WINDOWS\SYSTEM32\MSCPXL32.DLL  
Setup : REG_SZ : C:\WINDOWS\SYSTEM32\MSCPXL32.DLL  
UsageCount : REG_DWORD : 0x3  
```

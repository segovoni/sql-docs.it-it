---
title: Data/ora le conversioni di tipo di dati (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- conversions [ODBC]
- bindings [ODBC]
- ODBC, bindings and conversions
ms.assetid: 66b9d282-c88d-40e5-93c2-fd5499a74458
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: eb600fd98f6741084d725140bd6f9b326e4cf250
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37431690"
---
# <a name="datetime-data-type-conversions-odbc"></a>Conversioni dei tipi di dati datetime (ODBC)
  Le conversioni seguenti sono già definite da ODBC o sono un'estensione coerente di ODBC. Le conversioni fornite da ogni provider dipendono dalla community servita dal provider, pertanto si può riscontrare la presenza frequente di incoerenze. I valori tra parentesi quadre sono facoltativi.  
  
-   Il formato delle stringhe di data e ora è "yyyy-mm-dd[ hh:mm:ss [.9999999][ più/meno hh:mm]]"  
  
-   Il formato delle stringhe dell'ora è "hh:mm:ss [.9999999]"  
  
-   Il formato delle stringhe della data è "yyyy-mm-dd"  
  
 Le conversioni dalle stringhe consentono flessibilità nella larghezza degli spazi vuoti e dei campi. Per altre informazioni, vedere la sezione "Dati nei formati: stringhe e valori letterali" di [supporto dei tipi di dati per ODBC Date e miglioramenti per la fase](data-type-support-for-odbc-date-and-time-improvements.md).  
  
 Di seguito vengono fornite le regole di conversione generali:  
  
-   Se l'ora non è presente ma il ricevitore può archiviare l'ora, questa viene impostata su zero.  
  
-   Se la data non è presente ma il ricevitore può archiviarla, viene utilizzata la data corrente.  
  
-   Se nel tipo di dati utilizzato dal client non è presente il fuso orario, ma il server può archiviarlo, la data viene archiviata nel fuso orario del client. Questo comportamento differisce da quello del server.  
  
-   Se il fuso orario non è presente nel tipo di server ma è presente nel tipo di client, l'ora viene convertita in formato UTC prima di essere archiviata nel server.  
  
-   Se l'ora è presente ma il ricevitore non può archiviarla, il componente di ora viene ignorato.  
  
-   Se è presente una data ma il ricevitore non può archiviarla, il componente di data viene ignorato.  
  
-   Se quando si esegue la conversione da C a SQL si verifica il troncamento dei secondi o dei secondi frazionari, viene generato un record di diagnostica con SQLSTATE 22008 e il messaggio "Overflow del campo Datetime".  
  
-   Se quando si esegue la conversione da SQL a C si verifica il troncamento dei secondi o dei secondi frazionari, viene generato un record di diagnostica con SQLSTATE 01S07 e il messaggio "Troncamento frazionario".  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 [Conversioni da tipi di dati C a tipi di dati SQL](datetime-data-type-conversions-from-c-to-sql.md)  
 Sono elencati i problemi di cui tener conto durante le conversioni dai tipi C ai tipi di dati date/time di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Conversioni dai tipi di dati SQL ai tipi di dati C](datetime-data-type-conversions-from-sql-to-c.md)  
 Sono elencati i problemi di cui tener conto durante le conversioni dai tipi date/time di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ai tipi C.  
  
## <a name="see-also"></a>Vedere anche  
 [Data e miglioramenti per la fase &#40;ODBC&#41;](date-and-time-improvements-odbc.md)  
  
  

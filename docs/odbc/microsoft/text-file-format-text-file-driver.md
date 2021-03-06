---
title: Il formato di File di testo (Driver di File di testo) | Documenti Microsoft
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
- delimited text lines
- fixed-width text files
- text format [ODBC]
- text file driver [ODBC], text format
ms.assetid: f53cd4b5-0721-4562-a90f-4c55e6030cb9
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d2f0de1d7b5ca14c5ae51cd057244d0c3252780a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32911076"
---
# <a name="text-file-format-text-file-driver"></a>Formato di File di testo (Driver di File di testo)
Il driver ODBC testo supporta entrambi i file di testo delimitati e a larghezza fissa. Un file di testo è costituito da una riga di intestazione facoltativa e zero o più righe di testo.  
  
 Anche se la riga di intestazione Usa lo stesso formato come le altre righe nel file di testo, il driver ODBC testo interpreta le voci di riga di intestazione come nomi di colonna, non i dati.  
  
 Una riga di testo delimitato contiene uno o più valori di dati separati da delimitatori: virgole, tabulazioni o un delimitatore personalizzato. Lo stesso delimitatore deve essere utilizzato in tutto il file. I valori null sono indicati da due delimitatori in una riga senza dati tra di essi. Stringhe di caratteri in una riga di testo delimitato da virgole possono essere racchiusi tra virgolette doppie (""). Spazi vuoti non possono verificarsi prima o dopo i valori delimitato da virgole.  
  
 La larghezza di ogni voce di dati in una riga di testo a larghezza fissa viene specificata in uno schema. I valori null sono indicati da spazi vuoti.  
  
 Le tabelle sono limitate a un massimo di 255 campi. I nomi di campo sono limitati a 64 caratteri e la larghezza dei campi è limitate a 32.766 caratteri. I record sono limitati a 65.000 byte.  
  
 Un file di testo può essere aperto solo per un singolo utente. Più utenti non sono supportati.  
  
 La grammatica seguente, scritta per i programmatori, che definisce il formato di file di testo che può essere letti dal driver ODBC di testo:  
  
|Formato|Rappresentazione|  
|------------|--------------------|  
|Non corsivo|Caratteri che devono essere inseriti come indicato|  
|*Italics*|Argomenti che vengono definiti altrove nella grammatica|  
|parentesi quadre ([])|Elementi facoltativi|  
|le parentesi graffe ({})|Un elenco di scelte si escludono a vicenda|  
|le barre verticali (&#124;)|Opzioni si escludono a vicenda separate|  
|puntini di sospensione (...)|Elementi che possono essere ripetuti una o più volte|  
  
 Il formato di file di testo è:  
  
```  
text-file ::=  
   [delimited-header-line] [delimited-text-line]... end-of-file |  
   [fixed-width-header-line] [fixed-width-text-line]... end-of-file  
delimited-header-line ::= delimited-text-line  
delimited-text-line ::=  
   blank-line |  
   delimited-data [delimiter delimited-data]... end-of-line  
fixed-width-header-line ::= fixed-width-text-line  
fixed-width-text-line ::=  
   blank-line |  
   fixed-width-data [fixed-width-data]... end-of-line  
end-of-file ::= <EOF>  
blank-line ::= end-of-line  
delimited-data ::= delimited-string | number | date | delimited-null  
fixed-width-data ::= fixed-width-string | number | date | fixed-width-null  
```  
  
> [!NOTE]  
>  La larghezza di ogni colonna in un file di testo a larghezza fissa viene specificata nel file ini.  
  
```  
  
      end-of-line ::= <CR> | <LF> | <CR><LF>  
delimited-string ::= unquoted-string | quoted-stringunquoted-string ::= [character | digit] [character | digit | quote-character]...  
quoted-string ::=  
   quote-character  
   [character | digit | delimiter | end-of-line | embedded-quoted-string]...  
   quote-characterembedded-quoted-string ::=   quote-characterquote-character  
   [character | digit | delimiter | end-of-line]  
   quote-characterquote-characterfixed-width-string ::= [character | digit | delimiter | quote-character] ...  
character ::= any character except:  
   delimiterdigitend-of-fileend-of-linequote-characterdigit ::= 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9  
delimiter ::= , | <TAB> |   
custom-delimitercustom-delimiter ::= any character except:  
   end-of-fileend-of-linequote-character  
```  
  
> [!NOTE]  
>  Il delimitatore in un file di testo delimitato personalizzato è specificato nel file ini.  
  
```  
quote-character ::= "  
number ::= exact-number | approximate-number  
exact-number ::= [+ | -] {unsigned-integer[.unsigned-integer] |  
   unsigned-integer. |  
   .unsigned-integer}  
approximate-number ::= exact-number{e | E}[+ | -]unsigned-integer  
unsigned-integer ::= {digit}...  
date ::=  
   mm date-separator dd date-separator yy |  
   mmm date-separator dd date-separator yy |  
   dd date-separator mmm date-separator yy |  
   yyyy date-separator mm date-separator dd |  
   yyyy date-separator mmm date-separator dd  
mm ::= digit [digit]  
dd ::= digit [digit]  
yy ::= digit digit  
yyyy ::= digit digit digit digit  
mmm ::= Jan | Feb | Mar | Apr | May | Jun | Jul | Aug | Sep | Oct | Nov | Dec  
date-separator ::= - | / | .  
delimited-null ::=  
```  
  
> [!NOTE]  
>  Per i file delimitati, un valore NULL è rappresentato da dati non racchiuso tra delimitatori di due.  
  
```  
fixed-width-null ::= <SPACE>...  
```  
  
> [!NOTE]  
>  Per i file a larghezza fissa, un valore NULL è rappresentato da spazi.

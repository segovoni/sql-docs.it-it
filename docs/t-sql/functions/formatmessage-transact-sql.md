---
title: FORMATMESSAGE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/12/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- FORMATMESSAGE
- FORMATMESSAGE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmessages system table
- sys.messages catalog view
- FORMATMESSAGE function
- messages [SQL Server], formats
- errors [SQL Server], formats
ms.assetid: 83f18102-2035-4a87-acd0-8d96d03efad5
caps.latest.revision: 39
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7e4c0ee1c32807728b0e4444c80c8b689e1a26f9
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/04/2018
ms.locfileid: "37782342"
---
# <a name="formatmessage-transact-sql"></a>FORMATMESSAGE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Crea un messaggio in base a un messaggio esistente di sys.messages o a una stringa specificata. La funzionalità di FORMATMESSAGE è simile a quella dell'istruzione RAISERROR. Tuttavia, mentre RAISERROR stampa il messaggio immediatamente, FORMATMESSAGE restituisce il messaggio modificato per ulteriori elaborazioni.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
FORMATMESSAGE ( { msg_number  | ' msg_string ' } , [ param_value [ ,...n ] ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *msg_number*  
 ID del messaggio archiviato in sys.messages. Se *msg_number* è <= 13000 o se il messaggio non esiste in sys.messages, viene restituito NULL.  
  
 *msg_string*  
 **Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] alla [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
 È una stringa racchiusa tra virgolette singole contenente segnaposto per il valore del parametro. Il messaggio di errore può contenere un massimo di 2.047 caratteri. Se contiene più di 2.048 caratteri, vengono visualizzati solo i primi 2.044 e vengono aggiunti tre punti a indicare che il messaggio è stato troncato. I parametri di sostituzione utilizzano un maggior numero di caratteri rispetto a quanto viene visualizzato nell'output a causa della gestione dell'archiviazione interna.  Per informazioni sulla struttura di una stringa di messaggio e sull'uso di parametri nella stringa, vedere la descrizione dell'argomento *msg_str* in [RAISERROR &#40;Transact-SQL&#41;](../../t-sql/language-elements/raiserror-transact-sql.md).  
  
 *param_value*  
 Valore del parametro da utilizzare nel messaggio. È possibile specificare più di un valore di parametro. È necessario specificare i valori nell'ordine in cui le variabili di segnaposto sono elencate nel messaggio. Il numero di valori massimo consentito è 20.  
  
## <a name="return-types"></a>Tipi restituiti  
 **nvarchar**  
  
## <a name="remarks"></a>Remarks  
 In modo analogo all'istruzione RAISERROR, l'istruzione FORMATMESSAGE modifica il messaggio mediante la sostituzione delle variabili di segnaposto con i valori di parametro specificati. Per altre informazioni sui segnaposto consentiti nei messaggi di errore e sul processo di modifica, vedere [RAISERROR &#40;Transact-SQL&#41;](../../t-sql/language-elements/raiserror-transact-sql.md).  
  
 L'istruzione FORMATMESSAGE esegue la ricerca del messaggio nella lingua corrente dell'utente. Se non esiste una versione localizzata del messaggio, viene utilizzata la versione inglese (Stati Uniti).  
  
 Per i messaggi localizzati, i parametri specificati devono corrispondere ai segnaposti del parametro nella versione inglese (Stati Uniti). Ovvero, il parametro 1 nella versione localizzata deve corrispondere al parametro 1 nella versione inglese (Stati Uniti), il parametro 2 deve corrispondere al parametro 2 e così via.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-example-with-a-message-number"></a>A. Esempio con un numero di messaggio  
 Nell'esempio seguente viene usato un messaggio di replica `20009` archiviato in sys.messages, ad esempio "Impossibile aggiungere l'articolo '%s' alla pubblicazione '%s'". FORMATMESSAGE sostituisce i valori `First Variable` e `Second Variable` per i segnaposti dei parametri. La stringa risultante, "Impossibile aggiungere l'articolo 'First Variable' alla pubblicazione 'Second Variable'", viene archiviata nella variabile locale `@var1`.  
  
```  
SELECT text FROM sys.messages WHERE message_id = 20009 AND language_id = 1033;  
DECLARE @var1 VARCHAR(200);   
SELECT @var1 = FORMATMESSAGE(20009, 'First Variable', 'Second Variable');   
SELECT @var1;  
```  
  
### <a name="b-example-with-a-message-string"></a>B. Esempio con una stringa di messaggio  
  
**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] alla [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
 Nell'esempio seguente viene accettata come input una stringa.  
  
```  
SELECT FORMATMESSAGE('This is the %s and this is the %s.', 'first variable', 'second variable') AS Result;  
```  
  
 Restituisce: `This is the first variable and this is the second variable.`  
  
### <a name="c-additional-message-string-formatting-examples"></a>C. Esempi aggiuntivi di formattazione della stringa di messaggio  
 Gli esempi seguenti visualizzano una vasta gamma di opzioni di formattazione.  
  
```  
SELECT FORMATMESSAGE('Signed int %i, %d %i, %d, %+i, %+d, %+i, %+d', 5, -5, 50, -50, -11, -11, 11, 11);  
SELECT FORMATMESSAGE('Signed int with leading zero %020i', 5);  
SELECT FORMATMESSAGE('Signed int with leading zero 0 %020i', -55);  
SELECT FORMATMESSAGE('Unsigned int %u, %u', 50, -50);  
SELECT FORMATMESSAGE('Unsigned octal %o, %o', 50, -50);  
SELECT FORMATMESSAGE('Unsigned hexadecimal %x, %X, %X, %X, %x', 11, 11, -11, 50, -50);  
SELECT FORMATMESSAGE('Unsigned octal with prefix: %#o, %#o', 50, -50);  
SELECT FORMATMESSAGE('Unsigned hexadecimal with prefix: %#x, %#X, %#X, %X, %x', 11, 11, -11, 50, -50);  
SELECT FORMATMESSAGE('Hello %s!', 'TEST');  
SELECT FORMATMESSAGE('Hello %20s!', 'TEST');  
SELECT FORMATMESSAGE('Hello %-20s!', 'TEST');  
SELECT FORMATMESSAGE('Hello %20s!', 'TEST');  
```  
  
## <a name="see-also"></a>Vedere anche  
 [RAISERROR &#40;Transact-SQL&#41;](../../t-sql/language-elements/raiserror-transact-sql.md)  
 [THROW &#40;Transact-SQL&#41;](../../t-sql/language-elements/throw-transact-sql.md)   
 [sp_addmessage &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmessage-transact-sql.md)   
 [sys.messages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md)   
 [CONCAT &#40;Transact-SQL&#41;](../../t-sql/functions/concat-transact-sql.md)  
 [CONCAT_WS &#40;Transact-SQL&#41;](../../t-sql/functions/concat-ws-transact-sql.md)  
 [QUOTENAME &#40;Transact-SQL&#41;](../../t-sql/functions/quotename-transact-sql.md)  
 [REPLACE &#40;Transact-SQL&#41;](../../t-sql/functions/replace-transact-sql.md)  
 [REVERSE &#40;Transact-SQL&#41;](../../t-sql/functions/reverse-transact-sql.md)  
 [STRING_AGG &#40;Transact-SQL&#41;](../../t-sql/functions/string-agg-transact-sql.md)  
 [STRING_ESCAPE &#40;Transact-SQL&#41;](../../t-sql/functions/string-escape-transact-sql.md)  
 [STUFF &#40;Transact-SQL&#41;](../../t-sql/functions/stuff-transact-sql.md)  
 [TRANSLATE &#40;Transact-SQL&#41;](../../t-sql/functions/translate-transact-sql.md)  
 [Funzioni di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)   
  
  

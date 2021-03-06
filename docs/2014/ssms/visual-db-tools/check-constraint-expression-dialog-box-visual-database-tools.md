---
title: Finestra di dialogo Espressione vincolo CHECK (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.checkconstraintexpression
ms.assetid: beb6ce43-3913-4d66-8826-8e885335b790
caps.latest.revision: 13
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 843fe6a662c0d77962881683fb8d5842a4f44612
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37278264"
---
# <a name="check-constraint-expression-dialog-box-visual-database-tools"></a>Finestra di dialogo Espressione vincolo CHECK (Visual Database Tools)
  Quando si associa un vincolo CHECK a una tabella o colonna, è necessario includere un'espressione SQL. Digitare l'espressione di vincolo CHECK nella casella specifica.  
  
## <a name="uielement-list"></a>Elenco degli elementi di interfaccia  
 Espressione  
 Immettere l'espressione.  
  
 È possibile creare un'espressione di vincolo semplice per verificare i dati in base a una condizione semplice oppure creare un'espressione complessa, con operatori booleani, per verificare i dati in base a diverse condizioni. Si supponga ad esempio che nella tabella degli autori sia presente una colonna del codice postale in cui è richiesta una stringa di 5 caratteri. L'espressione di vincolo dell'esempio seguente garantisce che venga accettata solo l'immissione di numeri a 5 cifre:  
  
```  
zip LIKE '[0-9][0-9][0-9][0-9][0-9]'  
```  
  
 Oppure si supponga che nella tabella delle vendite sia presente una colonna delle quantità in cui è richiesto un valore maggiore di 0. Questo vincolo di esempio garantisce che vengano accettati solo valori positivi:  
  
```  
qty > 0  
```  
  
 Oppure si supponga che la tabella degli ordini preveda un limite relativamente al tipo di carte di credito accettate per tutti gli ordini con carte di credito. Il vincolo dell'esempio seguente garantisce che vengano accettate solo carte Visa, MasterCard o American Express se l'ordine viene effettuato con carta di credito:  
  
```  
NOT (payment_method = 'credit card') OR  
   (card_type IN ('VISA', 'MASTERCARD', 'AMERICAN EXPRESS'))  
```  
  
## <a name="to-define-a-constraint-expression"></a>Per definire un'espressione di vincolo  
 Nella scheda Vincoli CHECK delle pagine delle proprietà, digitare un'espressione nella casella Espressione di vincolo utilizzando la sintassi seguente:  
  
 `{constant | column_name | function | (subquery)}`  
  
 `[{operator | AND | OR | NOT}`  
  
 `{constant | column_name | function | (subquery)}...]`  
  
 La sintassi SQL è costituita dai parametri seguenti:  
  
|Parametro|Description|  
|---------------|-----------------|  
|constant|Valore letterale, ad esempio dati numerici o caratteri. I caratteri devono essere racchiusi tra virgolette semplici (')|  
|column_name|Specifica una colonna.|  
|function|Funzione predefinita.|  
|operatore|Operatore aritmetico, bit per bit, di confronto o operatore di stringa.|  
|AND|Si utilizza nelle espressioni booleane per collegare due espressioni. Viene restituito un risultato quando entrambe le espressioni sono true.<br /><br /> Quando un'istruzione contiene sia AND che OR, il parametro AND viene elaborato per primo. È tuttavia possibile modificare l'ordine di esecuzione tramite l'utilizzo delle parentesi.|  
|o|Si utilizza nelle espressioni booleane per collegare due o più condizioni. Viene restituito un risultato quando una delle due condizioni è true.<br /><br /> Quando un'istruzione contiene sia AND che OR, OR viene elaborato dopo AND. È tuttavia possibile modificare l'ordine di esecuzione tramite l'utilizzo delle parentesi.|  
|NOT|Nega qualsiasi espressione booleana (che può includere parole chiave come LIKE, NULL, BETWEEN, IN ed EXISTS).<br /><br /> Quando in un'istruzione sono utilizzati più operatori logici, NOT viene elaborato per primo. È tuttavia possibile modificare l'ordine di esecuzione tramite l'utilizzo delle parentesi.|  
  
## <a name="see-also"></a>Vedere anche  
 [I vincoli UNIQUE e Check](../../relational-databases/tables/unique-constraints-and-check-constraints.md)   
 [Creare vincoli UNIQUE](../../relational-databases/tables/create-unique-constraints.md)  
  
  

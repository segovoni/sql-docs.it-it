---
title: Utilizzando le pagine | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- PageSize property [ADO]
- pages [ADO]
- Recordset object [ADO]
- AbsolutePage property [ADO]
- PageCount property [ADO]
ms.assetid: 442b08c5-ccc7-4192-a1cc-22f250867782
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6afd42480be68c98eafa1d7531a79792620aa255
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35273320"
---
# <a name="using-pages"></a>Utilizzo delle pagine
Utilizzare il **PageCount** proprietà per determinare il numero di pagine di dati di **Recordset** oggetto. *Pagine* sono gruppi di record la cui dimensione è uguale al **PageSize** impostazione della proprietà. Anche se l'ultima pagina incompleta perché sono presenti record minore rispetto di **PageSize** valore, viene conteggiata come una pagina aggiuntiva nel **PageCount** valore. Se il **Recordset** oggetto non supporta questa proprietà, **PageCount** sarà -1 per indicare che il **PageCount** non è possibile determinare.  
  
 Utilizzare il **PageSize** proprietà per determinare il numero di record che costituiscono una pagina logica dei dati. La definizione di una dimensione di pagina consente di utilizzare il **AbsolutePage** proprietà per passare al primo record di una pagina specifica. Ciò è utile negli scenari di server Web quando si desidera consentire all'utente di spostarsi tra i dati, la visualizzazione di un determinato numero di record alla volta.  
  
 Questa proprietà può essere impostata in qualsiasi momento e il relativo valore verrà utilizzato per calcolare la posizione del primo record di una pagina specifica.  
  
 Utilizzare il **AbsolutePage** proprietà per identificare il numero di pagina in cui si trova il record corrente. Nuovamente, il provider deve supportare le funzionalità appropriate per questa proprietà sia disponibile.  
  
 **AbsolutePage** è basato su 1 e uguale a 1 quando il record corrente è il primo record il **Recordset**. Impostare questa proprietà per passare al primo record di una pagina specifica. Ottenere il numero totale di pagine dal **PageCount** proprietà.

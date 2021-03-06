---
title: 'Le funzionalità seguenti non sono supportate da Excel Services e potrebbero non essere visualizzati o potrebbe essere visualizzato solo parzialmente: commenti, forme o altri oggetti | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ade92e15-dfbf-496b-9378-a00bd83ba750
caps.latest.revision: 4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1bee0273ba256ea6861b4259d48e377528c5e4eb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37192422"
---
# <a name="the-following-features-are-not-supported-by-excel-services-and-may-not-display-or-may-display-only-partially-comments-shapes-or-other-objects"></a>Le funzionalità seguenti non sono supportate in Excel Services e potrebbero non venire visualizzate del tutto o parzialmente: Commenti, forme o altri oggetti
  Questo errore si verifica quando si aggiungono filtri dei dati a una cartella di lavoro di PowerPivot da un elenco di campi PowerPivot.  
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Applicabile a|PowerPivot per SharePoint|  
|Versione prodotto|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Causa|In Excel Web Access non è possibile eseguire il rendering dell'oggetto Shape utilizzato per controllare la collocazione e la formattazione dei filtri dei dati aggiunti a una cartella di lavoro dall'elenco campi di PowerPivot.|  
|Testo del messaggio|Le funzionalità seguenti non sono supportate in Excel Services e potrebbero non venire visualizzate del tutto o parzialmente:<br /><br /> Commenti, forme o altri oggetti<br /><br /> Alcune funzionalità, ad esempio le query su dati esterni, visualizzano i dati memorizzati nella cache che possono essere aggiornati solo in Microsoft Excel.|  
  
## <a name="explanation"></a>Spiegazione  
 Questo errore viene visualizzato Excel Web Access quando si apre una cartella di lavoro di PowerPivot in un browser e si fa clic sul **informazioni dettagliate** pulsante per il messaggio **non supportate funzionalità questa cartella di lavoro non venga visualizzata come previsto**.  
  
 Questo errore si verifica in quanto la cartella di lavoro di PowerPivot contiene filtri dei dati il cui layout viene controllato da un oggetto Shape nascosto in Excel. L'oggetto Shape controlla la formattazione e la collocazione dei filtri dei dati nelle posizioni orizzontali e verticali.  
  
 In Excel Services non è possibile eseguire il rendering di un oggetto Shape ma, poiché l'oggetto è nascosto, il fatto che non venga eseguito il rendering non rappresenta un problema.  
  
## <a name="user-action"></a>Azione dell'utente  
 Questo errore può essere ignorato. Fare clic su **OK** per chiudere il messaggio di errore e continuare a usare la cartella di lavoro e i filtri dei dati senza alcun problema.  
  
  

---
title: Modifica dei dati (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- modifying data [MDX]
- Multidimensional Expressions [Analysis Services], data modifications
- MDX [Analysis Services], data modifications
- data modifications [MDX]
ms.assetid: 363b662c-b839-4971-bbd7-1842f73ce141
caps.latest.revision: 29
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 98d437607eef280696766853f890e3827e000812
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37261395"
---
# <a name="modifying-data-mdx"></a>Modifica dei dati (MDX)
  Oltre che per recuperare e gestire i dati di dimensioni e cubi, il linguaggio MDX (Multidimensional Expressions) può essere usato anche per aggiornarli o eseguirne il *writeback*. Tali aggiornamenti possono essere temporanei, come nel caso delle analisi speculative, o di simulazione, oppure permanenti, come nel caso in cui le modifiche dipendono dall'analisi dei dati.  
  
 Gli aggiornamenti possono essere eseguiti a livello di dimensione o di cubo:  
  
 **Writeback delle dimensioni**  
 È possibile usare l'istruzione [ALTER CUBE Statement (MDX)](/sql/mdx/mdx-data-definition-alter-cube) per modificare i dati di una dimensione abilitata per la scrittura e [REFRESH CUBE Statement (MDX)](/sql/mdx/mdx-data-definition-refresh-cube) per riflettere l'eliminazione, la creazione e l'aggiornamento dei valori degli attributi. L'istruzione ALTER CUBE può essere inoltre utilizzata per svolgere operazioni complesse, ad esempio l'eliminazione di un intero sottoalbero di una gerarchia e la promozione dei figli di un membro eliminato.  
  
 **Writeback dei cubi**  
 È possibile usare l'istruzione [UPDATE CUBE](/sql/mdx/mdx-data-manipulation-update-cube) per aggiornare un cubo abilitato per la scrittura. L'istruzione UPDATE CUBE consente di aggiornare una tupla con un valore specifico. È possibile usare l'istruzione [REFRESH CUBE Statement (MDX)](/sql/mdx/mdx-data-definition-refresh-cube) per aggiornare i dati in una sessione client con i dati aggiornati del server.  
  
 Per altre informazioni, vedere [Utilizzo dei writeback dei cubi &#40;MDX&#41;](mdx-data-modification-using-cube-writebacks.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Nozioni fondamentali sulle Query MDX &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md)  
  
  

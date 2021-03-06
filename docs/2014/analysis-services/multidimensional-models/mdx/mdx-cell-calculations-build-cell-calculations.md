---
title: Creazione di calcoli di celle in MDX (MDX) | Microsoft Docs
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
- calculated cells [MDX]
- queries [MDX], cell calculations
- cells [MDX]
- MDX [Analysis Services], calculations
- calculation subcubes [MDX]
- calculated values [MDX]
- Multidimensional Expressions [Analysis Services], cell calculations
ms.assetid: 068aea63-d419-4791-a960-3d74e76f808e
caps.latest.revision: 30
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9b0a689858d4012f360e7f3893cfa844f3ecbdcf
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37161352"
---
# <a name="building-cell-calculations-in-mdx-mdx"></a>Compilazione di formule per il calcolo di celle in MDX (MDX)
  Nel linguaggio MDX (Multidimensional Expressions) sono disponibili numerosi strumenti per la generazione di valori calcolati, ad esempio membri calcolati, rollup personalizzati e membri personalizzati. Utilizzando tali caratteristiche è tuttavia difficile agire su un set specifico di celle o su una singola cella.  
  
 Per generare valori calcolati per celle specifiche, è necessario utilizzare la caratteristica MDX per le celle calcolate. Le celle calcolate consentono di definire una specifica sezione di celle, detta *sottocubo di calcolo*, e di applicare una formula a ogni singola cella del sottocubo di calcolo in base a una condizione facoltativa applicabile a ogni cella.  
  
 Le celle calcolate offrono inoltre funzionalità complesse, ad esempio le formule per la ricerca dell'obiettivo utilizzate negli indicatori di prestazioni chiave (KPI) oppure le formule per l'analisi speculativa. Questo livello di funzionalità si basa sulla caratteristica di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] per l'ordine di calcolo, che consente l'uso di sessioni di calcolo ricorsive con le celle calcolate, applicando le formule di calcolo in sessioni specifiche nell'ordine di calcolo. Per altre informazioni sull'ordine di calcolo, vedere [Informazioni sull'ordine di calcolo e di valutazione &#40;MDX&#41;](mdx-data-manipulation-understanding-pass-order-and-solve-order.md).  
  
 Per quanto concerne l'ambito di creazione, le celle calcolate sono simili sia ai set denominati che ai membri calcolati, poiché possono essere create temporaneamente per la durata di una sessione o di una singola query oppure possono essere rese disponibili a livello globale nell'ambito di un cubo.  
  
-   **Ambito query** Per creare una cella calcolata definita come parte di una query MDX e il cui ambito è pertanto limitato alla query, è necessario specificare la parola chiave WITH. La cella calcolata può essere quindi utilizzata in un'istruzione MDX SELECT. In questo modo, la cella calcolata creata utilizzando il `WITH` parola chiave può essere modificato senza alterare l'istruzione SELECT.  
  
     Per altre informazioni sulla creazione di membri calcolati mediante la parola chiave WITH, vedere [Creating Query-Scoped Cell Calculations &#40;MDX&#41;](../../multidimensional-models-olap-logical-cube-objects/calculations.md).  
  
-   **Ambito sessione** Per creare una cella calcolata il cui ambito risulti più ampio del contesto della query, ovvero il cui ambito corrisponda alla durata della sessione MDX, è necessario usare l'istruzione CREATE CELL CALCULATION o l'istruzione ALTER CUBE.  
  
     Per altre informazioni sulla creazione di celle calcolate in una sessione mediante l'istruzione CREATE CELL CALCULATION o l'istruzione ALTER CUBE, vedere [Creazione di celle calcolate con ambito sessione](mdx-cell-calculations-session-scoped-calculated-cells.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzione ALTER CUBE &#40;MDX&#41;](/sql/mdx/mdx-data-definition-alter-cube)   
 [Istruzione CREATE CELL CALCULATION &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-cell-calculation)   
 [Creazione di calcoli di celle con ambito Query &#40;MDX&#41;](../../multidimensional-models-olap-logical-cube-objects/calculations.md)   
 [Nozioni fondamentali sulle Query MDX &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md)  
  
  

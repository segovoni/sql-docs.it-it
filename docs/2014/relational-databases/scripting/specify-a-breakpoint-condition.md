---
title: Impostare una condizione del punto di interruzione | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vs.debug.breakpt.condition
helpviewer_keywords:
- Transact-SQL debugger, breakpoint conditions
ms.assetid: b43d8a2b-99a3-4fb7-8848-99c042ea7ef7
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8ecee19e4846d2ccf49c21d90b8ab9815ed63a5b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37282777"
---
# <a name="specify-a-breakpoint-condition"></a>Impostare una condizione del punto di interruzione
  Una condizione per il punto di interruzione è un'espressione [!INCLUDE[tsql](../../includes/tsql-md.md)] valutata dal debugger quando viene raggiunto il punto di interruzione. Se la condizione viene soddisfatta e viene raggiunto un numero di passaggi specificato, il debugger interrompe o esegue l'azione specificata per il punto di interruzione.  
  
## <a name="specifying-conditions"></a>Definizione delle condizioni  
 L'espressione specificata deve essere un'espressione Transact-SQL valida che restituisce un valore booleano. Per altre informazioni, vedere [Espressioni &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/expressions-transact-sql).  
  
 Se si specifica una condizione per il punto di interruzione con una sintassi non valida, viene immediatamente visualizzato un messaggio di avviso. Se si specifica una condizione con una sintassi valida ma una semantica non valida, viene visualizzato un messaggio di avviso la prima volta che viene raggiunto il punto di interruzione. In entrambi i casi, il debugger interrompe l'esecuzione al raggiungimento del punto di interruzione non valido.  
  
#### <a name="to-specify-a-condition"></a>Per specificare una condizione  
  
1.  Nella finestra dell'editor fare clic con il pulsante destro del mouse sul glifo del punto di interruzione, quindi scegliere **Condizione** dal menu di scelta rapida.  
  
     oppure  
  
     Nella finestra **Punti di interruzione** fare clic con il pulsante destro del mouse sul glifo del punto di interruzione e quindi scegliere **Condizione** dal menu di scelta rapida.  
  
2.  Nella finestra di dialogo **Condizione punto di interruzione** immettere un'espressione booleana valida nella casella **Condizione** .  
  
3.  Scegli **vale** se si desidera interrompere l'esecuzione quando l'espressione restituisce `true`, oppure scegliere **è stato modificato** se si desidera interrompere l'esecuzione quando viene modificato il valore dell'espressione.  
  
    > [!NOTE]  
    >  Il debugger non valuta l'espressione booleana fino a quando il primo il punto di interruzione non viene raggiunto. Se si sceglie **È stato modificato**, il debugger non considera la prima valutazione una modifica e quindi non interrompe l'esecuzione in corrispondenza della prima valutazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Specifica di un numero di passaggi](specify-a-hit-count.md)   
 [Specificare un'azione del punto di interruzione](specify-a-breakpoint-action.md)  
  
  

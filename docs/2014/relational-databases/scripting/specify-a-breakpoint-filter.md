---
title: Specificare un filtro per un punto di interruzione | Microsoft Docs
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
- vs.debug.breakpt.contraints
helpviewer_keywords:
- Transact-SQL debugger, breakpoint filter
ms.assetid: 7bf1dddd-7b0b-4c47-8a7b-28a5569b4fa5
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9bf7e4f7a162bf172812ed555463c061611237e0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37191781"
---
# <a name="specify-a-breakpoint-filter"></a>Impostazione di un filtro per un punto di interruzione
  Un filtro per un punto di interruzione limita il punto di interruzione in modo che agisca solo su computer o processi e thread del sistema operativo specificati. I filtri per i punti di interruzione vengono in genere utilizzati per il debug di applicazioni parallele.  
  
##  <a name="BKMK_ActionConsiderations"></a> Considerazioni sui filtri  
 I filtri per i punti di interruzione non vengono in genere utilizzati con il debugger [!INCLUDE[tsql](../../includes/tsql-md.md)] perché gli script e le stored procedure [!INCLUDE[tsql](../../includes/tsql-md.md)] non sono applicazioni parallele.  
  
#### <a name="to-specify-a-breakpoint-filter"></a>Per specificare un filtro per un punto di interruzione  
  
1.  Nella finestra dell'editor fare clic con il pulsante destro del mouse sul glifo del punto di interruzione, quindi scegliere **Filtro** dal menu di scelta rapida.  
  
     oppure  
  
     Nella finestra **Punti di interruzione** fare clic con il pulsante destro del mouse sul glifo del punto di interruzione, quindi scegliere **Filtro** dal menu di scelta rapida.  
  
2.  Nella finestra di dialogo **Filtri punti di interruzione** usare la casella **Filtro** per specificare i computer per nome o i processi e i thread del sistema operativo per nome o numero ID:  
  
    -   `MachineName` è il computer che esegue l'istanza del Motore di database.  
  
    -   `ProcessID`, e `ProcessName` sono relativi al processo di sistema operativo in esecuzione l'istanza del motore di Database.  
  
    -   `ThreadID` e `ThreadName` sono thread del sistema operativo in esecuzione il [!INCLUDE[tsql](../../includes/tsql-md.md)] batch, procedura o funzione nell'istanza del motore di Database.  
  
3.  Fare clic su **OK** per implementare le modifiche o su **Annulla** per uscire senza applicare le modifiche.  
  
## <a name="see-also"></a>Vedere anche  
 [Impostare una condizione del punto di interruzione](specify-a-breakpoint-condition.md)   
 [Specifica di un numero di passaggi](specify-a-hit-count.md)   
 [Specificare un'azione del punto di interruzione](specify-a-breakpoint-action.md)  
  
  

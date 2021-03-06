---
title: Attivare/disattivare un punto di interruzione | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c477ab89-a1cd-4f2c-aa7c-40525041100f
caps.latest.revision: 4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6a04f258a7f92c38f560eb0ecc68e7a24e37597a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37315611"
---
# <a name="toggle-a-breakpoint"></a>Attivare/disattivare un punto di interruzione
  L'azione di definizione di un punto di interruzione in un'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] è denominata impostazione/rimozione di un punto di interruzione.  
  
## <a name="breakpoints"></a>Punti di interruzione  
 Una volta impostato, il punto di interruzione è rappresentato da un'icona nella barra grigia a sinistra dell'istruzione. L'icona è nota come glifo del punto di interruzione. [!INCLUDE[tsql](../../includes/tsql-md.md)] I punti di interruzione vengono applicati a un'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] completa. Quando un punto di interruzione viene attivato, il debugger evidenzia l'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] associata.  
  
 Se sono presenti più istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] su una riga, è possibile impostare/rimuovere un punto di interruzione per ogni istruzione. Facendo clic nella barra grigia a sinistra della finestra, è possibile impostare/rimuovere un punto di interruzione nella prima istruzione della riga. Per impostare/rimuovere un punto di interruzione in un'istruzione successiva, è possibile evidenziare qualsiasi parte dell'istruzione o spostare il cursore all'interno dell'istruzione e quindi premere F9 o scegliere **Imposta/Rimuovi punto di interruzione** dal menu **Debug** . Se sono presenti più punti di interruzione su una riga, nella barra grigia a sinistra sarà presente il glifo di un solo punto di interruzione.  
  
 Dopo aver attivato o disattivato un punto di interruzione, è possibile eseguirvi diverse operazioni, ad esempio modificarne le proprietà oppure disabilitarlo temporaneamente. Per altre informazioni, vedere [Punti di interruzione Transact-SQL](transact-sql-breakpoints.md).  
  
## <a name="toggle-a-breakpoint"></a>Attivare/disattivare un punto di interruzione  
 **Per attivare o disattivare un punto di interruzione in un'istruzione Transact-SQL**  
  
1.  Fare clic sulla barra grigia a sinistra dell'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
2.  In alternativa, evidenziare qualsiasi parte dell'istruzione o spostare il cursore all'interno dell'istruzione, quindi effettuare una delle azioni seguenti:  
  
    -   Premere F9.  
  
    -   Scegliere **Imposta/Rimuovi punto di interruzione** dal menu **Debug**.  
  
  

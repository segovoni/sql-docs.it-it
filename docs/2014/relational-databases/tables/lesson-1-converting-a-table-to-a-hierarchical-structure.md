---
title: 'Lezione 1: Conversione di una tabella in una struttura gerarchica | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- HierarchyID
ms.assetid: 5ee6f19a-6dd7-4730-a91c-bbed1bd77e0b
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 32eed062497a0bb766e864ac58edd318c5cc7ff5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37325771"
---
# <a name="lesson-1-converting-a-table-to-a-hierarchical-structure"></a>Lezione 1: Conversione di una tabella in una struttura gerarchica
  I clienti che hanno tabelle che utilizzano un self-join per esprimere relazioni gerarchiche possono convertire le tabelle in una struttura gerarchica utilizzando questa lezione come guida. È relativamente facile eseguire la migrazione da questa rappresentazione a `hierarchyid`. Dopo la migrazione, gli utenti avranno una rappresentazione gerarchica compatta e facile da capire che può essere indicizzata in molti modi per eseguire query efficienti.  
  
 In questa lezione, verrà esaminata una tabella esistente, verrà creata una nuova tabella contenente una colonna `hierarchyid`, verrà popolata la tabella con i dati della tabella di origine e infine verranno illustrate tre strategie di indicizzazione. In questa lezione sono inclusi gli argomenti seguenti:  
  
-   [Esame della struttura corrente della tabella Employee](lesson-1-1-examining-the-current-structure-of-the-employee-table.md)  
  
-   [Popolamento di una tabella con dati gerarchici esistenti](lesson-1-2-populating-a-table-with-existing-hierarchical-data.md)  
  
-   [Ottimizzazione della tabella NewOrg](lesson-1-3-optimizing-the-neworg-table.md)  
  
-   [Riepilogo: Conversione di una tabella in una struttura gerarchica](lesson-1-4-summary-converting-a-table-to-a-hierarchical-structure.md)  
  
## <a name="prerequisites"></a>Prerequisiti  
 Questa lezione richiede il database di esempio [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
 [Esame della struttura corrente della tabella Employee](lesson-1-1-examining-the-current-structure-of-the-employee-table.md)  
  
## <a name="next-lesson"></a>Lezione successiva  
 [Lezione 2: Creazione e gestione di dati in una tabella gerarchica](lesson-2-creating-and-managing-data-in-a-hierarchical-table.md)  
  
  

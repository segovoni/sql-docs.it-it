---
title: La nuova colonna nell'output di sp_helptrigger potrebbe influire sulle applicazioni | Microsoft Docs
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
- sp_helptrigger
ms.assetid: b7c42a8f-f2e0-4fa3-b046-3cf39c854c47
caps.latest.revision: 18
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8d8cb7b6623cd15e2e7617a1ae63baeaebe4e375
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37306987"
---
# <a name="new-column-in-output-of-sphelptrigger-may-impact-applications"></a>La nuova colonna nell'output di sp_helptrigger potrebbe influire sulle applicazioni
  l'ultima colonna nel set di risultati restituita dal sistema sp_helptrigger trigger_schemaias di stored procedure.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Per ottenere informazioni sui trigger definiti in una specifica tabella, eseguire una query sulla vista del catalogo sys.triggers.  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Azione correttiva  
 Esaminare l'utilizzo di sp_helptrigger nelle applicazioni. Può essere necessario modificare le applicazioni in modo da gestire la colonna aggiuntiva. In alternativa, è possibile utilizzare invece la vista del catalogo sys. Triggers.  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento del motore di database](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Preparazione aggiornamento a SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  

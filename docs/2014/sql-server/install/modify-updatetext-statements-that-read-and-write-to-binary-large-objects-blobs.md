---
title: Modificare le istruzioni UPDATETEXT che leggono e scrivono oggetti binari di grandi dimensioni (BLOB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- UPDATETEXT statement
- text [SQL Server], UPDATETEXT statements
ms.assetid: b85da6a7-42f6-4707-a25e-3ded8958b94f
caps.latest.revision: 17
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 85036a4d91fc426a0195c4fd589fbddcadfb5da4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37234331"
---
# <a name="modify-updatetext-statements-that-read-and-write-to-binary-large-objects-blobs"></a>Modificare le istruzioni UPDATETEXT che eseguono operazioni di lettura e scrittura in oggetti BLOB (Binary Large Object)
  Sono state rilevate istruzioni UPDATETEXT che eseguono operazioni di lettura e scrittura negli stessi BLOB (Binary Large Object) utilizzando lo stesso puntatore di testo. In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] questo tipo di utilizzo dei puntatori di testo non è supportato.  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Azione correttiva  
 Copiare gli oggetti BLOB in una tabella temporanea o in una variabile di tabella e quindi riassegnare il valore alla colonna originale.  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento del motore di database](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Preparazione aggiornamento a SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  

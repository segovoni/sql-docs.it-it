---
title: Escludere file dal controllo del codice sorgente | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- excluding files from source control
- source controls [SQL Server Management Studio], file exclusions
ms.assetid: 7dcb6514-db5c-49eb-8b5a-2c766ce39aa7
caps.latest.revision: 21
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b3507f06db699e8e88de2fe2e22f870b97b896e7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37330441"
---
# <a name="exclude-files-from-source-control"></a>Esclusione di file dal controllo del codice sorgente
  Se la soluzione si sta lavorando contiene file che non richiedono servizi di controllo di origine, è possibile usare la **Escludi da controllo del codice sorgente** comando per escludere il file dal controllo del codice sorgente. In questo caso, il file rimarrà nel database di [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe ma non verrà più archiviato o estratto con il progetto.  
  
 È consigliabile usare la **Escludi da controllo del codice sorgente** comando solo sui file generati. Un file generato è uno che può essere interamente ricreati da [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] basata sul contenuto di un altro file nella soluzione.  
  
### <a name="to-exclude-a-file-from-source-control"></a>Per escludere un file dal controllo del codice sorgente  
  
1.  In Esplora soluzioni selezionare il file che si desidera escludere.  
  
2.  Nel **File** dal menu **controllo del codice sorgente**e quindi fare clic su **escludere**  *\<nomefile >* **da Controllo del codice sorgente**.  
  
## <a name="see-also"></a>Vedere anche  
 [Nozioni fondamentali di controlli di origine](../../2014/database-engine/source-control-basics.md)   
 [Impostare le opzioni di controllo di origine](../../2014/database-engine/set-source-control-options.md)   
 [Modificare le connessioni del controllo del codice sorgente](../../2014/database-engine/change-source-control-connections.md)  
  
  

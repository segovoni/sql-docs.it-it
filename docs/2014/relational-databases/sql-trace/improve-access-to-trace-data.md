---
title: Migliorare l'accesso ai dati della traccia | Microsoft Docs
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
- Profiler [SQL Server Profiler], space
- SQL Server Profiler, space
- space [SQL Server], SQL Server Profiler
ms.assetid: c260c000-fd53-4831-993f-df6894f3228b
caps.latest.revision: 13
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 86844ecd42735e74fbacf8909c1fa1bdb8c40ce7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37242371"
---
# <a name="improve-access-to-trace-data"></a>Migliorare l'accesso ai dati della traccia
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] usa lo spazio nella directory **temp** per migliorare l'accesso ai dati di traccia. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] richiede almeno 10 megabyte (MB) di spazio disponibile. Se lo spazio libero scende al di sotto di tale limite durante l'utilizzo di [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], tutte le funzioni di [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] verranno arrestate.  
  
 Quando [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] usa lo spazio della directory **temp** , è possibile che le dimensioni di questa directory **temp** aumentino rapidamente. Per evitare problemi legati all'aumento delle dimensioni, è possibile inserire la directory **temp** in un'unità non di sistema, modificando il valore della variabile di ambiente TEMP.  
  
 Nella procedura seguente viene illustrato come modificare il valore della variabile di ambiente TEMP nella maggior parte dei sistemi operativi Microsoft Windows. Per ulteriori informazioni sull'impostazione delle variabili di ambiente, vedere la documentazione relativa al sistema operativo Windows utilizzato.  
  
### <a name="to-change-the-temp-environment-variable-in-windows-operating-systems"></a>Per modificare la variabile di ambiente TEMP nei sistemi operativi Windows  
  
1.  Dal menu **Start** scegliere **Pannello di controllo**e quindi **Sistema**.  
  
2.  Nella finestra di dialogo **Proprietà del sistema** fare clic sulla scheda **Avanzate** e quindi fare clic **su Variabili d'ambiente**.  
  
3.  Scorrere verso il basso l'elenco **Variabili di sistema**, selezionare la riga corrispondente alla variabile **TEMP** e quindi fare clic su **Modifica**.  
  
4.  Nella finestra di dialogo **Modifica variabile di sistema** immettere il percorso e il nome dell'unità e della directory in cui si vuole inserire la directory **temp** .  
  
5.  Per salvare le modifiche, fare clic su **OK** .  
  
## <a name="see-also"></a>Vedere anche  
 [Avviare SQL Server Profiler](../../tools/sql-server-profiler/start-sql-server-profiler.md)   
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  

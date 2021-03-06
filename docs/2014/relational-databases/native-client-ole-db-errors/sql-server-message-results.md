---
title: Risultati dei messaggi SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- errors [OLE DB], SQL Server message results
- OLE DB error handling, SQL Server message results
ms.assetid: 6663c6f9-def1-4d9e-845b-2085e5efc401
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f5db120da45f57debacd2717983fe4ea4118cabe
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37431840"
---
# <a name="sql-server-message-results"></a>Risultati dei messaggi di SQL Server
  Quanto segue [!INCLUDE[tsql](../../includes/tsql-md.md)] non generano istruzioni [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] i set di righe del provider OLE DB Native Client o un conteggio delle righe interessate durante l'esecuzione:  
  
-   PRINT  
  
-   RAISERROR con gravità minore o uguale a 10  
  
-   DBCC  
  
-   SET SHOWPLAN  
  
-   SET STATISTICS  
  
 Queste istruzioni restituiscono uno o più messaggi informativi o determinano la restituzione da parte di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di messaggi informativi in sostituzione dei risultati del conteggio o del set di righe. In caso di esecuzione, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client restituisce S_OK e i messaggi sono disponibili per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consumer del provider OLE DB Native Client.  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client restituisce S_OK e include uno o più messaggi informativi disponibili in seguito all'esecuzione di molte [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzioni o l'esecuzione del consumer di un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] membro del provider OLE DB Native Client funzione.  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consumer del provider OLE DB Native Client che consente la specifica dinamica del testo della query deve verificare le interfacce di errore dopo ogni esecuzione della funzione membro indipendentemente dal valore del codice restituito, la presenza o assenza di un restituito **IRowset** oppure **IMultipleResults** riferimento all'interfaccia o un conteggio delle righe interessate.  
  
## <a name="see-also"></a>Vedere anche  
 [errori](errors.md)  
  
  

---
title: MSSQLSERVER_2518 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 2518 (Database Engine error)
ms.assetid: 54a13abc-4c33-43f0-b55d-e2e74a1381c8
caps.latest.revision: 19
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: acbc659ae81820e3cd2614075cbca0a21abf6b42
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2018
ms.locfileid: "34320822"
---
# <a name="mssqlserver2518"></a>MSSQLSERVER_2518
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|2518|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|DBCC_NO_EXPRESSION_EVAL_CLR_DISABLED|  
|Testo del messaggio|ID oggetto O_ID (oggetto "O_NAME"): impossibile verificare colonne calcolate e tipi definiti dall'utente per questo oggetto perché Common Language Runtime (CLR) è disabilitato.|  
  
## <a name="explanation"></a>Spiegazione  
Questo messaggio informativo indica che Query Processor non è riuscito a fornire a DBCC un oggetto interno per consentire la restituzione delle colonne calcolate e dei tipi CLR (Common Language Runtime) definiti dall'utente. Il problema si verifica perché CLR è incluso in una delle colonne, ma non è attivato. L'oggetto interno è incluso in tutte le colonne. Pertanto, l'impossibilità di restituire una singola colonna impedisce la creazione dell'oggetto interno. Ciò significa che non verrà controllata la correttezza delle colonne calcolate o che quest'ultime non verranno utilizzate durante il controllo DBCC della consistenza tra indici e tabelle di base.  
  
## <a name="user-action"></a>Azione dell'utente  
Attivare CLR ed eseguire nuovamente l'istruzione DBCC.  
  
## <a name="see-also"></a>Vedere anche  
[Abilitazione dell'integrazione con CLR](~/relational-databases/clr-integration/clr-integration-enabling.md)  
  

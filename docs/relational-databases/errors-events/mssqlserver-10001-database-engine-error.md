---
title: MSSQLSERVER_10001 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 10001 (Database Engine error)
ms.assetid: f8fd2d8d-a4af-4b6a-ba51-9123b7e4c9bf
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8d382b4141039597bb187cba249c17f0e0341232
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2018
ms.locfileid: "34320492"
---
# <a name="mssqlserver10001"></a>MSSQLSERVER_10001
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|10001|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|HR_E_UNEXPECTED|  
|Testo del messaggio|Il provider ha segnalato un errore irreversibile imprevisto.|  
  
## <a name="explanation"></a>Spiegazione  
L'elaborazione delle query distribuite ha rilevato un errore generico durante la chiamata nel provider OLE DB.  
  
## <a name="user-action"></a>Azione dell'utente  
Raccogliere gli eventi di traccia OLE DB mediante [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] e fornire questi dati al Servizio Supporto Tecnico Clienti Microsoft per il provider OLE DB.  
  
## <a name="see-also"></a>Vedere anche  
[Modelli e autorizzazioni di SQL Server Profiler](~/tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)  
[SQL Server Native Client &#40;OLE DB&#41;](~/relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  

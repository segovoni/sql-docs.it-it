---
title: MSSQLSERVER_5231 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 5231 (Database Engine error)
ms.assetid: 6954ae84-ed0b-4f4c-9d0a-e73f3d71476c
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e79aaa4a74d7beac5ae64e6f6f231c7db15f4519
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2018
ms.locfileid: "34318642"
---
# <a name="mssqlserver5231"></a>MSSQLSERVER_5231
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|5231|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|DBCC4_DEADLOCK_SKIPPED_OBJECT|  
|Testo del messaggio|ID oggetto O_ID (oggetto 'NAME'): si è verificato un deadlock durante il tentativo di bloccare questo oggetto per la verifica. L'oggetto è stato ignorato e non verrà elaborato.|  
  
## <a name="explanation"></a>Spiegazione  
Si è verificato un deadlock durante il tentativo da parte di DBCC di bloccare l'oggetto e DBCC è stato scelto come vittima del deadlock. L'oggetto non verrà elaborato.  
  
## <a name="user-action"></a>Azione dell'utente  
None  
  

---
title: MSSQLSERVER_8443 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 8443 (Database Engine error)
ms.assetid: a3541b9c-b1a8-4280-add1-275f08696b62
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 73c081a442b39c71b44c817db616c6eca360ece0
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2018
ms.locfileid: "34325352"
---
# <a name="mssqlserver8443"></a>MSSQLSERVER_8443
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|8443|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|SB_DIALOG_WO_CONV_GROUP|  
|Testo del messaggio|La conversazione con ID '%.*ls' e Initiator %d fa riferimento al gruppo di conversazione mancante '%.\*ls'. Eseguire DBCC CHECKDB per analizzare e riparare il database.|  
  
## <a name="explanation"></a>Spiegazione  
Il livello di metadati ha restituito NULL per il gruppo di conversazione. Il database è stato danneggiato in qualche modo. Una possibile causa di danneggiamento è un errore del disco.  
  
## <a name="user-action"></a>Azione dell'utente  
Eseguire DBCC CHECKDB in modalità di correzione per riportare il database in uno stato consistente. I messaggi potrebbero essere eliminati se necessario per ripristinare la consistenza. Verificare i log degli errori di sistema per vedere se l'errore è stato causato da un altro malfunzionamento del sistema.  
  

---
title: MSSQLSERVER_2570 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 2570 (Database Engine error)
ms.assetid: 29800aa9-81aa-4371-992c-487dbb617f46
caps.latest.revision: 20
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9aff7469725314ec0e8f2c4a4eb41a12ac53b367
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37428820"
---
# <a name="mssqlserver2570"></a>MSSQLSERVER_2570
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|2570|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|DBCC_COLUMN_VALUE_OUT_OF_RANGE|  
|Testo del messaggio|Pagina P_ID, slot S_ID nell'oggetto con ID O_ID, ID di indice I_ID, ID di partizione PN_ID, ID di unità di allocazione A_ID (tipo TYPE). Il valore della colonna COLUMN_NAME non è compreso nell'intervallo consentito per il tipo di dati "DATATYPE". Aggiornare la colonna a un valore valido.|  
  
## <a name="explanation"></a>Spiegazione  
 Il valore contenuto nella colonna specificata non è compreso nell'intervallo dei valori possibili per il tipo di dati della colonna.  
  
## <a name="user-action"></a>Azione dell'utente  
 L'errore non è reversibile. Aggiornare la colonna a un valore compreso nell'intervallo consentito per il tipo di dati della colonna ed eseguire di nuovo il comando.  Per altre informazioni, vedere l'articolo [923247](http://support.microsoft.com/kb/923247) della Knowledge Base.  
  
## <a name="see-also"></a>Vedere anche  
 [UPDATE &#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql)   
 [Tipi di dati &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)  
  
  

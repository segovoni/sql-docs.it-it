---
title: MSSQLSERVER_33081 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 33081 (Database Engine error)
ms.assetid: 839705e7-fa37-4c0d-9f3f-95a9eab98bcf
caps.latest.revision: 7
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: dcd7227607a76e81b6c05024240c8b24afb4382a
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2018
ms.locfileid: "34321542"
---
# <a name="mssqlserver33081"></a>MSSQLSERVER_33081
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|33081|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|SEC_DLL_TRUST_VERIFICATION_FAILED|  
|Testo del messaggio|Impossibile caricare il provider del servizio di crittografia '%.*ls' a causa di una firma Authenticode o un percorso file non valido.  Controllare i messaggi precedenti per altri errori.|  
  
## <a name="explanation"></a>Spiegazione  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non è stato in grado di caricare il provider del servizio di crittografia elencato nel messaggio di errore. Questo errore può essere provocato da numerose API Windows non corrette. Il buffer circolare contiene il nome dell'API non corretta e il codice di errore Windows restituito dall'API. Per ottenere altre informazioni, eseguire una query sulla vista sys.dm_os_ring_buffers nel modo seguente.  
  
```  
SELECT * FROM sys.dm_os_ring_buffers   
WHERE ring_buffer_type = 'RING_BUFFER_SECURITY_ERROR';  
```  
  
## <a name="user-action"></a>Azione dell'utente  
Per ricercare la causa del problema, individuare il codice di errore Windows in MSDN (http://msdn.microsoft.com/). Risolvere l'errore o contattare il Servizio Supporto Tecnico Clienti [!INCLUDE[msCoName](../../includes/msconame-md.md)] per ulteriori informazioni. Se è necessario contattare il Servizio Supporto Tecnico Clienti Microsoft, raccogliere le informazioni seguenti che dovranno essere comunicate al personale di supporto:  
  
-   Log degli errori che mostra l'errore relativo all'impossibilità di caricare il provider di crittografia.  
  
-   Output dell'istruzione seguente:  
  
    ```  
    SELECT * FROM sys.dm_os_ring_buffers   
    WHERE ring_buffer_type = 'RING_BUFFER_SECURITY_ERROR';  
    ```  
  
> [!NOTE]  
> Tentare di raccogliere subito le informazioni sul buffer circolare poiché possono essere perse durante un riavvio.  
  

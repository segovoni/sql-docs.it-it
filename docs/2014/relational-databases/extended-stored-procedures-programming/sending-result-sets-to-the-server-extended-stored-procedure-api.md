---
title: L'invio di set di risultati al Server (API Stored Procedure esteso) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], sending result sets
- result sets [SQL Server], extended stored procedures
ms.assetid: 9d54673d-ea9d-4ac6-825a-f216ad8b0e34
caps.latest.revision: 15
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 590565f15ac9d53b7209fa6808c4c24baeee6344
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37182248"
---
# <a name="sending-result-sets-to-the-server-extended-stored-procedure-api"></a>Invio di set di risultati al server (API delle stored procedure estese)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilizzare invece la funzionalità di integrazione con CLR.  
  
 Durante l'invio di un set di risultati [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], la stored procedure estesa deve chiamare l'API appropriata nel modo seguente:  
  
-   Il **srv_sendmsg** funzione può essere chiamata in qualsiasi ordine prima o dopo che tutte le righe (se presente) sono state inviate con **srv_sendrow**. Tutti i messaggi devono essere inviati al client prima che lo stato di completamento venga inviato con **srv_senddone**.  
  
-   La funzione **srv_sendrow** viene chiamata una volta per ogni riga inviata al client. Tutte le righe devono essere inviate al client prima che qualsiasi messaggio, valore di stato o stato di completamento venga inviato con **srv_sendmsg**, il **srv_status** argomento **srv_pfield**, o **srv_senddone**.  
  
-   L'invio di una riga che non ha tutte le colonne definite con **srv_describe** fa sì che l'applicazione generi un messaggio di errore informativo e restituisca FAIL al client. In questo caso, la riga non viene inviata.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di stored procedure estese](creating-extended-stored-procedures.md)  
  
  

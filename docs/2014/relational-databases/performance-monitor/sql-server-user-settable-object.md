---
title: Oggetto User Settable di SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- User Settable object
- SQLServer:User Settable
ms.assetid: 633de3ef-533c-4f0c-9c7b-c105129d8e94
caps.latest.revision: 21
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: b0976f5c637c5fbecc064bb6cd57235e94602d71
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37223326"
---
# <a name="sql-server-user-settable-object"></a>Oggetto Definibile dall'utente di SQLServer
  L'oggetto **Definibile dall'utente** di Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consente di creare istanze di contatore personalizzate. Utilizzare istanze di contatore personalizzate per monitorare gli aspetti del server non monitorati dai contatori esistenti, quali i componenti specifici del database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizzato (ad esempio, il numero di ordini registrati o l'inventario dei prodotti).  
  
 L'oggetto **Definibile dall'utente** contiene 10 istanze del contatore di query, da **User counter 1** a **User counter 10**. Tali contatori corrispondono alle stored procedure di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da **sp_user_counter1** a **sp_user_counter10**. Quando le stored procedure vengono eseguite dalle applicazioni utente, i valori impostati dalle stored procedure vengono visualizzati in Monitoraggio di sistema. Un contatore può monitorare qualsiasi valore integer, ad esempio una stored procedure che esegue il conteggio degli ordini di un prodotto specifico ricevuti in un giorno.  
  
> [!NOTE]  
>  Il polling delle stored procedure dei contatori utente non viene eseguito automaticamente da Monitoraggio di sistema. Per aggiornare i valori dei contatori, è necessario che le stored procedure vengano eseguite in modo esplicito da un'applicazione utente. Utilizzare un trigger per aggiornare automaticamente il valore del contatore. Ad esempio, per creare un contatore che esegue il monitoraggio del numero di righe di una tabella, creare un trigger INSERT e DELETE nella tabella per eseguire l'istruzione seguente: `SELECT COUNT(*) FROM table`. Ogni volta che il trigger viene attivato da un'operazione INSERT o DELETE eseguita nella tabella, il contatore di Monitoraggio di sistema viene aggiornato automaticamente.  
  
 Questa tabella illustra l'oggetto [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **User Settable** object.  
  
|Contatori di SQLServer:Definibile dall'utente|Description|  
|---------------------------------------|-----------------|  
|**Query**|L'oggetto **Definibile dall'utente** contiene il contatore di query. Gli utenti configurano il valore delle istanze **User counter** all'interno dell'oggetto query.|  
  
 Questa tabella illustra le **istanze** del contatore **Query** .  
  
|Istanze del contatore Query|Description|  
|-----------------------------|-----------------|  
|**User counter 1**|Definito tramite **sp_user_counter1**.|  
|**User counter 2**|Definito tramite **sp_user_counter2**.|  
|**User counter 3**|Definito tramite **sp_user_counter3**.|  
|…||  
|**User counter 10**|Definito tramite **sp_user_counter10**.|  
  
 Per utilizzare le stored procedure dei contatori utente, eseguirle dall'applicazione utente con un solo parametro integer che rappresenta il nuovo valore del contatore. Ad esempio, per impostare **User counter 1** sul valore 10, eseguire l'istruzione Transact-SQL seguente:  
  
```  
EXECUTE sp_user_counter1 10  
```  
  
 Le stored procedure dei contatori utente possono essere chiamate da qualsiasi posizione da cui possono essere chiamate le altre stored procedure, ad esempio le stored procedure personalizzate. Ad esempio, è possibile creare la stored procedure seguente per eseguire il conteggio del numero di connessioni e tentativi di connessione eseguiti dall'avvio di un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
```  
DROP PROC My_Proc  
GO  
CREATE PROC My_Proc  
AS   
   EXECUTE sp_user_counter1 @@CONNECTIONS  
GO  
```  
  
 La funzione @@CONNECTIONS restituisce il numero di connessioni o di tentativi di connessione eseguiti dall'avvio di un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il valore viene passato alla stored procedure **sp_user_counter1** come parametro.  
  
> [!IMPORTANT]  
>  Le query definite nelle stored procedure dei contatori utente dovrebbero essere il più semplici possibile. Le query che impegnano molta memoria e che eseguono operazioni di ordinamento e di hashing di ampia portata o le query che eseguono grandi quantità di operazioni di I/O richiedono l'utilizzo di numerose risorse e possono determinare un peggioramento delle prestazioni del sistema.  
  
## <a name="permissions"></a>Autorizzazioni  
 **sp_user_counter** è disponibile per tutti gli utenti, ma è possibile limitarne l'uso per qualsiasi contatore di query.  
  
## <a name="see-also"></a>Vedere anche  
 [Monitorare l'utilizzo delle risorse &#40;Monitor di sistema&#41;](monitor-resource-usage-system-monitor.md)  
  
  

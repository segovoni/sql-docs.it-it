---
title: sp_reinitsubscription (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_reinitsubscription
- sp_reinitsubscription_TSQL
helpviewer_keywords:
- sp_reinitsubscription
ms.assetid: d56ae218-6128-4ff9-b06c-749914505c7b
caps.latest.revision: 32
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 233448ed17ee55bb2d2c1c2b0a906191c73d4cf6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33000688"
---
# <a name="spreinitsubscription-transact-sql"></a>sp_reinitsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contrassegna la sottoscrizione per la reinizializzazione. Questa stored procedure viene eseguita nel server di pubblicazione per sottoscrizioni push.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_reinitsubscription [ [ @publication = ] 'publication' ]  
    [ , [ @article = ] 'article' ]  
        , [ @subscriber = ] 'subscriber'  
    [ , [ @destination_db = ] 'destination_db']  
    [ , [ @for_schema_change = ] 'for_schema_change']  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @ignore_distributor_failure = ] ignore_distributor_failure ]   
    [ , [ @invalidate_snapshot = ] invalidate_snapshot ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publication=**] **'***pubblicazione***'**  
 Nome della pubblicazione. *pubblicazione* viene **sysname**, con un valore predefinito è all.  
  
 [  **@article=**] **'***articolo***'**  
 Nome dell'articolo. *articolo* viene **sysname**, con un valore predefinito è all. Per le pubblicazioni ad aggiornamento immediato, *articolo* deve essere **tutti**; in caso contrario, la stored procedure ignora la pubblicazione e segnala un errore.  
  
 [  **@subscriber=**] **'***sottoscrittore***'**  
 Nome del Sottoscrittore. *Sottoscrittore* viene **sysname**, non prevede alcun valore predefinito.  
  
 [  **@destination_db=**] **'***destination_db***'**  
 Nome del database di destinazione. *destination_db* viene **sysname**, con un valore predefinito è all.  
  
 [  **@for_schema_change=**] **'***for_schema_change***'**  
 Specifica se viene eseguita la reinizializzazione in seguito a modifiche dello schema apportate nel database di pubblicazione. *for_schema_change* viene **bit**, con un valore predefinito è 0. Se **0**, le sottoscrizioni attive per le pubblicazioni che consentono l'aggiornamento immediato vengono riattivate a condizione l'intera pubblicazione e non solo di alcuni articoli, vengono reinizializzate. Le reinizializzazione viene pertanto avviata in seguito a modifiche dello schema. Se **1**, le sottoscrizioni attive vengono riattivate fino a quando non viene eseguito l'agente Snapshot.  
  
 [  **@publisher=** ] **'***publisher***'**  
 Specifica un server di pubblicazione non [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *server di pubblicazione* viene **sysname**, con un valore predefinito è NULL.  
  
> [!NOTE]  
>  *server di pubblicazione* non deve essere utilizzato per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] i server di pubblicazione.  
  
 [  **@ignore_distributor_failure=** ] *ignore_distributor_failure*  
 Consente la reinizializzazione anche se il server di distribuzione non esiste o è offline. *ignore_distributor_failure* viene **bit**, con un valore predefinito è 0. Se **0**, la reinizializzazione ha esito negativo se il server di distribuzione non esiste o è offline.  
  
 [  **@invalidate_snapshot=** ] *invalidate_snapshot*  
 Consente di invalidare lo snapshot della pubblicazione esistente. *invalidate_snapshot* viene **bit**, con un valore predefinito è 0. Se **1**, viene generato un nuovo snapshot per la pubblicazione.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_reinitsubscription** viene utilizzata nella replica transazionale.  
  
 **sp_reinitsubscription** non è supportato per la replica transazionale peer-to-peer.  
  
 Per le sottoscrizioni in cui lo snapshot iniziale viene applicato automaticamente e la pubblicazione non consente sottoscrizioni aggiornabili, l'agente snapshot deve essere eseguito al termine di questa stored procedure in modo che vengano preparati i file dello schema e del programma per la copia bulk e gli agenti di distribuzione siano quindi in grado di risincronizzare le sottoscrizioni.  
  
 Per le sottoscrizioni in cui lo snapshot iniziale viene applicato automaticamente e la pubblicazione consente sottoscrizioni aggiornabili, l'agente di distribuzione risincronizza la sottoscrizione utilizzando i file dello schema e del programma per la copia bulk più recenti creati in precedenza dall'agente snapshot. L'agente di distribuzione risincronizza la sottoscrizione immediatamente dopo l'esecuzione **sp_reinitsubscription**, se l'agente di distribuzione non è occupato; in caso contrario, la sincronizzazione può verificarsi dopo il (intervallo di messaggio specificato dal parametro della riga di comando dell'agente di distribuzione: **MessageInterval**).  
  
 **sp_reinitsubscription** non ha alcun effetto sulle sottoscrizioni in cui lo snapshot iniziale viene applicato manualmente.  
  
 Per risincronizzare le sottoscrizioni anonime di una pubblicazione, passare **tutti** o NULL come *sottoscrittore*.  
  
 La replica transazionale supporta la reinizializzazione della sottoscrizione a livello di articolo. Lo snapshot dell'articolo viene riapplicato nel Sottoscrittore durante la successiva sincronizzazione dopo che l'articolo è stato contrassegnato per la reinizializzazione. Se esistono articoli dipendenti sottoscritti dallo stesso Sottoscrittore, tuttavia, la riapplicazione dello snapshot nell'articolo potrebbe avere esito negativo, a meno che anche gli articoli dipendenti della pubblicazione non vengano reinizializzati automaticamente in particolari circostanze:  
  
-   Se il comando preliminare eseguito sull'articolo è 'drop', gli articoli di viste associate a schema e stored procedure associate a schema dell'oggetto di base di tale articolo devono essere anch'essi contrassegnati per la reinizializzazione.  
  
-   Se l'opzione dello schema dell'articolo include script dell'integrità referenziale dichiarata nelle chiavi primarie, gli articoli le cui tabelle di base includono relazioni di chiave esterna con le tabelle di base dell'articolo reinizializzato devono essere anch'essi contrassegnati per la reinizializzazione.  
  
## <a name="example"></a>Esempio  
 [!code-sql[HowTo#sp_reinittranpushsub](../../relational-databases/replication/codesnippet/tsql/sp-reinitsubscription-tr_1.sql)]  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server, i membri del **db_owner** ruolo predefinito del database o l'autore della sottoscrizione può eseguire **sp_reinitsubscription** .  
  
## <a name="see-also"></a>Vedere anche  
 [Reinizializzare una sottoscrizione](../../relational-databases/replication/reinitialize-a-subscription.md)   
 [Reinizializzare le sottoscrizioni](../../relational-databases/replication/reinitialize-subscriptions.md)   
 [Stored procedure per la replica &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  

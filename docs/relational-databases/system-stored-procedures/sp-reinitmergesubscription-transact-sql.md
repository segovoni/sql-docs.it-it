---
title: sp_reinitmergesubscription (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/04/2017
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
- sp_reinitmergesubscription_TSQL
- sp_reinitmergesubscription
helpviewer_keywords:
- sp_reinitmergesubscription
ms.assetid: 249a4048-e885-48e0-a92a-6577f59de751
caps.latest.revision: 30
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: be5906700c4a1ced7b6977923bfa5d63e4678401
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32998258"
---
# <a name="spreinitmergesubscription-transact-sql"></a>sp_reinitmergesubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contrassegna una sottoscrizione di tipo merge per la reinizializzazione alla successiva esecuzione dell'agente di merge. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_reinitmergesubscription [ [ @publication = ] 'publication'  
    [ , [ @subscriber = ] 'subscriber'  
    [ , [ @subscriber_db = ] 'subscriber_db'  
    [ , [ @upload_first = ] 'upload_first'  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publication =** ] **'***pubblicazione***'**  
 Nome della pubblicazione. *pubblicazione* viene **sysname**, il valore predefinito è **tutti**.  
  
 [  **@subscriber =** ] **'***sottoscrittore***'**  
 Nome del Sottoscrittore. *Sottoscrittore* viene **sysname**, il valore predefinito è **tutti**.  
  
 [  **@subscriber_db =** ] **'***subscriber_db***'**  
 Nome del database Sottoscrittore. *subscriber_db* viene **sysname**, il valore predefinito è **tutti**.  
  
 [  **@upload_first =** ] **'***upload_first***'**  
 Indica se le modifiche nel Sottoscrittore vengono caricate prima della reinizializzazione della sottoscrizione. *upload_first* viene **nvarchar(5**, con un valore predefinito è FALSE. Se **true**, le modifiche vengono caricate prima della reinizializzazione della sottoscrizione. Se **false**, le modifiche non vengono caricate.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_reinitmergesubscription** viene utilizzata nella replica di tipo merge.  
  
 **sp_reinitmergesubscription** può essere chiamato dal server di pubblicazione per reinizializzare le sottoscrizioni di tipo merge. È consigliabile rieseguire anche l'agente snapshot.  
  
 Se si aggiunge, elimina o modifica un filtro con parametri, le modifiche in sospeso nel Sottoscrittore non possono essere caricate nel server di pubblicazione durante la reinizializzazione. Per caricare le modifiche in sospeso, sincronizzare tutte le sottoscrizioni prima di modificare il filtro.  
  
## <a name="example"></a>Esempio  
 [!code-sql[HowTo#sp_reinitmergepushsub](../../relational-databases/replication/codesnippet/tsql/sp-reinitmergesubscripti_1.sql)]  
  
## <a name="example"></a>Esempio  
 [!code-sql[HowTo#sp_reinitmergepushsubwithupload](../../relational-databases/replication/codesnippet/tsql/sp-reinitmergesubscripti_2.sql)]  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server o **db_owner** ruolo predefinito del database possono eseguire **sp_reinitmergesubscription**.  
  
## <a name="see-also"></a>Vedere anche  
 [Reinizializzare le sottoscrizioni](../../relational-databases/replication/reinitialize-subscriptions.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

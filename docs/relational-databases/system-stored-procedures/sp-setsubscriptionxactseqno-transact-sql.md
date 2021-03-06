---
title: sp_setsubscriptionxactseqno (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
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
- sp_setsubscriptionxactseqno
- sp_setsubscriptionxactseqno_TSQL
helpviewer_keywords:
- sp_setsubscriptionxactseqno
ms.assetid: cdb4e0ba-5370-4905-b03f-0b0c6f080ca6
caps.latest.revision: 16
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: f59325c709b8d16d5e120a135d5d9f9697692b1e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33000468"
---
# <a name="spsetsubscriptionxactseqno-transact-sql"></a>sp_setsubscriptionxactseqno (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Viene utilizzata durante la risoluzione dei problemi e consente di specificare il numero di sequenza del file di log (LSN) della successiva transazione che dovrà essere applicata dall'agente di distribuzione nel Sottoscrittore, in modo che l'agente possa ignorare una transazione non riuscita. Questa stored procedure viene eseguita nel database di sottoscrizione del Sottoscrittore. e non è supportata per Sottoscrittori non SQL Server.  
  
> [!CAUTION]  
>  Se si utilizza questa stored procedure in modo non corretto oppure si specifica un valore LSN non corretto, è possibile che l'agente di distribuzione annulli modifiche già applicate nel Sottoscrittore oppure ignori tutte le restanti modifiche.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_setsubscriptionxactseqno [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'  
        , [ @xact_seqno = ] xact_seqno   
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publisher=** ] **'***publisher***'**  
 Nome del server di pubblicazione. *server di pubblicazione* viene **sysname**, non prevede alcun valore predefinito.  
  
 [  **@publisher_db=** ] **'***publisher_db***'**  
 Nome del database di pubblicazione. *publisher_db* viene **sysname**, non prevede alcun valore predefinito. Per un Server di pubblicazione non SQL, *publisher_db* è il nome del database di distribuzione.  
  
 [  **@publication=** ] **'***pubblicazione***'**  
 Nome della pubblicazione. *pubblicazione* viene **sysname**, non prevede alcun valore predefinito. Quando l'agente di distribuzione è condiviso da più di una pubblicazione, è necessario specificare un valore all per *pubblicazione*.  
  
 [  **@xact_seqno=** ] *xact_seqno*  
 LSN della successiva transazione del server di distribuzione da applicare nel Sottoscrittore. *xact_seqno* viene **varbinary(16)**, non prevede alcun valore predefinito.  
  
## <a name="result-set"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**XACT_SEQNO ORIGINALE**|**varbinary(16)**|LSN originale della successiva transazione da applicare nel Sottoscrittore.|  
|**XACT_SEQNO AGGIORNATO**|**varbinary(16)**|LSN aggiornato della successiva transazione da applicare nel Sottoscrittore.|  
|**NUMERO DI FLUSSO DELLA SOTTOSCRIZIONE**|**int**|Numero di flussi di sottoscrizione utilizzati durante l'ultima sincronizzazione.|  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_setsubscriptionxactseqno** viene utilizzata nella replica transazionale.  
  
 **sp_setsubscriptionxactseqno** non può essere utilizzata in una topologia di replica transazionale peer-to-peer.  
  
 **sp_setsubscriptionxactseqno** può essere usato per ignorare una transazione specifica che sta causando un errore quando viene applicato nel Sottoscrittore. Quando si verifica un errore e dopo che l'agente di distribuzione viene arrestata, chiamare [sp_helpsubscriptionerrors &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-helpsubscriptionerrors-transact-sql.md) nel server di distribuzione per recuperare il valore xact_seqno della transazione non riuscita e quindi chiamare **sp_setsubscriptionxactseqno**, passando questo valore per *xact_seqno*. In questo modo verranno elaborati solo i comandi successivi a questo LSN.  
  
 Specificare un valore di **0** per *xact_seqno* per recapitare tutti i comandi in sospeso nel database di distribuzione al sottoscrittore.  
  
 **sp_setsubscriptionxactseqno** potrebbe non riuscire se l'agente di distribuzione utilizza più flussi di sottoscrizione.  
  
 Quando si verifica questo errore, è necessario eseguire l'agente di distribuzione con un flusso di sottoscrizione singolo. Per altre informazioni, vedere [Replication Distribution Agent](../../relational-databases/replication/agents/replication-distribution-agent.md).  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server o **db_owner** ruolo predefinito del database possono eseguire **sp_setsubscriptionxactseqno**.  
  
  

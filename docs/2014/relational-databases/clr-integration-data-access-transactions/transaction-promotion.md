---
title: La promozione delle transazioni | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: clr
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- distributed transactions [CLR integration]
- promoting transactions [CLR integration]
- Enlist keyword
- transaction promotion [CLR integration]
ms.assetid: 5bc7e26e-28ad-4198-a40d-8b2c648ba304
caps.latest.revision: 13
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 789fa82f6afc23c09028726c837ff5d37a082a06
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37349243"
---
# <a name="transaction-promotion"></a>Promozione delle transazioni
  Transazione *promozione* descrive una transazione lightweight locale che può essere promossa automaticamente a una transazione completamente distribuibile in base alle esigenze. Quando una stored procedure gestita viene richiamata all'interno di una transazione del database sul server, il codice CLR (Common Language Runtime) viene eseguito nel contesto di una transazione locale.  Se all'interno di una transazione del database viene aperta una connessione a un server remoto, la connessione al server remoto viene inserita nella transazione distribuita e la transazione locale viene promossa automaticamente a una transazione distribuita. La promozione delle transazioni riduce pertanto l'overhead delle transazioni distribuite posticipando la creazione di una transazione distribuita finché non si rende necessaria. Tale promozione è automatica se è stata abilitata utilizzando la parola chiave `Enlist` e non richiede alcun intervento da parte dello sviluppatore. Il provider di dati .NET Framework per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fornisce supporto per la promozione delle transazioni mediante le classi dello spazio dei nomi `System.Data.SqlClient` di .NET Framework.  
  
## <a name="the-enlist-keyword"></a>Parola chiave Enlist  
 La proprietà `ConnectionString` di un oggetto `SqlConnection` supporta la parola chiave `Enlist` che indica se `System.Data.SqlClient` individua i contesti transazionali e inserisce automaticamente la connessione in una transazione distribuita. Se questa parola chiave viene impostata su true (impostazione predefinita), la connessione viene inserita automaticamente nel contesto della transazione corrente del thread di apertura. Se invece la parola chiave viene impostata su false, la connessione SqlClient non interagisce con una transazione distribuita. Se non si specifica `Enlist` nella stringa di connessione, la connessione viene inserita automaticamente in una transazione distribuita se ne viene individuata una al momento dell'apertura della connessione.  
  
## <a name="distributed-transactions"></a>Transazioni distribuite  
 Le transazioni distribuite utilizzano in genere un numero elevato di risorse di sistema. [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC) gestisce tali transazioni e integra tutti gli strumenti di gestione delle risorse alle quali si accede dalle transazioni. La promozione delle transazioni, d'altra parte, rappresenta una forma speciale di transazione `System.Transactions` che delega in modo efficiente il lavoro di una semplice transazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. `System.Transactions`, `System.Data.SqlClient` e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] coordinano il lavoro di gestione della transazione, promuovendola a una transazione completamente distribuita, se necessario.  
  
 Il vantaggio dell'utilizzo della promozione delle transazioni è che quando viene aperta una connessione con una transazione `TransactionScope` attiva e non sono aperte altre connessioni, la transazione esegue il commit come transazione lightweight, anziché incorrere nell'overhead aggiuntivo di una transazione completamente distribuita. Per altre informazioni sulle `TransactionScope`, vedere [utilizzando System. Transactions](../native-client-ole-db-transactions/transactions.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Integrazione con CLR e transazioni](clr-integration-and-transactions.md)  
  
  

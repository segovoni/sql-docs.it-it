---
title: BEGIN DISTRIBUTED TRANSACTION (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/29/2016
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DISTRIBUTED
- BEGIN_DISTRIBUTED_TRANSACTION_TSQL
- DISTRIBUTED_TSQL
- BEGIN DISTRIBUTED TRANSACTION
dev_langs:
- TSQL
helpviewer_keywords:
- BEGIN DISTRIBUTED TRANSACTION statement
- distributed transactions [SQL Server], starting
- MS DTC, transaction management
- distributed transactions [SQL Server], BEGIN DISTRIBUTED TRANSACTION statement
- servers [SQL Server], distributed transactions
- starting distributed transactions
- remote servers [SQL Server], distributed transactions
- starting transactions
ms.assetid: c3bc2716-39d3-4061-8c6a-8734899231ac
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d75638152141d1035bfad5affe3d24b50db14d60
ms.sourcegitcommit: a6596c62f607041c4402f7d5b41a232fca257c14
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36253233"
---
# <a name="begin-distributed-transaction-transact-sql"></a>BEGIN DISTRIBUTED TRANSACTION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contrassegna il punto di inizio di una transazione distribuita [!INCLUDE[tsql](../../includes/tsql-md.md)] gestita da [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC).  
    
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
BEGIN DISTRIBUTED { TRAN | TRANSACTION }   
     [ transaction_name | @tran_name_variable ]   
[ ; ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *transaction_name*  
 Nome di transazione definito dall'utente e utilizzato per tenere traccia della transazione distribuita nelle utilità MS DTC. *transaction_name* deve essere conforme alle regole per gli identificatori e deve rispettare il limite \<= 32 per il numero di caratteri.  
  
 @*tran_name_variable*  
 Nome di una variabile definita dall'utente contenente un nome di transazione utilizzato per tenere traccia della transazione distribuita nelle utilità MS DTC. La variabile deve essere dichiarata con un tipo di dati **char**, **varchar**, **nchar** o **nvarchar**.  
  
## <a name="remarks"></a>Remarks  
 L'istanza di [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] in cui viene eseguita l'istruzione BEGIN DISTRIBUTED TRANSACTION è l'origine della transazione e controlla il completamento della transazione. Quando viene successivamente eseguita un'istruzione COMMIT TRANSACTION o ROLLBACK TRANSACTION per la sessione, l'istanza di controllo richiede che il completamento della transazione distribuita in tutte le istanze coinvolte venga gestito da MS DTC.  
  
 L'isolamento dello snapshot a livello di transazione non supporta le transazioni distribuite.  
  
 L'integrazione di istanze remote del [!INCLUDE[ssDE](../../includes/ssde-md.md)] in una transazione distribuita in genere avviene quando una sessione già integrata nella transazione distribuita esegue una query distribuita in cui viene fatto riferimento a un server collegato.  
  
 Se, ad esempio, l'istruzione BEGIN DISTRIBUTED TRANSACTION viene eseguita nel ServerA, la sessione chiama una stored procedure nel ServerB e un'altra stored procedure nel ServerC. La stored procedure nel ServerC esegue una query distribuita sul ServerD e quindi nella transazione distribuita vengono coinvolti tutti i quattro computer. L'istanza di [!INCLUDE[ssDE](../../includes/ssde-md.md)] nel ServerA è l'istanza di origine e di controllo della transazione.  
  
 Le sessioni coinvolte in transazioni distribuite [!INCLUDE[tsql](../../includes/tsql-md.md)] non ottengono un oggetto transazione passabile a un'altra sessione per l'integrazione esplicita nella transazione distribuita. L'unico modo per consentire l'integrazione di un server remoto nella transazione consiste nell'utilizzare il server come destinazione di una chiamata di stored procedure remota o di una query distribuita.  
  
 Quando una query distribuita viene eseguita in una transazione locale, la transazione viene promossa automaticamente a una transazione distribuita se l'origine dati OLE DB di destinazione supporta ITransactionLocal. Se l'origine dati OLE DB di destinazione non supporta ITransactionLocal, nella query distribuita è possibile eseguire solo operazioni di lettura.  
  
 Una sessione già integrata nella transazione distribuita esegue una chiamata di stored procedure remota in cui viene fatto riferimento a un server remoto.  
  
 L'opzione **sp_configure remote proc trans** determina se le chiamate di stored procedure remote in una transazione locale causano automaticamente la promozione della transazione locale a una transazione distribuita gestita da MS DTC. È possibile usare l'opzione SET REMOTE_PROC_TRANSACTIONS a livello di connessione per ignorare l'impostazione predefinita dell'istanza specificata da **sp_configure remote proc trans**. Quando si attiva questa opzione, una chiamata di stored procedure remota causa la promozione di una transazione locale a una transazione distribuita. La connessione in cui viene creata la transazione MS DTC diventa l'origine della transazione. L'istruzione COMMIT TRANSACTION avvia un'operazione di commit coordinata da MS DTC. Se l'opzione **sp_configure remote proc trans** è impostata su ON, le chiamate di stored procedure remote eseguite in transazioni locali vengono protette automaticamente come parte di transazioni distribuite senza che sia necessario riprogrammare le applicazioni in modo che eseguano l'istruzione BEGIN DISTRIBUTED TRANSACTION anziché l'istruzione BEGIN TRANSACTION.  
  
 Per ulteriori informazioni sull'ambiente e sul processo delle transazioni distribuite, vedere la documentazione di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza al ruolo public.  
  
## <a name="examples"></a>Esempi  
 In questo esempio viene eliminato un candidato dal database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] sia nell'istanza locale di [!INCLUDE[ssDE](../../includes/ssde-md.md)] che in un'istanza in un server remoto. Entrambi i database eseguiranno il commit o il rollback della transazione.  
  
> [!NOTE]  
>  Se nel computer che esegue l'istanza di [!INCLUDE[ssDE](../../includes/ssde-md.md)] non è installato MS DTC, in questo esempio viene visualizzato un messaggio di errore. Per ulteriori informazioni sull'installazione di MS DTC, vedere la documentazione di Microsoft Distributed Transaction Coordinator.  
  
```  
USE AdventureWorks2012;  
GO  
BEGIN DISTRIBUTED TRANSACTION;  
-- Delete candidate from local instance.  
DELETE AdventureWorks2012.HumanResources.JobCandidate  
    WHERE JobCandidateID = 13;  
-- Delete candidate from remote instance.  
DELETE RemoteServer.AdventureWorks2012.HumanResources.JobCandidate  
    WHERE JobCandidateID = 13;  
COMMIT TRANSACTION;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [BEGIN TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/begin-transaction-transact-sql.md)   
 [COMMIT TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/commit-transaction-transact-sql.md)   
 [COMMIT WORK &#40;Transact-SQL&#41;](../../t-sql/language-elements/commit-work-transact-sql.md)   
 [ROLLBACK TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/rollback-transaction-transact-sql.md)   
 [ROLLBACK WORK &#40;Transact-SQL&#41;](../../t-sql/language-elements/rollback-work-transact-sql.md)   
 [SAVE TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/save-transaction-transact-sql.md)  
  
  

---
title: MSSQLSERVER_916 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 916 (Database Engine error)
ms.assetid: 73eb6581-99fe-49a5-9b42-e239d7ffe27f
caps.latest.revision: 8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9734019354c2a2143c184b65e44951835eb73cc0
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37418996"
---
# <a name="mssqlserver916"></a>MSSQLSERVER_916
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|916|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|NOTUSER|  
|Testo del messaggio|L'entità server "%.*ls" non è in grado di accedere al database "%.\*ls" nel contesto di sicurezza corrente.|  
  
## <a name="explanation"></a>Spiegazione  
 L'accesso non dispone delle autorizzazioni sufficienti per connettersi al database denominato. Gli account di accesso che possono connettersi a questa istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ma che non dispongono di autorizzazioni specifiche in un database ricevono le autorizzazioni di utente guest. Si tratta di una misura di sicurezza per impedire agli utenti di un database di connettersi ad altri database per cui non dispongono di privilegi. È possibile ricevere questo messaggio di errore quando l'utente guest non dispone delle autorizzazioni CONNECT per il database denominato e la proprietà TRUSTWORTHY non è impostata. È possibile ricevere questo messaggio di errore quando l'utente guest non dispone delle autorizzazioni CONNECT per il database denominato.  
  
 Quando l'autorizzazione CONNECT al database msdb viene negata o revocata, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] può ricevere questo errore quando Esplora oggetti tenta di mostrare lo stato di gestione basata su criteri di ciascun database. Esplora oggetti usa le autorizzazioni dell'accesso corrente per cercare nel database msdb queste informazioni, operazione che causa l'errore. Viene inoltre visualizzato il messaggio di errore seguente:  
  
 Impossibile recuperare i dati per la richiesta specificata. (Microsoft.SqlServer.Management.Sdk.Sfc)  
  
## <a name="user-action"></a>Azione dell'utente  
  
> [!WARNING]  
>  Prima di eludere questa misura di sicurezza, assicurarsi di sapere quali utenti sono autenticati in vari database. I metodi seguenti consentono agli utenti che dispongono delle autorizzazioni per un database di connettersi ad altri database che potrebbero esporre i dati a utenti malintenzionati. Quando i database indipendenti sono abilitati, i passaggi seguenti consentono ai proprietari di un database di concedere l'accesso all'altro database nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 È possibile connettersi al database in uno dei modi seguenti:  
  
-   Concedere l'accesso specifico al database denominato. Nell'esempio seguente viene concesso l'accesso `Adventure-Works\Larry` al database `msdb`.  
  
     USE msdb ;  
  
     GO  
  
     GRANT CONNECT TO [Adventure-Works\Larry] ;  
  
-   Concedere l'autorizzazione CONNECT al database denominato nel messaggio di errore per l'utente guest. Nell'esempio seguente viene concessa l'autorizzazione `CONNECT` per il database `msdb` per l'utente `guest`.  
  
     USE msdb ;  
  
     GO  
  
     GRANT CONNECT TO guest ;  
  
-   Abilitare la proprietà TRUSTWORTHY per il database che ha autenticato l'utente.  
  
     `ALTER DATABASE AdventureWorks SET TRUSTWORTHY ON;`  
  
  

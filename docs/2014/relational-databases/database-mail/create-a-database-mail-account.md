---
title: Creare un account di Posta elettronica database | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Database Mail [SQL Server], accounts
- accounts [Database Mail]
ms.assetid: c07abbc6-fc6a-470b-8fa3-532f2e06b16a
caps.latest.revision: 25
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 91934cd120a48f05ba73dbddf2433af4d1a6cd18
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37172912"
---
# <a name="create-a-database-mail-account"></a>Creare un account di Posta elettronica database.
  Per creare un account di Posta elettronica database, utilizzare la **Configurazione guidata Posta elettronica database** o [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
-   **Prima di iniziare:**  [Prerequisiti](#Prerequisites)  
  
-   **Per creare un account di Posta elettronica database usando:**  [Configurazione guidata Posta elettronica database](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)  
  
-   **Completamento:**  [Passaggi successivi per configurare Posta elettronica database](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Prerequisites"></a> Prerequisiti  
  
-   Determinare il nome del server e il numero di porta per il server SMTP (Simple Mail Transfer Protocol) utilizzato per inviare e-mail. Se il server SMTP richiede l'autenticazione, determinare il nome utente e la password per il server SMTP.  
  
-   Se lo si desidera, è possibile specificare il tipo e il numero di porta del server. Il tipo di server per la posta in uscita è sempre SMTP. La maggior parte dei server SMTP utilizza la porta predefinita, ovvero la 25.  
  
##  <a name="SSMSProcedure"></a> Utilizzo della Configurazione guidata Posta elettronica database  
 **Per creare un account di Posta elettronica database utilizzando una procedura guidata**  
  
-   In Esplora oggetti, connettersi all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] su cui si desidera configurare Posta elettronica database ed espandere l'albero di server.  
  
-   Espandere il nodo **Gestione**  
  
-   Fare doppio clic su Posta elettronica database per aprire la Configurazione guidata Posta elettronica database.  
  
-   Nella pagina **Selezione attività di configurazione** selezionare l'opzione **Gestisci account e profili di Posta elettronica database**e fare clic su **Avanti**.  
  
-   Nella pagina **Gestione profili e account** selezionare l'opzione **Crea un nuovo account** e fare clic su **Avanti**.  
  
-   Nella pagina **Nuovo account** , specificare il nome dell'account, la descrizione, informazione sul server di posta elettronica e tipo di autenticazione. Scegliere **Avanti**  
  
-   Per completare la creazione del nuovo account, rivedere le azioni da eseguire nella pagina **Completamento procedura guidata** quindi fare clic su **Fine** .  
  
##  <a name="TsqlProcedure"></a> Uso di Transact-SQL  
 **Per creare un account di Posta elettronica database utilizzando Transact-SQL**  
  
 Eseguire la stored procedure **msdb.dbo.sysmail_add_account_sp** per creare l'account, specificando le seguenti informazioni:  
  
-   Nome dell'account da creare.  
  
-   Descrizione dell'account (facoltativa).  
  
-   Indirizzo di posta elettronica visualizzato nei messaggi in uscita.  
  
-   Nome visualizzato nei messaggi in uscita.  
  
-   Nome del server SMTP.  
  
-   Nome utente da utilizzare per l'accesso se il server SMTP richiede l'autenticazione.  
  
-   Password da utilizzare per l'accesso se il server SMTP richiede l'autenticazione.  
  
 Nell'esempio seguente viene creato un nuovo account di Posta elettronica database.  
  
```  
EXECUTE msdb.dbo.sysmail_add_account_sp  
    @account_name = 'AdventureWorks Administrator',  
    @description = 'Mail account for administrative e-mail.',  
    @email_address = 'dba@Adventure-Works.com',  
    @display_name = 'AdventureWorks Automated Mailer',  
    @mailserver_name = 'smtp.Adventure-Works.com' ;  
```  
  
##  <a name="FollowUp"></a> Completamento: Passaggi successivi per la configurazione di Posta elettronica database  
  
-   [Creare un profilo di Posta elettronica database](create-a-database-mail-profile.md)  
  
  

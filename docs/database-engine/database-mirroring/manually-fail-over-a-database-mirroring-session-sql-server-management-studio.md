---
title: Failover manuale di una sessione di mirroring del database (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.suite: sql
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- failover [SQL Server], database mirroring
- manual failover [SQL Server]
- database mirroring [SQL Server], failover
ms.assetid: 4ecf9c63-b3a4-4c54-b553-5bc37973232b
caps.latest.revision: 32
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 7ecc779d19f919f7ff64015812838782b1a26e3d
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35311980"
---
# <a name="manually-fail-over-a-database-mirroring-session-sql-server-management-studio"></a>Failover manuale di una sessione di mirroring del database (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Quando il database con mirroring è sincronizzato, ovvero è in stato SYNCHRONIZED, il proprietario del database può iniziare il failover manuale al server mirror.  
  
 Durante un failover manuale, il ruolo del server principale e quello del server mirror vengono scambiati per il database in cui si verifica il failover. Il database mirror diventa il database principale e viceversa. Ad esempio, nella tabella seguente viene illustrato lo scambio dei ruoli di due partner di mirroring tramite un failover manuale: `SQLDBENGINE0_1` e `SQLDBENGINE0_2`.  
  
|Server|Prima del failover|Dopo il failover|  
|------------|---------------------|--------------------|  
|`SQLDBENGINE0_1`|PRINCIPAL|MIRROR|  
|`SQLDBENGINE0_2`|MIRROR|PRINCIPAL|  
  
 Si noti che questa operazione non influisce sui ruoli del server per le altre sessioni di mirroring del database. Per altre informazioni, vedere [Cambio di ruolo durante una sessione di mirroring del database &#40;SQL Server&#41;](../../database-engine/database-mirroring/role-switching-during-a-database-mirroring-session-sql-server.md)(Mirroring del database e log shipping).  
  
### <a name="to-manually-fail-over-database-mirroring"></a>Per eseguire il failover manuale del mirroring del database  
  
1.  Connettersi all'istanza del server principale e fare clic sul nome del server per espandere l'albero di server nel riquadro **Esplora oggetti** .  
  
2.  Espandere **Database**e selezionare il database di cui eseguire il failover.  
  
3.  Fare clic con il pulsante destro del mouse sul database, scegliere **Attività**e quindi fare clic su **Server mirror**. Viene visualizzata la pagina **Mirroring** della finestra di dialogo **Proprietà database** .  
  
4.  Fare clic su **Failover**.  
  
     Verrà visualizzata una finestra contenente una richiesta di conferma.  Il server principale prova a connettersi al server mirror utilizzando l'autenticazione di Windows. Se l'autenticazione di Windows non funziona, sul server principale viene visualizzata la finestra di dialogo **Connetti al server** . Se il server mirror usa l'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , selezionare **Autenticazione di SQL Server** nella casella **Autenticazione** . Nella casella di testo **Account di accesso** specificare l'account di accesso con cui connettersi al server mirror e nella casella di testo **Password** specificare la password per tale account.  
  
     Se il failover ha esito positivo, la finestra di dialogo **Proprietà database** viene chiusa. Il database mirror diventa il database principale e viceversa.  
  
     Se il failover non riesce, viene visualizzato un messaggio di errore e la finestra di dialogo rimane aperta.  
  
    > [!IMPORTANT]  
    >  Se una o più proprietà sono state modificate dopo l'apertura della pagina **Mirroring** , tali modifiche non verranno salvate.  
  
     La finestra di dialogo verrà chiusa automaticamente.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà del database &#40;Pagina Mirroring&#41;](../../relational-databases/databases/database-properties-mirroring-page.md)   
 [Mirroring del database &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)   
 [Eseguire il failover manuale di una sessione di mirroring del database &#40;Transact-SQL&#41;](../../database-engine/database-mirroring/manually-fail-over-a-database-mirroring-session-transact-sql.md)   
 [Sospendere o riprendere una sessione di mirroring del database &#40;SQL Server&#41;](../../database-engine/database-mirroring/pause-or-resume-a-database-mirroring-session-sql-server.md)   
 [Rimuovere il mirroring del database &#40;SQL Server&#41;](../../database-engine/database-mirroring/remove-database-mirroring-sql-server.md)  
  
  

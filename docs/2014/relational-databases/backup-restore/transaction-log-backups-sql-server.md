---
title: Backup di log delle transazioni [SQL Server] | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: backup-restore
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- backing up [SQL Server], transaction logs
- transaction log backups [SQL Server], creating
- log backups [SQL Server[
- transaction log backups [SQL Server], sequencing
ms.assetid: f4a44a35-0f44-4a42-91d5-d73ac658a3b0
caps.latest.revision: 51
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e0a796d00c24f099f6ca96b826eb41e7f0e103e4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37186598"
---
# <a name="transaction-log-backups-sql-server"></a>Backup di log delle transazioni (SQL Server)
  Le informazioni contenute in questo argomento sono rilevanti solo per i database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che utilizzano i modelli di recupero con registrazione completa o con registrazione minima delle operazioni bulk. In questo argomento viene illustrata l'esecuzione del backup del log delle transazioni di un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Per poter creare backup dei log è necessario aver creato almeno un backup completo. A quel punto, è possibile eseguire il backup del log delle transazioni in qualsiasi momento a meno che non sia già stato eseguito. È consigliabile eseguire backup del log spesso, sia per ridurre al minimo il rischio di perdita dei dati sia per consentire il troncamento del log. In genere, un amministratore del database crea un backup completo occasionale del database, ad esempio con cadenza settimanale ed eventualmente crea una serie di backup differenziali a intervalli più brevi, ad esempio giornalmente. Indipendentemente dei backup di database, l'amministratore esegue il backup del log delle transazioni a intervalli frequenti, ad esempio ogni 10 minuti. L'intervallo ottimale per un determinato tipo di backup dipende da fattori quali l'importanza dei dati, le dimensioni del database e il carico di lavoro del server.  
  
 **Contenuto dell'argomento**  
  
-   [Funzionamento di una sequenza di backup del Log](#LogBackupSequence)  
  
-   [Indicazioni](#Recommendations)  
  
-   [Attività correlate](#RelatedTasks)  
  
-   [Contenuto correlato](#RelatedContent)  
  
##  <a name="LogBackupSequence"></a> Funzionamento di una sequenza di backup del Log  
 La sequenza della *catena di log* dei backup del log delle transazioni è indipendente dai backup dei dati. Si consideri ad esempio la sequenza di eventi seguente:  
  
|Time|Evento|  
|----------|-----------|  
|8.00|Backup del database|  
|12.00|Backup del log delle transazioni|  
|16.00|Backup del log delle transazioni|  
|18.00|Backup del database|  
|20.00|Backup del log delle transazioni|  
  
 Il backup del log delle transazioni creato alle 20.00 contiene record del log delle transazioni a partire dalle 16.00 fino alle 20.00, il che include l'ora in cui è stato creato il backup del database completo, ovvero le 18.00. La sequenza di backup del log delle transazioni è continua dal backup del database completo iniziale creato alle 8.00 all'ultimo backup del log delle transazioni creato alle 20.00. Per informazioni su come applicare i backup del log, vedere l'esempio in [Applicare backup log delle transazioni &#40;SQL Server&#41;](transaction-log-backups-sql-server.md).  
  
##  <a name="Recommendations"></a> Indicazioni  
  
-   Se un log delle transazioni è danneggiato, il lavoro eseguito dopo il backup valido più recente viene perso. Pertanto è consigliabile inserire i file di log in una risorsa di archiviazione con tolleranza di errore.  
  
-   Se un database è danneggiato oppure deve essere ripristinato, è consigliabile creare un [backup della parte finale del log](tail-log-backups-sql-server.md) per consentire il ripristino del database al momento corrente.  
  
-   Per impostazione predefinita, per ogni operazione di backup eseguita in modo corretto viene aggiunta una voce al log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e al registro eventi di sistema. Se il backup del log viene eseguito di frequente, questi messaggi possono aumentare rapidamente, provocando la creazione di log degli errori di dimensioni elevate e rendendo difficile l'individuazione di altri messaggi. In questi casi è possibile eliminare tali voci di log utilizzando il flag di traccia 3226 se nessuno degli script dipende da esse. Per altre informazioni, vedere [Flag di traccia &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql).  
  
##  <a name="RelatedTasks"></a> Attività correlate  
 **Per creare un backup del log delle transazioni**  
  
-   [Eseguire il backup di un log delle transazioni &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md)  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Backup.SqlBackup%2A> (SMO)  
  
 Per pianificare i processi di backup, vedere [Use the Maintenance Plan Wizard](../maintenance-plans/use-the-maintenance-plan-wizard.md).  
  
##  <a name="RelatedContent"></a> Contenuto correlato  
 Nessuna.  
  
## <a name="see-also"></a>Vedere anche  
 [Log delle transazioni &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md)   
 [Backup e ripristino di database SQL Server](back-up-and-restore-of-sql-server-databases.md)   
 [Backup della parte finale del log &#40;SQL Server&#41;](tail-log-backups-sql-server.md)   
 [Applicare backup log delle transazioni &#40;SQL Server&#41;](transaction-log-backups-sql-server.md)  
  
  

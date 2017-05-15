---
title: Creare e collegare pianificazioni ai processi | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- jobs [SQL Server]
- scheduling jobs [SQL Server]
- jobs [SQL Server], scheduling
- CPU [SQL Server], idle conditions
- automatic job processing
- SQL Server Agent jobs, scheduling
- idle time [SQL Server]
ms.assetid: 079c2984-0052-4a37-a2b8-4ece56e6b6b5
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 5c104e70fc7b2e7065f9aa43a16aac88707391ea
ms.lasthandoff: 04/11/2017

---
# <a name="create-and-attach-schedules-to-jobs"></a>Creazione e collegamento di pianificazioni ai processi
La pianificazione dei processi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent comporta la definizione della condizione o delle condizioni che provocano l'inizio dell'esecuzione del processo senza interazione dell'utente. È possibile pianificare l'esecuzione automatica di un processo creando una nuova pianificazione per il processo o collegando una pianificazione esistente al processo.  
  
È possibile creare una pianificazione in due modi:  
  
-   Creare la pianificazione durante la creazione di un processo.  
  
-   Creare la pianificazione in Esplora oggetti.  
  
Dopo la creazione, la pianificazione può essere collegata a più processi anche se è stata creata per un processo specifico. È anche possibile scollegare le pianificazioni dai processi.  
  
Una pianificazione può essere basata sul tempo o su un evento. Ad esempio, è possibile pianificare l'esecuzione di un processo nei momenti seguenti:  
  
-   All'avvio di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent.  
  
-   Quando l'utilizzo della CPU del computer corrisponde al livello di inattività.  
  
-   Una sola volta in corrispondenza di una data e un'ora specifiche.  
  
-   Su base periodica.  
  
In alternativa alle pianificazioni di processi, è possibile creare un avviso che risponda a un evento tramite l'esecuzione di un processo.  
  
> [!NOTE]  
> È possibile eseguire una sola istanza del processo alla volta. Se si tenta di eseguire manualmente un processo mentre questo viene eseguito in base alla pianificazione, la richiesta di esecuzione verrà rifiutata da Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .  
  
Per impedire l'esecuzione di un processo pianificato, è necessario eseguire una delle operazioni seguenti:  
  
-   Disabilitare la pianificazione.  
  
-   Disabilitare il processo.  
  
-   Scollegare la pianificazione dal processo.  
  
-   Arrestare il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent.  
  
-   Eliminare la pianificazione.  
  
Se la pianificazione non è attivata, il processo potrà essere eseguito comunque in risposta a un avviso o quando viene eseguito manualmente da un utente. Se una pianificazione di processo non è attivata, sarà disattivata per tutti i processi che la utilizzano.  
  
È necessario riattivare esplicitamente una pianificazione disabilitata. La modifica della pianificazione non consente di riabilitarla automaticamente.  
  
## <a name="scheduling-start-dates"></a>Date di inizio della pianificazione  
La data di inizio di una pianificazione deve essere maggiore o uguale a 19900101.  
  
Quando si collega una pianificazione a un processo, è necessario controllare la data di inizio utilizzata dalla pianificazione per eseguire il processo la prima volta. La data di inizio dipende dal giorno e dall'ora in cui la pianificazione viene collegata al processo. Ad esempio, se si crea una pianificazione che viene eseguita ogni due lunedì alle 8.00 Se si crea un processo alle ore 10.00 di lunedì 3 marzo 2008, la data di inizio della pianificazione sarà lunedì 17 marzo 2008. Se si crea un altro processo martedì 4 marzo 2008, la data di inizio della pianificazione è lunedì 10 marzo 2008.  
  
È possibile modificare la data di inizio della pianificazione dopo avere collegato la pianificazione a un processo.  
  
## <a name="cpu-idle-schedules"></a>Pianificazioni con CPU inattiva  
Per ottimizzare l'utilizzo della CPU, è possibile definire una condizione di inattività della CPU per Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] . [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Tale impostazione consente all'agente di eseguire i processi nei momenti di minor carico di lavoro della CPU. Ad esempio è possibile pianificare un processo di ricompilazione degli indici quando la CPU è in stato inattivo o durante i periodi di produzione ridotta.  
  
Prima di definire i processi da eseguire durante l'inattività della CPU, è necessario determinare il carico di lavoro della CPU durante l'elaborazione normale. A tale scopo, utilizzare [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler_md.md)] o Performance Monitor per monitorare il traffico nel server e raccogliere statistiche. Le informazioni raccolte saranno utili per la definizione di una percentuale di utilizzo corrispondente allo stato di inattività della CPU e della durata di tale stato.  
  
Definire la condizione di inattività come valore percentuale. L'utilizzo della CPU dovrà rimanere inferiore a tale valore per un periodo di tempo specificato. Definire quindi il periodo di tempo. Quando l'utilizzo della CPU è inferiore alla percentuale specificata per il periodo di tempo specificato, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent avvia tutti i processi pianificati per l'esecuzione con CPU inattiva. Per ulteriori informazioni sull'uso di [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler_md.md)] o di Performance Monitor per monitorare l'utilizzo della CPU, vedere [Monitoraggio dell'utilizzo della CPU](http://msdn.microsoft.com/en-us/2a02a3b6-07b2-4ad0-8a24-670414d19812).  
  
## <a name="related-tasks"></a>Attività correlate  
  
|||  
|-|-|  
|**Description**|**Argomento**|  
|Viene descritto come creare una pianificazione per un processo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent.|[Create a Schedule](../../ssms/agent/create-a-schedule.md)|  
|Viene descritto come pianificare un processo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent.|[Pianificare un processo](../../ssms/agent/schedule-a-job.md)|  
|Viene illustrato come definire la condizione di inattività della CPU per il server.|[Impostare tempo e durata di inattività della CPU &amp;#40;SQL Server Management Studio&amp;#41;](../../ssms/agent/set-cpu-idle-time-and-duration-sql-server-management-studio.md)|  
  
## <a name="see-also"></a>Vedere anche  
[sp_help_jobschedule](http://msdn.microsoft.com/en-us/2cded902-9272-4667-ac4b-a4f95a9f008e)  
[sysjobschedules](http://msdn.microsoft.com/en-us/ccdafec7-2a9b-4356-bffb-1caa3a12db59)  
  

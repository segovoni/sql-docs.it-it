---
title: Prerequisiti di migrazione di log shipping in gruppi di disponibilità Always On | Microsoft Docs
ms.custom: ''
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server], AlwaysOn Availability Groups
- Availability Groups [SQL Server], interoperability
ms.assetid: 2738ce65-205e-4682-92d8-dc7e37c58b2b
caps.latest.revision: 24
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: aa4ad02887ee8c0a5fdb0c7fa32f52593e910942
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34770657"
---
# <a name="prereqs-migrating-log-shipping-to-always-on-availability-groups"></a>Prerequisiti di migrazione di log shipping in gruppi di disponibilità Always On
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  In questo argomento vengono descritti i prerequisiti per convertire un database primario per il log shipping insieme a uno o più dei relativi database secondari in un database primario AlwaysOn e nei relativi database secondari.  
  
> [!NOTE]  
>  In un gruppo di disponibilità è possibile configurare qualsiasi database primario o secondario (possibilmente leggibile) come un database primario per il log shipping.  
  
 **Contenuto dell'argomento:**  
  
-   [Prerequisiti dei gruppi di disponibilità](#AGPrereqsRealAddress)  
  
-   [Prerequisiti per il log shipping](#LogShipPrereqs)  
  
-   [Attività correlate](#RelatedTasks)  
  
-   [Contenuto correlato](#RelatedContent)  
  
##  <a name="AGPrereqsRealAddress"></a> Prerequisiti dei gruppi di disponibilità  
 Per consentire l'esecuzione dei processi di backup sulla replica primaria del gruppo di disponibilità, usare le impostazioni di backup seguenti per i gruppi di disponibilità AlwaysOn:  
  
|Proprietà|Impostazione|  
|--------------|-------------|  
|Preferenza di backup automatico del gruppo di disponibilità.|Solo nella replica primaria|  
|Priorità di backup della replica primaria.|>0|  
  
 **Per ulteriori informazioni:**  
  
 [Visualizzare le proprietà dei gruppi di disponibilità &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/view-availability-group-properties-sql-server.md)  
  
 [Configurare il backup su repliche di disponibilità &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/configure-backup-on-availability-replicas-sql-server.md)  
  
##  <a name="LogShipPrereqs"></a> Prerequisiti per il log shipping  
  
-   È necessario che il database primario per il log shipping risieda nell'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] che ospita la replica primaria iniziale/corrente del gruppo di disponibilità.  
  
-   Per fare in modo che un determinato database secondario per il log shipping venga convertito in un database secondario AlwaysOn, tale database dovrà:  
  
    -   Utilizzare lo stesso nome del database primario.  
  
    -   Risiedere su un'istanza del server in cui viene ospitata una replica secondaria del gruppo di disponibilità.  
  
 Dopo l'esecuzione del processo di backup sul database primario, disabilitare il processo di backup e al termine dell'esecuzione del processo di ripristino su un determinato database secondario, disabilitare il processo di ripristino.  
  
 Dopo avere creato tutti i database secondari per il gruppo di disponibilità, se si desidera eseguire backup sulle repliche secondarie, è necessario configurare nuovamente la preferenza di backup automatico del gruppo di disponibilità.  
  
 **Per ulteriori informazioni:**  
  
 [Converting a logshipping configuration to Availability Group](https://blogs.msdn.microsoft.com/sqlalwayson/2012/01/09/converting-a-logshipping-configuration-to-availability-group/) (Conversione di una configurazione per il log shipping in un gruppo di disponibilità) (blog su SQL Server)  
  
##  <a name="RelatedTasks"></a> Attività correlate  
 **Log shipping**  
  
-   [Aggiornamento del log shipping a SQL Server 2016 &#40;Transact-SQL&#41;](../../../database-engine/log-shipping/upgrading-log-shipping-to-sql-server-2016-transact-sql.md)  
  
-   [Rimuovere il log shipping &#40;SQL Server&#41;](../../../database-engine/log-shipping/remove-log-shipping-sql-server.md)  
  
 **Gruppi di disponibilità AlwaysOn**  
  
-   [Usare la Creazione guidata Gruppo di disponibilità &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Utilizzare la finestra di dialogo Nuovo gruppo di disponibilità &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [Creare un gruppo di disponibilità &#40;Transact-SQL&#41;](../../../database-engine/availability-groups/windows/create-an-availability-group-transact-sql.md)  
  
-   [Creare un gruppo di disponibilità &#40;PowerShell di SQL Server&#41;](../../../database-engine/availability-groups/windows/create-an-availability-group-sql-server-powershell.md)  
  
-   [Creare un join di un database secondario a un gruppo di disponibilità &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [Configurare il backup su repliche di disponibilità &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/configure-backup-on-availability-replicas-sql-server.md)  
  
##  <a name="RelatedContent"></a> Contenuto correlato  
  
-   **Blog:**  
  
     [Converting a logshipping configuration to Availability Group](https://blogs.msdn.microsoft.com/sqlalwayson/2012/01/09/converting-a-logshipping-configuration-to-availability-group/)  
  
     [Pagina relativa all'aggiunta di un database primario e di database secondari per il log shipping in un gruppo di disponibilità esistente](https://blogs.msdn.microsoft.com/sqlalwayson/2012/02/01/add-a-log-shipping-primary-database-and-secondary-databases-to-an-existing-availability-group/)  
  
     [Pagina relativa ai blog del team di SQL Server AlwaysOn in cui è disponibile il blog del team ufficiale di SQL Server AlwaysOn](https://blogs.msdn.microsoft.com/sqlalwayson/)  
  
     [Pagina relativa ai blog del Servizio Supporto Tecnico Clienti per gli ingegneri di SQL Server](http://blogs.msdn.com/b/psssql/)  
  
-   **White paper:**  
  
     [Pagina relativa alla guida alla migrazione in cui viene illustrata la migrazione in gruppi di disponibilità AlwaysOn da distribuzioni precedenti in cui vengono combinati il mirroring del database e il log shipping](http://msdn.microsoft.com/library/jj635217)  
  
     [Pagina relativa ai white paper Microsoft per SQL Server 2012](http://msdn.microsoft.com/library/hh403491.aspx)  
  
     [Pagina relativa ai white paper del team di consulenza clienti di SQL Server](http://sqlcat.com/)  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sul log shipping &#40;SQL Server&#41;](../../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Panoramica di gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Monitoraggio di Gruppi di disponibilità &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/monitoring-of-availability-groups-sql-server.md)  
  
  

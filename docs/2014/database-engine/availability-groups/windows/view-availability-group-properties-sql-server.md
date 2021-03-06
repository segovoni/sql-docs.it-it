---
title: Visualizzazione delle Proprietà dei gruppi di disponibilità (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server]
ms.assetid: 61243c87-bd62-4510-863f-2a8f347caf1f
caps.latest.revision: 11
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7c59f778735c524ca8b1d0b41469114b21e5b591
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37312321"
---
# <a name="view-availability-group-properties-sql-server"></a>Visualizzazione delle Proprietà dei gruppi di disponibilità (SQL Server)
  In questo argomento viene illustrato come visualizzare le proprietà di un gruppo di disponibilità per un gruppo di disponibilità AlwaysOn tramite [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../../includes/tsql-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  

  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 **Per visualizzare e modificare le proprietà di un gruppo di disponibilità**  
  
1.  In Esplora oggetti connettersi all'istanza del server che ospita la replica primaria ed espandere l'albero del server.  
  
2.  Espandere il nodo **Disponibilità elevata AlwaysOn** e il nodo **Gruppi di disponibilità** .  
  
3.  Fare clic con il pulsante destro del mouse sul gruppo di disponibilità di cui si desidera visualizzare le proprietà e selezionare il comando **Proprietà** .  
  
4.  Nella finestra di dialogo **Proprietà gruppo di disponibilità** , utilizzare le pagine **Generale** e **Preferenze di backup** per visualizzare e, talvolta, modificare le proprietà del gruppo di disponibilità selezionato. Per altre informazioni, vedere [Proprietà dei gruppi di disponibilità/Nuovo gruppo di disponibilità &#40;pagina Generale&#41;](availability-group-properties-new-availability-group-general-page.md) e [Proprietà dei gruppi di disponibilità/Nuovo gruppo di disponibilità &#40;pagina Preferenze di backup&#41;](availability-group-properties-new-availability-group-backup-preferences-page.md).  
  
     Utilizzare la pagina **Autorizzazioni** per visualizzare gli account di accesso, i ruoli e le autorizzazioni esplicite correnti associati al gruppo di disponibilità. Per ulteriori informazioni, vedere [Permissions or Securables Page](../../../relational-databases/security/permissions-or-securables-page.md).  
  

  
##  <a name="TsqlProcedure"></a> Uso di Transact-SQL  
 **Per visualizzare le proprietà e lo stato di un gruppo di disponibilità**  
  
 Per eseguire una query sulle proprietà e sugli stati dei gruppi di disponibilità per cui l'istanza del server ospita una replica di disponibilità, utilizzare le viste seguenti:  
  
 [sys.availability_groups](/sql/relational-databases/system-catalog-views/sys-availability-groups-transact-sql)  
 Restituisce una riga per ogni gruppo di disponibilità per il quale l'istanza locale di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ospita una replica di disponibilità. Ogni riga contiene una copia memorizzata nella cache dei metadati del gruppo di disponibilità.  
  
 **Nomi delle colonne:** group_id, name, resource_id, resource_group_id, failure_condition_level, health_check_timeout, automated_backup_preference, automated_backup_preference_desc  
  
 [sys.availability_groups_cluster](/sql/relational-databases/system-catalog-views/sys-availability-groups-cluster-transact-sql)  
 Restituisce una riga per ogni gruppo di disponibilità nel cluster WSFC. Ogni riga contiene i metadati del gruppo di disponibilità del cluster WSFC (Windows Server Failover Clustering).  
  
 **Nomi delle colonne:** group_id, name, resource_id, resource_group_id, failure_condition_level, health_check_timeout, automated_backup_preference, automated_backup_preference_desc  
  
 [sys.dm_hadr_availability_group_states](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-group-states-transact-sql)  
 Restituisce una riga per ogni gruppo di disponibilità che dispone di una replica di disponibilità sull'istanza locale di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Ogni riga visualizza gli stati che definiscono l'integrità di un determinato gruppo di disponibilità.  
  
 **:** group_id, primary_replica, primary_recovery_health, primary_recovery_health_desc, secondary_recovery_health, secondary_recovery_health_desc, synchronization_health, synchronization_health_desc  
  

  
##  <a name="RelatedTasks"></a> Attività correlate  
 **Per visualizzare le informazioni sui gruppi di disponibilità**  
  
-   [Visualizzazione delle proprietà della replica di disponibilità &#40;SQL Server&#41;](view-availability-replica-properties-sql-server.md)  
  
-   [Visualizzare le proprietà del listener del gruppo di disponibilità &#40;SQL Server&#41;](view-availability-group-listener-properties-sql-server.md)  
  
-   [Criteri AlwaysOn per problemi operativi con gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](always-on-policies-for-operational-issues-always-on-availability.md)
  
-   [Usare il Dashboard Always On &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
-   [Monitorare Gruppi di disponibilità &#40;Transact-SQL&#41;](monitor-availability-groups-transact-sql.md)  
  
 **Per configurare un gruppo di disponibilità esistente**  
  
-   [Aggiungere una replica secondaria a un gruppo di disponibilità &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [Rimuovere una replica secondaria da un gruppo di disponibilità &#40;SQL Server&#41;](remove-a-secondary-replica-from-an-availability-group-sql-server.md)  
  
-   [Aggiungere un database a un gruppo di disponibilità &#40;SQL Server&#41;](availability-group-add-a-database.md)  
  
-   [Rimuovere un database secondario da un gruppo di disponibilità &#40;SQL Server&#41;](remove-a-secondary-database-from-an-availability-group-sql-server.md)  
  
-   [Creare o configurare un listener del gruppo di disponibilità &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [Rimuovere un listener del gruppo di disponibilità &#40;SQL Server&#41;](remove-an-availability-group-listener-sql-server.md)  
  
-   [Rimuovere un database primario da un gruppo di disponibilità &#40;SQL Server&#41;](remove-a-primary-database-from-an-availability-group-sql-server.md)  
  
-   [Rimuovere un gruppo di disponibilità &#40;SQL Server&#41;](remove-an-availability-group-sql-server.md)  
  
 **Per eseguire manualmente il failover di un gruppo di disponibilità**  
  
-   [Eseguire un failover manuale pianificato di un gruppo di disponibilità &#40;SQL Server&#41;](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md)  
  
-   [Eseguire un failover manuale forzato di un gruppo di disponibilità &#40;SQL Server&#41;](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)  
  

  
## <a name="see-also"></a>Vedere anche  
 [Panoramica di gruppi di disponibilità AlwaysOn &#40;SQL Server&#41; ](overview-of-always-on-availability-groups-sql-server.md) [monitorare gruppi di disponibilità &#40;Transact-SQL&#41; ](monitor-availability-groups-transact-sql.md) [criteri AlwaysOn per problemi operativi con AlwaysOn I gruppi di disponibilità &#40;SQL Server&#41;](always-on-policies-for-operational-issues-always-on-availability.md) 
  
  

---
title: Panoramica dei cmdlet di PowerShell per gruppi di disponibilità AlwaysOn (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], PowerShell cmdlets
- Availability Groups [SQL Server], about
- PowerShell [SQL Server], cmdlets
ms.assetid: b3fef0d5-b6d7-4386-a0f0-d06c165ad4de
caps.latest.revision: 35
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 09fbe31747ef722775a0156939f02fb49103fd22
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37231971"
---
# <a name="overview-of-powershell-cmdlets-for-alwayson-availability-groups-sql-server"></a>Panoramica dei cmdlet di PowerShell per Gruppi di disponibilità AlwaysOn (SQL Server)
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] PowerShell è una shell della riga di comando basata su attività e un linguaggio di scripting progettato appositamente per l'amministrazione del sistema. [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] fornisce un set di cmdlet di PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] per distribuire, gestire e monitorare gruppi di disponibilità, repliche di disponibilità e database di disponibilità.  
  
> [!NOTE]  
>  Con l'inizio corretto di un'azione è possibile che venga completato un cmdlet di PowerShell. Ciò non implica che l'azione desiderata, ad esempio il failover di un gruppo di disponibilità, sia stata completata. Quando si genera lo script di una sequenza di azioni, può essere necessario controllare lo stato delle azioni e attenderne il completamento.  
  
 In questo argomento vengono presentati i cmdlet per i seguenti set di attività:  
  
-   [Configurazione di un'istanza del server per gruppi di disponibilità AlwaysOn](#ConfiguringServerInstance)  
  
-   [Backup e ripristino dei database e dei log delle transazioni](#BnRcmdlets)  
  
-   [Creazione e gestione di un gruppo di disponibilità](#DeployManageAGs)  
  
-   [Creazione e gestione di un listener del gruppo di disponibilità](#AGlisteners)  
  
-   [Creazione e gestione di una replica di disponibilità](#DeployManageARs)  
  
-   [Aggiunta e gestione di un database di disponibilità](#DeployManageDbs)  
  
-   [Monitoraggio dello stato di integrità di un gruppo di disponibilità](#MonitorTblshtAGs)  
  
> [!NOTE]  
>  Per un elenco di argomenti in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] documentazione Online di cui viene descritto come usare i cmdlet per eseguire [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] attività, vedere la sezione "Attività correlate" di [Panoramica di gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).  
  
##  <a name="ConfiguringServerInstance"></a> Configurazione di un'istanza del Server per gruppi di disponibilità AlwaysOn  
  
|Cmdlet|Description|Supportati in|  
|-------------|-----------------|------------------|  
|`Disable-SqlAlwaysOn`|Disabilita la funzionalità [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] su un'istanza del server.|L'istanza del server specificata dal parametro `Path`, `InputObject` o `Name`. (L'edizione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] deve supportare [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]).|  
|`Enable-SqlAlwaysOn`|Abilita [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] su un'istanza di [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] che supporta la funzionalità [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] . Per informazioni sul supporto per [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], vedere [prerequisiti, restrizioni e consigli per gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).|Qualsiasi edizione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] che supporta [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].|  
|`New-SqlHadrEndPoint`|Crea un nuovo endpoint del mirroring del database in un'istanza del server. Questo endpoint è richiesto per lo spostamento di dati tra il database primario e quelli secondari.|Qualsiasi istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|  
|`Set-SqlHadrEndpoint`|Modifica le proprietà di un endpoint del mirroring del database esistente, ad esempio il nome, lo stato o le proprietà di autenticazione.|Istanza del server che supporta [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] e in cui non è presente un endpoint del mirroring del database|  
  
##  <a name="BnRcmdlets"></a> Backing Up and Restoring Databases and Transaction Logs  
  
|Cmdlet|Description|Supportati in|  
|-------------|-----------------|------------------|  
|`Backup-SqlDatabase`|Crea un backup dei dati o del log.|Qualsiasi database online (per [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], un database nell'istanza del server che ospita la replica primaria)|  
|`Restore-SqlDatabase`|Ripristina un backup.|Qualsiasi istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (per [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], un'istanza del server che ospita una replica secondaria)<br /><br /> **\*\* Importanti \* \***  quando si prepara un database secondario, è necessario usare i `-NoRecovery` parametro in ogni `Restore-SqlDatabase` comando.|  
  
 Per informazioni sull'uso di questi cmdlet per preparare un database secondario, vedere [Preparare manualmente un database secondario per un gruppo di disponibilità &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).  
  
##  <a name="DeployManageAGs"></a> Creating and Managing an Availability Group  
  
|Cmdlet|Description|Supportati in|  
|-------------|-----------------|------------------|  
|`New-SqlAvailabilityGroup`|Crea un nuovo gruppo di disponibilità.|Istanza del server per ospitare la replica primaria|  
|`Remove-SqlAvailabilityGroup`|Elimina un gruppo di disponibilità.|Istanza del server abilitata per HADR|  
|`Set-SqlAvailabilityGroup`|Imposta le proprietà di un gruppo di disponibilità; porta un gruppo di disponibilità online/offline|Istanza del server che ospita la replica primaria|  
|`Switch-SqlAvailabilityGroup`|Inizia una delle seguenti modalità di failover:<br /><br /> Failover forzato di un gruppo di disponibilità (con possibile perdita di dati).<br /><br /> Failover manuale di un gruppo di disponibilità.|Istanza del server che ospita la replica secondaria di destinazione|  
  
##  <a name="AGlisteners"></a> Creating and Managing an Availability Group Listener  
  
|Cmdlet|Description|Supportati in|  
|------------|-----------------|------------------|  
|`New-SqlAvailabilityGroupListener`|Crea un nuovo listener del gruppo di disponibilità e lo collega a un gruppo di disponibilità esistente.|Istanza del server che ospita la replica primaria|  
|`Set-SqlAvailabilityGroupListener`|Modifica l'impostazione della porta su un listener del gruppo di disponibilità esistente.|Istanza del server che ospita la replica primaria|  
|`Add-SqlAvailabilityGroupListenerStaticIp`|Aggiunge un indirizzo IP statico a una configurazione del listener del gruppo di disponibilità esistente. L'indirizzo IP può essere un indirizzo IPv4 con subnet o un indirizzo IPv6.|Istanza del server che ospita la replica primaria|  
  
##  <a name="DeployManageARs"></a> Creating and Managing an Availability Replica  
  
|Cmdlet|Description|Supportati in|  
|-------------|-----------------|------------------|  
|**New-SqlAvailabilityReplica**|Crea una nuova replica di disponibilità È possibile usare il `-AsTemplate` parametro per creare un oggetto di replica di disponibilità in memoria per ogni nuova replica di disponibilità.|Istanza del server che ospita la replica primaria|  
|`Join-SqlAvailabilityGroup`|Viene creato un join della replica secondaria al gruppo di disponibilità.|Istanza del server che ospita la replica secondaria|  
|**Remove-SqlAvailabilityReplica**|Elimina una replica di disponibilità.|Istanza del server che ospita la replica primaria|  
|`Set-SqlAvailabilityReplica`|Imposta le proprietà di una replica di disponibilità.|Istanza del server che ospita la replica primaria|  
  
##  <a name="DeployManageDbs"></a> Adding and Managing an Availability Database  
  
|Cmdlet|Description|Supportati in|  
|-------------|-----------------|------------------|  
|**Add-SqlAvailabilityDatabase**|Nella replica primaria viene aggiunto un database a un gruppo di disponibilità.<br /><br /> In una replica secondaria viene creato un join di un database secondario a un gruppo di disponibilità.|Qualsiasi istanza del server che ospita una replica di disponibilità (il comportamento è diverso per le repliche primarie e per quelle secondarie)|  
|**Remove-SqlAvailabilityDatabase**|Nella replica primaria il database viene rimosso dal gruppo di disponibilità.<br /><br /> In una replica secondaria il database secondario locale viene rimosso dalla replica secondaria locale.|Qualsiasi istanza del server che ospita una replica di disponibilità (il comportamento è diverso per le repliche primarie e per quelle secondarie)|  
|`Resume-SqlAvailabilityDatabase`|Riprende lo spostamento dati per un database di disponibilità sospeso.|L'istanza del server in cui si trova il database è stata sospesa.|  
|`Suspend-SqlAvailabilityDatabase`|Sospende lo spostamento dati per un database di disponibilità.|Qualsiasi istanza del server che ospita una replica di disponibilità.|  
  
##  <a name="MonitorTblshtAGs"></a> Monitoring Availability Group Health  
 Con i cmdlet [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] seguenti è possibile monitorare lo stato di un gruppo di disponibilità, nonché delle repliche e dei database relativi.  
  
> [!IMPORTANT]  
>  È necessario disporre delle autorizzazioni CONNECT, VIEW SERVER STATE e VIEW ANY DEFINITION per eseguire questi cmdlet.  
  
|Cmdlet|Description|Supportati in|  
|------------|-----------------|------------------|  
|`Test-SqlAvailabilityGroup`|Valuta l'integrità di un gruppo di disponibilità valutando i criteri della gestione basata su criteri di SQL Server.|Qualsiasi istanza del server che ospita una replica di disponibilità*.|  
|`Test-SqlAvailabilityReplica`|Valuta l'integrità delle repliche di disponibilità valutando i criteri della gestione basata su criteri di SQL Server.|Qualsiasi istanza del server che ospita una replica di disponibilità*.|  
|`Test-SqlDatabaseReplicaState`|Valuta l'integrità di un database di disponibilità su tutte le repliche di disponibilità aggiunte valutando i criteri della gestione basata su criteri di SQL Server.|Qualsiasi istanza del server che ospita una replica di disponibilità*.|  
  
 * Per visualizzare informazioni su tutte le repliche di disponibilità in un gruppo di disponibilità, usare l'istanza del server che ospita la replica primaria.  
  
 Per altre informazioni, vedere [usare i criteri AlwaysOn per visualizzare l'integrità di un gruppo di disponibilità &#40;SQL Server&#41;](use-always-on-policies-to-view-the-health-of-an-availability-group-sql-server.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica di gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Visualizzare la Guida di SQL Server PowerShell](../../../powershell/sql-server-powershell.md)  
  
  

---
title: availability_groups (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.availability_groups_TSQL
- availability_groups_TSQL
- sys.availability_groups
- availability_groups
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- sys.availability_groups catalog view
ms.assetid: da7fa55f-c008-45d9-bcfc-3513b02d9e71
caps.latest.revision: 42
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d92fb6ad5444abd447352d691887ce066c9fd7d8
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33181847"
---
# <a name="sysavailabilitygroups-transact-sql"></a>sys.availability_groups (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Restituisce una riga per ogni gruppo di disponibilità per il quale l'istanza locale di SQL Server ospita una replica di disponibilità. Ogni riga contiene una copia memorizzata nella cache dei metadati del gruppo di disponibilità.  
   
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**group_id**|**uniqueidentifier**|Identificatore univoco (GUID) del gruppo di disponibilità.|  
|**name**|**sysname**|Nome del gruppo di disponibilità. Si tratta di un nome specificato dall'utente che deve essere univoco all'interno del cluster di failover di Windows Server (WSFC).|  
|**resource_id**|**nvarchar(40)**|ID della risorsa del cluster WSFC.|  
|**resource_group_id**|**nvarchar(40)**|ID del gruppo di risorse del cluster WSFC del gruppo di disponibilità.|  
|**failure_condition_level**|**int**|Definite dall'utente livello condizione di errore in cui deve essere attivato un failover automatico, uno dei valori integer illustrati nella tabella immediatamente sotto questa tabella.<br /><br /> I livelli delle condizioni di errore (1-5) vanno dal livello 1, meno restrittivo, al livello 5, più restrittivo. Un livello della condizione specifico include tutti i livelli meno restrittivi. Il livello della condizione più restrittivo, ovvero il livello 5, include pertanto i quattro livelli della condizione meno restrittivi (1-4), il livello 4 include i livelli 1-3 e così via.<br /><br /> Per modificare questo valore, utilizzare l'opzione FAILURE_CONDITION_LEVEL del [ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzione.|  
|**health_check_timeout**|**int**|Tempo di attesa (in millisecondi) per il [sp_server_diagnostics](../../relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql.md) sistema stored procedure per restituire informazioni sull'integrità del server, prima che si presuppone che l'istanza del server sia lenta o bloccata. Il valore predefinito è 30000 millisecondi (30 secondi).<br /><br /> Per modificare questo valore, utilizzare l'opzione HEALTH_CHECK_TIMEOUT del [ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzione.|  
|**automated_backup_preference**|**tinyint**|Percorso preferito per l'esecuzione di backup nei database di disponibilità del gruppo di disponibilità. Di seguito sono i valori possibili e le relative descrizioni.<br /><br /> <br /><br /> 0: principale. I backup devono essere sempre eseguiti sulla replica primaria.<br /><br /> 1: solo secondario. È preferibile eseguire i backup in una replica secondaria.<br /><br /> 2: preferisco secondario. È preferibile eseguire i backup in una replica secondaria, ma nel caso in cui non sia disponibile alcuna replica secondaria per le operazioni di backup, è possibile eseguire i backup nella replica primaria. Questo è il comportamento predefinito.<br /><br /> 3: tutte le repliche. Nessuna preferenza sull'utilizzo della replica primaria o di una replica secondaria per l'esecuzione dei backup.<br /><br /> <br /><br /> Per altre informazioni, vedere [Repliche secondarie attive: Backup in repliche secondarie &#40;gruppi di disponibilità Always On&#41;](../../database-engine/availability-groups/windows/active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md).|  
|**automated_backup_preference_desc**|**nvarchar(60)**|Descrizione di **automated_backup_preference**, uno di:<br /><br /> PRIMARY<br /><br /> SECONDARY_ONLY<br /><br /> SECONDARY<br /><br /> Nessuno|  
|**version**|**smallint**|La versione dei metadati del gruppo di disponibilità archiviato nel Cluster di Failover di Windows. Questo numero di versione viene incrementato quando vengono aggiunte nuove funzionalità.|  
|**basic_features**|**bit**|Specifica se si tratta di un gruppo di disponibilità di base. Per altre informazioni, vedere [Gruppi di disponibilità di base &#40;gruppi di disponibilità Always On&#41;](../../database-engine/availability-groups/windows/basic-availability-groups-always-on-availability-groups.md).|  
|**dtc_support**|**bit**|Specifica se il supporto DTC è stato abilitato per questo gruppo di disponibilità. Il **DTC_SUPPORT** opzione di **CREATE AVAILABILITY GROUP** controlla questa impostazione.|  
|**db_failover**|**bit**|Specifica se il gruppo di disponibilità supporta il failover per le condizioni di integrità del database. Il **DB_FAILOVER** opzione di **CREATE AVAILABILITY GROUP** controlla questa impostazione.|  
|**is_distributed**|**bit**|Specifica se si tratta di un gruppo di disponibilità distribuito. Per altre informazioni, vedere [Gruppi di disponibilità distribuiti &#40;gruppi di disponibilità Always On&#41;](../../database-engine/availability-groups/windows/distributed-availability-groups-always-on-availability-groups.md).|  
  
## <a name="failure-condition-level--values"></a>Valori del livello condizione di errore  
 Nella tabella seguente vengono descritti i livelli di condizione di errore possibili per il **failure_condition_level** colonna.  
  
|Value|Condizione di errore|  
|-----------|-----------------------|  
|1|Specifica che deve essere avviato un failover automatico quando si verifica una delle condizioni seguenti:<br /><br /> <br /><br /> -La [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] servizio è inattivo.<br /><br /> -Il lease del gruppo di disponibilità per la connessione al cluster di failover WSFC scade poiché non viene ricevuto alcun Acknowledgement dall'istanza del server. Per altre informazioni, vedere [Funzionamento: timeout lease di SQL Server Always On](http://blogs.msdn.com/b/psssql/archive/2012/09/07/how-it-works-sql-server-Always%20On-lease-timeout.aspx).|  
|2|Specifica che deve essere avviato un failover automatico quando si verifica una delle condizioni seguenti:<br /><br /> <br /><br /> -L'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non si connette al cluster e l'utente specificato **health_check_timeout** viene superata la soglia del gruppo di disponibilità.<br /><br /> -La replica di disponibilità è in stato di errore.|  
|3|Specifica che deve essere avviato un failover automatico in caso di errori interni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] critici, ad esempio spinlock orfani, gravi violazioni dell'accesso in scrittura o dumping eccessivo.<br /><br /> Si tratta del valore predefinito.|  
|4|Specifica che deve essere avviato un failover automatico in caso di errori interni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con gravità moderata, ad esempio una condizione persistente di memoria insufficiente nel pool di risorse interno di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|5|Specifica che deve essere avviato un failover automatico in caso di qualsiasi condizione di errore qualificata, tra cui:<br /><br /> <br /><br /> -Esaurimento dei thread di lavoro del motore SQL.<br /><br /> -Il rilevamento di un deadlock irrisolvibile.|  
  
## <a name="security"></a>Sicurezza  
  
### <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione VIEW ANY DEFINITION nell'istanza del server.  
  
## <a name="see-also"></a>Vedere anche  
 [sys.availability_replicas &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-availability-replicas-transact-sql.md)   
 [Gruppi di disponibilità Always On &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)   
 [Monitorare gruppi di disponibilità & #40; Transact-SQL & #41;](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [Monitorare Gruppi di disponibilità &#40;Transact-SQL&#41;](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)  
  
  

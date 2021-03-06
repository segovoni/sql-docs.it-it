---
title: Sys. Databases (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- databases
- databases_TSQL
- sys.databases
- sys.databases_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.databases catalog view
ms.assetid: 46c288c1-3410-4d68-a027-3bbf33239289
caps.latest.revision: 152
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 49f8ab952cad03717474d17a4697063050777e26
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33182527"
---
# <a name="sysdatabases-transact-sql"></a>sys.databases (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Contiene una riga per ogni database nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Se non è un database `ONLINE`, o `AUTO_CLOSE` è impostato su `ON` e il database viene chiuso, i valori di alcune colonne potrebbero essere `NULL`. Se un database è `OFFLINE`, la riga corrispondente non è visibile agli utenti con privilegi limitati. Per visualizzare la riga corrispondente se il database è `OFFLINE`, un utente deve disporre almeno del `ALTER ANY DATABASE` autorizzazione a livello di server, o `CREATE DATABASE` disporre dell'autorizzazione per il `master` database.  
  

  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Nome del database univoco in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o in un server [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|  
|**database_id**|**int**|ID del database univoco in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o in un server [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|  
|**source_database_id**|**int**|Non-NULL = ID del database di origine di questo snapshot di database.<br /> NULL = Non è uno snapshot di database.|  
|**owner_sid**|**varbinary(85)**|ID di sicurezza (SID) del proprietario esterno del database, registrato nel server. Per informazioni che possono disporre di un database, vedere il **ALTER AUTHORIZATION per i database** sezione [ALTER AUTHORIZATION](../../t-sql/statements/alter-authorization-transact-sql.md).|  
|**create_date**|**datetime**|Data di creazione o di ridenominazione del database. Per **tempdb**, questo valore cambia ogni volta che il server viene riavviato.|  
|**compatibility_level**|**tinyint**|Integer corrispondente alla versione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per cui è compatibile il comportamento:<br /> **Valore** : **si applica a**<br /> 70: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<br /> 80: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<br /> 90: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]<br /> 100: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]<br /> 110: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]<br /> 120: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]<br /> 130: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] |  
|**nome_regole_di_confronto**|**sysname**|Regole di confronto per il database. Rappresentano le regole di confronto predefinite nel database.<br /> NULL = Il database non è online o l'opzione AUTO_CLOSE è impostata su ON e il database è chiuso.|  
|**user_access**|**tinyint**|Impostazione per l'accesso utente:<br /> 0 = MULTI_USER specificato<br /> 1 = SINGLE_USER specificato<br /> 2 = RESTRICTED_USER specificato|  
|**user_access_desc**|**nvarchar(60)**|Descrizione dell'impostazione per l'accesso utente.|  
|**is_read_only**|**bit**|1 = Il database è READ_ONLY<br /> 0 = Il database è READ_WRITE|  
|**is_auto_close_on**|**bit**|1 = AUTO_CLOSE è ON<br /> 0 = AUTO_CLOSE è OFF|  
|**is_auto_shrink_on**|**bit**|1 = AUTO_SHRINK è ON<br /> 0 = AUTO_SHRINK è OFF|  
|**state**|**tinyint**|**Valore &#124; si applica a**<br /> 0 = ONLINE <br /> 1 = RESTORING <br /> 2 = recupero in corso: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /> 3 = RECOVERY_PENDING: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /> 4 = SUSPECT <br /> 5 = EMERGENCY: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /> 6 = non in linea: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /> 7 = COPIA: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] [!INCLUDE[ssGeoDR](../../includes/ssgeodr-md.md)] <br /> 10 = OFFLINE_SECONDARY: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] [!INCLUDE[ssGeoDR](../../includes/ssgeodr-md.md)] <br /><br /> **Nota:** per i database Always On, eseguire una query di `database_state` oppure `database_state_desc` le colonne di [DM hadr_database_replica_states](../../relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql.md).|  
|**state_desc**|**nvarchar(60)**|Descrizione dello stato del database. Vedere lo stato.|  
|**is_in_standby**|**bit**|Il database è di sola lettura per il log di ripristino.|  
|**is_cleanly_shutdown**|**bit**|1 = Il database è stato chiuso normalmente, recupero non necessario all'avvio<br /> 0 = Il database non è stato chiuso normalmente, recupero necessario all'avvio|  
|**is_supplemental_logging_enabled**|**bit**|1 = SUPPLEMENTAL_LOGGING è ON<br /> 0 = SUPPLEMENTAL_LOGGING è OFF|  
|**snapshot_isolation_state**|**tinyint**|Stato delle transazioni di isolamento dello snapshot consentite, in base all'impostazione ALLOW_SNAPSHOT_ISOLATION:<br /> 0 = Lo stato di isolamento dello snapshot è OFF (valore predefinito). L'isolamento dello snapshot non è consentito.<br /> 1 = Lo stato di isolamento dello snapshot è ON. L'isolamento dello snapshot è consentito.<br /> 2 = Lo stato di isolamento dello snapshot è in transizione verso lo stato OFF. Tutte le modifiche delle transazioni hanno un numero di versione. Non è possibile avviare nuove transazioni utilizzando l'isolamento dello snapshot. Il database resta in transizione verso lo stato OFF fino a quando tutte le transazioni attive al momento dell'esecuzione di ALTER DATABASE non vengono completate.<br /> 3 = Lo stato di isolamento dello snapshot è in transizione verso lo stato ON. Le modifiche delle nuove transazioni hanno un numero di versione. Le transazioni non possono utilizzare l'isolamento dello snapshot fino a quando lo stato di isolamento non diventa 1 (ON). Il database resta in transizione verso lo stato ON fino a quando tutte le transazioni di aggiornamento attive al momento dell'esecuzione di ALTER DATABASE non vengono completate.|  
|**snapshot_isolation_state_desc**|**nvarchar(60)**|Descrizione dello stato delle transazioni di isolamento dello snapshot consentite, in base all'opzione ALLOW_SNAPSHOT_ISOLATION.|  
|**is_read_committed_snapshot_on**|**bit**|1 = Opzione READ_COMMITTED_SNAPSHOT impostata su ON. Le operazioni di lettura con il livello di isolamento Read committed sono basate sulle analisi snapshot e non acquisiscono blocchi.<br /> 0 = Opzione READ_COMMITTED_SNAPSHOT impostata su OFF (impostazione predefinita). Le operazioni di lettura con il livello di isolamento Read committed utilizzano i blocchi di condivisione.|  
|**recovery_model**|**tinyint**|Modello di recupero selezionato:<br /> 1 = FULL<br /> 2 = BULK_LOGGED<br /> 3 = SIMPLE|  
|**recovery_model_desc**|**nvarchar(60)**|Descrizione del modello di recupero selezionato.|  
|**page_verify_option**|**tinyint**|Impostazione dell'opzione PAGE_VERIFY:<br /> 0 = NONE<br /> 1 = TORN_PAGE_DETECTION<br /> 2 = CHECKSUM|  
|**page_verify_option_desc**|**nvarchar(60)**|Descrizione dell'impostazione dell'opzione PAGE_VERIFY.|  
|**is_auto_create_stats_on**|**bit**|1 = AUTO_CREATE_STATISTICS è ON<br /> 0 = AUTO_CREATE_STATISTICS è OFF|  
|**is_auto_create_stats_incremental_on**|**bit**|Indica l'impostazione predefinita per l'opzione incrementale delle statistiche automatiche.<br /> 0 = Le statistiche a creazione automatica sono non incrementali<br /> 1 = Le statistiche a creazione automatica sono incrementali, se possibile<br /> **Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**is_auto_update_stats_on**|**bit**|1 = AUTO_UPDATE_STATISTICS è ON<br /> 0 = AUTO_UPDATE_STATISTICS è OFF|  
|**is_auto_update_stats_async_on**|**bit**|1 = AUTO_UPDATE_STATISTICS_ASYNC è ON<br /> 0 = AUTO_UPDATE_STATISTICS_ASYNC è OFF|  
|**is_ansi_null_default_on**|**bit**|1 = ANSI_NULL_DEFAULT è ON<br /> 0 = ANSI_NULL_DEFAULT è OFF|  
|**is_ansi_nulls_on**|**bit**|1 = ANSI_NULLS è ON<br /> 0 = ANSI_NULLS è OFF|  
|**is_ansi_padding_on**|**bit**|1 = ANSI_PADDING è ON<br /> 0 = ANSI_PADDING è OFF|  
|**is_ansi_warnings_on**|**bit**|1 = ANSI_WARNINGS è ON<br /> 0 = ANSI_WARNINGS è OFF|  
|**is_arithabort_on**|**bit**|1 = ARITHABORT è ON<br /> 0 = ARITHABORT è OFF|  
|**is_concat_null_yields_null_on**|**bit**|1 = CONCAT_NULL_YIELDS_NULL è ON<br /> 0 = CONCAT_NULL_YIELDS_NULL è OFF|  
|**is_numeric_roundabort_on**|**bit**|1 = NUMERIC_ROUNDABORT è ON<br /> 0 = NUMERIC_ROUNDABORT è OFF|  
|**is_quoted_identifier_on**|**bit**|1 = QUOTED_IDENTIFIER è ON<br /> 0 = QUOTED_IDENTIFIER è OFF|  
|**is_recursive_triggers_on**|**bit**|1 = RECURSIVE_TRIGGERS è ON<br /> 0 = RECURSIVE_TRIGGERS è OFF|  
|**is_cursor_close_on_commit_on**|**bit**|1 = CURSOR_CLOSE_ON_COMMIT è ON<br /> 0 = CURSOR_CLOSE_ON_COMMIT è OFF|  
|**is_local_cursor_default**|**bit**|1 = CURSOR_DEFAULT è locale<br /> 0 = CURSOR_DEFAULT è globale|  
|**is_fulltext_enabled**|**bit**|1 = La funzionalità full-text è abilitata per il database<br /> 0 = La funzionalità full-text è disabilitata per il database|  
|**is_trustworthy_on**|**bit**|1 = Database contrassegnato come attendibile<br /> 0 = Database non contrassegnato come attendibile|  
|**is_db_chaining_on**|**bit**|1 = Il concatenamento della proprietà tra database è impostato su ON<br /> 0 = Il concatenamento della proprietà tra database è impostato su OFF|  
|**is_parameterization_forced**|**bit**|1 = La parametrizzazione è FORCED<br /> 0 = La parametrizzazione è SIMPLE|  
|**is_master_key_encrypted_by_server**|**bit**|1 = Il database include una chiave master crittografata<br /> 0 = Il database non include una chiave master crittografata|  
|**is_query_store_on**|**bit**|1 = la query store è abilitata per questo database. Controllare [database_query_store_options](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md) per visualizzare lo stato di archivio query.<br /> 0 = la query store non è abilitato<br /> **Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] a [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
|**is_published**|**bit**|1 = Database di pubblicazione in una topologia di replica snapshot o transazionale<br /> 0 = Il database non è un database di pubblicazione|  
|**is_subscribed**|**bit**|Questa colonna non viene utilizzata. Restituirà sempre 0, indipendentemente dallo stato del sottoscrittore del database.|  
|**is_merge_published**|**bit**|1 = Database di pubblicazione in una topologia di replica di tipo merge<br /> 0 = Il database non è un database di pubblicazione in una topologia di replica di tipo merge|  
|**is_distributor**|**bit**|1 = Database di distribuzione per una topologia di replica<br /> 0 = Il database non è un database di distribuzione per una topologia di replica|  
|**is_sync_with_backup**|**bit**|1 = Database contrassegnato per la sincronizzazione della replica con backup<br /> 0 = Database non contrassegnato per la sincronizzazione della replica con backup|  
|**service_broker_guid**|**uniqueidentifier**|Identificatore di Service Broker per questo database. Utilizzato come il **broker_instance** della destinazione nella tabella di routing.|  
|**is_broker_enabled**|**bit**|1 = Il broker nel database sta inviando e ricevendo messaggi.<br /> 0 = Tutti i messaggi inviati resteranno nella coda di trasmissione e i messaggi ricevuti non verranno inseriti nelle code in questo database.<br /> Per impostazione predefinita, Service Broker è disabilitato per i database ripristinati o collegati, L'eccezione è rappresentata dal mirroring del database, in cui Service Broker viene abilitato dopo il failover.|  
|**log_reuse_wait**|**tinyint**|Riutilizzo di spazio log delle transazioni è attualmente in attesa uno dei seguenti come ultimo checkpoint. (Per ulteriori spiegazioni di questi valori, vedere [Log delle transazioni](../../relational-databases/logs/the-transaction-log-sql-server.md).)<br /> 0 = Nessuno<br />   1 = Checkpoint (quando un database utilizza un modello di recupero e ha un filegroup ottimizzato per la memoria, si prevede che la colonna log_reuse_wait indichi il checkpoint o xtp_checkpoint). **Si applica a** [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />  2 = Backup del log **si applica a** [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />  3 = backup attivo o il ripristino **si applica a** [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />  4 = transazione attiva **si applica a** [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />  5 = mirroring del database **si applica a** [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />  6 = replica **si applica a** [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />  7 = creazione dello snapshot di database **si applica a** [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />  8 = analisi del log **si applica a**<br />  9 = di gruppi di disponibilità AlwaysOn replica secondaria applica i record di log delle transazioni del database a un database secondario corrispondente. **Si applica a** [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Nelle versioni precedenti di SQL Server, 9 = Altro (temporaneo).<br />  10 = solo per uso interno **si applica a** [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />  11 = solo per uso interno **si applica a** [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /> 12 = solo per uso interno **si applica a** [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />13 = pagina più recente **si applica a** [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /> 14 = altro **si applica a** [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br />  16 = XTP_CHECKPOINT (quando un database utilizza un modello di recupero e ha un filegroup ottimizzato per la memoria, si prevede che la colonna log_reuse_wait indichi il checkpoint o xtp_checkpoint). **Si applica a** [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|**LOG_REUSE_WAIT_DESC**|**nvarchar(60)**|La descrizione del riutilizzo dello spazio del log delle transazioni è attualmente in attesa come ultimo checkpoint.|  
|**is_date_correlation_on**|**bit**|1 = DATE_CORRELATION_OPTIMIZATION è ON<br /> 0 = DATE_CORRELATION_OPTIMIZATION è OFF|  
|**is_cdc_enabled**|**bit**|1 = Database abilitato per l'acquisizione dei dati delle modifiche. Per altre informazioni, vedere [Sys. sp_cdc_enable_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-db-transact-sql.md).|  
|**is_encrypted**|**bit**|Indica se il database è crittografato (riflette l'ultimo stato impostato utilizzando la clausola ALTER DATABASE SET ENCRYPTION). I possibili valori sono i seguenti:<br /> 1 = Crittografato<br /> 0 = Non crittografato<br /> Per altre informazioni sulla crittografia del database, vedere [Transparent Data Encryption &#40;TDE&#41;](../../relational-databases/security/encryption/transparent-data-encryption.md).<br /> Se il database è in corso la decrittografia, **is_encrypted** Mostra un valore pari a 0. È possibile visualizzare lo stato del processo di crittografia utilizzando il [Sys.dm database_encryption_keys](../../relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql.md) vista a gestione dinamica.|  
|**is_honor_broker_priority_on**|**bit**|Indica se nel database vengono rispettate le priorità di conversazione (riflette l'ultimo stato impostato utilizzando la clausola ALTER DATABASE SET HONOR_BROKER_PRIORITY). I possibili valori sono i seguenti:<br /> 1 = HONOR_BROKER_PRIORITY è ON<br /> 0 = HONOR_BROKER_PRIORITY è OFF|  
|**replica_id**|**uniqueidentifier**|Identificatore univoco della replica di disponibilità di [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] locale del gruppo di disponibilità, se presente, di cui fa parte il database.<br /> NULL = il database non fa parte di una replica di disponibilità di un gruppo di disponibilità.<br /> **Si applica a**: da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**group_database_id**|**uniqueidentifier**|Identificatore univoco del database all'interno di un sempre nel gruppo di disponibilità, se presente, in cui si trova il database. **group_database_id** è lo stesso per il database nella replica primaria e in ogni replica secondaria in cui il database è stato aggiunto al gruppo di disponibilità.<br /> NULL = il database non fa parte di una replica di disponibilità in alcun gruppo di disponibilità.<br /> **Si applica a**: da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**resource_pool_id**|**int**|L'ID del pool di risorse per cui è stato eseguito il mapping al database. Questa pool di risorse controlla la memoria totale disponibile alle tabelle ottimizzate per la memoria nel database.<br /> **Si applica a**: da [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|**default_language_lcid**|**smallint**|Indica l'ID locale (LCID) della lingua predefinita di un database indipendente.<br /> **Nota** funziona come il [configurare l'opzione di configurazione Server default language](../../database-engine/configure-windows/configure-the-default-language-server-configuration-option.md) dei **sp_configure**. Questo valore è **null** per un database non indipendente.<br /> **Si applica a**: da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**default_language_name**|**nvarchar(128)**|Indica la lingua predefinita di un database indipendente.<br /> Questo valore è **null** per un database non indipendente.<br /> **Si applica a**: da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**default_fulltext_language_lcid**|**int**|Indica l'ID locale (LCID) della lingua full-text predefinita del database indipendente.<br /> **Nota** funziona come il valore predefinito [configurare l'opzione di configurazione Server default full-text language](../../database-engine/configure-windows/configure-the-default-full-text-language-server-configuration-option.md) dei **sp_configure**. Questo valore è **null** per un database non indipendente.<br /> **Si applica a**: da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**default_fulltext_language_name**|**nvarchar(128)**|Indica la lingua full-text predefinita del database indipendente.<br /> Questo valore è **null** per un database non indipendente.<br /> **Si applica a**: da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**is_nested_triggers_on**|**bit**|Indica se nel database indipendente sono consentiti trigger nidificati.<br /> 0 = I trigger nidificati non sono consentiti<br /> 1 = I trigger nidificati sono consentiti<br /> **Nota** funziona come il [configurare l'opzione di configurazione del Server nested triggers](../../database-engine/configure-windows/configure-the-nested-triggers-server-configuration-option.md) dei **sp_configure**. Questo valore è **null** per un database non indipendente. Vedere [Sys. Configurations &#40;Transact-SQL&#41; ](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md) per ulteriori informazioni.<br /> **Si applica a**: da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**is_transform_noise_words_on**|**bit**|Indica se le parole non significative devono essere trasformate nel database indipendente.<br /> 0 = Le parole non significative non devono essere trasformate.<br /> 1 = Le parole non significative devono essere trasformate.<br /> **Nota** funziona come il [server transform noise words Server Configuration Option](../../database-engine/configure-windows/transform-noise-words-server-configuration-option.md) dei **sp_configure**. Questo valore è **null** per un database non indipendente. Vedere [Sys. Configurations &#40;Transact-SQL&#41; ](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md) per ulteriori informazioni.<br /> **Si applica a**: da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|**two_digit_year_cutoff**|**smallint**|Indica un valore di un numero compreso tra 1753 e 9999 per rappresentare l'anno di cambio data per l'interpretazione degli anni a due cifre come anni a quattro cifre.<br /> **Nota** funziona come il [configurare l'anno a due cifre cutoff Server Configuration Option](../../database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option.md) dei **sp_configure**. Questo valore è **null** per un database non indipendente. Vedere [Sys. Configurations &#40;Transact-SQL&#41; ](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md) per ulteriori informazioni.<br /> **Si applica a**: da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**containment**|**tinyint non null**|Indica lo stato di indipendenza del database.<br />  0 = L'indipendenza del database è disabilitata. **Si applica a**: da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]<br /> 1 = database si trova nello stato di indipendenza parziale **si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|**containment_desc**|**nvarchar(60) non null**|Indica lo stato di indipendenza del database.<br /> NONE = Database legacy (zero indipendenza)<br /> PARTIAL = Database parzialmente indipendente<br /> **Si applica a**: da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**target_recovery_time_in_seconds**|**int**|Tempo stimato, in secondi, per il recupero del database. Ammette valori Null.<br /> **Si applica a**: da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**delayed_durability**|**int**|L'impostazione di durabilità posticipata:<br /> 0 = DISABILITATO<br /> 1 = CONSENTITO<br /> 2 = FORZATO<br /> Per altre informazioni, vedere [Controllo della durabilità delle transazioni](../../relational-databases/logs/control-transaction-durability.md).<br /> **Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|  
|**delayed_durability_desc**|**nvarchar(60)**|L'impostazione di durabilità posticipata:<br /> DISABLED<br /> ALLOWED<br /> FORCED<br /> **Si applica a**: da [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].<br /> **Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|  
|**is_memory_optimized_elevate_to_snapshot_on**|**bit**|Le tabelle con ottimizzazione per la memoria sono accessibili tramite l'isolamento SNAPSHOT quando l'impostazione della sessione HIGH TRANSACTION ISOLATION LEVEL è impostata su un livello di isolamento inferiore, READ COMMITTED o READ UNCOMMITTED.<br /> 1 = Il livello di isolamento minimo è SNAPSHOT.<br /> 0 = Il livello di isolamento non è elevato.|  
|**is_federation_member**|**bit**|Indica se il database è un membro di una federazione.<br /> **Si applica a**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
|**is_remote_data_archive_enabled**|**bit**|Indica se il database è stato esteso.<br /> 0 = il database non è abilitata per l'estensione.<br /> 1 = il database è abilitata per l'estensione.<br /> **Si applica a**: da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /> Per ulteriori informazioni, vedere [estensione Database](../../sql-server/stretch-database/stretch-database.md).|  
|**is_mixed_page_allocation_on**|**bit**|Indica se le tabelle e indici nel database possono allocare pagine iniziali da extent misti.<br /> 0 = le tabelle e indici nel database sempre allocano pagine iniziali da extent uniformi.<br /> 1 = le tabelle e indici nel database possono allocare pagine iniziali da extent misti.<br /> **Si applica a**: da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /> Per altre informazioni, vedere l'opzione SET MIXED_PAGE_ALLOCATION di [opzioni ALTER DATABASE SET &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md).|  
|**is_temporal_retention_enabled**|**bit**|Indica se l'attività di pulizia dei criteri di conservazione temporale è abilitato.<br /> **Si applica a**: Database SQL di Azure|
|**catalog_collation_type**|**int**|L'impostazione di regole di confronto del catalogo:<br />0 = DATABASE_DEFAULT<br />2 = SQL_Latin_1_General_CP1_CI_AS<br /> **Si applica a**: Database SQL di Azure|
|**catalog_collation_type_desc**|**nvarchar(60)**|L'impostazione di regole di confronto del catalogo:<br />DATABASE_DEFAULT<br />SQL_Latin_1_General_CP1_CI_AS<br /> **Si applica a**: Database SQL di Azure|
  
## <a name="permissions"></a>Autorizzazioni  
 Se il chiamante di `sys.databases` non è il proprietario del database e il database non è `master` o `tempdb`, le autorizzazioni minime necessarie per visualizzare la riga corrispondente sono `ALTER ANY DATABASE` o `VIEW ANY DATABASE` autorizzazione a livello di server o `CREATE DATABASE` disporre dell'autorizzazione per la `master` database. Il database a cui è connesso il chiamante può sempre essere visualizzato `sys.databases`.  
  
> [!IMPORTANT]  
>  Per impostazione predefinita, il ruolo public è il `VIEW ANY DATABASE` autorizzazione, che consente a tutti gli account di accesso visualizzare informazioni sul database. Per bloccare la capacità di rilevare un database, un account di accesso `REVOKE` il `VIEW ANY DATABASE` autorizzazioni `public`, o `DENY` il ' autorizzazione VIEW ANY DATABASE per singoli account di accesso.  
  
## <a name="includesssdsincludessssds-mdmd-remarks"></a>Osservazioni su [!INCLUDE[ssSDS](../../includes/sssds-md.md)]  
 In [!INCLUDE[ssSDS](../../includes/sssds-md.md)], questa vista è disponibile nel `master` database e nei database utente. Nel `master` database, questa vista restituisce le informazioni sul `master` database e tutti i database utente nel server. In un database utente questa vista restituisce informazioni solo sul database corrente e sul database master.  
  
 Utilizzare la vista `sys.databases` nel database `master` del server del [!INCLUDE[ssSDS](../../includes/sssds-md.md)] in cui viene creato il nuovo database. Verrà avviata la copia del database, è possibile eseguire una query di `sys.databases` e `sys.dm_database_copies` viste dal `master` database del server di destinazione per recuperare ulteriori informazioni sullo stato della copia.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-query-the-sysdatabases-view"></a>A. Eseguire una query sulla vista sys.databases  
 L'esempio seguente restituisce alcune delle colonne disponibili nel `sys.databases` visualizzazione.  
  
```  
SELECT name, user_access_desc, is_read_only, state_desc, recovery_model_desc  
FROM sys.databases;  
```  
  
### <a name="b-check-the-copying-status-in-includesssdsincludessssds-mdmd"></a>B. Verificare lo stato di copia in [!INCLUDE[ssSDS](../../includes/sssds-md.md)]  
 Le query di esempio seguente il `sys.databases` e `sys.dm_database_copies` viste per restituire informazioni su un database dell'operazione di copia.  
  
**Si applica a**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|  
  
```  
-- Execute from the master database.  
SELECT a.name, a.state_desc, b.start_date, b.modify_date, b.percentage_complete  
FROM sys.databases AS a  
INNER JOIN sys.dm_database_copies AS b ON a.database_id = b.database_id  
WHERE a.state = 7;  
```  
### <a name="c-check-the-temporal-retention-policy-status-in-includesssdsincludessssds-mdmd"></a>C. Controllare lo stato di criteri di conservazione temporale in [!INCLUDE[ssSDS](../../includes/sssds-md.md)]  
 Le query di esempio seguente il `sys.databases` per restituire informazioni se l'attività di pulizia di memorizzazione temporale è abilitato. Tenere presente che dopo l'operazione di ripristino temporale conservazione è disabilitato per impostazione predefinita. Utilizzare `ALTER DATABASE` per abilitarlo in modo esplicito.
  
**Si applica a**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]  
  
```  
-- Execute from the master database.  
SELECT a.name, a.is_temporal_history_retention_enabled 
FROM sys.databases AS a;
```  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [sys.database_mirroring_witnesses &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/database-mirroring-witness-catalog-views-sys-database-mirroring-witnesses.md)   
 [Sys. database_recovery_status &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-recovery-status-transact-sql.md)   
 [Viste del catalogo di database e file &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql.md)   
 [sys.dm_database_copies &#40;Database SQL di Azure&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-database-copies-azure-sql-database.md)  
  
  

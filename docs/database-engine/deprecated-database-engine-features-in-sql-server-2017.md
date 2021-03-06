---
title: Funzionalità del motore di database deprecate in SQL Server 2017 | Microsoft Docs
ms.custom: ''
ms.date: 05/09/2018
ms.prod: sql
ms.prod_service: high-availability
ms.component: database-engine
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- deprecated features [SQL Server]
- Database Engine [SQL Server], backward compatibility
- deprecation [SQL Server], feature list
ms.assetid: ''
caps.latest.revision: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 9b356e2405a42ba2f8e73feb81f110e58a3fbdad
ms.sourcegitcommit: feff98b3094a42f345a0dc8a31598b578c312b38
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/11/2018
ms.locfileid: "34052091"
---
# <a name="deprecated-database-engine-features-in-sql-server-2017"></a>Funzionalità del motore di database deprecate in SQL Server 2017
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

  In questo argomento verranno descritte le funzionalità deprecate di [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] ancora disponibili in [!INCLUDE[sssqlv14-md](../includes/sssqlv14-md.md)]. È consigliabile non usare le funzionalità deprecate nelle nuove applicazioni.  
  
Quando una funzionalità è contrassegnata come deprecata significa che:
-  La funzionalità è solo in modalità manutenzione. Non verranno apportate nuove modifiche, incluse quelle correlate all'interoperabilità con le nuove funzionalità.
-  Microsoft si impegna a non rimuovere una funzionalità deprecata dalle versioni future per semplificare gli aggiornamenti. Tuttavia, in rare situazioni, una funzionalità potrebbe essere rimossa in modo permanente da [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] se ne limita le innovazioni future.
-  Per i nuovi progetti di sviluppo, non è consigliabile usare funzionalità deprecate.      
  
È possibile monitorare l'utilizzo delle funzionalità deprecate tramite il contatore delle prestazioni [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] :Funzionalità deprecate e gli eventi di traccia. Per altre informazioni, vedere [Usare oggetti di SQL Server](../relational-databases/performance-monitor/use-sql-server-objects.md).  
  
Il valore di questi contatori è disponibile anche tramite l'istruzione seguente:  
  
```sql  
SELECT * FROM sys.dm_os_performance_counters   
WHERE object_name = 'SQLServer:Deprecated Features';  
```  

> [!NOTE]  
> Questo elenco è identico all'elenco [!INCLUDE[sssql15-md](../includes/sssql15-md.md)]. Non sono presenti funzionalità nuove o deprecate del motore di database annunciate per [!INCLUDE[sssqlv14-md](../includes/sssqlv14-md.md)].

## <a name="features-deprecated-in-the-next-version-of-sql-server"></a>Funzionalità deprecate nella prossima versione di SQL Server  
Le funzionalità del [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] seguenti verranno deprecate nella prossima versione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Non usare queste funzionalità in un nuovo progetto di sviluppo e modificare non appena possibile le applicazioni in cui sono attualmente implementate. Il valore **Nome funzionalità** viene visualizzato negli eventi di traccia come ObjectName e nei contatori delle prestazioni e in `sys.dm_os_performance_counters` come nome dell'istanza. Il valore **ID funzionalità** viene visualizzato negli eventi di traccia come ID dell'oggetto.  
  
|Category|Funzionalità deprecata|Sostituzione|Nome funzionalità|ID funzionalità|  
|--------------|------------------------|-----------------|------------------|----------------|  
|Backup e ripristino|RESTORE { DATABASE &#124; LOG } WITH [MEDIA]PASSWORD continua a essere deprecata. BACKUP { DATABASE &#124; LOG } WITH PASSWORD e BACKUP { DATABASE &#124; LOG } WITH MEDIAPASSWORD non sono più disponibili.|Nessuna.|BACKUP DATABASE o LOG WITH PASSWORD<br /><br /> BACKUP DATABASE o LOG WITH MEDIAPASSWORD|104<br /><br /> 103|  
|Livelli di compatibilità|Aggiornamento dalla versione 110 ([!INCLUDE[ssKatmai](../includes/sskatmai-md.md)][!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]).|Quando una versione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] non viene più [supportata](http://aka.ms/sqllifecycle), il livello di compatibilità del database associato verrà contrassegnato come deprecato. Microsoft continuerà tuttavia a supportare per quanto possibile le applicazioni certificate in qualsiasi livello di compatibilità del database supportato al fine di facilitare gli aggiornamenti. Per informazioni sui livelli di compatibilità supportati, vedere [Livello di compatibilità ALTER DATABASE &#40;Transact-SQL&#41;](../t-sql/statements/alter-database-transact-sql-compatibility-level.md).|Livello di compatibilità del database: 100|108|  
|Oggetti di database|Possibilità di restituire set di risultati dai trigger|None|Restituzione di risultati da un trigger|12|  
|Crittografia|Crittografia tramite RC4 o RC4_128 deprecata. Rimozione pianificata nella prossima versione. Decrittografia RC4 e RC4_128 non deprecata.|Utilizzare un'altra crittografia, ad esempio AES.|Algoritmo di crittografia deprecata|253|  
|Server remoti|sp_addremotelogin<br /><br /> sp_addserver<br /><br /> sp_dropremotelogin<br /><br /> sp_helpremotelogin<br /><br /> sp_remoteoption|Sostituire i server remoti utilizzando server collegati. sp_addserver può essere usata solo con l'opzione locale.|sp_addremotelogin<br /><br /> sp_addserver<br /><br /> sp_dropremotelogin<br /><br /> sp_helpremotelogin<br /><br /> sp_remoteoption|70<br /><br /> 69<br /><br /> 71<br /><br /> 72<br /><br /> 73|  
|Server remoti|\@\@remserver|Sostituire i server remoti utilizzando server collegati.|None|None|  
|Server remoti|SET REMOTE_PROC_TRANSACTIONS|Sostituire i server remoti utilizzando server collegati.|SET REMOTE_PROC_TRANSACTIONS|110|  
|Opzioni SET|**SET ROWCOUNT** per istruzioni **INSERT**, **UPDATE**e **DELETE**|Parola chiave TOP|SET ROWCOUNT|109|  
|Hint di tabella|Hint di tabella HOLDLOCK senza parentesi|Utilizzare HOLDLOCK con parentesi.|Hint di tabella HOLDLOCK senza parentesi|167|  
  
## <a name="features-deprecated-in-a-future-version-of-sql-server"></a>Funzionalità deprecate in una versione futura di SQL Server  
 Le funzionalità del [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] seguenti sono supportate nella prossima versione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], ma verranno deprecate in una versione successiva. La versione specifica di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] non è stata determinata.  
  
|Category|Funzionalità deprecata|Sostituzione|Nome funzionalità|ID funzionalità|  
|--------------|------------------------|-----------------|------------------|----------------|  
|Livelli di compatibilità|sp_dbcmptlevel|ALTER DATABASE … SET COMPATIBILITY_LEVEL. Per altre informazioni, vedere [Livello di compatibilità ALTER DATABASE &#40;Transact-SQL&#41;](../t-sql/statements/alter-database-transact-sql-compatibility-level.md).|sp_dbcmptlevel|80|  
|Livelli di compatibilità|Livello di compatibilità 110 e 120 del database.|Pianificare l'aggiornamento del database e dell'applicazione per una versione successiva.|Livello di compatibilità 110 del database<br /><br /> Livello di compatibilità 120 del database||  
|XML|Generazione schema XDR inline|La direttiva XMLDATA all'opzione FOR XML è deprecata. Utilizzare la generazione XSD in caso di modalità RAW e AUTO. Non sono disponibili sostituzioni per la direttiva XMLDATA in modalità EXPLICIT.|XMLDATA|181|  
|Backup e ripristino|BACKUP { DATABASE &#124; LOG } TO TAPE<br /><br /> BACKUP { DATABASE &#124; LOG } TO *device_that_is_a_tape*|BACKUP { DATABASE &#124; LOG } TO DISK<br /><br /> BACKUP { DATABASE &#124; LOG } TO *device_that_is_a_disk*|BACKUP DATABASE o LOG TO TAPE|235|  
|Backup e ripristino|sp_addumpdevice '**tape**'|sp_addumpdevice '**disk**'|ADDING TAPE DEVICE|236|  
|Backup e ripristino|sp_helpdevice|sys.backup_devices|sp_helpdevice|100|  
|Regole di confronto|Korean_Wansung_Unicode<br /><br /> Lithuanian_Classic<br /><br /> SQL_AltDiction_CP1253_CS_AS|Nessuna. Queste regole di confronto sono presenti in [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)], ma non è possibile visualizzarle tramite fn_helpcollations.|Korean_Wansung_Unicode<br /><br /> Lithuanian_Classic<br /><br /> SQL_AltDiction_CP1253_CS_AS|191<br /><br /> 192<br /><br /> 194|  
|Regole di confronto|Hindi<br /><br /> Macedonian|Queste regole di confronto sono presenti in [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] e versioni successive, ma non è possibile visualizzarle tramite fn_helpcollations. Utilizzare Macedonian_FYROM_90 e Indic_General_90.|Hindi<br /><br /> Macedonian|190<br /><br /> 193|  
|Regole di confronto|Azeri_Latin_90<br /><br /> Azeri_Cyrilllic_90|Azeri_Latin_100<br /><br /> Azeri_Cyrilllic_100|Azeri_Latin_90<br /><br /> Azeri_Cyrilllic_90|232<br /><br /> 233|  
|Configurazione|SET ANSI_NULLS OFF e opzione di database ANSI_NULLS OFF<br /><br /> SET ANSI_PADDING OFF e opzione di database ANSI_PADDING OFF<br /><br /> SET CONCAT_NULL_YIELDS_NULL OFF e opzione di database CONCAT_NULL_YIELDS_NULL OFF<br /><br /> SET OFFSETS|Nessuna.<br /><br /> ANSI_NULLS, ANSI_PADDING e CONCAT_NULLS_YIELDS_NULL saranno sempre impostate su ON. SET OFFSETS non sarà disponibile.|SET ANSI_NULLS OFF<br /><br /> SET ANSI_PADDING OFF<br /><br /> SET CONCAT_NULL_YIELDS_NULL OFF<br /><br /> SET OFFSETS<br /><br /> ALTER DATABASE SET ANSI_NULLS OFF<br /><br /> ALTER DATABASE SET ANSI_PADDING OFF<br /><br /> ALTER DATABASE SET CONCAT_NULL_YIELDS_NULL OFF|111<br /><br /> 113<br /><br /> 112<br /><br /> 36<br /><br /> 111<br /><br /> 113<br /><br /> 112|  
|Tipi di dati|sp_addtype<br /><br /> sp_droptype|CREATE TYPE<br /><br /> DROP TYPE|sp_addtype<br /><br /> sp_droptype|62<br /><br /> 63|  
|Tipi di dati|Sintassi**timestamp** per il tipo di dati **rowversion** |Sintassi del tipo di dati**rowversion** |timestamp|158|  
|Tipi di dati|Possibilità di inserire valori Null in colonne di tipo **timestamp** .|Utilizzare DEFAULT.|INSERT NULL in colonne TIMESTAMP|179|  
|Tipi di dati|Opzione di tabella 'text in row'|Usare i tipi di dati **varchar(max)**, **nvarchar(max)** e **varbinary(max)**. Per altre informazioni, vedere [sp_tableoption &#40;Transact-SQL&#41;](../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md).|Opzione di tabella text in row|9|  
|Tipi di dati|Tipi di dati:<br /><br /> **text**<br /><br /> **ntext**<br /><br /> **image**|Usare i tipi di dati **varchar(max)**, **nvarchar(max)** e **varbinary(max)** .|Tipi di dati: **text**, **ntext** o **image**|4|  
|Gestione di database|sp_attach_db<br /><br /> sp_attach_single_file_db|Istruzione CREATE DATABASE con l'opzione FOR ATTACH. Per ricompilare più file di log in caso di nuovo percorso di uno o più di questi file, utilizzare l'opzione FOR ATTACH_REBUILD_LOG.|sp_attach_db<br /><br /> sp_attach_single_file_db|81<br /><br /> 82|  
|Oggetti di database|CREATE DEFAULT<br /><br /> DROP DEFAULT<br /><br /> sp_bindefault<br /><br /> sp_unbindefault|Parola chiave DEFAULT in CREATE TABLE e ALTER TABLE|CREATE_DROP_DEFAULT<br /><br /> sp_bindefault<br /><br /> sp_unbindefault|162<br /><br /> 64<br /><br /> 65|  
|Oggetti di database|CREATE RULE<br /><br /> DROP RULE<br /><br /> sp_bindrule<br /><br /> sp_unbindrule|Parola chiave CHECK in CREATE TABLE e ALTER TABLE|CREATE_DROP_RULE<br /><br /> sp_bindrule<br /><br /> sp_unbindrule|161<br /><br /> 66<br /><br /> 67|  
|Oggetti di database|sp_change_users_login|Utilizzare ALTER USER.|sp_change_users_login|231|  
|Oggetti di database|sp_depends|sys.dm_sql_referencing_entities e sys.dm_sql_referenced_entities|sp_depends|19|  
|Oggetti di database|sp_renamedb|MODIFY NAME in ALTER DATABASE|sp_renamedb|79|  
|Oggetti di database|sp_getbindtoken|Utilizzare MARS o transazioni distribuite.|sp_getbindtoken|98|  
|Opzioni di database|sp_bindsession|Utilizzare MARS o transazioni distribuite.|sp_bindsession|97|  
|Opzioni di database|sp_resetstatus|ALTER DATABASE SET { ONLINE &#124; EMERGENCY }|sp_resetstatus|83|  
|Opzioni di database|Opzione TORN_PAGE_DETECTION di ALTER DATABASE|Opzione PAGE_VERIFY TORN_PAGE_DETECTION di ALTER DATABASE|ALTER DATABASE WITH TORN_PAGE_DETECTION|102|  
|DBCC|DBCC DBREINDEX|Opzione REBUILD di ALTER INDEX|DBCC DBREINDEX|11|  
|DBCC|DBCC INDEXDEFRAG|Opzione REORGANIZE di ALTER INDEX|DBCC INDEXDEFRAG|18|  
|DBCC|DBCC SHOWCONTIG|sys.dm_db_index_physical_stats|DBCC SHOWCONTIG|10|  
|DBCC|DBCC PINTABLE<br /><br /> DBCC UNPINTABLE|Non ha alcun effetto.|DBCC [UN]PINTABLE|189|  
|Proprietà estese|Level0type = 'type' e Level0type = 'USER' per l'aggiunta di proprietà estese a oggetti Type di livello 1 o 2.|Utilizzare Level0type = 'USER' soltanto per aggiungere una proprietà estesa direttamente a un utente o un ruolo.<br /><br /> Utilizzare Level0type = 'SCHEMA' per aggiungere una proprietà estesa a tipi di livello 1, ad esempio TABLE o VIEW, oppure a tipi di livello 2, ad esempio COLUMN o TRIGGER. Per altre informazioni, vedere [sp_addextendedproperty &#40;Transact-SQL&#41;](../relational-databases/system-stored-procedures/sp-addextendedproperty-transact-sql.md).|EXTPROP_LEVEL0TYPE<br /><br /> EXTPROP_LEVEL0USER|13<br /><br /> 14|  
|Programmazione di stored procedure estese|srv_alloc<br /><br /> srv_convert<br /><br /> srv_describe<br /><br /> srv_getbindtoken<br /><br /> srv_got_attention<br /><br /> srv_message_handler<br /><br /> srv_paramdata<br /><br /> srv_paraminfo<br /><br /> srv_paramlen<br /><br /> srv_parammaxlen<br /><br /> srv_paramname<br /><br /> srv_paramnumber<br /><br /> srv_paramset<br /><br /> srv_paramsetoutput<br /><br /> srv_paramstatus<br /><br /> srv_paramtype<br /><br /> srv_pfield<br /><br /> srv_pfieldex<br /><br /> srv_rpcdb<br /><br /> srv_rpcname<br /><br /> srv_rpcnumber<br /><br /> srv_rpcoptions<br /><br /> srv_rpcowner<br /><br /> srv_rpcparams<br /><br /> srv_senddone<br /><br /> srv_sendmsg<br /><br /> srv_sendrow<br /><br /> srv_setcoldata<br /><br /> srv_setcollen<br /><br /> srv_setutype<br /><br /> srv_willconvert<br /><br /> srv_wsendmsg|Utilizzare invece la funzionalità di integrazione CLR.|XP_API|20|  
|Programmazione di stored procedure estese|sp_addextendedproc<br /><br /> sp_dropextendedproc<br /><br /> sp_helpextendedproc|Utilizzare invece la funzionalità di integrazione CLR.|sp_addextendedproc<br /><br /> sp_dropextendedproc<br /><br /> sp_helpextendedproc|94<br /><br /> 95<br /><br /> 96|  
|Stored procedure estese|xp_grantlogin<br /><br /> xp_revokelogin<br /><br /> xp_loginConfig|Utilizzare CREATE_LOGIN<br /><br /> Utilizzare l'argomento DROP LOGIN IsIntegratedSecurityOnly di SERVERPROPERTY.|xp_grantlogin<br /><br /> xp_revokelogin<br /><br /> xp_loginConfig|44<br /><br /> 45<br /><br /> 59|  
|Funzioni|fn_get_sql|sys.dm_exec_sql_text|fn_get_sql|151|  
|Algoritmi hash|Algoritmi MD2, MD4, MD5, SHA e SHA1. Non sono disponibili nel livello di compatibilità 130.|Usare SHA2_256 o SHA2_512.|Algoritmo hash deprecato||  
|Disponibilità elevata|mirroring del database|[!INCLUDE[ssHADR](../includes/sshadr-md.md)]<br /><br /> Se l'edizione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] non supporta [!INCLUDE[ssHADR](../includes/sshadr-md.md)], utilizzare il log shipping.|DATABASE_MIRRORING|267|  
|Opzioni per indici|sp_indexoption|ALTER INDEX|sp_indexoption|78|  
|Opzioni per indici|Sintassi di CREATE TABLE, ALTER TABLE o CREATE INDEX senza parentesi per racchiudere le opzioni.|Riscrivere le istruzioni in modo che utilizzino la sintassi corrente.|INDEX_OPTION|33|  
|Opzioni di istanza|Opzione di sp_configure 'allow updates'|Le tabelle di sistema non sono più aggiornabili. L'impostazione non ha alcun effetto.|sp_configure 'allow updates'|173|  
|Opzioni di istanza|Opzioni di sp_configure:<br /><br /> 'locks'<br /><br /> 'open objects'<br /><br /> 'set working set size'|Configurata automaticamente. L'impostazione non ha alcun effetto.|sp_configure 'locks'<br /><br /> sp_configure 'open objects'<br /><br /> sp_configure 'set working set size'|174<br /><br /> 175<br /><br /> 176|  
|Opzioni di istanza|Opzione di sp_configure 'priority boost'|Le tabelle di sistema non sono più aggiornabili. L'impostazione non ha alcun effetto. In alternativa, usare l'opzione start /high … program.exe di Windows.|sp_configure 'priority boost'|199|  
|Opzioni di istanza|Opzione di sp_configure 'remote proc trans'|Le tabelle di sistema non sono più aggiornabili. L'impostazione non ha alcun effetto.|sp_configure 'remote proc trans'|37|  
|Server collegati|Specifica del provider SQLOLEDB per i server collegati.|SQL Server Native Client (SQLNCLI)|SQLOLEDB per server collegati|19|  
|Utilizzo di blocchi|sp_lock|sys.dm_tran_locks|sp_lock|99|  
|Metadati|FILE_ID<br /><br /> INDEXKEY_PROPERTY|FILE_IDEX<br /><br /> sys.index_columns|FILE_ID<br /><br /> INDEXKEY_PROPERTY|15<br /><br /> 17|  
|Servizi Web XML nativi|Istruzione CREATE o ALTER ENDPOINT con l'opzione FOR SOAP.<br /><br /> sys.endpoint_webmethods<br /><br /> sys.soap_endpoints|Usare Windows Communications Foundation (WCF) o ASP.NET.|CREATE/ALTER ENDPOINT<br /><br /> sys.endpoint_webmethods<br /><br /> EXT_soap_endpoints<br /><br /> sys.soap_endpoints|21<br /><br /> 22<br /><br /> 23|  
|Database rimovibili|sp_certify_removable<br /><br /> sp_create_removable|sp_detach_db|sp_certify_removable<br /><br /> sp_create_removable|74<br /><br /> 75|  
|Database rimovibili|sp_dbremove|DROP DATABASE|sp_dbremove|76|  
|Security|Sintassi di ALTER LOGIN WITH SET CREDENTIAL|Nuova sintassi di ALTER LOGIN ADD e DROP CREDENTIAL|ALTER LOGIN WITH SET CREDENTIAL|230|  
|Security|sp_addapprole<br /><br /> sp_dropapprole|CREATE APPLICATION ROLE<br /><br /> DROP APPLICATION ROLE|sp_addapprole<br /><br /> sp_dropapprole|53<br /><br /> 54|  
|Security|sp_addlogin<br /><br /> sp_droplogin|CREATE LOGIN<br /><br /> DROP LOGIN|sp_addlogin<br /><br /> sp_droplogin|39<br /><br /> 40|  
|Security|sp_adduser<br /><br /> sp_dropuser|CREATE USER<br /><br /> DROP USER|sp_adduser<br /><br /> sp_dropuser|49<br /><br /> 50|  
|Security|sp_grantdbaccess<br /><br /> sp_revokedbaccess|CREATE USER<br /><br /> DROP USER|sp_grantdbaccess<br /><br /> sp_revokedbaccess|51<br /><br /> 52|  
|Security|sp_addrole<br /><br /> sp_droprole|CREATE ROLE<br /><br /> DROP ROLE|sp_addrole<br /><br /> sp_droprole|56<br /><br /> 57|  
|Security|sp_approlepassword<br /><br /> sp_password|ALTER APPLICATION ROLE<br /><br /> ALTER LOGIN|sp_approlepassword<br /><br /> sp_password|55<br /><br /> 46|  
|Security|sp_changeobjectowner|ALTER SCHEMA o ALTER AUTHORIZATION|sp_changeobjectowner|58|  
|Security|sp_control_dbmasterkey_password|La chiave master è obbligatoria e la password deve essere corretta.|sp_control_dbmasterkey_password|274|  
|Security|sp_defaultdb<br /><br /> sp_defaultlanguage|ALTER LOGIN|sp_defaultdb<br /><br /> sp_defaultlanguage|47<br /><br /> 48|  
|Security|sp_denylogin<br /><br /> sp_grantlogin<br /><br /> sp_revokelogin|ALTER LOGIN DISABLE<br /><br /> CREATE LOGIN<br /><br /> DROP LOGIN|sp_denylogin<br /><br /> sp_grantlogin<br /><br /> sp_revokelogin|42<br /><br /> 41<br /><br /> 43|  
|Security|USER_ID|DATABASE_PRINCIPAL_ID|USER_ID|16|  
|Security|sp_srvrolepermission<br /><br /> sp_dbfixedrolepermission|Le informazioni restituite da queste stored procedure risultano corrette in [!INCLUDE[ssVersion2000](../includes/ssversion2000-md.md)]. L'output non riflette le modifiche apportate alla gerarchia di autorizzazioni implementata in [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]. Per ulteriori informazioni, vedere [Autorizzazioni dei ruoli predefiniti del server](http://msdn.microsoft.com/library/ms175892\(SQL.100\).aspx).|sp_srvrolepermission<br /><br /> sp_dbfixedrolepermission|61<br /><br /> 60|  
|Security|GRANT ALL<br /><br /> DENY ALL<br /><br /> REVOKE ALL|Autorizzazioni specifiche GRANT, DENY e REVOKE.|Autorizzazione ALL|35|  
|Security|Funzione intrinseca PERMISSIONS|Eseguire una query su sys.fn_my_permissions.|PERMISSIONS|170|  
|Security|SETUSER|EXECUTE AS|SETUSER|165|  
|Security|Algoritmi di crittografia RC4 e DESX|Utilizzare un altro algoritmo, ad esempio AES.|Algoritmo DESX|238|  
|Opzioni SET|SET FMTONLY|[sys.dm_exec_describe_first_result_set &#40;Transact-SQL&#41;](../relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-transact-sql.md), [sys.dm_exec_describe_first_result_set_for_object &#40;Transact-SQL&#41;](../relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-for-object-transact-sql.md), [sp_describe_first_result_set &#40;Transact-SQL&#41;](../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md) e [sp_describe_undeclared_parameters &#40;Transact-SQL&#41;](../relational-databases/system-stored-procedures/sp-describe-undeclared-parameters-transact-sql.md).|SET FMTONLY|250|  
|Opzioni di configurazione del server|opzione c2 audit<br /><br /> default trace enabled - opzione|[Opzione di configurazione del server common criteria compliance enabled](../database-engine/configure-windows/common-criteria-compliance-enabled-server-configuration-option.md)<br /><br /> [Eventi estesi](../relational-databases/extended-events/extended-events.md)|sp_configure 'c2 audit mode'<br /><br /> sp_configure 'default trace enabled'|252<br /><br /> 253|  
|Classi SMO|Classe **Microsoft.SQLServer. Management.Smo.Information**<br /><br /> Classe **Microsoft.SQLServer. Management.Smo.Settings**<br /><br /> Classe **Microsoft.SQLServer.Management. Smo.DatabaseOptions**<br /><br /> Proprietà **Microsoft.SqlServer.Management.Smo. DatabaseDdlTrigger.NotForReplication**|Classe **Microsoft.SqlServer.  Management.Smo.Server**<br /><br /> Classe **Microsoft.SqlServer.  Management.Smo.Server**<br /><br /> Classe **Microsoft.SqlServer. Management.Smo.Database**<br /><br /> None|None|None|  
|SQL Server Agent|Notifica**net send** <br /><br /> Notifica tramite cercapersone|Notifica tramite posta elettronica<br /><br /> Notifica tramite posta elettronica |None|None|  
|[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]|Integrazione di Esplora soluzioni in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]||None|None|  
|Stored procedure di sistema|sp_db_increased_partitions|Nessuna. Il supporto per l'estensione del numero di partizioni è disponibile per impostazione predefinita in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].|sp_db_increased_partitions|253|  
|Tabelle di sistema|sysaltfiles<br /><br /> syscacheobjects<br /><br /> syscolumns<br /><br /> syscomments<br /><br /> sysconfigures<br /><br /> sysconstraints<br /><br /> syscurconfigs<br /><br /> sysdatabases<br /><br /> sysdepends<br /><br /> sysdevices<br /><br /> sysfilegroups<br /><br /> sysfiles<br /><br /> sysforeignkeys<br /><br /> sysfulltextcatalogs<br /><br /> sysindexes<br /><br /> sysindexkeys<br /><br /> syslockinfo<br /><br /> syslogins<br /><br /> sysmembers<br /><br /> sysmessages<br /><br /> sysobjects<br /><br /> sysoledbusers<br /><br /> sysopentapes<br /><br /> sysperfinfo<br /><br /> syspermissions<br /><br /> sysprocesses<br /><br /> sysprotects<br /><br /> sysreferences<br /><br /> sysremotelogins<br /><br /> sysservers<br /><br /> systypes<br /><br /> sysusers|Viste di compatibilità. Per altre informazioni, vedere [Viste di compatibilità &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md).<br /><br /> **Importante:** nelle viste di compatibilità non vengono esposti metadati per le funzionalità introdotte in [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]. È consigliabile aggiornare le applicazioni per l'utilizzo delle viste del catalogo. Per altre informazioni, vedere [Viste del catalogo &#40;Transact-SQL&#41;](../relational-databases/system-catalog-views/catalog-views-transact-sql.md).|sysaltfiles<br /><br /> syscacheobjects<br /><br /> syscolumns<br /><br /> syscomments<br /><br /> sysconfigures<br /><br /> sysconstraints<br /><br /> syscurconfigs<br /><br /> sysdatabases<br /><br /> sysdepends<br /><br /> sysdevices<br /><br /> sysfilegroups<br /><br /> sysfiles<br /><br /> sysforeignkeys<br /><br /> sysfulltextcatalogs<br /><br /> sysindexes<br /><br /> sysindexkeys<br /><br /> syslockinfo<br /><br /> syslogins<br /><br /> sysmembers<br /><br /> sysmessages<br /><br /> sysobjects<br /><br /> sysoledbusers<br /><br /> sysopentapes<br /><br /> sysperfinfo<br /><br /> syspermissions<br /><br /> sysprocesses<br /><br /> sysprotects<br /><br /> sysreferences<br /><br /> sysremotelogins<br /><br /> sysservers<br /><br /> systypes<br /><br /> sysusers|141<br /><br /> None<br /><br /> 133<br /><br /> 126<br /><br /> 146<br /><br /> 131<br /><br /> 147<br /><br /> 142<br /><br /> 123<br /><br /> 144<br /><br /> 128<br /><br /> 127<br /><br /> 130<br /><br /> 122<br /><br /> 132<br /><br /> 134<br /><br /> 143<br /><br /> 140<br /><br /> 119<br /><br /> 137<br /><br /> 125<br /><br /> 139<br /><br /> 145<br /><br /> 157<br /><br /> 121<br /><br /> 153<br /><br /> 120<br /><br /> 129<br /><br /> 138<br /><br /> 136<br /><br /> 135<br /><br /> 124|  
|Tabelle di sistema|sys.numbered_procedures<br /><br /> sys.numbered_procedure_parameters|None|numbered_procedures<br /><br /> numbered_procedure_parameters|148<br /><br /> 149|  
|Funzioni di sistema|fn_virtualservernodes<br /><br /> fn_servershareddrives|sys.dm_os_cluster_nodes<br /><br /> sys.dm_io_cluster_shared_drives|fn_virtualservernodes<br /><br /> fn_servershareddrives|155<br /><br /> 156|  
|Viste di sistema|sys.sql_dependencies|sys.sql_expression_dependencies|sys.sql_dependencies|198|  
|Compressione di tabelle|Utilizzo del formato di archiviazione vardecimal.|Il formato di archiviazione vardecimal è deprecato. Con la compressione dei dati di[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] vengono compressi sia i valori decimali sia altri tipi di dati. È consigliabile utilizzare la compressione dei dati anziché il formato di archiviazione vardecimal.|Formato di archiviazione vardecimal|200|  
|Compressione di tabelle|Utilizzo della procedura sp_db_vardecimal_storage_format.|Il formato di archiviazione vardecimal è deprecato. Con la compressione dei dati di[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] vengono compressi sia i valori decimali sia altri tipi di dati. È consigliabile utilizzare la compressione dei dati anziché il formato di archiviazione vardecimal.|sp_db_vardecimal_storage_format|201|  
|Compressione di tabelle|Utilizzo della procedura sp_estimated_rowsize_reduction_for_vardecimal.|Utilizzare la compressione dei dati e la procedura sp_estimate_data_compression_savings.|sp_estimated_rowsize_reduction_for_vardecimal|202|  
|Hint di tabella|Specifica di NOLOCK o READUNCOMMITTED nella clausola FROM di un'istruzione UPDATE o DELETE.|Rimuovere l'hint di tabella NOLOCK o READUNCOMMITTED dalla clausola FROM.|NOLOCK o READUNCOMMITTED in UPDATE o DELETE|1|  
|Hint di tabella|Specifica di hint di tabella senza utilizzare la parola chiave WITH.|Utilizzare WITH.|Hint di tabella senza WITH|8|  
|Hint di tabella|INSERT_HINTS||INSERT_HINTS|34|  
|Textpointer|WRITETEXT<br /><br /> UPDATETEXT<br /><br /> READTEXT|None|UPDATETEXT o WRITETEXT<br /><br /> READTEXT|115<br /><br /> 114|  
|Textpointer|TEXTPTR()<br /><br /> TEXTVALID()|None|TEXTPTR<br /><br /> TEXTVALID|5<br /><br /> 6|  
|[!INCLUDE[tsql](../includes/tsql-md.md)]|Sequenza di chiamata di funzioni ::|Sostituita da SELECT *column_list* FROM sys.\<*function_name*>().<br /><br /> Sostituire, ad esempio, `SELECT * FROM ::fn_virtualfilestats(2,1)`con `SELECT * FROM sys.fn_virtualfilestats(2,1)`.|Sintassi per la chiamata di funzioni '::'|166|  
|[!INCLUDE[tsql](../includes/tsql-md.md)]|Riferimenti a colonne in 3 e 4 parti.|Il funzionamento conforme allo standard prevede nomi in 2 parti.|Nome di colonna in più di due parti|3|  
|[!INCLUDE[tsql](../includes/tsql-md.md)]|Stringa racchiusa tra virgolette utilizzata come alias di colonna per un'espressione in un elenco SELECT:<br /><br /> '*string_alias*' = *expression*|*expression* [AS] *column_alias*<br /><br /> *expression* [AS] [*column_alias*]<br /><br /> *expression* [AS] "*column_alias*"<br /><br /> *expression* [AS] '*column_alias*'<br /><br /> *column_alias* = *expression*|Valori letterali stringa come alias di colonna|184|  
|[!INCLUDE[tsql](../includes/tsql-md.md)]|Procedure numerate|Nessuna. Non usare.|ProcNums|160|  
|[!INCLUDE[tsql](../includes/tsql-md.md)]|Sintassi*table_name.index_name* nell'istruzione DROP INDEX|Sintassi*index_name* ON *table_name* nell'istruzione DROP INDEX.|DROP INDEX con nome in due parti|163|  
|[!INCLUDE[tsql](../includes/tsql-md.md)]|Istruzioni [!INCLUDE[tsql](../includes/tsql-md.md)] che non terminano con un punto e virgola.|Terminare le istruzioni [!INCLUDE[tsql](../includes/tsql-md.md)] con un punto e virgola (;).|None|None|  
|[!INCLUDE[tsql](../includes/tsql-md.md)]|GROUP BY ALL|Utilizzare una soluzione personalizzata caso per caso con UNION o una tabella derivata.|GROUP BY ALL|169|  
|[!INCLUDE[tsql](../includes/tsql-md.md)]|ROWGUIDCOL come nome di colonna nelle istruzioni DML.|Utilizzare $rowguid.|ROWGUIDCOL|182|  
|[!INCLUDE[tsql](../includes/tsql-md.md)]|IDENTITYCOL come nome di colonna nelle istruzioni DML.|Utilizzare $identity.|IDENTITYCOL|183|  
|[!INCLUDE[tsql](../includes/tsql-md.md)]|Utilizzo di # e ## come nomi di tabelle e di stored procedure temporanee.|Usare almeno un carattere aggiuntivo.|'#' e '##' come nomi di tabelle e stored procedure temporanee|185|  
|[!INCLUDE[tsql](../includes/tsql-md.md)]|Uso di \@, \@\@ o \@\@ come identificatori [!INCLUDE[tsql](../includes/tsql-md.md)].|Non usare come identificatori \@ o \@\@ o nomi che iniziano con \@\@.|"\@" e nomi che iniziano con "\@\@" come identificatori [!INCLUDE[tsql](../includes/tsql-md.md)]|186.|  
|[!INCLUDE[tsql](../includes/tsql-md.md)]|Utilizzo della parola chiave DEFAULT come valore predefinito.|Non utilizzare la parola DEFAULT come valore predefinito.|Parola chiave DEFAULT come valore predefinito|187|  
|[!INCLUDE[tsql](../includes/tsql-md.md)]|Utilizzo di uno spazio come separatore tra gli hint di tabella.|Per separare gli hint di tabella, utilizzare la virgola.|Più hint di tabella senza virgola|168|  
|[!INCLUDE[tsql](../includes/tsql-md.md)]|L'elenco di selezione di una vista indicizzata aggregata deve contenere COUNT_BIG (\*) in modalità compatibilità 90|Usare COUNT_BIG (\*).|Elenco di selezione di una vista indicizzata senza COUNT_BIG(\*)|2|  
|[!INCLUDE[tsql](../includes/tsql-md.md)]|Applicazione indiretta di hint di tabella a una chiamata di una funzione con valori di tabella composta da più istruzioni tramite una vista.|Nessuna.|Hint di funzione con valori di tabella indiretti|7|  
|[!INCLUDE[tsql](../includes/tsql-md.md)]|Sintassi di ALTER DATABASE:<br /><br /> MODIFY FILEGROUP READONLY<br /><br /> MODIFY FILEGROUP READWRITE|MODIFY FILEGROUP READ_ONLY<br /><br /> MODIFY FILEGROUP READ_WRITE|MODIFY FILEGROUP READONLY<br /><br /> MODIFY FILEGROUP READWRITE|195<br /><br /> 196|  
|Altro|DB-Library<br /><br /> Embedded SQL for C|Nonostante supporti connessioni da applicazioni esistenti che utilizzano le API DB-Library ed Embedded SQL, il [!INCLUDE[ssDE](../includes/ssde-md.md)] non include la documentazione o i file necessari per svolgere attività di programmazione per applicazioni che utilizzano tali API. In una versione futura del [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] verrà eliminato il supporto per le connessioni da applicazioni DB-Library o Embedded SQL. Non utilizzare pertanto DB-Library o Embedded SQL per sviluppare nuove applicazioni. Quando si modificano applicazioni esistenti, rimuovere tutte le dipendenze da DB-Library o Embedded SQL. Invece di queste API, usare lo spazio dei nomi SQLClient o un'API, ad esempio ODBC. In[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] non è inclusa la DLL DB-Library necessaria per eseguire queste applicazioni. Per eseguire applicazioni DB-Library o Embedded SQL, è necessario disporre della DLL DB-Library di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] versione 6.5, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 7.0 o [!INCLUDE[ssVersion2000](../includes/ssversion2000-md.md)].|None|None|  
|Strumenti|SQL Server Profiler per l'acquisizione della traccia|Utilizzare il profile degli eventi estesi incorporato in SQL Server Management Studio.|SQL Server Profiler|None|  
|Strumenti|SQL Server Profiler per la riproduzione della traccia|[SQL Server Distributed Replay](../tools/distributed-replay/sql-server-distributed-replay.md)|SQL Server Profiler|None|  
|Trace Management Objects|Spazio dei nomi Microsoft.SqlServer.Management.Trace (contiene le API per gli oggetti Trace and Replay di SQL Server)|Configurazione della traccia: <xref:Microsoft.SqlServer.Management.XEvent><br /><br /> Lettura della traccia: <xref:Microsoft.SqlServer.XEvent.Linq><br /><br /> Riproduzione della traccia: nessuna|||  
|Stored procedure, funzioni e viste del catalogo della traccia SQL|sp_trace_create<br /><br /> sp_trace_setevent<br /><br /> sp_trace_setfilter<br /><br /> sp_trace_setstatus<br /><br /> fn_trace_geteventinfo<br /><br /> fn_trace_getfilterinfo<br /><br /> fn_trace_getinfo<br /><br /> fn_trace_gettable<br /><br /> sys.traces<br /><br /> sys.trace_events<br /><br /> sys.trace_event_bindings<br /><br /> sys.trace_categories<br /><br /> sys.trace_columns<br /><br /> sys.trace_subclass_values|[Eventi estesi](../relational-databases/extended-events/extended-events.md)|sp_trace_create<br /><br /> sp_trace_setevent<br /><br /> sp_trace_setfilter<br /><br /> sp_trace_setstatus<br /><br /> fn_trace_geteventinfo<br /><br /> fn_trace_getfilterinfo<br /><br /> fn_trace_getinfo<br /><br /> fn_trace_gettable<br /><br /> sys.traces<br /><br /> sys.trace_events<br /><br /> sys.trace_event_bindings<br /><br /> sys.trace_categories<br /><br /> sys.trace_columns<br /><br /> sys.trace_subclass_values|258<br /><br /> 260<br /><br /> 261<br /><br /> 259<br /><br /> 256<br /><br /> 257|  
  
> [!NOTE]  
> Il parametro **OUTPUT** del cookie per **sp_setapprole** è attualmente documentato come **varbinary(8000)** che rappresenta la lunghezza massima corretta. Tuttavia, l'implementazione corrente restituisce **varbinary(50)**. Se gli sviluppatori hanno allocato **varbinary(50)** , potrebbe essere necessario apportare modifiche all'applicazione qualora le dimensioni restituite dal cookie aumentino in una versione successiva. Sebbene non si tratti di un problema relativo a elementi deprecati, questo aspetto viene riportato in quanto le modifiche all'applicazione sono simili. Per altre informazioni, vedere [sp_setapprole &#40;Transact-SQL&#41;](../relational-databases/system-stored-procedures/sp-setapprole-transact-sql.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Funzionalità del motore di database non più usate in SQL Server 2016](../database-engine/discontinued-database-engine-functionality-in-sql-server-2016.md)  
  
  


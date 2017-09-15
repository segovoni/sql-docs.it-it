---
title: ALTER TRIGGER (Transact-SQL) | Documenti Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 05/08/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER TRIGGER
- ALTER_TRIGGER_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DDL triggers, modifying
- triggers [SQL Server], modifying
- modifying triggers
- ALTER TRIGGER statement
- DML triggers, modifying
ms.assetid: 2a99c7c1-ac2f-4637-aa7c-3d1bf514e500
caps.latest.revision: 74
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1ae43399e1154e326ccee3d8760d59c71b73de5b
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="alter-trigger-transact-sql"></a>ALTER TRIGGER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Modifica la definizione di un trigger DML, DDL o LOGON precedentemente creato dall'istruzione CREATE TRIGGER. I trigger vengono creati tramite l'istruzione CREATE TRIGGER. Possono essere creati direttamente dalle [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzioni o uno dei metodi di assembly creati nel [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] common language runtime (CLR) e caricati in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per ulteriori informazioni sui parametri utilizzati nell'istruzione ALTER TRIGGER, vedere [CREATE TRIGGER & #40; Transact-SQL & #41; ](../../t-sql/statements/create-trigger-transact-sql.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- SQL Server Syntax  
-- Trigger on an INSERT, UPDATE, or DELETE statement to a table or view (DML Trigger)  

ALTER TRIGGER schema_name.trigger_name   
ON  ( table | view )   
[ WITH <dml_trigger_option> [ ,...n ] ]  
 ( FOR | AFTER | INSTEAD OF )   
{ [ DELETE ] [ , ] [ INSERT ] [ , ] [ UPDATE ] }   
[ NOT FOR REPLICATION ]   
AS { sql_statement [ ; ] [ ...n ] | EXTERNAL NAME <method specifier>   
[ ; ] }   
  
<dml_trigger_option> ::=  
    [ ENCRYPTION ]  
    [ <EXECUTE AS Clause> ]  
  
<method_specifier> ::=  
    assembly_name.class_name.method_name  
  
-- Trigger on an INSERT, UPDATE, or DELETE statement to a table 
-- (DML Trigger on memory-optimized tables)  

ALTER TRIGGER schema_name.trigger_name   
ON  ( table  )   
[ WITH <dml_trigger_option> [ ,...n ] ]  
 ( FOR | AFTER )   
{ [ DELETE ] [ , ] [ INSERT ] [ , ] [ UPDATE ] }   
AS { sql_statement [ ; ] [ ...n ] }   
  
<dml_trigger_option> ::=  
    [ NATIVE_COMPILATION ]  
    [ SCHEMABINDING ]  
    [ <EXECUTE AS Clause> ]  
  
-- Trigger on a CREATE, ALTER, DROP, GRANT, DENY, REVOKE, 
-- or UPDATE statement (DDL Trigger)  
  
ALTER TRIGGER trigger_name   
ON { DATABASE | ALL SERVER }   
[ WITH <ddl_trigger_option> [ ,...n ] ]  
{ FOR | AFTER } { event_type [ ,...n ] | event_group }   
AS { sql_statement [ ; ] | EXTERNAL NAME <method specifier>   
[ ; ] }  
}   
  
<ddl_trigger_option> ::=  
    [ ENCRYPTION ]  
    [ <EXECUTE AS Clause> ]  
  
<method_specifier> ::=  
    assembly_name.class_name.method_name  
  
-- Trigger on a LOGON event (Logon Trigger)  

ALTER TRIGGER trigger_name   
ON ALL SERVER   
[ WITH <logon_trigger_option> [ ,...n ] ]  
{ FOR| AFTER } LOGON   
AS { sql_statement  [ ; ] [ ,...n ] | EXTERNAL NAME < method specifier >  
  [ ; ] }  
  
<logon_trigger_option> ::=  
    [ ENCRYPTION ]  
    [ EXECUTE AS Clause ]  
  
<method_specifier> ::=  
    assembly_name.class_name.method_name  
```  
  
```  
-- Windows Azure SQL Database Syntax   
-- Trigger on an INSERT, UPDATE, or DELETE statement to a table or view (DML Trigger)   
  
ALTER TRIGGER schema_name. trigger_name   
ON (table | view )   
 [ WITH <dml_trigger_option> [ ,...n ] ]   
 ( FOR | AFTER | INSTEAD OF )   
{ [ DELETE ] [ , ] [ INSERT ] [ , ] [ UPDATE ] }   
AS { sql_statement [ ; ] [...n ] }   
  
<dml_trigger_option> ::=   
    [ <EXECUTE AS Clause> ]   
  
-- Trigger on a CREATE, ALTER, DROP, GRANT, DENY, REVOKE, or UPDATE statement (DDL Trigger)   
  
ALTER TRIGGER trigger_name   
ON { DATABASE }   
 [ WITH <ddl_trigger_option> [ ,...n ] ]   
{ FOR | AFTER } { event_type [ ,...n ] | event_group }   
AS { sql_statement   
[ ; ] }  
}   
  
<ddl_trigger_option> ::=   
    [ <EXECUTE AS Clause> ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *schema_name*  
 Nome dello schema a cui appartiene un trigger DML. L'ambito dei trigger DML è definito nello schema della tabella o della vista in cui sono i trigger stessi creati. *schema**Name* è facoltativo solo se il trigger DML e la tabella o visualizzazione corrispondente appartenenza allo schema predefinito. *schema_name* non può essere specificato per i trigger DDL o logon.  
  
 *trigger_name*  
 Trigger esistente da modificare.  
  
 *tabella* | *visualizzazione*  
 Tabella o vista nella quale viene eseguito il trigger DML. Il nome completo della tabella o vista è facoltativo.  
  
 DATABASE  
 Applica l'ambito di un trigger DDL al database corrente. Se specificato, il trigger viene attivato ogni volta che *event_type* o *event_group* si verifica nel database corrente.  
  
 ALL SERVER  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Applica l'ambito di un trigger DDL o LOGON al server corrente. Se specificato, il trigger viene attivato ogni volta che *event_type* o *event_group* si verifica in un punto qualsiasi nel server corrente.  
  
 WITH ENCRYPTION  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Crittografa le voci sys.syscommentssys.sql_modules che contengono il testo dell'istruzione ALTER TRIGGER. Tramite il parametro WITH ENCRYPTION è possibile evitare la pubblicazione del trigger come parte della replica di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Non è possibile specificare WITH ENCRYPTION per i trigger CLR.  
  
> [!NOTE]  
>  Se si crea un trigger tramite WITH ENCRYPTION, occorre specificarlo nuovamente nell'istruzione ALTER TRIGGER affinché questa opzione rimanga abilitata.  
  
 EXECUTE AS  
 Specifica il contesto di sicurezza nel quale viene eseguito il trigger. Consente di controllare l'account utente utilizzato dall'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per convalidare le autorizzazioni su ogni oggetto di database a cui fa riferimento il trigger.  
  
 Per altre informazioni, vedere [Clausola EXECUTE AS &#40;Transact-SQL&#41;](../../t-sql/statements/execute-as-clause-transact-sql.md).  
  
 NATIVE_COMPILATION  
 Indica che il trigger è compilato in modo nativo.  
  
 Questa opzione è obbligatoria per i trigger sulle tabelle con ottimizzazione per la memoria.  
  
 SCHEMABINDING  
 Assicura che le tabelle a cui fa riferimento un trigger non possono essere eliminate o modificate.  
  
 Questa opzione è necessaria per i trigger sulle tabelle con ottimizzazione per la memoria e non è supportata per i trigger sulle tabelle tradizionali.  
  
 AFTER  
 Specifica che il trigger viene attivato solo dopo la corretta esecuzione dell'istruzione di trigger SQL. È inoltre necessario che tutte le operazioni referenziali di propagazione e le verifiche dei vincoli siano state completate correttamente prima che il trigger venga attivato.  
  
 Se viene specificata solo la parola chiave FOR, AFTER è il valore predefinito.  
  
 È possibile definire i trigger AFTER DML solo nelle tabelle.  
  
 INSTEAD OF  
 Specifica che il trigger DML viene eseguito al posto dell'istruzione di trigger SQL. Il trigger risulta pertanto prioritario rispetto alle azioni delle istruzioni di trigger. Non è possibile specificare INSTEAD OF per i trigger DDL o LOGON.  
  
 In una tabella o vista è possibile definire al massimo un trigger INSTEAD OF per ogni istruzione INSERT, UPDATE o DELETE. È tuttavia possibile definire viste che fanno riferimento ad altre viste. Ogni vista include un trigger INSTEAD OF.  
  
 I trigger INSTEAD OF non sono supportati in viste create con la clausola WITH CHECK OPTION. Se un trigger INSTEAD OF viene aggiunto a una vista per la quale è stato specificato WITH CHECK OPTION, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] genera un errore. Per poter definire il trigger INSTEAD OF, è necessario rimuovere l'opzione tramite l'istruzione ALTER VIEW.  
  
 { [ DELETE ] [ , ] [ INSERT ] [ , ] [ UPDATE ] } | { [INSERT ] [ , ] [ UPDATE ] }  
 Specifica quali istruzioni di modifica dei dati eseguite nella tabella o vista attivano il trigger DML. È necessario specificare almeno un'opzione. Nella definizione di trigger è consentita qualsiasi combinazione delle opzioni nell'ordine desiderato. Se vengono specificate più opzioni, è necessario separarle con una virgola.  
  
 Per i trigger INSTEAD OF, l'opzione DELETE non è consentita in tabelle contenenti una relazione referenziale che specifica un'operazione di propagazione ON DELETE. In modo analogo, l'opzione UPDATE non è consentita in tabelle contenenti una relazione referenziale che specifica un'operazione di propagazione ON UPDATE. Per altre informazioni, vedere [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md).  
  
 *event_type*  
 Nome di un evento del linguaggio [!INCLUDE[tsql](../../includes/tsql-md.md)] che, dopo l'esecuzione, attiva un trigger DDL. Sono elencati gli eventi validi per i trigger DDL in [eventi DDL](../../relational-databases/triggers/ddl-events.md).  
  
 *event_group*  
 Nome di un raggruppamento predefinito di eventi del linguaggio [!INCLUDE[tsql](../../includes/tsql-md.md)]. Il trigger DDL viene attivato dopo l'esecuzione di qualsiasi [!INCLUDE[tsql](../../includes/tsql-md.md)] evento del linguaggio a cui appartiene *event_group*. Gruppi di eventi valido per i trigger DDL sono elencati in [gruppi di eventi DDL](../../relational-databases/triggers/ddl-event-groups.md). Al termine dell'esecuzione, ALTER TRIGGER *event_group* funge anche da macro aggiungendo i tipi di evento include alla vista del catalogo sys. trigger_events.  
  
 NOT FOR REPLICATION  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Indica che il trigger non deve essere eseguito quando un agente di replica modifica la tabella coinvolta nel trigger.  
  
 *sql_statement*  
 Condizioni e azioni del trigger.  
  
 Per i trigger sulle tabelle con ottimizzazione per la memoria, l'unico *sql_statement* consentite al livello superiore è un blocco atomico. T-SQL consentite all'interno del blocco atomico è limitato da T-SQL consentite all'interno delle procedure native.  
  
 NOME esterno \<method_specifier >  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Specifica il metodo di un'assembly da associare al trigger. Il metodo non deve accettare nessun argomento e restituire void. *CLASS_NAME* deve essere un valore valido [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] identificatore e deve esistere come classe nell'assembly con visibilità dell'assembly. La classe non può essere nidificata.  
  
## <a name="remarks"></a>Osservazioni  
 Per ulteriori informazioni sull'istruzione ALTER TRIGGER, vedere la sezione Osservazioni in [CREATE TRIGGER & #40; Transact-SQL & #41; ](../../t-sql/statements/create-trigger-transact-sql.md).  
  
> [!NOTE]  
>  Le opzioni EXTERNAL_NAME e ON_ALL_SERVER non sono disponibili in un database indipendente.  
  
## <a name="dml-triggers"></a>Trigger DML  
 L'istruzione ALTER TRIGGER supporta viste ad aggiornamento manuale tramite trigger INSTEAD OF in tabelle e viste. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] applica ALTER TRIGGER allo stesso modo per tutti i tipi di trigger (AFTER, INSTEAD-OF).  
  
 È possibile specificare il primo e l'ultimo trigger AFTER che si desidera eseguire in una tabella utilizzando sp_settriggerorder. È possibile specificare solo un primo e un ultimo trigger AFTER in una tabella. Se nella stessa tabella sono inclusi altri trigger AFTER, vengono eseguiti in modo casuale.  
  
 Se il primo o l'ultimo trigger viene modificato tramite un'istruzione ALTER TRIGGER, l'attributo first (primo) o last (ultimo) impostato per il trigger modificato viene rimosso ed è necessario reimpostare il valore di ordinamento tramite sp_settriggerorder.  
  
 Un trigger AFTER viene eseguito solo dopo il completamento dell'esecuzione dell'istruzione SQL di attivazione, comprese tutte le operazioni referenziali di propagazione e le verifiche di vincolo associate all'oggetto aggiornato o eliminato. L'operazione di trigger AFTER controlla gli effetti dell'istruzione di trigger e tutte le operazioni UPDATE e DELETE referenziali di propagazione attivate con l'istruzione di trigger.  
  
 Quando un'operazione DELETE in una tabella figlio o di riferimento è il risultato di un'operazione CASCADE su un'operazione DELETE eseguita dalla tabella padre e viene definito un trigger INSTEAD OF per DELETE nella tabella figlio, il trigger viene ignorato mentre l'operazione DELETE viene eseguita.  
  
## <a name="ddl-triggers"></a>Trigger DDL  
 Diversamente dai trigger DML, i trigger DDL non sono definiti a livello di ambito di schema. Pertanto, non è possibile utilizzare OBJECT_ID, OBJECT_NAME, OBJECTPROPERTY e OBJECTPROPERTY(EX) durante l'esecuzione di query sui metadati relativi ai trigger DDL. Utilizzare in alternativa le viste del catalogo. Per ulteriori informazioni, vedere [ottenere informazioni sui trigger DDL](../../relational-databases/triggers/get-information-about-ddl-triggers.md).  
  
## <a name="logon-triggers"></a>Trigger LOGON  
 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] non supporta i trigger sugli eventi di accesso.  
  
## <a name="permissions"></a>Permissions  
 Per modificare un trigger DML è necessaria l'autorizzazione ALTER sulla tabella o vista in cui è definito il trigger.  
  
 Per modificare un trigger DDL definito con ambito server (ON ALL SERVER) o un trigger LOGON è necessaria l'autorizzazione CONTROL SERVER nel server. Per modificare un trigger DDL definito con ambito database (ON DATABASE) è necessaria l'autorizzazione ALTER ANY DATABASE DDL TRIGGER nel database corrente.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene creato un trigger DML nel database AdventureWorks 2012, che visualizza un messaggio definito dall'utente al client quando un utente tenta di aggiungere o modificare dati nel `SalesPersonQuotaHistory` tabella. Il trigger viene quindi modificato tramite `ALTER TRIGGER` per applicare il trigger soltanto sulle attività `INSERT`. Questo trigger risulta molto utile, in quanto ricorda all'utente che aggiorna o inserisce righe nella tabella di inviare una notifica al reparto `Compensation` .  
  
```  
CREATE TRIGGER Sales.bonus_reminder  
ON Sales.SalesPersonQuotaHistory  
WITH ENCRYPTION  
AFTER INSERT, UPDATE   
AS RAISERROR ('Notify Compensation', 16, 10);  
GO  

-- Now, change the trigger.  
ALTER TRIGGER Sales.bonus_reminder  
ON Sales.SalesPersonQuotaHistory  
AFTER INSERT  
AS RAISERROR ('Notify Compensation', 16, 10);  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [DROP TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/drop-trigger-transact-sql.md)   
 [ENABLE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/enable-trigger-transact-sql.md)   
 [DISABLE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/disable-trigger-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sp_helptrigger &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helptrigger-transact-sql.md)   
 [Creazione di una stored procedure](../../relational-databases/stored-procedures/create-a-stored-procedure.md)   
 [sp_addmessage & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addmessage-transact-sql.md)   
 [Transazioni](../../relational-databases/native-client-ole-db-transactions/transactions.md)   
 [Ottieni informazioni sui trigger DML](../../relational-databases/triggers/get-information-about-dml-triggers.md)   
 [Ottenere informazioni sui trigger DDL](../../relational-databases/triggers/get-information-about-ddl-triggers.md)   
 [sys.triggers &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-triggers-transact-sql.md)   
 [sys.trigger_events &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trigger-events-transact-sql.md)   
 [sys.sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [sys.assembly_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-assembly-modules-transact-sql.md)   
 [sys.server_triggers &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-triggers-transact-sql.md)   
 [sys.server_trigger_events &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql.md)   
 [sys.server_sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql.md)   
 [sys.server_assembly_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-assembly-modules-transact-sql.md)   
 [Apportare modifiche allo schema nei database di pubblicazione](../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)  
  
  

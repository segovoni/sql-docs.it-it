---
title: Classe di evento Audit Schema Object Access | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Audit Schema Object Access event class
ms.assetid: 1c099fa2-c857-4128-aca0-ed8cc3078a43
caps.latest.revision: 29
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 982c9736da979ee303c0ca4d564bdfb8ce0e22a2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37240771"
---
# <a name="audit-schema-object-access-event-class"></a>Audit Schema Object Access - classe di evento
  La classe di evento **Audit Schema Object Access** viene generata quando viene usata un'autorizzazione per gli oggetti, ad esempio SELECT.  
  
## <a name="audit-schema-object-access-event-class-data-columns"></a>Colonne di dati della classe di evento Audit Schema Object Access  
  
|Nome colonna di dati|Tipo di dati|Description|ID colonna|Filtrabile|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**ApplicationName**|**nvarchar**|Nome dell'applicazione client in cui è stata creata la connessione a un'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Questa colonna viene popolata con i valori passati dall'applicazione e non con il nome visualizzato del programma.|10|Sì|  
|**ClientProcessID**|**int**|ID assegnato dal computer host al processo in cui è in esecuzione l'applicazione client. Questa colonna di dati viene popolata se tramite il client viene indicato l'ID del processo client.|9|Sì|  
|**ColumnPermissions**|**int**|Indica se è stata impostata un'autorizzazione a livello di colonna. Analizzare il testo dell'istruzione per determinare quali autorizzazioni sono state applicate. 1 = Sì, 0 = No.|44|Sì|  
|**DatabaseID**|**int**|ID del database specificato nell'istruzione di *database* USE oppure il database predefinito se per un'istanza specifica l'istruzione di *database* USE non è stata eseguita. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] visualizza il nome del database se la colonna di dati **ServerName** è acquisita nella traccia e il server è disponibile. Determinare il valore per un database utilizzando la funzione DB_ID.|3|Sì|  
|**DatabaseName**|**nvarchar**|Nome del database nel quale viene eseguita l'istruzione dell'utente.|35|Sì|  
|**DBUserName**|**nvarchar**|Nome dell'utente che ha eseguito l'istruzione nel database.|40|Sì|  
|**EventClass**|**int**|Tipo di evento = 114.|27|no|  
|**EventSequence**|**int**|Sequenza di un determinato evento all'interno della richiesta.|51|no|  
|**HostName**|**nvarchar**|Nome del computer in cui viene eseguito il client. Questa colonna di dati viene popolata se il client fornisce il nome host. Per determinare il nome host, usare la funzione HOST_NAME.|8|Sì|  
|**IsSystem**|**int**|Indica se l'evento è stato generato per un processo di sistema o un processo utente. 1 = sistema, 0 = utente.|60|Sì|  
|**LoginName**|**nvarchar**|Nome dell'account di accesso dell'utente (account di sicurezza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o credenziali di accesso di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows nel formato DOMINIO\nomeutente).|11|Sì|  
|**LoginSid**|**image**|ID di sicurezza (SID) dell'utente connesso. Queste informazioni sono disponibili nella vista del catalogo **sys.server_principals** . Il SID è univoco per ogni account di accesso nel server.|41|Sì|  
|**NTDomainName**|**nvarchar**|Dominio Windows di appartenenza dell'utente.|7|Sì|  
|**NTUserName**|**nvarchar**|Nome utente di Windows.|6|Sì|  
|**ObjectName**|**nvarchar**|Nome dell'oggetto di cui vengono controllate le autorizzazioni.|34|Sì|  
|**ObjectType**|**int**|Valore che rappresenta il tipo di oggetto coinvolto nell'evento. Questo valore corrisponde alla colonna type nella vista del catalogo **sys.objects** . Per i valori, vedere [Colonna ObjectType per gli eventi di traccia](objecttype-trace-event-column.md).|28|Sì|  
|**OwnerName**|**nvarchar**|Nome dell'utente del database proprietario dell'oggetto di destinazione.|37|Sì|  
|**ParentName**|**nvarchar**|Nome dello schema in cui è incluso l'oggetto.|59|Sì|  
|**Autorizzazioni**|**bigint**|Valore intero che rappresenta il tipo di autorizzazioni controllato.<br /><br /> 1=SELECT ALL<br /><br /> 2=UPDATE ALL<br /><br /> 4=REFERENCES ALL<br /><br /> 8=INSERT<br /><br /> 16=DELETE<br /><br /> 32=EXECUTE (solo procedure)|19|Sì|  
|**RequestID**|**int**|ID della richiesta contenente l'istruzione.|49|Sì|  
|**ServerName**|**nvarchar**|Nome dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracciata.|26|no|  
|**SessionLoginName**|**Nvarchar**|Nome dell'account di accesso dell'utente che ha avviato la sessione. Se ad esempio si stabilisce la connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con l'account di accesso Login1 e si esegue un'istruzione con l'account di accesso Login2, **SessionLoginName** indica Login1 e **LoginName** indica Login2. In questa colonna sono visualizzati sia gli account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che quelli di Windows.|64|Sì|  
|**SPID**|**int**|ID della sessione in cui si è verificato l'evento.|12|Sì|  
|**StartTime**|**datetime**|Ora di inizio dell'evento, se disponibile.|14|Sì|  
|**Esito positivo**|**int**|1 = esito positivo. 0 = esito negativo. Ad esempio, il valore 1 indica che il controllo delle autorizzazioni ha avuto esito positivo e il valore 0 che il controllo ha avuto esito negativo.|23|Sì|  
|**TextData**|**ntext**|Testo SQL dell'istruzione.|1|Sì|  
|**TransactionID**|**bigint**|ID della transazione assegnato dal sistema.|4|Sì|  
|**XactSequence**|**bigint**|Token usato per descrivere la transazione corrente.|50|Sì|  
  
## <a name="see-also"></a>Vedere anche  
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  

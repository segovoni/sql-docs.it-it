---
title: Colonne di dati di controllo di sicurezza | Documenti Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: trace-events
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 06bb8b1c6906ebbced1ed7cf52d254564c77d084
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34045555"
---
# <a name="security-audit-data-columns"></a>Colonne di dati degli eventi di controllo di sicurezza
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  La categoria di eventi Controllo di sicurezza include le classi di eventi seguenti:  
  
||||  
|-|-|-|  
|**ID evento**|**Nome evento**|**Descrizione evento**|  
|1|Audit Login|Raccoglie tutti i nuovi eventi di connessione generati dopo l'avvio della traccia, ad esempio quando un client richiede una connessione a un server che esegue un'istanza di SQL Server.|  
|2|Audit Logout|Raccoglie tutti i nuovi eventi di disconnessione generati dopo l'avvio della traccia, ad esempio quando un client esegue un comando di disconnessione.|  
|4|Audit Server Starts And Stops|Registra le attività di chiusura, avvio e sospensione.|  
|18|Audit Object Permission Event|Registra le modifiche alle autorizzazioni per gli oggetti.|  
|19|Audit Admin Operations Event|Registra operazioni del server per eseguire il backup, il ripristino, la sincronizzazione, il collegamento, lo scollegamento, il caricamento o il salvataggio di immagini.|  
  
 Nelle tabelle seguenti vengono elencate le colonne di dati per ognuna di queste classi di eventi.  
  
## <a name="audit-login"></a>Audit Login  
  
|||||  
|-|-|-|-|  
|**Nome colonna**|**ID colonna**|**Tipo di colonna**|**Descrizione colonna**|  
|EventClass|0|1|La classe di evento viene utilizzata per suddividere gli eventi in categorie.|  
|CurrentTime|2|5|Ora di inizio dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|StartTime|3|5|Ora di inizio dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|Severity|22|1|Livello di gravità di un'eccezione.|  
|Operazione completata|23|1|1 = esito positivo. 0 = esito negativo (ad esempio, 1 indica l'esito positivo di un controllo delle autorizzazioni e 0 indica l'esito negativo di tale controllo).|  
|Errore|24|1|Numero di errore di un evento specifico.|  
|ConnectionID|25|1|ID connessione univoco.|  
|NTUserName|32|8|Nome utente di Windows.|  
|NTDomainName|33|8|Dominio Windows di appartenenza dell'utente.|  
|ClientHostName|35|8|Nome del computer in cui viene eseguito il client. Questa colonna di dati viene popolata se il nome host viene fornito dal client.|  
|ClientProcessID|36|1|ID di processo dell'applicazione client.|  
|ApplicationName|37|8|Nome dell'applicazione client in cui è stata creata la connessione al server. Questa colonna viene popolata con i valori passati dall'applicazione e non con il nome visualizzato del programma.|  
|NTCanonicalUserName|40|8|Nome dell'utente in forma canonica. Ad esempio, engineering.microsoft.com/software/someone.|  
|ServerName|43|8|Nome del server che produce l'evento.|  
  
## <a name="audit-logout"></a>Audit Logout  
  
|**Nome colonna**|**ID colonna**|**Tipo di colonna**|**Descrizione colonna**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|La classe di evento viene utilizzata per suddividere gli eventi in categorie.|  
|CurrentTime|2|5|Ora di inizio dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|EndTime|4|5|Ora di fine dell'evento. Questa colonna non viene popolata per le classi degli eventi di avvio, ad esempio SQL:BatchStarting o SP:Starting. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|Durata|5|2|Durata dell'evento in millisecondi.|  
|CPUTime|6|2|Tempo della CPU in millisecondi utilizzato dall'evento.|  
|Operazione completata|23|1|1 = esito positivo. 0 = esito negativo (ad esempio, 1 indica l'esito positivo di un controllo delle autorizzazioni e 0 indica l'esito negativo di tale controllo).|  
|ConnectionID|25|1|ID connessione univoco.|  
|NTUserName|32|8|Nome utente di Windows.|  
|NTDomainName|33|8|Dominio Windows di appartenenza dell'utente.|  
|ClientHostName|35|8|Nome del computer in cui viene eseguito il client. Questa colonna di dati viene popolata se il nome host viene fornito dal client.|  
|ClientProcessID|36|1|ID di processo dell'applicazione client.|  
|ApplicationName|37|8|Nome dell'applicazione client in cui è stata creata la connessione al server. Questa colonna viene popolata con i valori passati dall'applicazione e non con il nome visualizzato del programma.|  
|NTCanonicalUserName|40|8|Nome dell'utente in forma canonica. Ad esempio, engineering.microsoft.com/software/someone.|  
|ServerName|43|8|Nome del server che produce l'evento.|  
  
## <a name="audit-server-starts-and-stops"></a>Audit Server Starts And Stops  
  
|**Nome colonna**|**ID colonna**|**Tipo di colonna**|**Descrizione colonna**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|La classe di evento viene utilizzata per suddividere gli eventi in categorie.|  
|EventSubclass|1|1|La sottoclasse di evento fornisce informazioni aggiuntive su ogni classe di evento:<br /><br /> 1: Instance Shutdown<br /><br /> 2: Instance Started<br /><br /> 3: Instance Paused<br /><br /> 4: Instance Continued|  
|CurrentTime|2|5|Ora di inizio dell'evento, se disponibile. I formati previsti per l'applicazione di filtri sono "YYYY-MM-DD" e "YYYY-MM-DD HH:MM:SS".|  
|Severity|22|1|Livello di gravità di un'eccezione.|  
|Operazione completata|23|1|1 = esito positivo. 0 = esito negativo (ad esempio, 1 indica l'esito positivo di un controllo delle autorizzazioni e 0 indica l'esito negativo di tale controllo).|  
|Errore|24|1|Numero di errore di un evento specifico.|  
|TextData|42|9|Dati di testo associati all'evento.|  
|ServerName|43|8|Nome del server che produce l'evento.|  
  
## <a name="audit-object-permission-event"></a>Audit Object Permission Event  
  
|**Nome colonna**|**ID colonna**|**Tipo di colonna**|**Descrizione colonna**|  
|---------------------|-------------------|---------------------|----------------------------|  
|ObjectID|11|8|ID oggetto (è una stringa).|  
|ObjectType|12|1|Tipo di oggetto.|  
|ObjectName|13|8|Nome dell'oggetto.|  
|ObjectPath|14|8|Percorso dell'oggetto. Elenco delimitato da virgole di elementi padre, a partire dall'elemento padre dell'oggetto.|  
|ObjectReference|15|8|Riferimento all'oggetto. Codificato in formato XML per tutti gli elementi padre. L'oggetto è descritto tramite tag.|  
|Severity|22|1|Livello di gravità di un'eccezione.|  
|Operazione completata|23|1|1 = esito positivo. 0 = esito negativo (ad esempio, 1 indica l'esito positivo di un controllo delle autorizzazioni e 0 indica l'esito negativo di tale controllo).|  
|Errore|24|1|Numero di errore di un evento specifico.|  
|ConnectionID|25|1|ID connessione univoco.|  
|DatabaseName|28|8|Nome del database in cui è in esecuzione l'istruzione dell'utente.|  
|NTUserName|32|8|Nome utente di Windows.|  
|NTDomainName|33|8|Dominio Windows di appartenenza dell'utente.|  
|ClientHostName|35|8|Nome del computer in cui viene eseguito il client. Questa colonna di dati viene popolata se il nome host viene fornito dal client.|  
|ClientProcessID|36|1|ID di processo dell'applicazione client.|  
|ApplicationName|37|8|Nome dell'applicazione client in cui è stata creata la connessione al server. Questa colonna viene popolata con i valori passati dall'applicazione e non con il nome visualizzato del programma.|  
|SessionID|39|8|GUID della sessione.|  
|NTCanonicalUserName|40|8|Nome dell'utente in forma canonica. Ad esempio, engineering.microsoft.com/software/someone.|  
|SPID|41|1|ID processo server. Identifica in modo univoco una sessione utente. Corrisponde direttamente al GUID di sessione utilizzato da XML/A.|  
|TextData|42|9|Dati di testo associati all'evento.|  
|ServerName|43|8|Nome del server che produce l'evento.|  
  
## <a name="audit-admin-operations-event"></a>Audit Admin Operations Event  
  
|**Nome colonna**|**ID colonna**|**Tipo di colonna**|**Descrizione colonna**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventSubclass|1|1|La sottoclasse di evento fornisce informazioni aggiuntive su ogni classe di evento:<br /><br /> 1: **Backup**<br /><br /> 2: **Restore**<br /><br /> 3: **Synchronize**<br /><br /> 4: **Detach**<br /><br /> 5: **Attach**<br /><br /> 6: **ImageLoad**<br /><br /> 7: **ImageSave**|  
|Severity|22|1|Livello di gravità di un'eccezione.|  
|Operazione completata|23|1|1 = esito positivo. 0 = esito negativo (ad esempio, 1 indica l'esito positivo di un controllo delle autorizzazioni e 0 indica l'esito negativo di tale controllo).|  
|Errore|24|1|Numero di errore di un evento specifico.|  
|ConnectionID|25|1|ID connessione univoco.|  
|DatabaseName|28|8|Nome del database in cui è in esecuzione l'istruzione dell'utente.|  
|NTUserName|32|8|Nome utente di Windows.|  
|NTDomainName|33|8|Dominio Windows di appartenenza dell'utente.|  
|ClientHostName|35|8|Nome del computer in cui viene eseguito il client. Questa colonna di dati viene popolata se il nome host viene fornito dal client.|  
|ClientProcessID|36|1|ID di processo dell'applicazione client.|  
|ApplicationName|37|8|Nome dell'applicazione client in cui è stata creata la connessione al server. Questa colonna viene popolata con i valori passati dall'applicazione e non con il nome visualizzato del programma.|  
|SessionID|39|8|GUID della sessione.|  
|NTCanonicalUserName|40|8|Nome dell'utente in forma canonica. Ad esempio, engineering.microsoft.com/software/someone.|  
|SPID|41|1|ID processo server. Identifica in modo univoco una sessione utente. Corrisponde direttamente al GUID di sessione utilizzato da XML/A.|  
|TextData|42|9|Dati di testo associati all'evento.|  
|ServerName|43|8|Nome del server che produce l'evento.|  
  
## <a name="see-also"></a>Vedere anche  
 [Categoria di eventi Controllo di sicurezza](../../analysis-services/trace-events/security-audit-event-category.md)  
  
  

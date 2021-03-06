---
title: MSSQLSERVER_208 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 208 (Database Engine error)
ms.assetid: 4b1895f5-3197-4da1-af86-954c93507956
caps.latest.revision: 13
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b67ec400cd45b70831786f348eb672bb2e7f3bdf
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37431200"
---
# <a name="mssqlserver208"></a>MSSQLSERVER_208
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|208|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|SQ_BADOBJECT|  
|Testo del messaggio|Il nome di oggetto '%.*ls' non è valido.|  
  
## <a name="explanation"></a>Spiegazione  
 Non è possibile individuare l'oggetto specificato.  
  
### <a name="possible-causes"></a>Possibili cause  
 L'errore può essere causato da uno dei problemi seguenti:  
  
-   L'oggetto non è stato specificato correttamente.  
  
-   L'oggetto non esiste nel database corrente oppure in quello specificato.  
  
-   L'oggetto esiste, ma potrebbe non essere esposto all'utente. È possibile ad esempio che l'utente non disponga di autorizzazioni sull'oggetto oppure l'oggetto è stato creato all'interno di un'istruzione EXECUTE, ma l'accesso è stato eseguito al di fuori dell'ambito dell'istruzione EXECUTE.  
  
## <a name="user-action"></a>Azione dell'utente  
 Verificare le informazioni seguenti e correggere l'istruzione in base alle esigenze.  
  
-   Correttezza dell'ortografia dell'oggetto.  
  
-   Correttezza del contesto di database corrente. Se per l'oggetto non è specificato un nome di database, l'oggetto deve esistere nel database corrente. Per altre informazioni sull'impostazione del contesto di database, vedere [USE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/use-transact-sql).  
  
-   Esistenza dell'oggetto nelle tabelle di sistema. Per verificare l'esistenza di una tabella o un altro oggetto con ambito schema, eseguire una query nella vista del catalogo **sys.objects**. Se l'oggetto non è presente nelle tabelle di sistema, significa che è stato eliminato o l'utente non dispone delle autorizzazioni necessarie per visualizzare i metadati dell'oggetto. Per altre informazioni sulle autorizzazioni per visualizzare i metadati degli oggetti, vedere [Configurazione della visibilità dei metadati](../security/metadata-visibility-configuration.md).  
  
-   Presenza dell'oggetto nello schema predefinito dell'utente. Se questa condizione non si verifica, l'oggetto deve essere specificato nel formato in due parti *schema_name.object_name*. Si noti che è sempre necessario richiamare funzioni a valori scalari utilizzando almeno un nome in due parti.  
  
-   Distinzione tra maiuscole e minuscole delle regole di confronto del database.  
  
     Quando in un database vengono utilizzate regole di confronto con distinzione tra maiuscole e minuscole, il nome dell'oggetto deve corrispondere alla combinazione di maiuscole e minuscole dell'oggetto nel database. Ad esempio, se un oggetto è specificato come **MiaTabella** in un database con regole di confronto che rispettano la distinzione tra maiuscole e minuscole, le query che si riferiscono all'oggetto come **miatabella** o **Miatabella** restituiranno l'errore 208 poiché i nomi degli oggetti non corrispondono.  
  
     Per verificare le regole di confronto del database, eseguire l'istruzione seguente.  
  
    ```  
    SELECT collation_name FROM sys.databases WHERE name = 'database_name';  
    ```  
  
     L'abbreviazione CS nel nome delle regole di confronto indica che le regole di confronto rispettano la distinzione tra maiuscole e minuscole. Ad esempio, Latin1_General_CS_AS è una regola di confronto con distinzione tra maiuscole e minuscole e distinzione tra caratteri accentati e non accentati, mentre CI indica una regola di confronto senza distinzione tra maiuscole e minuscole.  
  
-   Autorizzazioni di accesso all'oggetto concesse all'utente. Per verificare le autorizzazioni di cui l'utente dispone sull'oggetto, usare la funzione di sistema **Has_Perms_By_Name**.  
  
## <a name="see-also"></a>Vedere anche  
 [USE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/use-transact-sql)   
 [Configurazione della visibilità dei metadati](../security/metadata-visibility-configuration.md)   
 [HAS_PERMS_BY_NAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/has-perms-by-name-transact-sql)  
  
  

---
title: Finestra di dialogo Proprietà (SSAS - tabulare) del database | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.ssmsimbi.DatabaseProperties.f1
ms.assetid: 0f0ec02f-7b55-40ea-8a04-ed0deb1efd7a
caps.latest.revision: 9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 31f4e6201246467517cf3fdd39bb03906b3bde24
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37299331"
---
# <a name="database-properties-dialog-box-ssas---tabular"></a>Finestra di dialogo Proprietà database (SSAS - Tabulare)
  In questa finestra di dialogo vengono forniti timestamp e altre informazioni descrittive, nonché proprietà personalizzabili che determinano se nel database vengono utilizzati dati memorizzati nella cache. Altre proprietà personalizzabili includono la modifica del nome del database e l'impostazione delle opzioni di rappresentazione.  
  
## <a name="options"></a>Opzioni  
  
|Nome|Definizione|  
|----------|----------------|  
|**Nome**|**Nome** è il nome del database che identifica in modo univoco il database nel server. Quando si modifica il nome del database, considerare l'impatto su report e applicazioni client in cui viene utilizzato il nome corrente nelle stringhe di connessione esistenti. Sarà necessario aggiornare le stringhe di connessione nei report esistenti per evitare errori di accesso negato. È inoltre probabile che nel modello tabulare origine di questo database venga utilizzato il nome originale. Considerare l'aggiornamento delle proprietà di distribuzione del database nel modello per assicurarsi che gli aggiornamenti futuri del modello vengano pubblicati nel database desiderato.|  
|**ID**|Consente di visualizzare l'identificatore del database.|  
|**Descrizione**|Consente di modificare la descrizione del database.|  
|**Timestamp creazione**|Consente di visualizzare la data e l'ora di creazione del database.|  
|**Ultimo aggiornamento schema**|Consente di visualizzare la data e l'ora dell'ultimo aggiornamento dei metadati del database.|  
|**Ultimo aggiornamento**|Consente di visualizzare la data e l'ora dell'ultimo aggiornamento dei dati del database.|  
|**Modalità lettura / scrittura**|Si tratta di una proprietà di sola lettura, ma è possibile modificarla usando una sequenza di comandi **Detach** e **Attach** , in cui la proprietà è un parametro del comando **Attach** . Per altre informazioni, vedere [Proprietà ReadWriteMode del database](multidimensional-models/database-readwritemodes.md).|  
|**DirectQueryMode**|Viene specificato se nel database viene utilizzata solo l'archiviazione in memoria (non l'archiviazione su disco), solo l'archiviazione basata su disco o una combinazione delle due. I valori validi sono InMemory, DirectQuery, InMemoryWithDirectQuery (per lo più basata su memoria ma in alcuni casi con paging su disco) o DirectQueryWithInMemory (per lo più basata su disco ma in alcuni casi con archiviazione in memoria). Per altre informazioni, vedere [scenari di distribuzione DirectQuery &#40;modello tabulare di SSAS&#41;](directquery-deployment-scenarios-ssas-tabular.md).|  
|**Impostazioni di rappresentazione origine dati**|Viene specificato l'account di rappresentazione utilizzato per le connessioni al database quando vengono elaborati o aggiornati i dati in partizioni locali o remote, le query eseguite su un archivio dati relazionale (tramite DirectQuery), le associazioni out-of-line e la sincronizzazione del database dalla destinazione all'origine.<br /><br /> I valori validi includono l'account del servizio Analysis Services o un set specifico di credenziali di Windows. Non specificare **Usa credenziali dell'utente corrente**. Tale opzione per le credenziali non è supportata per un database modello tabulare.|  
|**Ultima elaborazione**|Consente di visualizzare la data e l'ora dell'ultima elaborazione del database.|  
|**Dimensioni stimate**|Consente di visualizzare le dimensioni stimate del database.|  
|**Percorso di archiviazione**|Specifica la posizione del database. Se il database si trova nella directory dati predefinita, questo valore sarà vuoto.|  
  
  

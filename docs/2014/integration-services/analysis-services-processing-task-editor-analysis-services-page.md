---
title: Editor attività elaborazione (pagina Analysis Services) di Analysis Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.asprocessingtask.as.f1
helpviewer_keywords:
- Analysis Services Processing Task Editor
ms.assetid: 5612be78-57cf-4e4e-92cf-6bfa9f971040
caps.latest.revision: 28
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a131a7a25e9539eac5d7090508e3b67aa79fd9a1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37187188"
---
# <a name="analysis-services-processing-task-editor-analysis-services-page"></a>Editor attività Elaborazione Analysis Services (pagina Analysis Services)
  Usare la pagina **Analysis Services** della finestra di dialogo **Editor attività Elaborazione Analysis Services** per specificare una gestione connessione Analysis Services, selezionare gli oggetti analitici da elaborare e impostare le opzioni di elaborazione e di gestione degli errori.  
  
 Quando si elaborano modelli tabulari, tenere presente quanto segue:  
  
1.  Non è possibile effettuare analisi di impatto sui modelli tabulari.  
  
2.  Alcune opzioni di elaborazione per la modalità tabulare non sono esposte, ad esempio Elaborazione deframmentazione e Elabora ricalcolo. È possibile eseguire queste funzioni tramite l'attività Esegui DDL.  
  
3.  Alcune opzioni di elaborazione fornite, ad esempio l'elaborazione di indici, non sono appropriate per i modelli tabulari, pertanto non devono essere utilizzate.  
  
4.  Le impostazioni batch vengono ignorate per i modelli tabulari.  
  
 Per altre informazioni su questa attività, vedere [Attività Elaborazione Analysis Services](control-flow/analysis-services-processing-task.md).  
  
## <a name="options"></a>Opzioni  
 **Analysis Services - gestione connessione**  
 Consente di selezionare una gestione connessione Analysis Services esistente nell'elenco o di crearne una nuova usando il pulsante **Nuova** .  
  
 **Nuova**  
 Consente di creare una nuova gestione connessione Analysis Services.  
  
 **Argomenti correlati:** [Analysis Services Connection Manager](connection-manager/analysis-services-connection-manager.md), [Riferimento all'interfaccia utente della finestra di dialogo Aggiungi gestione connessione Analysis Services](connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md)  
  
 **Elenco oggetti**  
 |Proprietà|Description|  
|--------------|-----------------|  
|**Nome oggetto**|Consente di visualizzare i nomi degli oggetti specificati.|  
|**Tipo**|Consente di visualizzare i tipi degli oggetti specificati.|  
|**Opzioni elaborazione**|Consente di selezionare un'opzione di elaborazione nell'elenco.<br /><br /> **Argomenti correlati**: [elaborazione degli oggetti modello multidimensionale](../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md)|  
|**Impostazioni**|Consente di visualizzare le impostazioni di elaborazione per gli oggetti specificati.|  
  
 **Aggiungi**  
 Consente di aggiungere un oggetto di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] all'elenco.  
  
 **Rimuovi**  
 Selezionare un oggetto, quindi fare clic su **Elimina**.  
  
 **Analisi di impatto**  
 Consente di eseguire un'analisi di impatto sull'oggetto selezionato.  
  
 **Argomenti correlati:** [Finestra di dialogo Analisi di impatto &#40;Analysis Services - Dati multidimensionali&#41;](../../2014/analysis-services/impact-analysis-dialog-box-analysis-services-multidimensional-data.md)  
  
 **Riepilogo impostazioni batch**  
 |Proprietà|Description|  
|--------------|-----------------|  
|**Ordine di elaborazione**|Consente di specificare se gli oggetti devono essere elaborati sequenzialmente o in un batch. Se si utilizza l'elaborazione parallela, consente di specificare il numero di oggetti da elaborare simultaneamente.|  
|**Modalità transazione**|Consente di specificare la modalità di transazione per l'elaborazione sequenziale.|  
|**Errori dimensione**|Consente di specificare il funzionamento dell'attività quando si verificano errori.|  
|**Percorso log degli errori di chiave della dimensione**|Consente di specificare il percorso del file nel quale vengono registrati gli errori.|  
|**Elabora oggetti interessati**|Indica se vengono elaborati anche gli oggetti dipendenti o interessati.|  
  
 **Cambia impostazioni**  
 Consente di modificare le opzioni di elaborazione e la gestione degli errori nelle chiavi della dimensione.  
  
 **Argomenti correlati:** [Finestra di dialogo Cambia impostazioni &#40;Analysis Services - Dati multidimensionali&#41;](../../2014/analysis-services/change-settings-dialog-box-analysis-services-multidimensional-data.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento ai messaggi e agli errori di Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Editor attività elaborazione di Analysis Services &#40;pagina Generale&#41;](general-page-of-integration-services-designers-options.md)   
 [Attività Esegui DDL Analysis Services](control-flow/analysis-services-execute-ddl-task.md)  
  
  

---
title: Opzioni query-risultati (pagina della griglia) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.query.grid.f1
ms.assetid: 764bf435-3aab-4c62-b4e0-64fe020a5a95
caps.latest.revision: 18
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: ba8b1d1fb182ca0f16fe157630253b74b9580eb2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37312291"
---
# <a name="query-options-results-grid-page"></a>Risultati di Opzioni query (pagina Griglia)
  Utilizzare questa pagina per specificare le opzioni di visualizzazione di un set di risultati di query in formato griglia.  
  
## <a name="options"></a>Opzioni  
 **Includi la query del set di risultati**  
 Restituisce il testo della query come parte del set di risultati.  
  
 **Includi intestazioni di colonna durante la copia o salvataggio dei risultati**  
 Consente di includere le intestazioni di colonna (titoli) durante la copia dei risultati negli Appunti o il salvataggio in un file. Deselezionare questa casella di controllo se si desidera che i risultati salvati o copiati contengano solo i dati senza le intestazioni di colonna.  
  
 **Elimina risultati dopo l'esecuzione**  
 Consente di liberare memoria eliminando i risultati delle query dopo la loro visualizzazione.  
  
 **Visualizzare i risultati in una scheda separata**  
 Consente di visualizzare il set dei risultati in una nuova finestra del documento anziché nella parte inferiore della finestra del documento della query.  
  
 **Passare alla scheda risultati dopo l'esecuzione di query**  
 Consente di impostare automaticamente lo stato attivo dello schermo sul set dei risultati.  
  
 **Dimensioni massime caratteri recuperati**  
 **Dati non XML**:  
  
 Consente di immettere un valore compreso tra 1 e 65535 per specificare il numero massimo di caratteri che sarà possibile visualizzare in ogni cella.  
  
> [!NOTE]  
>  Se si specifica un numero elevato di caratteri, i dati nel set di risultati potrebbero non essere visualizzati completamente. Il numero massimo di caratteri visualizzati in ogni cella dipende dalle dimensioni del carattere. Se si specifica un valore elevato in questa casella e vengono restituiti set di risultati di notevoli dimensioni, la memoria per [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] potrebbe risultare insufficiente con effetti negativi sulle prestazioni del sistema.  
  
 **Dati XML**:  
  
 Consente di selezionare i valori **1 MB**, **2 MB**o **5 MB**. Selezionare **Illimitate** per recuperare tutti i caratteri.  
  
 **Ripristina predefiniti**  
 Reimposta le impostazioni predefinite originali per tutti i valori nella pagina.  
  
  

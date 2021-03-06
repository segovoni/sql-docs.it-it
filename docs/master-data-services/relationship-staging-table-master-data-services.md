---
title: Tabella di gestione temporanea delle relazioni (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 04/01/2016
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- relationships staging table [Master Data Services]
- database [Master Data Services], relationships table
ms.assetid: e19b6002-67bd-4e7d-9f19-ecb455522b1a
caps.latest.revision: 8
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: eb81e8c1ac664474cf9482bb76b27e7f3f2fdc54
ms.sourcegitcommit: de5e726db2f287bb32b7910831a0c4649ccf3c4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2018
ms.locfileid: "35335315"
---
# <a name="relationship-staging-table-master-data-services"></a>Tabella di gestione temporanea delle relazioni (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Usare la tabella di staging delle relazioni nel database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] per modificare il percorso dei membri in una gerarchia esplicita, in base alla relazione esistente tra i membri.  
  
##  <a name="TableColumns"></a> Colonne della tabella  
 Nella seguente tabella viene illustrato il motivo per cui viene utilizzato ogni campo della tabella di staging Relazione.  
  
|Nome colonna|Descrizione|valore|  
|-----------------|-----------------|-----------|  
|**ID**|Un identificatore assegnato automaticamente.|Non immettere un valore in questo campo. Se il batch non è stato elaborato, questo campo è vuoto.|  
|**RelationshipType**|Obbligatorio<br /><br /> Il tipo di relazione impostata.|I valori possibili sono:<br /><br /> **1**:Padre<br /><br /> **2**: Pari livello (allo stesso livello)|  
|**ImportStatus_ID**|Obbligatorio<br /><br /> Lo stato del processo di importazione.|I valori possibili sono:<br /><br /> **0**, specificato per indicare che il record è pronto per la gestione temporanea.<br /><br /> **1**, assegnato automaticamente indica che il processo di gestione temporanea del record ha avuto esito positivo.<br /><br /> **2**, assegnato automaticamente e indica che il processo di gestione temporanea del record non è riuscito.|  
|**Batch_ID**|Richiesto solo dal servizio Web<br /><br /> Un identificatore assegnato automaticamente che raggruppa i record per la gestione temporanea.<br /><br /> Se il batch non è stato elaborato, questo campo è vuoto.|A tutti i membri nel batch viene assegnato questo identificatore, visualizzato nella colonna [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] ID **dell'interfaccia utente di** .|  
|**BatchTag**|Richiesto, salvo che dal servizio Web<br /><br /> Un nome univoco per il batch, composto da un massimo di 50 caratteri.||  
|**HierarchyName**|Obbligatorio<br /><br /> Il nome della gerarchia esplicita. Ogni membro consolidato può appartenere solo ad un'unica gerarchia.||  
|**ParentCode**|Obbligatorio<br /><br /> Per le relazioni padre-figlio, il codice del membro consolidato che sarà il padre della foglia figlio o del membro consolidato.<br /><br /> Per le relazioni di pari livello, il codice di uno degli elementi di pari livello.||  
|**ChildCode**|Obbligatorio<br /><br /> Per le relazioni padre-figlio, il codice del membro consolidato o foglia che sarà il figlio.<br /><br /> Per le relazioni di pari livello, il codice di uno degli elementi di pari livello.||  
|**Ordinamento**|Facoltativo<br /><br /> Un valore intero che indica l'ordine del membro in relazione agli altri membri sottostanti l'elemento padre. Ciascun membro figlio deve disporre di un identificatore univoco.||  
|**ErrorCode**|Visualizza un codice di errore. Per tutti i record con **ImportStatus_ID** di **2**, vedere [Errori del processo di gestione temporanea &#40;Master Data Services&#41;](../master-data-services/staging-process-errors-master-data-services.md).||  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica: Importazione di dati da tabelle &#40;Master Data Services&#41;](../master-data-services/overview-importing-data-from-tables-master-data-services.md)   
 [Visualizzare gli errori che si verificano durante il processo di gestione temporanea &#40;Master Data Services&#41;](../master-data-services/view-errors-that-occur-during-staging-master-data-services.md)   
 [Errori del processo di gestione temporanea &#40;Master Data Services&#41;](../master-data-services/staging-process-errors-master-data-services.md)  
  
  

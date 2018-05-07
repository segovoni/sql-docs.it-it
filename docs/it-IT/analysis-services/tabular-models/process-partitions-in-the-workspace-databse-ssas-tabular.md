---
title: Elaborare partizioni nel database dell'area di lavoro | Documenti Microsoft
ms.custom: ''
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 3a369705-43fa-4961-9045-32e06fbdde33
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: bbd67799b4939db9d11a1e78ca44cc453cadd344
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="process-partitions-in-the-workspace-databse"></a>Elaborare partizioni nel database dell'area di lavoro 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Le partizioni consentono di dividere una tabella in parti logiche. Ogni partizione può quindi essere elaborata (aggiornata) indipendentemente dalle altre. Nelle attività di questo argomento viene descritto come elaborare le partizioni nel database dell'area lavoro modello tramite la finestra di dialogo **Elabora partizioni** in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 Dopo aver distribuito un modello in un'altra istanza di Analysis Services, gli amministratori di database possono creare e gestire partizioni nel modello (distribuito) tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], script o utilizzando un pacchetto di IS. Per ulteriori informazioni, vedere [creare e gestire partizioni di modelli tabulari](../../analysis-services/tabular-models/create-and-manage-tabular-model-partitions-ssas-tabular.md).  
  
###  <a name="bkmk_create_new"></a> Per elaborare una partizione  
  
1.  In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]fare clic sul menu **Modello** , scegliere **Elabora** (Aggiorna) e quindi fare clic su **Elabora partizioni**.  
  
2.  Nella casella di riepilogo **Modalità** selezionare una delle modalità di elaborazione seguenti:  
  
    |Modalità|Description|  
    |----------|-----------------|  
    |**Elaborazione predefinita**|Rileva lo stato di elaborazione di un oggetto partizione ed esegue l'elaborazione necessaria per recapitare oggetti partizione non elaborati o elaborati parzialmente in uno stato di elaborazione completa. Vengono caricati i dati per le tabelle vuote e le partizioni; vengono compilate o ricompilate le gerarchie, le colonne calcolate e le relazioni.|  
    |**Elaborazione completa**|Elabora un oggetto partizione e tutti gli oggetti in esso contenuti. Quando viene eseguita l'elaborazione completa per un oggetto che è stato già elaborato, in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] vengono eliminati tutti i dati dell'oggetto, quindi quest'ultimo viene elaborato. Questo tipo di elaborazione è necessario quando è stata apportata una modifica strutturale a un oggetto.|  
    |**Elaborare dati**|Carica i dati in una partizione o in una tabella senza ricompilare le gerarchie o le relazioni oppure ricalcolare le colonne calcolate e le misure.|  
    |**Elaborazione pulizia**|Rimuove tutti i dati da una partizione.|  
    |**Elaborazione aggiunta**|Aggiornare in modo incrementale la partizione con i nuovi dati.|  
  
3.  Nella colonna della casella di controllo **Elabora** selezionare le partizioni che si desidera elaborare con la modalità scelta, quindi fare clic su **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Partizioni](../../analysis-services/tabular-models/partitions-ssas-tabular.md)   
 [Creare e gestire partizioni nel database dell'area di lavoro](../../analysis-services/tabular-models/create-and-manage-partitions-in-the-workspace-database-ssas-tabular.md)  
  
  
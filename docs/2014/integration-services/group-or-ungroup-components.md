---
title: Raggruppare o separare componenti | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- grouping containers
- tasks [Integration Services], grouping
- containers [Integration Services], grouping
- grouping tasks
ms.assetid: 34320838-c271-4f8c-90b3-1254690890bb
caps.latest.revision: 45
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: cece9e943ad2c551b60f4a468a3ce0b89d85059f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37227781"
---
# <a name="group-or-ungroup-components"></a>Raggruppare o separare componenti
  Le schede **Flusso di controllo**, **Flusso di dati**e **Gestori eventi** in Progettazione [!INCLUDE[ssIS](../includes/ssis-md.md)] supportano il raggruppamento comprimibile. Se un pacchetto include molti contenitori, è possibile che le schede contengano un numero di elementi talmente elevato da impedire di visualizzare contemporaneamente tutti gli elementi del flusso di controllo del pacchetto e di individuare l'elemento che si desidera utilizzare. La funzionalità raggruppamento comprimibile consente di risparmiare spazio nell'area di lavoro e semplificare la gestione di pacchetti di grandi dimensioni.  
  
 È possibile selezionare i componenti che si desidera raggruppare, eseguire il raggruppamento, quindi espandere o comprimere i gruppi in base alle proprie esigenze. Espandendo un gruppo sarà possibile accedere alle proprietà dei componenti inclusi. I vincoli di precedenza che connettono attività e contenitori vengono automaticamente inclusi nel gruppo.  
  
 Di seguito sono riportate alcune considerazioni per il raggruppamento di componenti.  
  
-   Per raggruppare componenti, il flusso di controllo, il flusso di dati o il gestore eventi deve contenere più di un componente.  
  
-   I gruppi possono inoltre essere nidificati, consentendo la creazione di sottogruppi. Nell'area di progettazione è possibile implementare più gruppi non nidificati, ma un componente può appartenere a un solo gruppo, a meno che i gruppi non siano nidificati.  
  
-   Quando si salva un pacchetto, in Progettazione [!INCLUDE[ssIS](../includes/ssis-md.md)] viene salvato anche il raggruppamento, ma quest'ultimo non ha alcun effetto sull'esecuzione del pacchetto. La possibilità di raggruppare componenti è una funzionalità della fase di progettazione e non influisce sul comportamento di un pacchetto in fase di esecuzione.  
  
### <a name="to-group-components"></a>Per raggruppare componenti  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]aprire il progetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] che contiene il pacchetto desiderato.  
  
2.  In Esplora soluzioni fare doppio clic sul pacchetto per aprirlo.  
  
3.  Fare clic sulla scheda **Flusso di controllo**, **Flusso di dati**o **Gestori eventi** .  
  
4.  Nell'area di progettazione della scheda selezionare i componenti da raggruppare, fare clic con il pulsante destro del mouse su un componente selezionato e quindi scegliere **Raggruppa**.  
  
5.  Per salvare il pacchetto aggiornato, scegliere **Salva elementi selezionati** dal menu **File** .  
  
### <a name="to-ungroup-components"></a>Per separare componenti  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]aprire il progetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] che contiene il pacchetto desiderato.  
  
2.  In Esplora soluzioni fare doppio clic sul pacchetto per aprirlo.  
  
3.  Fare clic sulla scheda **Flusso di controllo**, **Flusso di dati**o **Gestori eventi** .  
  
4.  Nell'area di progettazione della scheda selezionare il gruppo che contiene il componente da separare, fare clic con il pulsante destro del mouse e quindi scegliere **Separa**.  
  
5.  Per salvare il pacchetto aggiornato, scegliere **Salva elementi selezionati** dal menu **File** .  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiungere o eliminare un'attività o un contenitore in un flusso di controllo](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)  
     
 [Connettere attività e contenitori tramite un vincolo di precedenza predefinito](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md)  
  
  

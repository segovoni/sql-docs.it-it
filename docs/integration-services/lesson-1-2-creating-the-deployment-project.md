---
title: 'Passaggio 2: Creazione del progetto di distribuzione | Microsoft Docs'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: tutorial
applies_to:
- SQL Server 2016
ms.assetid: 59990fe2-7036-4e9c-8efc-6ece9e66eda7
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d0468fa10f703723c9283ecfe523486b834f447b
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2018
ms.locfileid: "35400273"
---
# <a name="lesson-1-2---creating-the-deployment-project"></a>Lezione 1-2 - Creazione del progetto di distribuzione
In [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]l'unità distribuibile è rappresentata da un progetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Per poter distribuire i pacchetti, è necessario creare un nuovo progetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] e aggiungervi tutti i pacchetti e gli eventuali file ausiliari che di desidera distribuire unitamente ai pacchetti.  
  
### <a name="to-create-the-integration-services-project"></a>Per creare il progetto di Integration Services  
  
1.  Fare clic su **Start**, scegliere **Tutti i programmi**, **Microsoft SQL Server**e quindi fare clic su **SQL Server Data Tools**.  
  
2.  Dal menu **File** scegliere **Nuovo**e quindi **Progetto** per creare un nuovo progetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
3.  Nella finestra di dialogo **Nuovo progetto** selezionare **Progetto di Integration Services** nel riquadro **Modelli** .  
  
4.  Nella casella **Nome** modificare il nome predefinito in **Deployment Tutorial**. Facoltativamente, deselezionare la casella di controllo **Crea directory per soluzione** .  
  
5.  Accettare il percorso predefinito o fare clic su **Sfoglia** per trovare la cartella che si vuole usare.  
  
6.  Nella finestra di dialogo **Percorso progetto** fare clic sulla cartella e scegliere **Apri**.  
  
7.  Fare clic su **OK**.  
  
8.  Per impostazione predefinita, viene creato e aggiunto al progetto un pacchetto vuoto denominato Package.dtsx. Questo pacchetto non verrà tuttavia utilizzato. Al progetto verranno infatti aggiunti i pacchetti esistenti. Poiché nella distribuzione vengono inclusi tutti i pacchetti del progetto, è consigliabile eliminare Package.dtsx. A tale scopo, fare clic con il pulsante destro del mouse su di esso e scegliere **Elimina**.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
[Passaggio 3: Aggiunta di pacchetti e altri file](../integration-services/lesson-1-3-adding-packages-and-other-files.md)  
  
## <a name="see-also"></a>Vedere anche  
[Progetti di Integration Services &#40;SSIS&#41;](~/integration-services/integration-services-ssis-projects-and-solutions.md)  
  
  
  


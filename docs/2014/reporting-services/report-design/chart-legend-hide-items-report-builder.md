---
title: Nascondere elementi legenda nel grafico (Generatore report e SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 92256240-0cd5-4be4-8904-d1e3b93cb6b3
caps.latest.revision: 6
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 26e3fe8feb400bb9280a37f8f33bebf510377fe0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37261877"
---
# <a name="hide-legend-items-on-the-chart-report-builder-and-ssrs"></a>Nascondere elementi legenda nel grafico (Generatore report e SSRS)
  Per impostazione predefinita, qualsiasi serie aggiunta a un grafico senza forme verrà aggiunta come elemento nella legenda. Per grafici a torta, ad anello, a imbuto e a piramide, qualsiasi serie aggiunta al grafico determina l'aggiunta di punti dati singoli nella legenda.  
  
 È possibile nascondere qualsiasi elemento della legenda. Quando si nasconde un elemento della legenda, questo rimane comunque visualizzato nel grafico. Ciò si rivela utile nelle situazioni in cui non si desidera mostrare ulteriori informazioni per una serie aggiunta al grafico. Se ad esempio è stata aggiunta una serie calcolata come una media mobile al grafico, potrebbe essere necessario nascondere questa voce nella legenda in modo che vengano mostrate informazioni aggiuntive solo per la serie originale.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-hide-an-item-from-display-in-the-legend"></a>Per nascondere un elemento visualizzato nella legenda  
  
1.  Fare clic con il pulsante destro del mouse sulla serie da nascondere e scegliere **Proprietà serie**.  
  
2.  Fare clic su **Legenda**. Selezionare l'opzione **Non mostrare questa serie in una legenda** .  
  
    > [!NOTE]  
    >  Non è possibile nascondere una serie per un solo gruppo. Se è stato aggiunto un campo all'area **Gruppi di serie** , verranno nascoste tutte le serie che appartengono a questo gruppo.  
  
## <a name="see-also"></a>Vedere anche  
 [Formattazione della legenda in un grafico &#40;Report e SSRS&#41;](chart-legend-formatting-report-builder.md)   
 [Formattazione dei punti dati in un grafico &#40;Report e SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)   
 [Modificare il testo di un elemento legenda &#40;Generatore report e SSRS&#41;](chart-legend-change-item-text-report-builder.md)   
 [Aggiungere una media mobile a un grafico &#40;Generatore report e SSRS&#41;](add-a-moving-average-to-a-chart-report-builder-and-ssrs.md)   
 [Finestra di dialogo Proprietà legenda, Generale &#40;Generatore report e SSRS&#41;](../legend-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  

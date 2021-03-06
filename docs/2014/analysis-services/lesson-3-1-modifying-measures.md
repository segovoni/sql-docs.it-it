---
title: Modifica delle misure | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 7bd48810-15ce-45ff-862b-372d08606995
caps.latest.revision: 14
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 447032ab32e222f3827c34020aef612e8125a518
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37232381"
---
# <a name="modifying-measures"></a>Modifica delle misure
  È possibile usare la proprietà **FormatString** per definire impostazioni di formattazione che controllano la modalità di visualizzazione delle misure agli utenti. In questa attività vengono impostate le proprietà di formattazione per le misure di valuta e di percentuale nel cubo [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial.  
  
### <a name="to-modify-the-measures-of-the-cube"></a>Per modificare le misure del cubo  
  
1.  Passare alla scheda **Struttura cubo** di Progettazione cubi per il cubo [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial, espandere il gruppo di misure **Internet Sales** nel riquadro **Misure** , fare clic con il pulsante destro del mouse su **Order Quantity**, quindi scegliere **Proprietà**.  
  
2.  Nella finestra Proprietà fare clic sull'icona a forma di puntina da disegno **Nascondi automaticamente** per mantenere aperta la finestra Proprietà.  
  
     Con la finestra Proprietà aperta risulta più agevole modificare le proprietà per diversi elementi nel cubo.  
  
3.  Nella finestra Proprietà fare clic sull'elenco **FormatString** e quindi digitare **#,#**.  
  
4.  Sulla barra degli strumenti della scheda **Struttura cubo** fare clic sull'icona **Mostra griglie delle misure** a sinistra.  
  
     Nella visualizzazione griglia è possibile selezionare più misure contemporaneamente.  
  
5.  Selezionare le misure seguenti. Per selezionare più misure, fare clic su ognuna di esse tenendo premuto CTRL:  
  
    -   **Unit Price**  
  
    -   **Extended Amount**  
  
    -   **Discount Amount**  
  
    -   **Product Standard Cost**  
  
    -   **Total Product Cost**  
  
    -   **Sales Amount**  
  
    -   **Tax Amt**  
  
    -   **Freight**  
  
6.  Nell'elenco **FormatString** della finestra Proprietà selezionare **Currency**.  
  
7.  Nell'elenco a discesa nella parte superiore della finestra Proprietà sotto la barra del titolo selezionare la misura **Unit Price Discount Pct**, quindi selezionare **Percent** nell'elenco **FormatString** .  
  
8.  Nella finestra Proprietà modificare il **Name** proprietà per il **Unit Price Discount Pct** misura `Unit Price Discount Percentage`.  
  
9. Nel **misure** riquadro, fare clic su **Tax Amt** e modificare il nome della misura in `Tax Amount`.  
  
10. Nella finestra Proprietà fare clic sull'icona **Nascondi automaticamente** per nascondere la finestra Proprietà, quindi fare clic su **Mostra albero delle misure** sulla barra degli strumenti della scheda **Struttura cubo** .  
  
11. Scegliere **Salva tutti** dal menu **File**.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
 [Modifica della dimensione Customer](lesson-3-2-modifying-the-customer-dimension.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Definire le dimensioni del Database](multidimensional-models/define-database-dimensions.md)   
 [Configurare le proprietà delle misure](multidimensional-models/configure-measure-properties.md)  
  
  

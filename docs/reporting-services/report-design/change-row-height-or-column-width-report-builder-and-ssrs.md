---
title: Modificare l'altezza di riga o la larghezza di colonna (Generatore report e SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: report-design
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f061c204-5cd5-4467-9a9c-8a12803d93ba
caps.latest.revision: 9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c731a73e7d409bbc178901165140f694596887ce
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33020528"
---
# <a name="change-row-height-or-column-width-report-builder-and-ssrs"></a>Modificare l'altezza di riga o la larghezza di colonna (Generatore report e SSRS)
  Quando si imposta un'altezza di riga, si specifica l'altezza massima della riga nel report visualizzabile. Per impostazione predefinita, tuttavia, le caselle di testo nella riga sono impostate in modo da ingrandirsi verticalmente per poter contenere i dati immessi in fase di esecuzione. Per questo motivo, può verificarsi che una riga si espanda oltre l'altezza specificata dall'utente. Per impostare un'altezza di riga fissa è necessario modificare le proprietà della casella di testo in modo che non venga espansa automaticamente.  
  
 Quando si imposta una larghezza di colonna, si specifica la larghezza massima della colonna nel report visualizzabile. Le colonne non si espandono automaticamente in senso orizzontale in base al testo.  
  
 Se una cella in una riga o in una colonna contiene un rettangolo o un'area dati, l'altezza e la larghezza minima della cella vengono determinate in base all'altezza e alla larghezza dell'elemento contenuto. Per altre informazioni, vedere [Tipi di rendering  &#40;Generatore report e SSRS &#41;](../../reporting-services/report-design/rendering-behaviors-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-row-height-by-moving-row-handles"></a>Per modificare l'altezza delle righe spostando gli handle di riga  
  
1.  In visualizzazione della struttura fare clic in un punto qualsiasi dell'area dati Tablix per selezionarla. Lungo il bordo esterno dell'area dati Tablix vengono visualizzati alcuni handle di riga grigi.  
  
2.  Passare con il puntatore del mouse sul bordo dell'handle di riga che si desidera espandere. Verrà visualizzata una freccia doppia.  
  
3.  Fare clic per selezionare il bordo della riga e spostarlo più in alto o più in basso per regolare l'altezza della riga.  
  
### <a name="to-change-row-height-by-setting-cell-properties"></a>Per modificare l'altezza delle righe impostando le proprietà delle celle  
  
1.  In visualizzazione Progettazione fare clic su una cella nella riga di tabella.  
  
     ![Cella selezionata in una tabella](../../reporting-services/report-design/media/table-selectcell.png "Cella selezionata in una tabella")  
  
2.  Nel riquadro **Proprietà** visualizzato modificare la proprietà **Altezza** , quindi fare clic in un punto qualsiasi all'esterno del riquadro **Proprietà** .  
  
     ![Riquadro Proprietà per la cella della tabella selezionata](../../reporting-services/report-design/media/cell-propertiespane.png "Riquadro Proprietà per la cella della tabella selezionata")  
  
### <a name="to-prevent-a-row-from-automatically-expanding-vertically"></a>Per impedire che una riga si espanda automaticamente in senso verticale  
  
1.  In visualizzazione della struttura fare clic in un punto qualsiasi dell'area dati Tablix per selezionarla. Lungo il bordo esterno dell'area dati Tablix vengono visualizzati alcuni handle di riga grigi.  
  
2.  Fare clic sull'handle di riga per selezionare la riga.  
  
3.  Nel riquadro Proprietà impostare CanGrow su **False**.  
  
    > [!NOTE]  
    >  Se non viene visualizzato il riquadro Proprietà, scegliere **Proprietà** dal menu **Visualizza**.  
  
### <a name="to-change-column-width"></a>Per modificare la larghezza delle colonne  
  
1.  In visualizzazione della struttura fare clic in un punto qualsiasi dell'area dati Tablix per selezionarla. Lungo il bordo esterno dell'area dati Tablix vengono visualizzati alcuni handle di colonna grigi.  
  
2.  Passare con il puntatore del mouse sul bordo dell'handle di colonna che si desidera espandere. Verrà visualizzata una freccia doppia.  
  
3.  Fare clic per selezionare il bordo della colonna e spostarlo verso sinistra o verso destra per regolare la larghezza della colonna.  
  
## <a name="see-also"></a>Vedere anche  
 [Area dati Tablix (Generatore report e SSRS)](tablix-data-region-report-builder-and-ssrs.md)   
 [Celle, righe e colonne dell'area dati Tablix (Generatore report e SSRS)](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md)   
 [Tabelle (Generatore report e SSRS)](../../reporting-services/report-design/tables-report-builder-and-ssrs.md)   
 [Matrici (Generatore report e SSRS)](create-a-matrix-report-builder-and-ssrs.md)   
 [Elenchi (Generatore report e SSRS)](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)   
 [Tabelle, matrici ed elenchi (Generatore report e SSRS)](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  

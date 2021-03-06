---
title: Aggiungere o eliminare un indicatore (Generatore report e SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a8b1aac1-53ef-47a4-afc0-8fa866c6c480
caps.latest.revision: 6
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: e6e09fbd1af47c63d12d5c1b726e6a0ad23cf5b7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37294131"
---
# <a name="add-or-delete-an-indicator-report-builder-and-ssrs"></a>Aggiungere o eliminare un indicatore (Generatore report e SSRS)
  Gli indicatori sono piccoli misuratori sui quali è possibile leggere immediatamente lo stato di un singolo valore di dati. Per altre informazioni in merito, vedere [Indicatori &#40;Generatore report e SSRS&#41;](indicators-report-builder-and-ssrs.md).  
  
 Gli indicatori sono posizionati comunemente nelle celle di una tabella o di una matrice, ma possono essere utilizzati anche separatamente, affiancati ai misuratori o incorporati nei misuratori.  
  
 Quando si aggiunge un indicatore per la prima volta, viene configurato per impostazione predefinita in modo da utilizzare le percentuali come unità di misura. Gli intervalli delle percentuali sono distribuiti uniformemente tra i membri del set di indicatori e l'ambito di valori mostrati dall'indicatore rappresenta l'elemento padre dell'indicatore, ad esempio una tabella o una matrice.  
  
 È possibile aggiornare i valori e gli stati di indicatori. Per altre informazioni, vedere gli argomenti seguenti:  
  
-   [Modificare le icone degli indicatori e dei set &#40;Report e SSRS&#41;](change-indicator-icons-and-indicator-sets-report-builder-and-ssrs.md)  
  
-   [Impostare e configurare le unità di misura &#40;Report e SSRS&#41;](set-and-configure-measurement-units-report-builder-and-ssrs.md)  
  
-   [Imposta ambito di sincronizzazione &#40;Report e SSRS&#41;](set-synchronization-scope-report-builder-and-ssrs.md)  
  
 Poiché un indicatore viene posizionato nel pannello del misuratore, è necessario selezionare l'indicatore anziché il pannello quando si vuole configurare l'indicatore tramite la finestra di dialogo **Proprietà indicatori** o il riquadro **Proprietà** . Nell'immagine seguente viene mostrato un indicatore selezionato nel relativo pannello del misuratore.  
  
 ![rs_GaugePanelWithIndicator](../media/rs-gaugepanelwithindicator.gif "rs_GaugePanelWithIndicator")  
  
> [!NOTE]  
>  A seconda della larghezza della colonna e della lunghezza dei valori di dati, il testo nella tabella o nelle celle della matrice potrebbe essere sottoposto a wrapping ed essere quindi visualizzato su più righe. In tal caso, l'icona dell'indicatore potrebbe essere adattata e assumere una forma diversa rendendola così meno leggibile. Posizionare l'indicatore in un rettangolo per assicurarsi che l'icona non sia mai adattata.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-an-indicator-to-a-table-or-matrix"></a>Per aggiungere un indicatore a una tabella o a una matrice  
  
1.  Aprire un report esistente o crearne uno nuovo contenente una tabella e una matrice con i dati che si desidera visualizzare. Per altre informazioni, vedere [Tabelle &#40;Generatore report e SSRS&#41;](tables-report-builder-and-ssrs.md) o [Matrici &#40;Generatore report e SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md).  
  
2.  Inserire una colonna nella tabella o nella matrice. Per altre informazioni, vedere [Inserire o eliminare una colonna &#40;Generatore report e SSRS&#41;](insert-or-delete-a-column-report-builder-and-ssrs.md).  
  
3.  Facoltativamente, nella scheda **Inserisci** fare clic su **Rettangolo**e quindi fare clic su una cella nella nuova colonna.  
  
4.  Nella scheda **Inserisci** fare clic su **Indicatore**e quindi fare clic su una cella nella nuova colonna.  
  
     Se è stato aggiunto un rettangolo a una cella, fare clic su quella cella.  
  
5.  Nel riquadro sinistro della finestra di dialogo **Seleziona tipo indicatore** fare clic sul tipo di indicatore desiderato e quindi sul set di indicatori.  
  
6.  Fare clic su **OK**.  
  
7.  Fare clic sull'indicatore. Viene visualizzato il riquadro **Dati del misuratore** .  
  
8.  Nell'area **Valori** , nell'elenco a discesa **(valore non specificato)** , fare clic sul campo di cui si vuole visualizzare i valori come un indicatore.  
  
     L'indicatore è configurato per utilizzare valori predefiniti. Per impostazione predefinita, gli indicatori vengono configurati per utilizzare le percentuali come unità di misura e gli intervalli di percentuale sono distribuiti uniformemente tra i membri dell'indicatore; il valore mostrato dall'indicatore utilizza l'ambito del gruppo più vicino.  
  
### <a name="to-delete-an-indicator-to-a-table-or-matrix"></a>Per eliminare un indicatore in una tabella o in una matrice  
  
1.  Fare clic con il pulsante destro del mouse sull'indicatore da eliminare e scegliere **Elimina**.  
  
    > [!NOTE]  
    >  È probabile che un indicatore sia posizionato in un pannello del misuratore che contiene altri indicatori o misuratori. Se i pannelli del misuratore contengono più elementi, assicurarsi di fare clic sull'indicatore da eliminare e non sul pannello del misuratore. Se si fa clic e quindi si elimina il pannello del misuratore, verranno eliminati i pannelli del misuratore e tutti gli elementi in esso contenuti.  
  
2.  Fare clic su **Elimina**.  
  
## <a name="see-also"></a>Vedere anche  
 [Indicatori &#40;Generatore report e SSRS&#41;](indicators-report-builder-and-ssrs.md)  
  
  

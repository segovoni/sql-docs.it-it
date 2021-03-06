---
title: Impostare l'orientamento della casella di testo (Generatore report e SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 64bd53f4-2f31-4732-8c2e-64c7b54b6972
caps.latest.revision: 7
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 5b9a3e2df3b95b6d186c5a68af5f1322e951072b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37205001"
---
# <a name="set-text-box-orientation-report-builder-and-ssrs"></a>Impostare l'orientamento della casella di testo (Generatore report e SSRS)
  Una casella di testo può essere orientata in direzioni diverse: orizzontalmente, verticalmente (testo leggibile dall'alto in basso) o ruotata di 270 gradi (testo leggibile dal basso in alto). Poiché l'orientamento è impostato sulla casella di testo e non sul testo, questa modifica viene applicata a tutto il testo nella casella. Non è possibile specificare orientamenti diversi per parti del testo. Per adattare il testo ruotato ridimensionare manualmente la larghezza della colonna e l'altezza della riga.  
  
 La proprietà WritingMode, che consente di specificare l'orientamento del testo, non è disponibile nel **proprietà casella di testo** nella finestra di dialogo. Per impostarla, è necessario aprire il riquadro Proprietà. Sono valori disponibili per la proprietà WritingMode **orizzontali** (testo leggibile da sinistra a destra), **verticale** (testo lettura dall'alto verso il basso), **Rotate270** (testo leggibile basso verso l'alto). Per adattare il testo è necessario ridimensionare manualmente la larghezza della colonna e l'altezza della riga.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-set-text-orientation"></a>Per impostare l'orientamento del testo  
  
1.  Creare un nuovo report o aprirne uno esistente.  
  
2.  Se il riquadro Proprietà non è aperto, fare clic sulla scheda **Visualizza** e selezionare la casella di controllo **Proprietà** .  
  
3.  Fare clic sulla casella di testo di cui si desidera modificare l'orientamento del testo.  
  
4.  Individuare proprietà nel riquadro proprietà e nell'elenco a discesa selezionare l'orientamento del testo da applicare alla casella di testo WritingMode.  
  
    > [!NOTE]  
    >  Se le proprietà nel riquadro Proprietà sono organizzate in categorie, WritingMode si trova nella categoria **Localizzazione** .  
  
5.  Nella casella di riepilogo selezionare **Horizontal**, **Vertical**o **Rotate270**.  
  
## <a name="see-also"></a>Vedere anche  
 [Le caselle di testo &#40;Report e SSRS&#41;](text-boxes-report-builder-and-ssrs.md)   
 [Esercitazione: Formattazione di testo &#40;Generatore report&#41;](../tutorial-format-text-report-builder.md)  
  
  

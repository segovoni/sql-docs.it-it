---
title: Creare e gestire gerarchie | Documenti Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c9282c3b28ca5998cc21d2906f06d50f862e49a9
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34044835"
---
# <a name="create-and-manage-hierarchies"></a>Creare e gestire gerarchie 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Le gerarchie possono essere create e gestite in Progettazione modelli in Vista diagramma. Per visualizzare Progettazione modelli in Vista diagramma, in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], fare clic sul menu **Modello** , scegliere **Vista modelli**, quindi **Vista diagramma**.  
  
 In questo articolo include le attività seguenti:  
  
-   [Creare una gerarchia](#bkmk_create)  
  
-   [Modificare una gerarchia](#bkmk_edit)  
  
-   [Eliminare una gerarchia](#bkmk_delete)  
  
##  <a name="bkmk_create"></a> Creare una gerarchia  
 È possibile creare una gerarchia utilizzando le colonne e il menu di scelta rapida della tabella. Quando si crea una gerarchia, un nuovo livello padre viene visualizzato con le colonne selezionate come livelli figlio.  
  
#### <a name="to-create-a-hierarchy-from-the-context-menu"></a>Per creare una gerarchia dal menu di scelta rapida  
  
1.  Nella finestra di una tabella di Progettazione modelli (Vista diagramma) fare clic con il pulsante destro del mouse su una colonna, quindi scegliere **Crea gerarchia**.  
  
     Per selezionare più colonne, fare clic su ciascuna colonna, fare clic con il pulsante destro del mouse per aprire il menu di scelta rapida, quindi scegliere **Crea gerarchia**.  
  
     Nella parte inferiore della finestra della tabella viene creato un livello di gerarchia padre e le colonne selezionate vengono copiate nella gerarchia come livelli figlio.  
  
2.  Digitare un nome per la gerarchia.  
  
 È possibile trascinare colonne aggiuntive nel livello padre della gerarchia; tale operazione ne comporta la copia. Rilasciare il livello figlio per posizionarlo nel punto in cui si desidera venga visualizzato nella gerarchia.  
  
> [!NOTE]  
>  Il comando Crea gerarchia sarà disabilitato nel menu di scelta rapida se si effettua una selezione multipla di una misura con una o più colonne oppure se si selezionano colonne da più tabelle.  
  
##  <a name="bkmk_edit"></a> Modificare una gerarchia  
 È possibile rinominare una gerarchia o un livello figlio, modificare l'ordine dei livelli figlio, aggiungere altre colonne come livelli figlio, rimuovere un livello figlio da una gerarchia, mostrare il nome di origine di un livello figlio (il nome della colonna) e nascondere un livello figlio se il suo nome coincide con quello del livello padre della gerarchia.  
  
#### <a name="to-change-the-name-of-a-hierarchy-or-child-level"></a>Per modificare il nome di una gerarchia o di un livello figlio  
  
1.  Fare clic con il pulsante destro del mouse sul livello padre della gerarchia o su un livello figlio, quindi scegliere **Rinomina**.  
  
2.  Digitare un nuovo nome o modificarne uno esistente.  
  
#### <a name="to-change-the-order-of-a-child-level-in-a-hierarchy"></a>Per modificare l'ordine di un livello figlio in una gerarchia  
  
-   Fare clic e trascinare un livello figlio in una nuova posizione all'interno della gerarchia.  
  
-   In alternativa, fare clic con il pulsante destro del mouse su un livello figlio della gerarchia e scegliere Sposta su per spostare in alto il livello nell'elenco oppure Sposta giù per spostarlo in basso.  
  
-   In alternativa, fare clic su un livello figlio per selezionarlo, quindi premere ALT+freccia SU per spostare in alto il livello oppure ALT+freccia GIÙ per spostarlo in basso.  
  
#### <a name="to-add-another-child-level-to-a-hierarchy"></a>Per aggiungere un altro livello figlio a una gerarchia  
  
-   Fare clic e trascinare una colonna nel livello padre o in un percorso specifico della gerarchia. La colonna verrà copiata come livello figlio della gerarchia.  
  
-   In alternativa, fare clic con il pulsante destro del mouse su una colonna, scegliere **Aggiungi a gerarchia**, quindi fare clic sulla gerarchia.  
  
> [!NOTE]  
>  È possibile aggiungere una colonna nascosta dai report come livello figlio alla gerarchia. Il livello figlio non sarà nascosto.  
  
#### <a name="to-remove-a-child-level-from-a-hierarchy"></a>Per rimuovere un livello figlio da una gerarchia  
  
-   Fare clic con il pulsante destro del mouse su un livello figlio, quindi scegliere **Rimuovi da gerarchia**.  
  
-   In alternativa, fare clic su un livello figlio e premere **CANC**.  
  
> [!NOTE]  
>  Se si rinomina un livello figlio della gerarchia, non condividerà più lo stesso nome della colonna da cui è stato copiato. Utilizzare il comando **Mostra nome di origine** per visualizzare la colonna da cui è stato copiato.  
  
#### <a name="to-show-a-source-name"></a>Per mostrare un nome di origine  
  
-   Fare clic con il pulsante destro del mouse su un livello figlio della gerarchia, quindi scegliere **Show Source Name**(Mostra nome di origine). Viene visualizzato il nome della colonna da cui è stato copiato.  
  
##  <a name="bkmk_delete"></a> Eliminare una gerarchia  
  
#### <a name="to-delete-a-hierarchy-and-remove-its-child-levels"></a>Per eliminare una gerarchia e rimuovere i relativi livelli figlio  
  
-   Fare clic con il pulsante destro del mouse sul livello padre della gerarchia, quindi scegliere Elimina gerarchia.  
  
-   In alternativa, fare clic sul livello padre della gerarchia e premere CANC. Verranno rimossi anche tutti i livelli figlio.  
  
## <a name="see-also"></a>Vedere anche  
 [Progettazione di modelli tabulari ](../../analysis-services/tabular-models/tabular-model-designer-ssas.md)   
 [Gerarchie](../../analysis-services/tabular-models/hierarchies-ssas-tabular.md)   
 [Misure](../../analysis-services/tabular-models/measures-ssas-tabular.md)  
  
  

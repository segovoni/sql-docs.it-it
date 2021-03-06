---
title: Impostazione chiave e tipo (Creazione guidata dimensione) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.dimensionkeyandtype.f1
ms.assetid: d7d5db55-36c3-45f6-ade3-29aa516589c1
caps.latest.revision: 22
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 897aa6a576c93776cbefb29cbf80c858a651b229
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37293441"
---
# <a name="specify-dimension-key-and-type-dimension-wizard"></a>Impostazione chiave e tipo della dimensione (Creazione guidata dimensione)
  La pagina **Impostazione chiave e tipo della dimensione** consente di definire l'attributo chiave della dimensione e di indicare se si tratta di una dimensione a modifica lenta.  
  
> [!NOTE]  
>  Questa pagina viene visualizzata solo se si seleziona **Build the dimension without using a data source** (Compila dimensione senza usare un'origine dei dati) nella pagina **Select Build Method** (Selezione metodo di compilazione) e **Dimensione standard** nella pagina **Selezione tipo di dimensione** .  
  
## <a name="options"></a>Opzioni  
 **Attributo chiave**  
 Consente di selezionare l'attributo che costituirà l'attributo chiave per la dimensione.  
  
> [!NOTE]  
>  Se non sono stati definiti attributi per la dimensione, l'unico valore disponibile per questa opzione sarà **Creare automaticamente l'attributo chiave**. Questo valore non è disponibile se sono stati definiti attributi per la dimensione.  
  
 **Si tratta di una dimensione a modifica**  
 Selezionare questa opzione per indicare che si tratta di una dimensione a modifica lenta. Selezionando questa opzione vengono create colonne e attributi aggiuntivi che possono essere utilizzati per tenere traccia di tutti gli spostamenti dei membri tra le gerarchie della dimensione.  
  
## <a name="see-also"></a>Vedere anche  
 [Guida F1 di creazione guidata dimensione](dimension-wizard-f1-help.md)   
 [Dimensioni &#40;Analysis Services - dati multidimensionali&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)   
 [Dimensioni nei modelli multidimensionali](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  

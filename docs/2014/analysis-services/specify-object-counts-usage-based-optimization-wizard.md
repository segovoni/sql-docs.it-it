---
title: Impostazione conteggi oggetti (basata sull'utilizzo di ottimizzazione guidata) | Microsoft Docs
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
- sql12.asvs.storagedesignwizard.calculatingobjectcounts.f1
ms.assetid: 306c7c25-ae24-4852-ab8c-c82f68a4bc1f
caps.latest.revision: 25
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c5578f6ef177a6d4b638dac5fdef947147124e18
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37201881"
---
# <a name="specify-object-counts-usage-based-optimization-wizard"></a>Impostazione conteggi oggetti (Ottimizzazione guidata basata sulle statistiche di utilizzo)
  Utilizzare la pagina **Impostazione conteggi oggetti** per eseguire automaticamente il conteggio degli oggetti nel cubo o per digitare manualmente conteggi stimati. L' Ottimizzazione guidata basata sulle statistiche di utilizzo utilizza i conteggi per valutare i requisiti di archiviazione.  
  
## <a name="options"></a>Opzioni  
 **Oggetti Cube**  
 Consente di valutare le dimensioni e gli attributi nel cubo. Solo gli attributi che non hanno loro `AggregationUsage` impostata nella proprietà di **controlla utilizzo aggregazioni** pagina della procedura guidata vengono visualizzati perché questi sono gli unici attributi che è necessario il conteggio specificato.  
  
 **Conteggio stimato**  
 Viene visualizzato il numero stimato di righe nel gruppo di misure e il numero di membri di attributi stimato nelle dimensioni del database. È possibile digitare un valore da utilizzare come conteggio stimato o è possibile calcolare i totali stimati. Per calcolare il totale, digitare 0 nel campo e quindi fare clic su **Conta**. I campi che presentano già un conteggio non vengono aggiornati.  
  
 **Numero di partizioni**  
 (Facoltativo) Digitare il numero stimato di righe nel gruppo di misure e il numero di membri di attributi stimato nelle dimensioni del database.  
  
 **Count**  
 Consente di calcolare e di ripopolare i valori nella colonna **Conteggio stimato** per tutti i campi vuoti. I campi che presentano già un conteggio non vengono aggiornati.  
  
## <a name="see-also"></a>Vedere anche  
 [Guida F1 guidata di progettazione delle aggregazioni](aggregation-design-wizard-f1-help.md)   
 [Procedure guidate di Analysis Services &#40;dati multidimensionali&#41;](analysis-services-wizards-multidimensional-data.md)  
  
  

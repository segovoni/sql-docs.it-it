---
title: Report concetto dei parametri (Generatore Report e SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b0aa2159-4e49-4713-8824-5ef9a9edbc62
caps.latest.revision: 8
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 860099dc49e0fe383d7b53ac379c4671ead2477b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37296061"
---
# <a name="report-parameters-concept-report-builder-and-ssrs"></a>Concetto dei parametri di report (Generatore report e SSRS)
  È possibile aggiungere parametri a un report per collegare report correlati, controllare l'aspetto del report, filtrare i dati del report o per limitare l'ambito di un report a percorsi o utenti specifici.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 I parametri di report vengono creati nei modi seguenti:  
  
-   Automaticamente, quando si definisce la query del set di dati contenente le variabili di query. Per ogni variabile di query, vengono creati un parametro del report e un parametro di query del set di dati con lo stesso nome. Un parametro di query può essere un riferimento a una variabile do query o a un parametro di input per una stored procedure.  
  
-   Automaticamente, quando si aggiunge un riferimento a un set di dati condiviso contenente parametri di query.  
  
-   Manualmente, quando si creano parametri del report nel riquadro dei dati del report. I parametri rappresentano una delle raccolte predefinite che è possibile includere in un'espressione di un report. Poiché le espressioni sono usate per definire valori nell'intera definizione di un report, è possibile usare i parametri per controllare l'aspetto del report o per passare i valori ai sottoreport o report correlati che usano anch'essi i parametri.  
  
 Per altre informazioni, vedere [Report Parameters &#40;Report Builder and Report Designer&#41;](report-parameters-report-builder-and-report-designer.md).  
  
 I parametri sono usati di frequente per filtrare i dati del report sia prima che dopo la restituzione dei dati al report. Per altre informazioni, vedere [Filtrare, raggruppare e ordinare i dati &#40;Generatore report e SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md).  
  
 Quando si progetta un report, i parametri corrispondenti vengono salvati nella definizione del report. Quando si pubblica un report, i parametri corrispondenti vengono salvati e gestiti separatamente della definizione del report. Una volta salvato il report nel server di report, è possibile eseguire le operazioni seguenti:  
  
-   Modificare i valori dei parametri del report direttamente nel server di report indipendentemente dalla definizione del report.  
  
-   Creare più report collegati in cui ogni report collegato è un collegamento alla definizione del report con un set di valori di parametro separato che può essere gestito indipendentemente nel server di report.  
  
 Se si intende creare snapshot, cronologie o sottoscrizioni di report in un report pubblicato, è necessario capire come i parametri del report influiscono sui requisiti di progettazione per il report.  
  
## <a name="see-also"></a>Vedere anche  
 [Concetti relativi alla creazione di report &#40;Report e SSRS&#41;](report-authoring-concepts-report-builder-and-ssrs.md)   
 [Set di dati condivisi e incorporati del report &#40;Generatore report e SSRS&#41;](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [Esercitazione: Aggiungere un parametro al Report &#40;Generatore Report&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md)  
  
  

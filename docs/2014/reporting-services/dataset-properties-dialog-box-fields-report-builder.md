---
title: Finestra di dialogo Proprietà set di dati, campi (Generatore Report) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- "10021"
ms.assetid: 75c7e54a-3d20-4c9a-88da-ab36dce2ce42
caps.latest.revision: 14
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: cffc9683eacab63c3c8175406ba8ba724cf0ccce
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37262247"
---
# <a name="dataset-properties-dialog-box-fields-report-builder"></a>Finestra di dialogo Proprietà set di dati, Campi (Generatore report)
  Selezionare **Campi** nella finestra di dialogo **Proprietà set di dati** per modificare la raccolta di campi per il set di dati del report. L'elenco dei campi viene generato automaticamente, tuttavia è possibile usare la scheda **Campi** per aggiungere, modificare ed eliminare campi di query e calcolati.  
  
 I campi calcolati sono supportati solo nei set di dati incorporati. Per altre informazioni, vedere [Set di dati condivisi e incorporati del report &#40;Generatore report e SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).  
  
## <a name="options"></a>Opzioni  
 **Aggiungi**  
 Consente di aggiungere un nuovo campo di query o calcolato al set di dati.  
  
 **Elimina**  
 Consente di eliminare il campo selezionato dal set di dati.  
  
 **Nome del campo**  
 Consente di digitare un nome per il campo. Il campo deve essere univoco nel set di dati. Per ogni campo esistente nel set di dati, il nome viene prepopolato.  
  
 **Origine campo**  
 Immettere un valore per il campo.  
  
 Per un campo calcolato, l'origine del campo deve essere il nome di un campo esistente recuperato dalla query del set di dati o da un'espressione creata. Ad esempio, per creare un campo che rappresenta 10 volte il valore nel campo Sales della query, utilizzare l'espressione `=10 * Fields!Sales.Value`.  
  
 Per un campo query, l'origine del campo deve essere il nome di un campo esistente recuperato dalla query del set di dati.  
  
 **Espressione (fx)**  
 Consente di aggiungere o modificare un'espressione per il nuovo campo calcolato. Questo pulsante viene visualizzato solo quando si fa clic su **Aggiungi** e si seleziona **Campo calcolato**.  
  
## <a name="see-also"></a>Vedere anche  
 [Raccolta di campi del set di dati &#40;Generatore report e SSRS&#41;](report-data/dataset-fields-collection-report-builder-and-ssrs.md)   
 [Creare un set di dati condiviso o un set di dati incorporato &#40;Generatore report e SSRS&#41;](report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)   
 [Guida di Generatore report per finestre di dialogo, riquadri e procedure guidate](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [Finestra di dialogo Proprietà set di dati, le opzioni &#40;Generatore Report&#41;](report-data/dataset-properties-dialog-box-options-report-builder.md)   
 [Finestra di dialogo Proprietà set di dati, filtri &#40;Generatore Report&#41;](../../2014/reporting-services/dataset-properties-dialog-box-filters-report-builder.md)   
 [Finestra di dialogo Proprietà set di dati, i parametri &#40;Generatore Report&#41;](../../2014/reporting-services/dataset-properties-dialog-box-parameters-report-builder.md)   
 [Finestra di dialogo Proprietà set di dati, la Query &#40;Generatore Report&#41;](report-data/dataset-properties-dialog-box-query-report-builder.md)   
 [Espressioni &#40;Generatore report e SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md)   
 [Connessioni dati, origini dati e stringhe di connessione in Generatore report](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-report-builder.md)  
  
  

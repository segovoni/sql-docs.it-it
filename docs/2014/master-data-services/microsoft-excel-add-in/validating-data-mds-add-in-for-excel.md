---
title: Convalida dei dati (componente aggiuntivo MDS per Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 71eda98f-01a4-4fff-8246-be3133782523
caps.latest.revision: 6
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: f2da7f9179f86b148d1f195121372ff9def985db
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37158852"
---
# <a name="validating-data-mds-add-in-for-excel"></a>Convalida dei dati (componente aggiuntivo MDS per Excel)
  Nel [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]quando si pubblicano i dati, vengono eseguiti due tipi di convalida:  
  
-   Tutte le regole business definite sono applicate ai dati.  
  
-   I dati vengono controllati in base ai valori di attributo consentiti (ad esempio il numero di caratteri o il tipo di dati).  
  
 In ogni caso, i dati validi vengono pubblicati nel repository MDS. I dati non validi vengono evidenziati e i dettagli dell'errore possono essere visualizzati nelle colonne di stato.  
  
## <a name="when-validation-occurs"></a>Esecuzione della convalida  
 Nel [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], la convalida viene eseguita quando si pubblicano dati nuovi o modificati oppure quando si applicano manualmente regole business.  
  
 Quando le regole business hanno esito negativo, i dati vengono comunque pubblicati nel repository MDS. Quando la convalida dell'input ha esito negativo, i dati non vengono pubblicati nel repository.  
  
## <a name="validation-statuses"></a>Stati di convalida  
 Nel [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]sono possibili gli stati di convalida seguenti.  
  
|Stato|Description|  
|------------|-----------------|  
|Errore|Si è verificato un errore di convalida di uno o più valori nella riga in base alle regole business definite da un amministratore di MDS.|  
|Non convalidato|I valori nella riga non sono ancora stati convalidati in base alle regole business.|  
|Esito positivo|Tutti i valori nella riga sono stati convalidati in base alle regole business.|  
  
## <a name="input-statuses"></a>Stati di input  
 Nel [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]sono possibili gli stati di input seguenti  
  
|Stato|Description|  
|------------|-----------------|  
|Errore|Uno o più valori nella riga non soddisfano i requisiti di sistema, come la lunghezza o il tipo di dati. Il valore non è aggiornato nel repository MDS.|  
|Nuova riga|I valori nella riga non sono ancora stati pubblicati nel repository MDS.|  
|Read Only|L'utente che ha eseguito l'accesso dispone di autorizzazioni di sola lettura per uno o più valori nella riga e non è possibile aggiornare il valore o i valori.|  
|Non modificato|Nessun valore nella riga è stato modificato nel foglio di lavoro. Ciò non significa che i valori nel repository non sono stati modificati. Per ottenere i dati più recenti nel foglio, fare clic su **Carica o aggiorna** nel gruppo **Connetti e carica**.<br /><br /> Questa è l'impostazione predefinita per ogni riga.|  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Descrizione dell'attività|Argomento|  
|----------------------|-----------|  
|Determinare quali valori non passano le regole business definite.|[Applicare le regole di Business &#40;componente aggiuntivo MDS per Excel&#41;](apply-business-rules-mds-add-in-for-excel.md)|  
|Per correggere gli errori di convalida, visualizzare tutte le transazioni eseguite per un membro.|[Visualizzare tutte le annotazioni o transazioni per un membro &#40;componente aggiuntivo MDS per Excel&#41;](view-all-annotations-or-transactions-for-a-member-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a>Contenuto correlato  
  
-   [Pubblicazione di dati &#40;componente aggiuntivo MDS per Excel&#41;](overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
  

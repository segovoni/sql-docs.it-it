---
title: Finestra di dialogo Proprietà assembly (Analysis Services - dati multidimensionali) | Microsoft Docs
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
- sql12.asvs.sqlserverstudio.assemblyproperties.f1
ms.assetid: da1174d6-d82b-4337-ac19-7368dbd95a84
caps.latest.revision: 19
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 20a5837b112106952e649bc25fcda5a3d93ab3fa
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37192581"
---
# <a name="assembly-properties-dialog-box-analysis-services---multidimensional-data"></a>Finestra di dialogo Proprietà assembly (Analysis Services - Dati multidimensionali)
  Utilizzare la finestra di dialogo **Proprietà assembly** in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] per impostare le proprietà di un riferimento ad assembly in un database di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . È possibile visualizzare la finestra di dialogo **Proprietà assembly** facendo clic con il pulsante destro del mouse su un assembly in **Esplora oggetti** e scegliendo **Proprietà**.  
  
## <a name="options"></a>Opzioni  
  
|Nome|Definizione|  
|----------|----------------|  
|**Nome**|Consente di modificare il nome del riferimento a un assembly.<br /><br /> Nota: cambiando questo valore non si modifica il nome dell'assembly definito nel riferimento, ma il nome usato dall'istanza o dal database di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] per indicare il riferimento all'assembly.|  
|**ID**|Consente di visualizzare l'ID dell'assembly a cui si riferisce il riferimento a un assembly.|  
|**Descrizione**|Consente di modificare la descrizione del riferimento a un assembly.|  
|**Timestamp creazione**|Consente di visualizzare la data e l'ora di creazione del riferimento a un assembly.|  
|**Ultimo aggiornamento schema**|Consente di visualizzare la data e l'ora dell'ultimo aggiornamento ai metadati per il riferimento a un assembly.|  
|**Tipo**|Consente di visualizzare il tipo del riferimento a un assembly. Vengono visualizzati i valori seguenti:<br /><br /> **Assembly .NET**: il riferimento all'assembly fa riferimento a un [!INCLUDE[msCoName](../includes/msconame-md.md)] assembly .NET Framework.<br /><br /> **DLL COM**: il riferimento all'assembly fa riferimento a una libreria COM.|  
|**Origine**|Consente di visualizzare l'origine del riferimento a un assembly. Questa proprietà in genere contiene il percorso completo e il nome file di assembly a cui si riferisce il riferimento a un assembly.|  
|**Set di autorizzazioni**|Consente di selezionare il set di autorizzazioni utilizzato per determinare l'accesso al riferimento a un assembly. Per altre informazioni sui valori disponibili per questa proprietà, vedere <xref:Microsoft.AnalysisServices.ClrAssembly.PermissionSet%2A>.|  
|**Impostazioni di rappresentazione**|Consente di selezionare le impostazioni di rappresentazione da utilizzare per l'accesso al riferimento a un assembly. Per altre informazioni sui valori disponibili per questa proprietà, vedere [Elemento ImpersonationInfo &#40;ASSL&#41;](scripting/properties/impersonationinfo-element-assl.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Finestre di progettazione e finestre di dialogo di Analysis Services &#40;dati multidimensionali&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Gestione di assembly di modelli multidimensionali](multidimensional-models/multidimensional-model-assemblies-management.md)  
  
  

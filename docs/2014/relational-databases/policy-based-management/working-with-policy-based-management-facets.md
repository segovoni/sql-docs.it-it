---
title: Usare la copia di facet della gestione basata su criteri | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- viewing Policy-Based Management facets
- facets [Policy-Based Management], copying
- facets [Policy-Based Management], viewing
- copying Policy-Based Management facets
ms.assetid: 88d025c4-07c2-4e4d-8634-204249a8c82c
caps.latest.revision: 29
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 8b2b7217faed4a594c83a7eca6927a24733ac353
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37272597"
---
# <a name="working-with-policy-based-management-facets"></a>Utilizzo della copia di facet della gestione basata su criteri
  Un facet di gestione basata su criteri è un set di proprietà logiche correlate a un'area di interesse di gestione. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ha diversi facet predefiniti. Il facet di gestione della superficie di attacco, ad esempio, definisce come proprietà le funzionalità disabilitate per impostazione predefinita.  
  
 Quando si gestiscono molti ambienti [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] simili, è possibile configurare un facet in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], copiare lo stato del facet in un file, quindi importare il file come criteri in un'altra istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Una volta convertito lo stato in criteri, è possibile applicare i criteri ad altre istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], nonché ad altri oggetti delle istanze, database o oggetti di database.  
  
 In questo argomento viene descritto come copiare lo stato di un facet in un file XML.  
  
##  <a name="BeforeYouBegin"></a> Autorizzazioni  
 Le procedure descritte in questo argomento richiedono l'appartenenza al ruolo PolicyAdministratorRole nel database msdb.  
  
## <a name="viewing-and-copying-facet-states"></a>Visualizzazione e copia di stati di un facet  
 [Visualizzare i facet della gestione basata su criteri in un oggetto di SQL Server](view-the-policy-based-management-facets-on-a-sql-server-object.md)  
  
 [Copiare lo stato di un facet della gestione basata su criteri in un file XML](copy-a-policy-based-management-facet-state-to-an-xml-file.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Amministrazione di server tramite la gestione basata su criteri](administer-servers-by-using-policy-based-management.md)  
  
  

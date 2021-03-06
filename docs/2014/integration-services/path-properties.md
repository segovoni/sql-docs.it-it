---
title: Le proprietà del percorso | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- paths [Integration Services], properties
ms.assetid: 89b1e347-9579-4f6b-af74-c6519ea08eea
caps.latest.revision: 25
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 9d5917edcf5038028075d0f71b70a8e90acc53d7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37285427"
---
# <a name="path-properties"></a>Proprietà del percorso
  Gli oggetti del flusso di dati nel modello a oggetti [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] hanno proprietà comuni e proprietà personalizzate a livello di componente, input e output, colonne di input e colonne di output. Molte proprietà hanno valori di sola lettura assegnati in fase di esecuzione dal motore del flusso di dati.  
  
 In questo argomento vengono elencate e descritte le proprietà personalizzate dei percorsi che connettono gli oggetti del flusso di dati.  
  
## <a name="path-properties"></a>Proprietà del percorso  
 Nel modello a oggetti [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] un percorso che connette componenti nel flusso di dati implementa l'interfaccia <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100>.  
  
 Nella tabella seguente vengono descritte le proprietà configurabili dei percorsi in un flusso di dati. Inoltre, il motore del flusso di dati assegna valori a proprietà di sola lettura aggiuntive che non sono elencate qui.  
  
|Nome proprietà|Tipo di dati|Description|  
|-------------------|---------------|-----------------|  
|PathAnnotation|Integer (enumerazione)|Un valore che indica se un'annotazione deve essere visualizzata con il percorso sulla superficie dell'area di progettazione. I valori possibili sono `AsNeeded`, `SourceName`, `PathName`, e `Never`. Il valore predefinito è `AsNeeded`.|  
|DestinationName|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100>|L'input associato al percorso.|  
|SourceName|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100>|L'output associato al percorso.|  
  
## <a name="see-also"></a>Vedere anche  
 [Percorsi in Integration Services](data-flow/integration-services-paths.md)   
 [Proprietà comuni](../../2014/integration-services/common-properties.md)   
 [Proprietà personalizzate della trasformazione](data-flow/transformations/transformation-custom-properties.md)   
 [Proprietà del flusso di dati che è possibile impostare tramite espressioni](../../2014/integration-services/data-flow-properties-that-can-be-set-by-using-expressions.md)  
  
  

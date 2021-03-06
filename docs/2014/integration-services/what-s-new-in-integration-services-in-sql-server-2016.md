---
title: Cosa&#39;s nuovo (Integration Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Integration Services, what's new
- what's new [Integration Services]
ms.assetid: da6999c7-e5e3-4a59-a284-1da635995af1
caps.latest.revision: 112
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 39b6e64dbf6add0b026e384432059875cf724507
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37221681"
---
# <a name="what39s-new-integration-services"></a>Cosa&#39;s nuovo (Integration Services)
  [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] è invariato dalla versione precedente.  
  
 Per informazioni su altri [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] prodotti e tecnologie, vedere [What ' s New in SQL Server 2014](../sql-server/what-s-new-in-sql-server-2016.md).  
  
 Per altre informazioni sulle modifiche relative al [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Business Intelligence, vedere [What ' s New in Analysis Services e Business Intelligence](../analysis-services/what-s-new-in-analysis-services.md).  
  
##  <a name="ValidateXML"></a> Output di convalida XML avanzato in Attività XML  
 Convalidare i documenti XML e ottenere output avanzato degli errori abilitando la `ValidationDetails` proprietà dell'attività XML. Prima di `ValidationDetails` proprietà è disponibile, convalida di XML da parte dell'attività XML restituiva solo un risultato true o false, senza informazioni sugli errori o le relative posizioni sulle. A questo punto, quando si imposta `ValidationDetails` su true, l'output file contiene informazioni dettagliate su ogni errore, inclusi il numero di riga e la posizione. È possibile usare questa informazione per comprendere, individuare e risolvere gli errori nei documenti XML. Per ulteriori informazioni, vedere [Validate XML with the XML Task](control-flow/xml-task.md).  
  
 [!INCLUDE[ssIS](../includes/ssis-md.md)] introdotto il `ValidationDetails` proprietà [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Service Pack 2. Questa nuova proprietà non è stata annunciata o documentata in quel momento. Il `ValidationDetails` proprietà è anche disponibile in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] e in SQL Server 2016.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzionalità supportate dalle edizioni di SQL Server 2014](../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
  
  

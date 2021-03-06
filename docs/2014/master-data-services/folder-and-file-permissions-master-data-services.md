---
title: Autorizzazioni per file e cartelle (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- security [Master Data Services], file and folder
- folders [Master Data Services]
- files [Master Data Services]
ms.assetid: 6402d81d-7349-47b1-95ca-99b0c0f4f373
caps.latest.revision: 7
author: leolimsft
ms.author: lle
manager: craigg
robots: noindex,nofollow
ms.openlocfilehash: 1cee48c465b95598f4bdbcca6f22df2cf623945d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37318771"
---
# <a name="folder-and-file-permissions-master-data-services"></a>Autorizzazioni per file e cartelle [Master Data Services]
  Quando si installa [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], cartelle e file vengono installati nel file system nel percorso di installazione specificato per le funzionalità condivise di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Se si usa il percorso di installazione predefinito per [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] funzionalità condivise, il percorso di installazione per [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] viene *unità*: \Programmi\Microsoft SQL Server\120\Master Data Services. Sebbene sia possibile modificare il percorso di installazione delle funzionalità condivise, è necessario considerare le autorizzazioni ereditate dalla cartella padre e quelle impostate in modo esplicito per [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].  
  
## <a name="inherited-permissions"></a>Autorizzazioni ereditate  
 Le autorizzazioni della cartella di **Microsoft SQL Server** , della cartella di **Master Data Services** e della maggior parte delle sottocartelle e dei file sono ereditate dalla cartella padre specificata nel programma di installazione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Se si sceglie il percorso di installazione predefinito, la cartella padre dalla quale vengono ereditate le autorizzazioni è *unità*:\Programmi. Nella tabella seguente vengono descritte le autorizzazioni predefinite per la cartella **Programmi**.  
  
> [!NOTE]  
>  Se si modificano le autorizzazioni predefinite di **Programmi**o si sceglie un percorso di installazione diverso, le autorizzazioni di cartelle e file di [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] vengono ereditate dalla relativa cartella padre e possono essere diverse rispetto a quelle descritte nella tabella seguente.  
  
###### <a name="program-files-default-permissions"></a>Autorizzazioni predefinite di Programmi  
  
|Nome di gruppo o di account|Autorizzazioni|  
|---------------------------|-----------------|  
|CREATOR OWNER|Autorizzazioni speciali|  
|SYSTEM|Autorizzazioni speciali|  
|Administrators|Autorizzazioni speciali|  
|Utenti|Lettura ed esecuzione, Visualizzazione contenuto cartella, Lettura|  
|TrustedInstaller|Visualizzazione contenuto cartella, Autorizzazioni speciali|  
  
## <a name="explicit-permissions"></a>Autorizzazioni esplicite  
 La cartella **MDSTempDir** e il file Web.config di [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] (nella cartella **WebApplication** ) non ereditano autorizzazioni. Le autorizzazioni di cui dispongono sono impostate in modo esplicito quando si installa [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], indipendentemente dal percorso di installazione scelto. Non modificare queste autorizzazioni.  
  
###### <a name="mdstempdir-permissions"></a>Autorizzazioni di MDSTempDir  
  
|Nome di gruppo o di account|Autorizzazioni|  
|---------------------------|-----------------|  
|SYSTEM|Modifica, Lettura ed esecuzione, Visualizzazione contenuto cartella, Lettura, Scrittura|  
|Administrators|Modifica, Lettura ed esecuzione, Visualizzazione contenuto cartella, Lettura, Scrittura|  
|MDS_ServiceAccounts|Modifica, Lettura ed esecuzione, Visualizzazione contenuto cartella, Lettura, Scrittura|  
  
###### <a name="webconfig-permissions"></a>Autorizzazioni di Web.config  
  
|Nome di gruppo o di account|Autorizzazioni|  
|---------------------------|-----------------|  
|SYSTEM|Controllo completo, Modifica, Lettura ed esecuzione, Lettura, Scrittura|  
|Administrators|Controllo completo, Modifica, Lettura ed esecuzione, Lettura, Scrittura|  
|MDS_ServiceAccounts|Lettura ed esecuzione, Lettura|  
  
 Per altre informazioni sul contenuto del file Web.config di [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], vedere [Guida di riferimento alla configurazione Web &#40;Master Data Services&#41;](web-configuration-reference-master-data-services.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Installazione di Master Data Services](install-windows/install-master-data-services.md)  
  
  

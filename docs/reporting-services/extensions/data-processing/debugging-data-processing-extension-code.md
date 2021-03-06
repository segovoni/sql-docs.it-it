---
title: Debug del codice di un'estensione per l'elaborazione dati | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.component: extensions
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- debugging data processing extensions [Reporting Services]
- troubleshooting [Reporting Services], data processing extensions
- data processing extensions [Reporting Services], debugging
ms.assetid: e963e205-9ae0-446d-97df-028a1d2727d9
caps.latest.revision: 40
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 2fb83b02372a5ecb7313185f18d841884ffab775
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33014778"
---
# <a name="debugging-data-processing-extension-code"></a>Debug del codice di un'estensione per l'elaborazione dati
  In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] sono disponibili diversi strumenti di debug che consentono di analizzare il codice delle estensioni per l'elaborazione dati e di individuare gli errori. Gli strumenti più appropriati da utilizzare variano in base alla finalità desiderata. In questo esempio viene utilizzato [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)].  
  
#### <a name="to-debug-your-data-processing-extension-code"></a>Per eseguire il debug del codice di un'estensione per l'elaborazione dati  
  
1.  Avviare [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)] e aprire il progetto di estensione per l'elaborazione dati.  
  
2.  Compilare il progetto e distribuire l'assembly di estensioni per l'elaborazione dati e il file con estensione pdb associato in Gestione report. Per altre informazioni sulla distribuzione, vedere [Procedura: Distribuire un'estensione per l'elaborazione dati in Progettazione report](../../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension-to-report-designer.md).  
  
3.  Aprire un nuovo progetto report in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] lasciando aperto il codice dell'estensione per l'elaborazione dati in una finestra separata di [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
4.  Passare alla finestra di [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] che contiene il progetto di estensione per l'elaborazione dati e impostare alcuni punti di interruzione nel codice.  
  
5.  Con la finestra del progetto di estensione per l'elaborazione dati ancora attiva, scegliere **Connetti a processo** dal menu **Debug**.  
  
     Verrà visualizzata la finestra di dialogo **Connetti a processo**.  
  
6.  Nell'elenco di processi selezionare il processo devenv.exe che corrisponde al progetto report e fare clic su **Connetti**.  
  
7.  Definire l'origine dati del report usando la scheda **Dati report** del progetto report. In genere, si utilizza lo strumento generico Progettazione query per eseguire una query sull'origine dati personalizzata. In questo modo, è possibile richiamare il debugger ed eseguire il codice in corrispondenza dei punti di interruzione.  
  
8.  Esaminare il codice istruzione per istruzione premendo F11 Per ulteriori informazioni sull'utilizzo di [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] per eseguire il debug, vedere la documentazione di [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuzione di un'estensione per l'elaborazione dati](../../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension.md)   
 [Estensioni di Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Implementazione di un'estensione per l'elaborazione dati](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Libreria di estensioni di Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  

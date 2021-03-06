---
title: Riferimento della libreria del provider WMI Reporting Services (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: wmi-provider-library-reference
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- Reporting Services WMI Provider Library
apilocation:
- reportingservices.mof
helpviewer_keywords:
- WMI provider [Reporting Services], library
ms.assetid: 17ba711d-7eff-4423-9168-63dc425a3428
caps.latest.revision: 42
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 40642994242462f31e48b9eee234e511824467d0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33031118"
---
# <a name="reporting-services-wmi-provider-library-reference-ssrs"></a>Riferimento della libreria del provider WMI Reporting Services (SSRS)
  Il provider WMI (Windows Management Instrumentation) di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] supporta operazioni WMI che consentono di scrivere script e codice per modificare le impostazioni del server di report e di Gestione report.  
  
 Ad esempio, se si vuole modificare l'impostazione relativa all'uso della sicurezza integrata quando il server di report si connette al database del server di report, creare un'istanza della classe MSReportServer_ConfigurationSetting e usare la proprietà DatabaseIntegratedSecurity dell'istanza del server di report. Le classi mostrate nella tabella seguente rappresentano i componenti di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Le classi sono definite negli spazi dei nomi [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)] o [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)] . Ognuna delle classi supporta operazioni di lettura e scrittura. Le operazioni di creazione non sono supportate.  
  
## <a name="classes"></a>Classi  
 [Classe MSReportServer_Instance](../../reporting-services/wmi-provider-library-reference/msreportserver-instance-class.md)  
 Fornisce le informazioni di base necessarie affinché un client si connetta a un server di report installato.  
  
 [Classe MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
 Rappresenta i parametri di installazione e di runtime di un'istanza del server di report. Tali parametri sono archiviati nel file di configurazione per il server di report.  
  
 Per altre informazioni sulle operazioni WMI, vedere la documentazione di WMI SDK inclusa in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK.  
  
## <a name="see-also"></a>Vedere anche  
 [Accedere al provider WMI per Reporting Services](../../reporting-services/tools/access-the-reporting-services-wmi-provider.md)   
 [Riferimento tecnico &#40;SSRS&#41;](../../reporting-services/technical-reference-ssrs.md)  
  
  

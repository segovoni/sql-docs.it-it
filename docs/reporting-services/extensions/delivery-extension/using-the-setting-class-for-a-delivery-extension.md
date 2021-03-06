---
title: Using the Setting Class for a Delivery Extension (Uso della classe Setting per un'estensione per il recapito) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
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
- delivery extensions [Reporting Services], settings
- Setting class
ms.assetid: 50746639-da7c-46a5-ac7b-e87dd6b91880
caps.latest.revision: 32
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 5d74af9c4f9c1b5f9ddfd1504ad200f5d6ffa49b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33017318"
---
# <a name="using-the-setting-class-for-a-delivery-extension"></a>Utilizzo della classe Setting per un'estensione per il recapito
  La classe <xref:Microsoft.ReportingServices.Interfaces.Setting> si trova nello spazio dei nomi <xref:Microsoft.ReportingServices.Interfaces> e rappresenta le informazioni sulle impostazioni dell'estensione per un'estensione per il recapito. La classe <xref:Microsoft.ReportingServices.Interfaces.Setting> fornisce l'infrastruttura per l'archiviazione delle informazioni relative alle impostazioni necessarie per il corretto funzionamento di un'estensione per il recapito. Per il recapito tramite posta elettronica in un server report, ad esempio, a un utente viene richiesto di fornire le impostazioni specifiche del recapito tramite posta elettronica, come l'indirizzo del destinatario, l'indirizzo del mittente, la riga dell'oggetto del messaggio di posta elettronica e altro ancora. Anche i provider di recapito personalizzati richiederanno senza dubbio che l'utente fornisca impostazioni specifiche per consentire il recapito di notifiche e report da parte dell'estensione per il recapito.  
  
 La classe <xref:Microsoft.ReportingServices.Interfaces.Setting> viene utilizzata nell'implementazione della proprietà <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ExtensionSettings%2A> dell'interfaccia <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension>. La classe <xref:Microsoft.ReportingServices.Interfaces.Setting> viene inoltre utilizzata per l'elaborazione dei dati di impostazione delle estensioni forniti da un utente quando viene creata una sottoscrizione o una notifica.  
  
 Per un esempio su come usare la classe <xref:Microsoft.ReportingServices.Interfaces.Setting>, vedere [ Esempi del prodotto Reporting Services](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>Vedere anche  
 [Implementazione di un'estensione per il recapito](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Libreria di estensioni di Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  

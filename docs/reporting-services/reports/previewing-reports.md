---
title: Anteprima dei report | Microsoft Docs
ms.custom: ''
ms.date: 05/05/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: reports
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Report Designer [Reporting Services], previewing reports
- previewing reports [Reporting Services]
- printing previews
- test servers [Reporting Services]
ms.assetid: 85117f6c-828e-45c9-810f-e700d9bfba67
caps.latest.revision: 44
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 2cdd46a01c2151a828d58f851e3a4bdcb02e7483
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33028728"
---
# <a name="previewing-reports"></a>Anteprima dei report
  Durante la progettazione di un report di     [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , potrebbe essere necessario visualizzarlo prima di pubblicarlo in un ambiente di produzione. Tale operazione può essere eseguita passando alla modalità di anteprima in Progettazione report, utilizzando la finestra di anteprima in Progettazione report e pubblicando il report in un server di report in un ambiente di prova.  
  
> [!NOTE]  
>  Quando un report viene visualizzato in anteprima, i dati per il report vengono memorizzati nella cache in un file nel computer locale. Quando lo stesso report viene visualizzato di nuovo in anteprima utilizzando la stessa query, gli stessi parametri e le stesse credenziali, in Progettazione report viene recuperata la copia memorizzata nella cache anziché rieseguire la query. Il file di dati viene salvato come *\<nomereport>*.rdl.data nella stessa directory del file di definizione del report. e non viene eliminato alla chiusura di Progettazione report.  
  
## <a name="preview-mode"></a>Modalità di anteprima  
 È possibile fare clic su ![ssrs_ssdt_preview](../../reporting-services/media/ssrs-ssdt-preview.png "ssrs_ssdt_preview") per visualizzare un report in anteprima in Progettazione report. Il report verrà eseguito localmente, utilizzando le stesse funzionalità di elaborazione e rendering del report offerte dal server di report. Il report visualizzato è un'immagine interattiva. È quindi possibile selezionare parametri, fare clic sui collegamenti, visualizzare la mappa documento ed espandere e comprimere le aree nascoste del report. È inoltre possibile esportare il report in uno dei formati di rendering installati.  
  
## <a name="standalone-preview"></a>Anteprima autonoma  
 Per visualizzare in anteprima un report è possibile inoltre eseguire il progetto report in una configurazione per il debug, ad esempio per eseguire il debug degli assembly personalizzati scritti. Il report viene aperto nel browser predefinito. Per eseguire un progetto sono disponibili tre modi:  
  
-   Fare clic su **Avvia debug** dal menu **Debug** .  
  
-   Facendo clic sul pulsante **Avvia** sulla [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] barra degli strumenti standard ![ssrs_ssdt_startdebug](../../reporting-services/reports/media/ssrs-ssdt-startdebug.png "ssrs_ssdt_startdebug").  
  
-   Premere **F5**.  
  
 Se si utilizza una configurazione del progetto che compila il report senza distribuirlo, il report specificato nella proprietà **StartItem** della configurazione corrente viene aperto in una finestra di anteprima separata. La visualizzazione e la funzionalità del report nella finestra di anteprima sono uguali a quelle della modalità di anteprima.  
  
> [!NOTE]  
>  Prima di eseguire il debug di un report è necessario impostare un elemento iniziale. Ad esempio, se si esegue la modalità di debug e nel browser viene visualizzata la pagina del server di report principale e non il report desiderato nella modalità di anteprima. Per impostare un elemento iniziale, in Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto report, scegliere **Proprietà**, quindi selezionare il nome del report da visualizzare nella proprietà **StartItem**.  
  
 Se si desidera visualizzare in anteprima un report che non è l'elemento iniziale del progetto, selezionare una configurazione che compili il report senza distribuirlo, ad esempio la configurazione DebugLocal. Fare clic con il pulsante destro del mouse sul report e quindi scegliere **Esegui**. È necessario scegliere una configurazione che non preveda la distribuzione del report. In caso contrario, il report verrà pubblicato nel server di report anziché venire visualizzato in locale in una finestra di anteprima.  
  
## <a name="publishing-to-a-test-server"></a>Pubblicazione in un server di prova  
 È anche possibile testare i report pubblicandoli in un server di prova, passare al report desiderato e visualizzarne l’anteprima. La pubblicazione di un report in un server di prova è analoga alla pubblicazione di un report in un server di produzione. Per informazioni sulla pubblicazione di un report, vedere [Pubblicazione dei report in un server di report](../../reporting-services/reports/publishing-reports-to-a-report-server.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Stampa di report &#40;Generatore report e SSRS&#41;](../../reporting-services/report-builder/print-reports-report-builder-and-ssrs.md)   
 [Stampare un report &#40;Generatore report e SSRS&#41;](../../reporting-services/report-builder/print-a-report-report-builder-and-ssrs.md)   
 [Pubblicazione di report](http://msdn.microsoft.com/library/ef5a514e-e818-4041-a8b0-15835f9a046b)   
 [Uso di assembly personalizzati con i report](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)  
  
  

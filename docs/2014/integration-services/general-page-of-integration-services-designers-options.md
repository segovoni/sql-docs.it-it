---
title: Pagina Generale | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Business_Intelligence_Designers.Data_Transformation_Designers.General
ms.assetid: d695690a-923b-4036-945e-7621e8651deb
caps.latest.revision: 29
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4bc23fd22ec07f78e71713e1cce93d9845c35ccc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37229281"
---
# <a name="general-page"></a>Pagina Generale
  Usare la pagina **Generale** della pagina **Finestre di progettazione Integration Services** della finestra di dialogo **Opzioni** per specificare le opzioni per il caricamento, la visualizzazione e l'aggiornamento dei pacchetti.  
  
 Per aprire la pagina **Generale** , in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]dal menu **Strumenti** scegliere **Opzioni**, espandere **Finestre di progettazione Business Intelligence**e selezionare **Finestre di progettazione Integration Services**.  
  
## <a name="options"></a>Opzioni  
 **Controlla firma digitale al caricamento di un pacchetto**  
 Selezionare questa opzione per fare in modo che [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] controlli la firma digitale al caricamento di un pacchetto. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] controllerà solo se la firma digitale è presente, è valida e proviene da una fonte attendibile. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] non controlla se il pacchetto è stato modificato dopo la firma.  
  
 Se si imposta il valore del Registro di sistema **BlockedSignatureStates** , tale valore ha la priorità sull'opzione **Controlla firma digitale al caricamento di un pacchetto** . Per altre informazioni, vedere [Implementazione di criteri per le firme impostando un valore del Registro di sistema](implement-a-signing-policy-by-setting-a-registry-value.md).  
  
 Per altre informazioni sui certificati e i pacchetti digitali, vedere [Identificazione dell'origine dei pacchetti con firme digitali](security/identify-the-source-of-packages-with-digital-signatures.md).  
  
 **Mostra avviso se il pacchetto non è firmato**  
 Selezionare questa opzione per visualizzare un avviso quando viene caricato un pacchetto non firmato.  
  
 **Mostra etichette vincolo di precedenza**  
 Selezionare l'etichetta (Esito positivo, Esito negativo o Completamento) da visualizzare nei vincoli di precedenza durante la visualizzazione dei pacchetti in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
 **Linguaggio di scripting**  
 Selezionare il linguaggio di scripting predefinito per le nuove attività Script e per i componenti Script.  
  
 **Aggiorna stringhe di connessione per l'uso di nuovi nomi di provider**  
 Quando si aprono o si aggiornano pacchetti di [!INCLUDE[ssISversion2005](../includes/ssisversion2005-md.md)] , aggiornare le stringhe di connessione in modo da usare i nomi dei provider seguenti, per la versione corrente di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]:  
  
-   [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Provider OLE DB  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client  
  
 L'Aggiornamento guidato pacchetti [!INCLUDE[ssIS](../includes/ssis-md.md)] consente di aggiornare solo le stringhe di connessione archiviate nelle gestioni connessione. Non vengono aggiornate le stringhe di connessione costruite dinamicamente utilizzando il linguaggio delle espressioni di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] o il codice in un'attività Script.  
  
 **Crea nuovo ID pacchetto**  
 Durante l'aggiornamento di [!INCLUDE[ssISversion2005](../includes/ssisversion2005-md.md)] , creare nuovi ID pacchetti per le versioni aggiornate dei pacchetti.  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica della sicurezza &#40;Integration Services&#41;](security/security-overview-integration-services.md)   
 [Estensione di pacchetti tramite scripting](extending-packages-scripting/extending-packages-with-scripting.md)  
  
  

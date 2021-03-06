---
title: Impostare o modificare il livello di protezione dei pacchetti | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- passwords [Integration Services]
- packages [Integration Services],security
- security [Integration Services],protection levels
- protection level for packages [Integration Services]
ms.assetid: 904a5580-82ba-4a26-b0c5-d1c989975f61
caps.latest.revision: 10
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 94d29f4e488e68c5fda2549b793a26770480e30a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37201651"
---
# <a name="set-or-change-the-protection-level-of-packages"></a>Impostazione o modifica del livello di protezione dei pacchetti
  Per controllare l'accesso al contenuto dei pacchetti e ai valori sensibili contenuti, ad esempio password, impostare il valore della proprietà `ProtectionLevel`. Per poter compilare il progetto, ai pacchetti contenuti in un progetto deve essere assegnato lo stesso livello di protezione del progetto. Se si modifica l'impostazione della proprietà `ProtectionLevel` nel progetto, è necessario aggiornare manualmente l'impostazione delle proprietà per i pacchetti.  
  
 Per informazioni su come determinare il `ProtectionLevel` le impostazioni appropriate per i pacchetti nelle diverse fasi nel ciclo di vita del pacchetto, vedere [controllo di accesso per dati sensibili nei pacchetti](security/access-control-for-sensitive-data-in-packages.md). Per informazioni generali sulle funzionalità di sicurezza in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], vedere [Panoramica della sicurezza &#40;Integration Services&#41;](security/security-overview-integration-services.md).  
  
 Le procedure descritte in questo argomento viene descritto come usare una [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] o l'utilità della riga di comando dtutil per modificare il `ProtectionLevel` proprietà.  
  
> [!NOTE]  
>  Oltre alle procedure in questo argomento, in genere è possibile impostare o modificare il `ProtectionLevel` proprietà di un pacchetto quando si importa o Esporta il pacchetto. È inoltre possibile modificare la proprietà [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] di un pacchetto quando si utilizza l'importazione e l'esportazione guidata di `ProtectionLevel` per salvare un pacchetto.  
  
### <a name="to-set-or-change-the-protection-level-of-a-package-in-sql-server-data-tools"></a>Per impostare o modificare il livello di protezione di un pacchetto in SQL Server Data Tools  
  
1.  Esaminare i valori disponibili per il `ProtectionLevel` proprietà nell'argomento [impostando il livello di protezione dei pacchetti](security/access-control-for-sensitive-data-in-packages.md)e determinare il valore appropriato per il pacchetto.  
  
2.  In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]aprire il progetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] contenente il pacchetto.  
  
3.  Aprire il pacchetto nella finestra di progettazione [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
4.  Se nella finestra Proprietà non sono riportate le proprietà del pacchetto, fare clic sull'area di progettazione.  
  
5.  Nella finestra Proprietà, nelle **sicurezza** gruppo, selezionare il valore appropriato per il `ProtectionLevel` proprietà.  
  
     Se si seleziona un livello di protezione che richiede una password, immettere la password come valore della proprietà **PackagePassword** .  
  
6.  Per salvare il pacchetto modificato, scegliere **Salva elementi selezionati** dal menu **File** .  
  
### <a name="to-set-or-change-the-protection-level-of-packages-at-the-command-prompt"></a>Per impostare o modificare il livello di protezione dei pacchetti dal prompt dei comandi  
  
1.  Esaminare i valori disponibili per il `ProtectionLevel` proprietà nell'argomento [impostando il livello di protezione dei pacchetti](security/access-control-for-sensitive-data-in-packages.md)e determinare il valore appropriato per il pacchetto.  
  
2.  Controllare i mapping per il `Encrypt` opzione nell'argomento [dtutil Utility](dtutil-utility.md)e determinare il valore intero appropriato da utilizzare come valore dell'oggetto selezionato `ProtectionLevel` proprietà.  
  
3.  Aprire la finestra del prompt dei comandi.  
  
4.  Al prompt dei comandi, passare alla cartella che contiene i pacchetti per il quale si desidera impostare il `ProtectionLevel` proprietà.  
  
     Negli esempi di sintassi illustrati nel passaggio seguente si presuppone che questa cartella sia la cartella corrente.  
  
5.  Impostare o modificare il livello di protezione del pacchetto o dei pacchetti utilizzando un comando simile a quello degli esempi seguenti:  
  
    -   Il comando seguente imposta il `ProtectionLevel` proprietà di un pacchetto singolo nel file system sul livello 2, "Crittografa sensibili con una password", con la password "strongpassword":  
  
         `dtutil.exe /file "C:\Package.dtsx" /encrypt file;"C:\Package.dtsx";2;strongpassword`  
  
    -   Il comando seguente imposta la proprietà `ProtectionLevel` di tutti i pacchetti in una particolare cartella nel file system sul livello 2, "Crittografa tutti i dati sensibili con una password", con la password "strongpassword":  
  
         `for %f in (*.dtsx) do dtutil.exe /file %f /encrypt file;%f;2;strongpassword`  
  
         Se si utilizza un comando simile in un file batch, immettere il segnaposto del file "% f" come "%% f" nel file batch.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilità dtutil](dtutil-utility.md)  
  
  

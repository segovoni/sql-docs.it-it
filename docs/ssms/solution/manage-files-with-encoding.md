---
title: Gestire file con codifica | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-solutions
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- files [SQL Server Management Studio]
- encoding [SQL Server Management Studio]
- files [SQL Server Management Studio], encoding
ms.assetid: 919544c9-59f0-4cc6-bb2a-f1ad671eb74b
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2f04e3569753aa9a2f73f2e1f12cb51c9b20bbe3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33044398"
---
# <a name="manage-files-with-encoding"></a>Gestione di file con codifica
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Per facilitare la visualizzazione del codice in una lingua e in una piattaforma particolari, è possibile associare a un file una particolare codifica dei caratteri.  
  
## <a name="opening-files"></a>Apertura di file  
È possibile scegliere l'editor da utilizzare per modificare il file.  
  
#### <a name="to-open-a-file-with-a-specific-editor"></a>Per aprire un file con un editor specifico  
  
1.  Scegliere **Apri** dal menu **File**e quindi fare clic su **File**.  
  
2.  Nella finestra di dialogo **Apri file** selezionare il nome del file.  
  
3.  Fare clic sulla freccia accanto al pulsante **Apri** e quindi scegliere**Apri con** dal menu visualizzato.  
  
4.  Selezionare un editor dall'elenco **Selezionare un programma dall'elenco** e quindi fare clic su **Apri**. Per aprire il file con una particolare codifica, selezionare un editor che supporti questa funzionalità, ad esempio Editor di query SQL con codifica o Editor XML con codifica.  
  
## <a name="saving-files"></a>Salvataggio di file  
È inoltre possibile salvare il codice con una codifica Unicode o una tabella codici diversa per supportare diverse lingue, ad esempio quelle dell'Europa occidentale o orientale. Per facilitare la visualizzazione del codice nella lingua scelta, è possibile associare a un file una codifica dei caratteri e un tipo di terminazione riga particolari per supportare un dato sistema operativo. Alcuni caratteri, se utilizzati nei nomi di file, possono essere salvati solo con codifica Unicode.  
  
#### <a name="to-save-a-file-with-a-different-encoding-or-line-ending-type"></a>Per salvare un file con una codifica o un tipo di terminazione riga diversi  
  
1.  Scegliere **Apri** dal menu **Salva <filename> File**.  
  
2.  Nella finestra di dialogo **Salva file con nome** espandere il pulsante **Salva** e quindi fare clic su **Salva con codifica**.  
  
3.  Nella finestra di dialogo **Opzioni di salvataggio avanzate** selezionare la codifica desiderata dall'elenco **Codifica** .  
  
4.  Dall'elenco **Terminazioni riga**selezionare il tipo di terminazione riga desiderato.  
  
    > [!NOTE]  
    > Se il file viene salvato con codifica Unicode, è necessario archiviarlo in [!INCLUDE[msCoName](../../includes/msconame_md.md)] Visual SourceSafe come file binario in quanto Visual SourceSafe non supporta l'unione, il confronto e la visualizzazione delle differenze tra i file salvati come Unicode.  
  
Se si utilizza Visual SourceSafe per archiviare i file con ANSI, UTF8 o Unicode, tenere presenti le limitazioni seguenti per ognuno di essi:  
  
-   Nei file ANSI sono ammessi solo i caratteri supportati nella tabella codici corrente, con conseguenti limitazioni per l'uso internazionale.  
  
-   Nei file Unicode non è possibile utilizzare funzionalità di estrazione condivisa, controllo delle differenze o di unione in quanto questi file sono gestiti come file binari. È possibile utilizzare questo formato nei file internazionali.  
  
-   Non è possibile utilizzare in sicurezza file UTF8 con Visual SourceSafe perché durante l'archiviazione, l'estrazione, il controllo delle differenze e l'unione vengono apportate modifiche che causano problemi per gli editor di questo tipo di file.  
  
## <a name="see-also"></a>Vedere anche  
[File per la gestione di soluzioni e progetti](../../ssms/solution/files-that-manage-solutions-and-projects.md)  
[Associazione di estensioni di file a un editor di codice](http://msdn.microsoft.com/en-us/193630f4-93de-4950-8f36-68702531f925)  
  

---
title: Riferimento all'interfaccia utente della finestra di dialogo Aggiungi gestione connessione file | Microsoft Docs
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
- sql12.dts.designer.fileconnection.f1
helpviewer_keywords:
- Add File Connection Manager
ms.assetid: 9370bfb5-5993-4ad8-a9cd-2de53f320f34
caps.latest.revision: 32
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4bb50e21d596340c4d4c5ad9697836df589974ac
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37182708"
---
# <a name="add-file-connection-manager-dialog-box-ui-reference"></a>Riferimento all'interfaccia utente della finestra di dialogo Aggiungi gestione connessione file
  Utilizzare la finestra di dialogo **Aggiungi gestione connessione file** per definire una connessione a un gruppo di file o cartelle.  
  
 Per ulteriori informazioni sulla gestione connessione per più file, vedere [Multiple Files Connection Manager](multiple-files-connection-manager.md).  
  
> [!NOTE]  
>  Le attività predefinite e i componenti del flusso di dati in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] non utilizzano la gestione connessione per più file. È tuttavia possibile utilizzare la gestione connessione nell'attività Script o nel componente di script.  
  
## <a name="options"></a>Opzioni  
 **Tipo di utilizzo**  
 Consente di specificare il tipo di file da utilizzare per la gestione connessione per più file.  
  
|valore|Description|  
|-----------|-----------------|  
|**Creazione file**|La gestione connessione creerà i file.|  
|**File esistenti**|La gestione connessione utilizzerà i file esistenti.|  
|**Creazione cartelle**|La gestione connessione creerà le cartelle.|  
|**Cartelle esistenti**|La gestione connessione utilizzerà le cartelle esistenti.|  
  
 **File/Cartelle**  
 Consente di visualizzare i file o le cartelle aggiunti tramite i pulsanti descritti di seguito.  
  
 **Aggiungi**  
 Consente di aggiungere un file usando la finestra di dialogo **Seleziona file** o di aggiungere una cartella usando la finestra di dialogo **Sfoglia cartella** .  
  
 **Modifica**  
 Consente di selezionare un file o una cartella e quindi di sostituirli con un file o una cartella differente usando la finestra di dialogo **Seleziona file** o **Sfoglia cartella** .  
  
 **Rimuovi**  
 Consente di selezionare un file o una cartella e quindi di rimuoverli dall'elenco usando il pulsante **Rimuovi** .  
  
 **Pulsanti freccia**  
 Selezionare un file o una cartella e quindi utilizzare i pulsanti freccia per spostare il file o la cartella verso l'alto o verso il basso in modo da specificare la sequenza di accesso.  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento ai messaggi e agli errori di Integration Services](../integration-services-error-and-message-reference.md)  
  
  

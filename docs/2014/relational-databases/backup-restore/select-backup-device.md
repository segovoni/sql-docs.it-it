---
title: Seleziona dispositivo di backup | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: backup-restore
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.selectbackupdevice.f1
ms.assetid: 7887c9fd-15ce-4cc8-b069-845c1d09088c
caps.latest.revision: 26
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: aeecd5db3b5c8666eb7e585dbacc522da26f0c44
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37290937"
---
# <a name="select-backup-device"></a>Seleziona dispositivo di backup
  Utilizzare la finestra di dialogo **Seleziona dispositivo di backup** per selezionare un dispositivo di backup logico per l'operazione di ripristino.  
  
 Un dispositivo di backup logico è un dispositivo logico definito dall'utente che corrisponde a un dispositivo fisico, un'unità nastro o un'unità disco, disponibile tramite il sistema operativo.  
  
> [!NOTE]  
>  Se un backup utilizza più dispositivi di backup, è necessario che tutti corrispondano a un unico tipo di dispositivo.  
  
 **Per utilizzare SQL Server Management Studio per visualizzare il contenuto di un dispositivo di backup**  
  
-   [Visualizzare il contenuto di un nastro o di un file di backup &#40;SQL Server&#41;](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [Visualizzazione delle proprietà e del contenuto di un dispositivo di backup logico &#40;SQL Server&#41;](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
## <a name="options"></a>Opzioni  
 **Dispositivo di backup**  
 Nella casella di riepilogo selezionare il nome di un dispositivo di backup logico dal quale si desidera eseguire il ripristino.  
  
 Per informazioni su come visualizzare il contenuto di un dispositivo di backup, vedere [Visualizzare le proprietà e il contenuto di un dispositivo di backup logico &#40;SQL Server&#41;](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md).  
  
## <a name="remarks"></a>Note  
 Se nell'elenco non è visualizzato un dispositivo di backup logico contenente il backup di interesse, è possibile che il backup sia stato scritto direttamente su uno o più file o unità nastro. In questo caso, chiudere la finestra di dialogo **Seleziona dispositivo di backup** e selezionare **File** o **Nastro** nella casella di riepilogo **Supporti di backup** della finestra di dialogo **Seleziona backup** .  
  
## <a name="see-also"></a>Vedere anche  
 [Dispositivi di backup &#40;SQL Server&#41;](backup-devices-sql-server.md)  
  
  
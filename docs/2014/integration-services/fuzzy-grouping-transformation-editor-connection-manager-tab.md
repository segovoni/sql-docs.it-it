---
title: Editor trasformazione Raggruppamento fuzzy (scheda Gestione connessione) | Microsoft Docs
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
- sql12.dts.designer.fuzzygroupingtransformation.connection.f1
helpviewer_keywords:
- Fuzzy Grouping Transformation Editor
ms.assetid: 47b1446d-5331-473c-9cb5-a98b1f55bf5f
caps.latest.revision: 27
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 05c4af52fa196fe0c779ab3cef3be67d769b9616
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37164808"
---
# <a name="fuzzy-grouping-transformation-editor-connection-manager-tab"></a>Editor trasformazione Raggruppamento fuzzy (scheda Gestione connessione)
  Utilizzare la scheda **Gestione connessione** della finestra di dialogo **Editor trasformazione Raggruppamento fuzzy** per selezionare una connessione esistente o crearne una nuova.  
  
> [!NOTE]  
>  Sul server specificato dalla connessione deve essere in esecuzione [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. La trasformazione Raggruppamento fuzzy crea in tempdb oggetti dati temporanei che possono avere le stesse dimensioni dell'intero input della trasformazione. Durante l'esecuzione della trasformazione vengono eseguite query del server su tali oggetti temporanei. Queste query possono influire sulle prestazioni generali del server.  
  
 Per ulteriori informazioni sulla trasformazione Raggruppamento fuzzy, vedere [Fuzzy Grouping Transformation](data-flow/transformations/fuzzy-grouping-transformation.md).  
  
## <a name="options"></a>Opzioni  
 **Gestione connessione OLE DB**  
 Consente di selezionare una gestione connessione OLE DB esistente usando la casella di riepilogo o di creare una nuova connessione tramite il pulsante **Nuova** .  
  
 **Nuova**  
 Consente di creare una nuova connessione usando la finestra di dialogo **Configura gestione connessione OLE DB** .  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento ai messaggi e agli errori di Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Identificare righe di dati simili tramite la trasformazione Raggruppamento fuzzy](data-flow/transformations/identify-similar-data-rows-by-using-the-fuzzy-grouping-transformation.md)  
  
  

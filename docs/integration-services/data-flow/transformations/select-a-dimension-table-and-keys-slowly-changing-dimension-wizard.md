---
title: Selezione tabella dimensione e chiavi (Configurazione guidata dimensioni a modifica lenta) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.dts.loaddimwizard.selecttableandkeys.f1
ms.assetid: 01e0495f-de35-4607-ba19-0539e801e8fd
caps.latest.revision: 27
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f0da6b425699a7bc99bb373b85fb65167e0864be
ms.sourcegitcommit: de5e726db2f287bb32b7910831a0c4649ccf3c4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2018
ms.locfileid: "35332345"
---
# <a name="select-a-dimension-table-and-keys-slowly-changing-dimension-wizard"></a>Selezione tabella dimensione e chiavi (Configurazione guidata dimensioni a modifica lenta)
  Utilizzare la pagina **Selezione tabella dimensione e chiavi** per selezionare una tabella della dimensione da caricare ed eseguire il mapping tra le colonne del flusso di dati e le colonne che verranno caricate.  
  
 Per ulteriori informazioni su questa procedura guidata, vedere [Slowly Changing Dimension Transformation](../../../integration-services/data-flow/transformations/slowly-changing-dimension-transformation.md).  
  
## <a name="options"></a>Opzioni  
 **Connection manager**  
 Selezionare una gestione connessione OLE DB esistente nell'elenco oppure fare clic su **Nuova** per creare una nuova gestione connessione OLE DB.  
  
> [!NOTE]  
>  La Configurazione guidata dimensioni a modifica lenta supporta solo le gestioni connessioni OLE DB e le connessioni a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 **Nuova**  
 Nella finestra di dialogo **Configura gestione connessione OLE DB** selezionare una gestione connessione esistente oppure scegliere **Nuova** per creare una nuova connessione OLE DB.  
  
 **Tabella o vista**  
 Consente di selezionare una tabella o una vista dall'elenco.  
  
 **Colonne di input**  
 Consente di seleziona dall'apposito elenco le colonne di input per le quali è possibile definire il mapping.  
  
 **Colonne dimensione**  
 Consente di visualizzare tutte le colonne della dimensione disponibili.  
  
 **Tipo chiave**  
 Consente di selezionare una delle colonne della dimensione da utilizzare come chiave business. È necessario disporre di una chiave business.  
  
## <a name="see-also"></a>Vedere anche  
 [Configurazione degli output tramite Configurazione guidata dimensioni a modifica lenta](../../../integration-services/data-flow/transformations/configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  

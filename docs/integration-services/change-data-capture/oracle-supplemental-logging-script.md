---
title: Script di registrazione supplementare Oracle | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 5e6ee618-b89b-46c7-92ad-4fc5ef7b777a
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3920dd90361862b255879362ec36e9ac057bf7a2
ms.sourcegitcommit: de5e726db2f287bb32b7910831a0c4649ccf3c4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2018
ms.locfileid: "35331465"
---
# <a name="oracle-supplemental-logging-script"></a>Script di registrazione supplementare Oracle
  Questa finestra di dialogo contiene lo script della registrazione supplementare Oracle.  
  
 Quando si prepara un'istanza di CDC per l'utilizzo, nella finestra di progettazione di CDC viene creato uno script SQL Oracle per la configurazione della registrazione supplementare per le tabelle da acquisire. Nello script di registrazione supplementare è indicato quando una tabella specifica viene aggiornata. I record delle modifiche scritti nel log delle transazioni dovrebbero contenere i dati di tutte le colonne di interesse, non solo quelle modificate.  
  
 A seconda dei criteri DBA Oracle nell'organizzazione, l'esecuzione dello script di registrazione supplementare potrebbe richiedere l'esame e l'approvazione da parte di un amministratore di database Oracle.  
  
## <a name="options"></a>Opzioni  
 Di seguito sono riportate le opzioni disponibili relative all'esecuzione dello script.  
  
 **Run Script**  
 Tramite questa opzione è possibile eseguire lo script di registrazione supplementare nelle tabelle definite per l'istanza di CDC. Per eseguire questo script, l'utente Oracle deve disporre dell'autorizzazione ALTER TABLE per tutte le tabelle da acquisire e dell'autorizzazione SELECT per la vista DBA_LOG_GROUPS. L'utente Oracle deve inoltre disporre delle credenziali per utilizzare il database Oracle con le autorizzazioni necessarie. Il programma richiederà l'immissione delle credenziali Oracle per l'esecuzione dello script.  
  
 **Save As**  
 Tramite questa opzione è possibile salvare lo script in un file di testo. Utilizzare se un amministratore di database Oracle (DBA) deve esaminare ed eseguire lo script di registrazione supplementare. Salvando lo script in un file di testo sarà infatti possibile inviare quest'ultimo all'amministratore di database Oracle tramite posta elettronica o altro affinché possa essere eseguito in un secondo momento (tramite l'utilità Oracle SQL*Plus o altro strumento per l'esecuzione di script in un database Oracle).  
  
 **Copia**  
 Tramite questa opzione è possibile copiare lo script negli Appunti. Incollare lo script in un percorso desiderato qualora un amministratore di database Oracle (DBA) debba esaminare ed eseguire lo script di registrazione supplementare.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura di gestione di un'istanza di CDC](../../integration-services/change-data-capture/how-to-manage-a-cdc-instance.md)   
 [Gestire un'istanza di CDC](../../integration-services/change-data-capture/manage-a-cdc-instance.md)  
  
  

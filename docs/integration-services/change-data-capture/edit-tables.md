---
title: Modificare le tabelle | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- tabProps
ms.assetid: fed8fada-2abc-45e2-8228-0656f9c599cb
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d976c1c2ed5d79f4baaf59365a0ea812cfe15a19
ms.sourcegitcommit: de5e726db2f287bb32b7910831a0c4649ccf3c4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2018
ms.locfileid: "35333005"
---
# <a name="edit-tables"></a>Modificare le tabelle
  Utilizzare la scheda **Tabelle** per apportare modifiche alle tabelle e alle colonne selezionate dal database di origine Oracle. Nella scheda sono presenti gli elementi seguenti:  
  
 **Elenco Tabella**  
 Nell'elenco tabelle sono presenti tre colonne:  
  
-   **Nome tabella Oracle**: nome della tabella, incluso lo schema.  
  
-   **Istanza di acquisizione**: nome dell'istanza di acquisizione usato per denominare gli oggetti Change Data Capture specifici dell'istanza. L'istanza di acquisizione non può essere NULL. Se non è specificato, il nome deriva dal nome dello schema di origine più il nome della tabella di origine nel formato `<schema-name>_<table-name>.` Il nome dell'istanza di acquisizione non può superare i 100 caratteri e deve essere univoco nel database. È possibile fare clic in qualsiasi cella di questa colonna per modificare manualmente **capture_instance**.  
  
-   **Ruolo di sicurezza**: nome del ruolo del database utilizzato per ottenere l'accesso ai dati delle modifiche. È possibile fare clic in qualsiasi cella di questa colonna per modificare manualmente **security_role**.  
  
 **Aggiungi tabelle**  
 Fare clic su **Aggiungi tabelle** per aprire la finestra di dialogo Selezione tabelle in cui è possibile [aggiungere tabelle a un'istanza di CDC](../../integration-services/change-data-capture/add-tables-to-a-cdc-instance.md). Al primo accesso di questa sessione al database Oracle, è necessario [Connect to Oracle](../../integration-services/change-data-capture/connect-to-oracle.md).  
  
 **Modifica**  
 Selezionare una tabella dall'elenco e selezionare **Modifica** per aprire la finestra di dialogo **Proprietà** per tale tabella in cui è possibile [Modificare le proprietà della tabella](../../integration-services/change-data-capture/edit-the-table-properties.md).  
  
> [!NOTE]  
>  Non è possibile modificare il mapping dei tipi per le tabelle che dispongono già di tabelle mirror. Questa operazione è possibile unicamente per le tabelle nuove.  
  
 **Rimuovi**  
 Selezionare una tabella dall'elenco e fare clic su **Rimuovi** per rimuovere la tabella dall'istanza di CDC.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura di modifica delle proprietà dell'istanza di CDC](../../integration-services/change-data-capture/how-to-edit-the-cdc-instance-properties.md)   
 [Selezionare tabelle e colonne Oracle](../../integration-services/change-data-capture/select-oracle-tables-and-columns.md)  
  
  

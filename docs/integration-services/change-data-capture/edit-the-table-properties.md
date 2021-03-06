---
title: Modificare le proprietà delle tabelle | Microsoft Docs
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
- editTabProps
ms.assetid: 95ea72ba-8e40-4177-a963-0fb4d10c56e3
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 68e40d458f7a09d9fb073a9771aaeb9b80c6a06c
ms.sourcegitcommit: de5e726db2f287bb32b7910831a0c4649ccf3c4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2018
ms.locfileid: "35332855"
---
# <a name="edit-the-table-properties"></a>Modificare le proprietà delle tabelle
  Utilizzare questa finestra di dialogo per modificare colonne specifiche della tabella selezionata in cui vengono acquisite le modifiche. È anche possibile modificare le informazioni **Security Role** e **Capture Instance** .  
  
### <a name="to-edit-the-columns-to-include-in-the-cdc-instance"></a>Per modificare le colonne da includere nell'istanza di CDC  
  
1.  Eseguire una o entrambe le operazioni seguenti:  
  
    -   Selezionare la casella di controllo accanto a eventuali colonne aggiuntive che si desidera includere.  
  
    -   Deselezionare la casella di controllo accanto alle colonne che non si desidera più includere.  
  
### <a name="to-edit-the-security-role"></a>Per modificare il ruolo di sicurezza  
  
1.  Digitare un nuovo nome oppure modificare il nome esistente del ruolo di sicurezza nel campo **Security Role** .  
  
### <a name="to-create-a-new-capture-instance"></a>Per creare una nuova istanza di acquisizione  
  
1.  Nel campo **Name** della sezione **Security Role** immettere un nome per l'istanza di acquisizione. Per impostazione predefinita, il nome immesso nel campo è il nome dell'istanza di acquisizione corrente con **_NEW** aggiunto alla fine del nome, ad esempio **old_instance_NEW**.  
  
2.  Salvare l'istanza di acquisizione come:  
  
    -   **New Capture Instance**: viene salvata una nuova istanza di acquisizione e l'istanza di acquisizione precedente non viene eliminata.  
  
         **Nota**: non possono esistere più di due istanze di acquisizione per tabella. Se sono già presenti due istanze di acquisizione, l'opzione non è disponibile.  
  
    -   **Replace Existing**: l'istanza di acquisizione corrente viene eliminata e sostituita dall'istanza di acquisizione creata. Se per la tabella sono state definite due istanze di acquisizione, è necessario selezionarne una da sostituire.  
  
 **Nota**: è possibile rimuovere un'istanza di acquisizione dall'elenco di tabelle nella scheda **Table** .  
  
 Dopo avere immesso le informazioni in questa finestra di dialogo, scegliere **OK** per accettare le modifiche.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura di modifica delle proprietà dell'istanza di CDC](../../integration-services/change-data-capture/how-to-edit-the-cdc-instance-properties.md)   
 [Apportare modifiche alle tabelle selezionate per l'acquisizione di modifiche](../../integration-services/change-data-capture/make-changes-to-the-tables-selected-for-capturing-changes.md)  
  
  

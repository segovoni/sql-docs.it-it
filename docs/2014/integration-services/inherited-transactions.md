---
title: Transazioni ereditate | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- transactions [Integration Services], inherited
- child packages
- inherited transactions [Integration Services]
ms.assetid: 90db5564-d41e-4cfe-8c9e-4e68d41eff1c
caps.latest.revision: 34
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 6b2a4010ccdf7ec3138e180d5d90f6e779aa0529
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37215491"
---
# <a name="inherited-transactions"></a>Transazioni ereditate
  Un pacchetto può eseguire un altro pacchetto tramite l'attività Esegui pacchetto. Il pacchetto figlio, ovvero il pacchetto eseguito dall'attività Esegui pacchetto, può creare la propria transazione del pacchetto o ereditare quella del padre.  
  
 Un pacchetto figlio eredita la transazione del pacchetto padre se sono soddisfatte le due condizioni seguenti:  
  
-   Il pacchetto viene richiamato da un'attività Esegui pacchetto.  
  
-   Anche l'attività Esegui pacchetto che richiama il pacchetto partecipa alla transazione del pacchetto padre.  
  
 I contenitori e le attività del pacchetto figlio possono partecipare alla transazione del pacchetto padre solo se il pacchetto figlio partecipa alla transazione.  
  
## <a name="illustration-of-package-transactions"></a>Illustrazione delle transazioni del pacchetto  
 Nella figura seguente sono illustrati tre pacchetti che utilizzano transazioni. Ogni pacchetto include più attività. Per evidenziare il comportamento delle transazioni, sono visualizzate solo le attività Esegui pacchetto. Il pacchetto A esegue i pacchetti B e C. Il pacchetto B esegue a sua volta i pacchetti D ed E e il pacchetto C esegue il pacchetto F.  
  
 Ai pacchetti e alle attività sono associati gli attributi di transazione seguenti:  
  
-   **TransactionOption** è impostata su **Required** per i pacchetti A e C  
  
-   **TransactionOption** è impostata su **Supported** per i pacchetti B e D e per le attività Esegui pacchetto B, Esegui pacchetto D e Esegui pacchetto F.  
  
-   **TransactionOption** è impostata su **NotSupported** per il pacchetto E e per le attività Esegui pacchetto C e Esegui pacchetto E.  
  
 ![Flusso di transazioni ereditate](media/mw-dts-executepack.gif "Flusso di transazioni ereditate")  
  
 Solo i pacchetti B, D e F possono ereditare transazioni dal pacchetto padre.  
  
 I pacchetti B e D ereditano la transazione avviata dal pacchetto A.  
  
 Il pacchetto F eredita la transazione avviata dal pacchetto C.  
  
 I pacchetti A e C controllano le proprie transazioni.  
  
 Il pacchetto E non utilizza transazioni.  
  
## <a name="related-tasks"></a>Related Tasks  
 [Configurazione di un pacchetto per l'utilizzo di transazioni](../relational-databases/native-client-ole-db-transactions/transactions.md)  
  
  

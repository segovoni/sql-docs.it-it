---
title: Finestra di dialogo Imposta valore parametro | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: service
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ce9c2201-4e9a-4495-948f-b68deeaa7955
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 9e9e3a0004e28a1e18dcc594cf00ada8d808b0db
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="set-parameter-value-dialog-box"></a>Finestra di dialogo Imposta valore parametro
  Utilizzare la finestra di dialogo **Imposta valore parametro** per impostare i valori per i parametri e le proprietà di gestione connessione per progetti e pacchetti.  
  
 **Per saperne di più**  
  
-   [Aprire la finestra di dialogo Imposta valore parametro](#open_dialog)  
  
-   [Configurare le opzioni](#option)  
  
##  <a name="open_dialog"></a> Aprire la finestra di dialogo Imposta valore parametro  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]connettersi al server [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
     Verrà eseguita la connessione all'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] in cui è ospitato il database SSISDB.  
  
2.  In Esplora oggetti espandere l'albero per visualizzare il nodo dei **cataloghi di Integration Services** .  
  
3.  Espandere il nodo **SSISDB** .  
  
4.  Fare clic con il pulsante destro del mouse su un pacchetto o un progetto, scegliere **Configura**e quindi fare clic sul pulsante con i puntini di sospensione nella scheda **Parametri** o nella scheda **Gestioni connessioni** .  
  
##  <a name="option"></a> Configurare le opzioni  
 **Parametro**  
 Viene elencato il nome del parametro.  
  
 **Tipo**  
 Elenca il tipo di dati del valore del parametro.  
  
 **Descrizione**  
 Mostra una descrizione facoltativa per il parametro.  
  
 **Modifica valore**  
 Selezionare questa opzione per modificare il valore del parametro.  
  
 **Usa valore predefinito del pacchetto**  
 Selezionare questa opzione per utilizzare il valore del parametro predefinito archiviato nel pacchetto.  
  
 **Usa variabile di ambiente**  
 Selezionare questa opzione per utilizzare un valore della variabile archiviato nell'ambiente, a cui fa riferimento il progetto o il pacchetto. Per aggiungere un riferimento all'ambiente a un progetto o a un pacchetto, utilizzare la finestra di dialogo **Configura** . Per ulteriori informazioni, vedere [Configure Dialog Box](../../integration-services/catalog/configure-dialog-box.md).  
  
  

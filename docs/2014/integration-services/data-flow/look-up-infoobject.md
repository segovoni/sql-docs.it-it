---
title: Cerca InfoObject | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e7f4c132-a5ec-49d8-a964-45775432731f
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 7f4c7df344ac5e4fe2d00863615783195aed6d45
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37182769"
---
# <a name="look-up-infoobject"></a>Cerca InfoObject
  Utilizzare la finestra di dialogo **Cerca InfoObject** per cercare un InfoObject definito nel sistema SAP Netweaver BW. Quando viene visualizzato l'elenco degli InfoObject disponibili, selezionare l'InfoObject desiderato e le opzioni associate verranno compilate con i valori richiesti dalla destinazione SAP BW.  
  
 La destinazione SAP BW di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW utilizza la finestra di dialogo **Cerca InfoObject** . Per ulteriori informazioni sulla destinazione SAP BW, vedere [SAP BW Destination](sap-bw-destination.md).  
  
> [!IMPORTANT]  
>  La documentazione per Microsoft Connector 1.1 for SAP BW presuppone la conoscenza dell'ambiente SAP Netweaver BW. Per ulteriori informazioni su SAP Netweaver BW o per informazioni su come configurare oggetti e processi di SAP Netweaver BW, vedere la documentazione SAP.  
  
 **Per aprire la finestra di dialogo Cerca InfoObject**  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]aprire il pacchetto [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] che contiene la destinazione SAP BW.  
  
2.  Nella scheda **Flusso di dati** fare doppio clic sulla destinazione SAP BW.  
  
3.  Nell' **Editor destinazione SAP BW**fare clic su **Gestione connessione** per aprire la pagina **Gestione connessione** dell'editor.  
  
4.  Nella casella di gruppo **Crea oggetti SAP BW** della pagina **Gestione connessione** selezionare una delle seguenti opzioni:  
  
    1.  Selezionare **InfoCube**. Scegliere quindi **Crea**. Nella finestra di dialogo **Crea InfoCube per dati transazione** fare clic su **Cerca** nella colonna **IObject** per una delle righe nell'elenco. Ogni riga rappresenta una colonna nel flusso di dati del pacchetto.  
  
    2.  Selezionare **InfoSource**. Scegliere quindi **Crea**. Nella finestra di dialogo **Crea InfoSource** selezionare **Dati transazione**. Nella finestra di dialogo **Crea InfoSource per dati transazione** fare clic su **Cerca** nella colonna **IObject** per una delle righe nell'elenco. Ogni riga rappresenta una colonna nel flusso di dati del pacchetto.  
  
    3.  Selezionare **InfoSource**. Scegliere quindi **Crea**. Nella finestra di dialogo **Crea InfoSource** selezionare **Dati master**. Nella finestra di dialogo **Crea InfoSource per dati master** scegliere **Cerca**.  
  
 È inoltre possibile aprire la finestra di dialogo **Cerca InfoObject** facendo clic su **Aggiungi** nella sezione **Attributi** della finestra di dialogo **Crea nuovo InfoObject** .  
  
## <a name="lookup-options"></a>Opzioni di ricerca  
 Nelle caselle di testo dei campi di ricerca è possibile filtrare i risultati tramite il carattere jolly asterisco (*) oppure utilizzando una stringa parziale in combinazione con il carattere jolly asterisco. Tuttavia, se si lascia un campo di ricerca vuoto, il processo di ricerca restituirà solo stringhe vuote in tale campo.  
  
 **Caratteristiche**  
 Cercare InfoObject che rappresentino le caratteristiche.  
  
 **Unità**  
 Cercare InfoObject che rappresentino le unità.  
  
 **Cifre chiave**  
 Cercare InfoObject che rappresentino le cifre chiave.  
  
 **Caratteristiche ora**  
 Cercare InfoObject che rappresentino le caratteristiche orarie.  
  
 **Nome**  
 Immettere il nome dell'InfoObject da cercare oppure un nome parziale con il carattere jolly asterisco (*). In alternativa, utilizzare il carattere jolly asterisco da solo per includere tutti gli InfoObject.  
  
 **Descrizione**  
 Immettere la descrizione o una descrizione parziale con il carattere jolly asterisco (*). In alternativa, utilizzare il carattere jolly asterisco da solo per includere tutti gli InfoObject indipendentemente dalla descrizione.  
  
 **Cerca**  
 Cercare gli InfoObject corrispondenti definiti nel sistema SAP Netweaver BW.  
  
## <a name="lookup-results"></a>Risultati di ricerca  
 Dopo avere fatto clic sul pulsante Ricerca, viene visualizzato un elenco di InfoObject nel sistema SAP Netweaver BW in una tabella con le intestazioni di colonna seguenti.  
  
 **InfoObject**  
 Visualizza il nome dell'InfoObject definito nel sistema SAP Netweaver BW.  
  
 **Testo (breve)**  
 Visualizza il testo breve associato all'InfoObject.  
  
 Quando viene visualizzato l'elenco degli InfoObject disponibili, selezionare l'InfoObject desiderato e le opzioni associate verranno compilate con i valori richiesti dalla destinazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Crea InfoCube per dati transazione](create-infocube-for-transaction-data.md)   
 [Crea InfoSource](create-infosource.md)   
 [Crea InfoSource per dati transazione](create-infosource-for-transaction-data.md)   
 [Crea InfoSource per dati master](create-infosource-for-master-data.md)   
 [Crea nuovo InfoObject](create-new-infoobject.md)   
 [Editor destinazione SAP BW &#40;pagina Gestione connessione&#41;](sap-bw-destination-editor-connection-manager-page.md)   
 [Guida (F1) di Microsoft Connector 1.1 for SAP BW](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  

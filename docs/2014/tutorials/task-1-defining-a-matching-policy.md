---
title: 'Attività 1: Definizione dei criteri di corrispondenza | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6f89a720-fce5-4f60-bef3-a159bbc9f25c
caps.latest.revision: 6
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 58507594fa2872bc5433b63e0f932d2914291a31
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37282357"
---
# <a name="task-1-defining-a-matching-policy"></a>Attività 1: Definizione di criteri di corrispondenza
  In questa attività vengono creati criteri di corrispondenza in cui è contenuta una regola. La regola avrà un solo prerequisito: **Supplier ID**, il che significa che gli ID dei fornitori devono corrispondere prima di usare gli altri domini nella regola. La regola usa due altri domini: **Supplier Name** con **somiglianza** valore impostato su **70%** e **Contact Email** con  **Somiglianza** valore impostato su **il 30%**.  
  
1.  Nella pagina principale del **Client DQS**, fare clic su **freccia destra** accanto a **Suppliers** knowledge base, quindi seleziona **criteri di corrispondenza**.  
  
     ![Menu criteri sul principale di corrispondenza pagina](../../2014/tutorials/media/et-definingamatchingpolicy-01.jpg "Main Menu criteri di corrispondenza pagina")  
  
2.  Nel **mappa** pagina, selezionare **File di Excel** per **Zdroj dat**.  
  
3.  Fare clic su **esplorare**, verificare che il filtro sia impostato su **cartella di lavoro di Excel**e selezionare **Cleansed Supplier List. xls** file esportato dopo aver eseguito l'attività di pulizia.  
  
    > [!NOTE]  
    >  Al termine di questa attività, non è possibile esportare i risultati poiché questa attività è mirata principalmente alla definizione di criteri di corrispondenza. Verrà creato un progetto Data Quality per l'attività di corrispondenza che verrà eseguito per rimuovere i duplicati dall'elenco di fornitori utilizzando questi criteri di corrispondenza illustrati nella lezione successiva.  
  
4.  Mappa **SupplierID** colonna **Supplier ID** dominio **Supplier Name** colonna **Supplier Name** dominio,  **ContactEmailAddress** colonna **Contact Email** dominio. È sufficiente eseguire il mapping delle colonne di origine ai domini che si desidera utilizzare per la definizione dei criteri di corrispondenza. In questo caso, si stanno rendendo disponibili i domini Supplier ID, Supplier Name e Contact Email per l'attività relativa ai criteri di corrispondenza.  
  
     ![Eseguire il mapping di pagina del processo di definizione dei criteri di corrispondenza](../../2014/tutorials/media/et-definingamatchingpolicy-02.jpg "eseguire il mapping di pagina del processo di definizione dei criteri di corrispondenza")  
  
5.  Fare clic su **successivo** per spostare le **criteri di corrispondenza** pagina in cui si definiranno i criteri di corrispondenza con una regola in esso.  
  
6.  Fare clic su **creare una regola di corrispondenza** pulsante sulla barra degli strumenti per creare una regola nei criteri.  
  
     ![Creare un pulsante della barra degli strumenti di regola corrispondente](../../2014/tutorials/media/et-definingamatchingpolicy-03.jpg "creare un pulsante della barra degli strumenti di regola corrispondente")  
  
7.  Nel **Rule Details** riquadro a destra e immettere **Rimuovi fornitori duplicati** per il **nome regola**.  
  
8.  Fare clic su **Aggiungi nuovo elemento di dominio** sulla barra degli strumenti nel riquadro di destra.  
  
     ![Dettagli regola - aggiungere un nuovo pulsante di elemento di dominio](../../2014/tutorials/media/et-definingamatchingpolicy-04.jpg "dettagli regola - aggiungere un nuovo pulsante di elemento di dominio")  
  
9. Selezionare **Supplier ID** per il **domain** e selezionare il **prerequisiti** casella di controllo. Si noti che **somiglianza** viene automaticamente impostato su **Exact**. Impostando **Supplier ID** come la **prerequisiti**, si specifica che i valori per questo campo in due record diversi deve restituire una corrispondenza del 100%, altrimenti il record non vengono considerati una corrispondenza e le altre clausole di regola verranno ignorati.  
  
     ![Rimuovi Definizione regola fornitori duplicati](../../2014/tutorials/media/et-definingamatchingpolicy-05.jpg "Rimuovi fornitori duplicati definizione della regola")  
  
10. Fare clic su **Aggiungi nuovo elemento di dominio** dalla barra degli strumenti.  
  
11. Selezionare **Supplier Name** dominio, scegliere **simile** per **somiglianza**e il tipo **70** per il **peso**.  In questo caso, si specifica che i nomi dei fornitori non devono essere identici, ma possono essere simili per i record che devono essere considerati corrispondenti. Tramite il peso viene indicato il contributo del punteggio di questo campo al punteggio di corrispondenza complessivo.  
  
12. Ripetere i due passaggi precedenti per aggiungere **Contact Email** dominio con **30** per il **peso**.  
  
13. Si noti che il **punteggio corrispondente minimo** è impostata su **80%**, che è il valore visualizzato nel **generale** scheda della finestra di **configurazione** pagina di **Amministrazione DQS**. Questo punteggio può essere aumentato oltre questo valore soglia solo qui.  
  
14. Si noti che **cluster sovrapposti** opzione è selezionata. Con questa opzione, un record può essere visualizzato in più cluster. Se l'impostazione viene modificata su Cluster non sovrapposti, i cluster che presentano record comuni vengono combinati in uno unico.  
  
15. Il **avviare** pulsante in questa pagina consente di testare separatamente, ogni regola nei criteri mentre il pulsante Avvia nella pagina successiva consente di testare tutti i criteri (tutte le regole nel criterio).  
  
16. Fare clic su **successivo** per passare alle **risultati corrispondenza** pagina.  
  
## <a name="next-step"></a>Passaggio successivo  
 [Attività 2: Test e pubblicazione dei criteri di corrispondenza](../../2014/tutorials/task-2-testing-and-publishing-the-matching-policy.md)  
  
  

---
title: Implementare una trasformazione ricerca nella modalità Full Cache utilizzando la gestione connessione OLE DB | Microsoft Docs
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
- Lookup transformation [Integration Services]
ms.assetid: c4150e1b-bdff-4f7a-af4c-3401c34def83
caps.latest.revision: 16
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: cb6751b8f6cb3ebd982e53d4735c1aad940eb00f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37280377"
---
# <a name="implement-a-lookup-transformation-in-full-cache-mode-using-the-ole-db-connection-manager"></a>Implementazione di una trasformazione Ricerca in modalità Full cache utilizzando la gestione connessione OLE DB
  È possibile configurare la trasformazione Ricerca per utilizzare la modalità Full Cache e una gestione connessione OLE DB. In modalità Full Cache il set di dati di riferimento viene caricato nella cache prima dell'esecuzione della trasformazione Ricerca.  
  
 La trasformazione Ricerca esegue ricerche creando un join dei dati contenuti nelle colonne di input da un'origine dati connessa con le colonne in un set di dati di riferimento. Per altre informazioni, vedere [Trasformazione Ricerca](../data-flow/transformations/lookup-transformation.md).  
  
 Quando si configura la trasformazione Ricerca per l'utilizzo di una gestione connessione OLE DB, selezionare una tabella, una vista o una query SQL per generare il set di dati di riferimento.  
  
### <a name="to-implement-a-lookup-transformation-in-full-cache-mode-by-using-ole-db-connection-manager"></a>Per implementare una trasformazione Ricerca in modalità Full Cache utilizzando la gestione connessione OLE DB  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]aprire il progetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] contenente il pacchetto desiderato, quindi fare clic su di esso in Esplora soluzioni.  
  
2.  Nella scheda **Flusso di dati** trascinare la Trasformazione Ricerca dalla **Casella degli strumenti**all'area di progettazione.  
  
3.  Connettere la trasformazione Ricerca al flusso di dati trascinando un connettore da un'origine o una trasformazione precedente alla trasformazione Ricerca.  
  
    > [!NOTE]  
    >  Una trasformazione Ricerca può non essere convalidata se si connette a un file flat che contiene un campo di tipo data vuoto. La convalida della trasformazione varia a seconda che per la gestione connessione relativa al file flat sia configurato o meno il mantenimento dei valori Null. Per assicurarsi che la Trasformazione Ricerca venga convalidata, in **Editor origine file flat**nella **pagina Gestione connessione**selezionare l'opzione **Mantieni i valori Null dell'origine come valori Null nel flusso di dati** .  
  
4.  Fare doppio clic sulla trasformazione di origine o precedente per configurare il componente.  
  
5.  Fare doppio clic su Trasformazione Ricerca, quindi nella pagina **Generale**di **Editor trasformazione Ricerca** selezionare **Full cache**.  
  
6.  Nell'area **Tipo di connessione** selezionare **Gestione connessione OLE DB**.  
  
7.  Nell'elenco **Specificare come gestire le righe senza voci corrispondenti** selezionare un'opzione di gestione degli errori per le righe senza voci corrispondenti.  
  
8.  Nella pagina Connessione, selezionare una gestione connessione dall'elenco **Gestione connessione OLE DB** o fare clic su **Nuova** per creare una nuova gestione connessione. Per altre informazioni, vedere [Gestione connessione OLE DB](ole-db-connection-manager.md).  
  
9. Effettuare una delle attività seguenti:  
  
    -   Fare clic su **Usa una tabella o una vista**, quindi selezionare una tabella o una vista oppure fare clic su **Nuova** per creare una tabella o una vista.  
  
         -oppure-  
  
    -   Fare clic su **Usa i risultati di una query SQL**, quindi compilare una query nella finestra **Comando SQL** oppure fare clic su **Compila query** per compilare una query usando gli strumenti grafici disponibili in **Generatore query** .  
  
         -oppure-  
  
    -   In alternativa fare clic su **Sfoglia** per importare un'istruzione SQL da un file.  
  
     Per convalidare la query SQL, fare clic su **Analizza query**.  
  
     Per visualizzare un campione di dati, fare clic su **Anteprima**.  
  
10. Fare clic nella pagina **Colonne** e trascinare almeno una colonna dall'elenco **Colonne di input disponibili** a una colonna nell'elenco **Colonne di ricerca disponibili** .  
  
    > [!NOTE]  
    >  La trasformazione Ricerca esegue automaticamente il mapping delle colonne con lo stesso nome e lo stesso tipo di dati.  
  
    > [!NOTE]  
    >  È possibile eseguire il mapping solo di colonne con tipi di dati corrispondenti. Per altre informazioni, vedere [Tipi di dati di Integration Services](../data-flow/integration-services-data-types.md).  
  
11. Includere colonne di ricerca nell'output effettuando le attività seguenti:  
  
    1.  Nell'elenco **Colonne di ricerca disponibili** . selezionare le colonne.  
  
    2.  Nell'elenco **Operazione di ricerca** specificare se i valori dalle colonne di ricerca sostituiscono quelli nella colonna di input o vengono scritti in una nuova colonna.  
  
12. Per configurare l'output degli errori, fare clic sulla pagina **Output errori** e impostare le opzioni di gestione degli errori. Per altre informazioni, vedere [Editor trasformazione Ricerca &#40;pagina Output degli errori&#41;](../lookup-transformation-editor-error-output-page.md).  
  
13. Fare clic su **OK** per salvare le modifiche alla trasformazione Ricerca e quindi eseguire il pacchetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Implementare una trasformazione Ricerca in modalità Full Cache tramite la gestione connessione della cache](lookup-transformation-full-cache-mode-ole-db-connection-manager.md)   
 [Implementare una ricerca in modalità No Cache o Partial Cache](../data-flow/transformations/implement-a-lookup-in-no-cache-or-partial-cache-mode.md)   
 [Trasformazioni di Integration Services](../data-flow/transformations/integration-services-transformations.md)  
  
  

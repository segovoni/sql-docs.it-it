---
title: Matrice di classificazione (componenti aggiuntivi Data Mining SQL Server dati) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- mining models, validating
- classification matrix
- confusion table
- mining models, testing
ms.assetid: d6f620f4-39af-4714-9628-28ce3c361fca
caps.latest.revision: 14
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3d87c2d37ed69e2cc3f3e224ddf1a489b34425b8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37249641"
---
# <a name="classification-matrix-sql-server-data-mining-add-ins"></a>Matrice di classificazione (componenti aggiuntivi Data mining di SQL Server)
  ![Pulsante matrice di classificazione, barra multifunzione Data Mining](media/dmc-cmatrix.gif "pulsante matrice di classificazione, barra multifunzione Data Mining")  
  
 È possibile utilizzare la matrice di classificazione per valutare l'accuratezza di un modello per la stima. Per generare una matrice di classificazione, è necessario eseguire un set di dati di testing tramite il modello; inoltre mediante lo strumento della matrice di classificazione vengono confrontati i valori effettivi del set di testing con le stime eseguite dal modello. Osservando la matrice, è possibile determinare immediatamente la frequenza con cui il modello è corretto e quella con cui vengono eseguite stime in modo errato.  
  
 In questi componenti aggiuntivi, usare il **matrice di classificazione** guidato per selezionare un modello, specificare i dati di test e quindi generare una matrice di risultati.  
  
## <a name="how-to-read-a-classification-matrix"></a>Modalità di lettura di una matrice di classificazione  
 Si supponga che l'obiettivo sia quello di progettare un programma di fedeltà del cliente e di assegnare i clienti a categorie appropriate, in modo da fornire loro il livello adeguato di incentivi. Sono stati implementati tre livelli per il programma di ricompensa, vale a dire bronzo, argento e oro, assegnati ai clienti in una fase di valutazione. È stato inoltre progettato un modello tramite cui vengono analizzati i clienti e stimate le categorie corrette. A questo punto si utilizzerà la matrice di classificazione nei dati di prova per determinare l'efficacia del modello relativamente alla stima dell'offerta corretta per tutti i clienti.  
  
 Tramite la tabella della matrice di classificazione viene indicato il numero di clienti che verranno assegnati a ogni categoria in base al modello e il risultato ottenuto verrà confrontato con il numero di clienti effettivamente iscritti a ogni livello di ricompensa.  
  
||Bronzo (valore effettivo)|Oro (valore effettivo)|Argento (valore effettivo)|  
|-|-----------------------|---------------------|-----------------------|  
|Bronzo|**% 94.45**|% 15.18|% 1,70|  
|Oro|% 2.72|**% 84.82**|0,00%|  
|Argento|% 1.84|0,00%|**% 93.80**|  
|*Correggere*|*% 95.45*|*% 84.82*|*% 98.30*|  
|*Classificato in modo errato*|*% 4.55*|*% 15.18*|*% 1,70*|  
  
-   In ogni colonna vengono visualizzati i valori effettivi del set di dati di testing.  
  
-   In ogni riga vengono visualizzati i valori stimati.  
  
-   I valori in grassetto, rappresentati in diagonale dall'angolo superiore sinistro all'angolo inferiore destro della matrice, forniscono il quadro di ciò che è appropriato nel modello.  
  
-   Tutti gli altri valori all'esterno della diagonale rappresentano errori. Alcuni sono falsi positivi, vale a dire che con la stima eseguita dal modello il cliente è stato associato al programma oro ma non era corretto.  A seconda del dominio, i falsi positivi possono essere molto costosi.  
  
     Altri sono falsi negativi, vale a dire che con la stima eseguita dal modello il cliente non era interessato anche se è stato associato al programma. Anche in questo caso, a seconda del dominio del problema, il costo dell'opportunità persa potrebbe essere significativo.  
  
## <a name="using-the-classification-matrix-wizard"></a>Utilizzo della procedura guidata Matrice di classificazione  
  
1.  Selezionare il modello di data mining sul quale si desidera basare le stime.  
  
2.  Selezionare un'origine dei nuovi dati di test oppure utilizzare i dati di testing salvati con la struttura.  
  
3.  Selezionare la colonna di cui si desidera valutare l'accuratezza. È possibile selezionare solo una colonna quando si crea una matrice, ma la colonna può disporre di più valori.  
  
     Suggerimento: può essere difficile interpretare una matrice di classificazione se nella colonna stimabile vi sono numerose colonne da confrontare.  
  
     Nel **Seleziona colonne da stimare** pagina, è possibile inoltre specificare se si desidera visualizzare il numero di valori errati e corretti o visualizzare una percentuale.  
  
4.  Nella pagina Selezione dati di origine indicare se si utilizzano i dati di test esterni o i dati di test salvati con il modello.  
  
5.  Se si usano dati di test esterni, è necessario eseguire il mapping alle colonne di input il modello i **specificare la relazione** pagina della procedura guidata.  
  
     Se si utilizza il set di dati di test predefinito, il mapping viene eseguito automaticamente.  
  
6.  Fare clic su **fine** per eseguire stime sul modello e generare la matrice di classificazione.  
  
     La procedura guidata crea un report che contiene la matrice di classificazione e altri dettagli sull'analisi. Il report viene salvato come tabella in Excel, con un riepilogo nella parte superiore in cui vengono indicati il numero di case stimati correttamente e il numero di stime errate.  
  
### <a name="requirements"></a>Requisiti  
  
-   Per creare una matrice di classificazione, è necessario avere accesso a un modello di data mining esistente che supporta la misura dell'accuratezza. I modelli di previsione e quelli di associazione non possono essere misurati con questo strumento.  
  
-   Per il modello di misura è necessario stimare un valore che sia discreto o che sia già stato discretizzato.  
  
-   Se non è possibile utilizzare l'opzione per salvare un set di testing insieme alla struttura o al modello, è necessario ottenere un set di dati di input che disponga essenzialmente dello stesso numero di colonne, con tipi di dati corrispondenti, come quelli utilizzati nel modello.  
  
-   Sia il modello di data mining che i nuovi dati utilizzati per il testing devono contenere almeno una colonna stimabile e le colonne devono includere lo stesso tipo di dati.  
  
### <a name="known-issues"></a>Problemi noti  
 In SQL Server 2012 e SQL Server 2014, la possibilità di eseguire il mapping di set di dati di test interno al modello non funziona **matrice di classificazione** dello strumento. Tuttavia, è possibile specificare un set di dati esterno e selezionare il set di training come input per determinare l'errore nel set di dati originale.  
  
## <a name="see-also"></a>Vedere anche  
 [Convalida dei modelli e utilizzo dei modelli per la stima &#40;dati di componenti aggiuntivi Data Mining per Excel&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md)   
 [Esplorare i dati &#40;componenti aggiuntivi Data Mining di dati SQL Server&#41;](explore-data-sql-server-data-mining-add-ins.md)   
 [Rileva categorie &#40;strumenti di analisi tabelle per Excel&#41;](detect-categories-table-analysis-tools-for-excel.md)  
  
  

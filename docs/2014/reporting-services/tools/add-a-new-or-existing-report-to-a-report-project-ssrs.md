---
title: Aggiungere un report nuovo o esistente a un progetto report (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], creating
ms.assetid: 8bc0bb53-ad8a-464d-bb6a-7fea5fa62c5c
caps.latest.revision: 15
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 8d1d96273c21f2b22b3482a74b5b55370b09589e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37230181"
---
# <a name="add-a-new-or-existing-report-to-a-report-project-ssrs"></a>Aggiungere un report nuovo o esistente a un progetto report (SSRS)
  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], è possibile aggiungere un nuovo report tramite la creazione guidata Report o aggiungendo un nuovo report vuoto al progetto. È anche possibile aggiungere un report esistente. Dopo l'aggiunta di un report, il relativo nome verrà visualizzato nella cartella **Report** nel progetto.  
  
> [!NOTE]  
>  Per visualizzare in anteprima un report con le origini dati esistenti, è necessario disporre delle autorizzazioni per l'origine dati dal client di creazione report. Per altre informazioni, vedere [creare un'origine dati condivisa o un Embedded &#40;SSRS&#41;](../create-an-embedded-or-shared-data-source-ssrs.md).  
  
 Dopo l'aggiunta di un report, è possibile definire origini dati e set di dati, nonché progettarne il layout. Per iniziare, vedere [Creare un report tabella semplice &#40;esercitazione su SSRS&#41;](../create-a-basic-table-report-ssrs-tutorial.md) o [Tabelle &#40;Generatore report e SSRS&#41;](../report-design/tables-report-builder-and-ssrs.md).  
  
### <a name="to-add-a-new-report-using-the-report-wizard"></a>Per aggiungere un nuovo report tramite la Creazione guidata report  
  
1.  In Esplora soluzioni fare clic con il pulsante destro del mouse sulla cartella Report, quindi scegliere **Aggiungi nuovo report**. Verrà visualizzata la finestra di dialogo **Creazione guidata report** .  
  
     Tramite i passaggi della procedura guidata sarà possibile creare un'origine dati e un set di dati con una query, definire gruppi, specificare un layout, scegliere uno stile che include il colore e il tipo di carattere e creare il report. I passaggi includono:  
  
    -   **Selezione un'origine dati.** Il primo passaggio della creazione di un report consiste nel definire un'origine dati. Nella Creazione guidata report viene visualizzato un elenco di tutte le origini dei dati condivise disponibili nel progetto report, nonché un'opzione per la creazione di una nuova origine dei dati.  
  
    -   **Progettazione query.** Nel secondo passaggio si progetta la query. È possibile digitare la stringa della query, compilarla tramite Progettazione query o importare una query da un altro report. Per altre informazioni sugli strumenti di progettazione query, vedere [Strumenti di progettazione query in Reporting Services](../reporting-services-query-designers.md).  
  
    -   **Selezione tipo di report.** Nel terzo passaggio si seleziona il tipo di report desiderato. È possibile selezionare un report tabulare o matrice. Un report tabella include un numero fisso di colonne. Un report matrice, o a campi incrociati, include un numero variabile di colonne in base ai risultati della query. In un report mappa i dati analitici vengono visualizzati su uno sfondo geografico.  
  
    -   **Scegliere uno stile.** In questo passaggio si applica uno stile al report tramite un modello di stili. Selezionare un modello per applicare stili di carattere, colore e bordo al report. In Progettazione report sono disponibili sei modelli di stile: Ardesia, Foresta, Aziendale, Grassetto, Oceano e Generico. È inoltre possibile aggiungere ulteriori modelli di stili.  
  
        > [!NOTE]  
        >  È possibile modificare i modelli esistenti o aggiungerne di nuovi modificando il file StyleTemplates XML in \Programmi\Microsoft Visual Studio 10.0\Common7\IDE\PrivateAssemblies\Business Intelligence Wizards\Reports\Styles\\< lang\>cartella, dove \<lang > è il linguaggio in uso (ad esempio, se si usa la versione in lingua inglese di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], il nome della cartella è "EN"). Questa cartella è disponibile nel computer in cui è installato Progettazione report. Sono disponibili due copie del file StyleTemplates.xml. Per modificare gli stili applicati tramite Creazione guidata report, modificare il file nella cartella creata per la lingua in uso.  
  
    -   **Assegnazione di un nome al report.**  Nell'ultimo passaggio della procedura guidata si assegna un nome al report e si verificano i campi che verranno inclusi nel report. Dopo il completamento di tutti i passaggi il report viene creato automaticamente e aggiunto al progetto server di report.  
  
### <a name="to-add-a-new-blank-report"></a>Per aggiungere un report vuoto  
  
1.  Scegliere **Aggiungi nuovo elemento** dal menu **Progetto**.  
  
2.  In **Modelli**fare clic su **Report**.  
  
3.  Scegliere **Aggiungi**.  
  
     Un nuovo report vuoto verrà aggiunto al progetto e visualizzato nell'area di progettazione.  
  
### <a name="to-add-an-existing-report"></a>Per aggiungere un report esistente  
  
1.  Dal **Project** menu, fare clic su **Add**e quindi **elemento esistente**.  
  
2.  Passare al percorso del file con estensione rdl, selezionarlo, quindi fare clic su **Aggiungi**.  
  
     l report verrà aggiunto al progetto nella cartella **Report** . Quando il progetto verrà chiuso e riaperto, i report verranno disposti in ordine alfabetico.  
  
## <a name="see-also"></a>Vedere anche  
 [Esercitazioni su Reporting Services &#40;SSRS&#41;](../reporting-services-tutorials-ssrs.md)  
  
  

---
title: Definizione di una dimensione | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 112696db-3838-4b50-91bd-d2ce5fa04ee5
caps.latest.revision: 17
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5c2c40d27d4dc9310ee54d4211efe88777b8c62f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37246731"
---
# <a name="defining-a-dimension"></a>Definizione di una dimensione
  Nell'attività seguente si utilizzerà la Creazione guidata dimensione per compilare una dimensione Date.  
  
> [!NOTE]  
>  Per questa lezione è necessario aver completato tutte le procedure nella lezione 1.  
  
### <a name="to-define-a-dimension"></a>Per definire una dimensione  
  
1.  In Esplora soluzioni, a destra di Microsoft Visual Studio, fare clic con il pulsante destro del mouse su **Dimensioni**e scegliere **Nuova dimensione**. Verrà visualizzata la Creazione guidata dimensione.  
  
2.  Nella pagina iniziale di **Creazione guidata dimensione** fare clic su **Avanti**.  
  
3.  Nella pagina **Selezione metodo di creazione** verificare che la pagina **Usa una tabella esistente** sia selezionata e fare clic su **Avanti**.  
  
4.  Nella pagina **Impostazione informazioni origine** verificare che sia selezionata la vista origine dati **Adventure Works DW 2012** .  
  
5.  Nell'elenco **Tabella principale** selezionare **Data**.  
  
6.  Scegliere **Avanti**.  
  
7.  Nella pagina **Selezione attributi dimensione** selezionare le caselle di controllo accanto agli attributi seguenti:  
  
    -   **Date Key**  
  
    -   **Full Date Alternate Key**  
  
    -   **English Month Name**  
  
    -   **Calendar Quarter**  
  
    -   **Calendar Year**  
  
    -   **Calendar Semester**  
  
8.  Modificare l'impostazione della colonna **Tipo attributo** per l'attributo **Full Date Alternate Key** da **Regolare** a **Data**. A tale scopo, fare clic su **Regolare** nella colonna **Tipo attributo** . Fare quindi clic sulla freccia per espandere le opzioni. Fare poi clic su **Data** > **Calendario** > **Data**. Fare clic su **OK**. Ripetere questi passaggi per modificare il tipo di attributo per gli attributi seguenti:  
  
    -   **English Month Name** in **Mese**  
  
    -   **Calendar Quarter** in **Trimestre**  
  
    -   **Calendar Year** in **Anno**  
  
    -   **Calendar Semester** in **Semestre**  
  
9. Scegliere **Avanti**.  
  
10. Nel riquadro Anteprima della pagina **Completamento procedura guidata** è possibile visualizzare la dimensione **Date** e i relativi attributi.  
  
11. Fare clic su **Fine** per completare la procedura guidata.  
  
     In Esplora soluzioni nel progetto [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial la dimensione Date viene visualizzata nella cartella **Dimensioni** . Al centro dell'ambiente di sviluppo, in Progettazione dimensioni viene visualizzata la dimensione Date.  
  
12. Scegliere **Salva tutti** dal menu **File**.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
 [Definizione di un cubo](lesson-2-2-defining-a-cube.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Dimensioni nei modelli multidimensionali](multidimensional-models/dimensions-in-multidimensional-models.md)   
 [Creare una dimensione utilizzando una tabella esistente](multidimensional-models/create-a-dimension-by-using-an-existing-table.md)   
 [Creare una dimensione usando la Creazione guidata dimensione](multidimensional-models/create-a-dimension-using-the-dimension-wizard.md)  
  
  
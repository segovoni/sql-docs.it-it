---
title: Creare una dimensione mediante Creazione guidata dimensione | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- dimensions [Analysis Services], creating
ms.assetid: d84f66ae-7551-49bf-99d0-88368ca2dd0e
caps.latest.revision: 16
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2c9ee44e40fe25381f4b1e82b69de28fb49cfe56
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37171652"
---
# <a name="create-a-dimension-using-the-dimension-wizard"></a>Creare una dimensione utilizzando la Creazione guidata dimensione
  È possibile creare una nuova dimensione utilizzando Creazione guidata dimensione in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
### <a name="to-create-a-new-dimension"></a>Per creare una nuova dimensione  
  
1.  In **Esplora soluzioni**fare clic con il pulsante destro del mouse su **Dimensioni**e quindi scegliere **Nuova dimensione**.  
  
2.  Nella pagina **Selezione metodo di creazione** della Creazione guidata dimensione selezionare **Utilizza una tabella esistente**e quindi fare clic su **Avanti**.  
  
    > [!NOTE]  
    >  Si potrebbe dovere creare occasionalmente una dimensione senza utilizzare una tabella esistente. Per altre informazioni, vedere [Creare una dimensione generando una tabella non temporale nell'origine dati](create-a-dimension-by-generating-a-non-time-table-in-the-data-source.md) e [Creare una dimensione temporale generando una tabella dei tempi](create-a-time-dimension-by-generating-a-time-table.md).  
  
3.  Nella pagina **Impostazione informazioni origine** eseguire le operazioni seguenti:  
  
    1.  Nell'elenco **Vista origine dati** selezionare una vista origine dati.  
  
    2.  Nell'elenco **Tabella principale** selezionare la tabella delle dimensioni principale.  
  
    3.  Nell'elenco **Colonne chiave** esaminare le colonne chiave selezionate automaticamente dalla procedura guidata in base alla chiave primaria definita nella tabella delle dimensioni principale. Per modificare questa impostazione predefinita, specificare le colonne chiave che collegano la tabella della dimensione alla tabella dei fatti.  
  
    4.  Nell'elenco a discesa **Colonna nome** esaminare la colonna del nome selezionata automaticamente dalla procedura guidata.  
  
         Questo nome predefinito è adatto quando la colonna contiene informazioni descrittive. Tuttavia, è possibile specificare un nome che contenga valori più significativi per l'utente finale. Ad esempio, se un attributo della categoria di prodotto in una dimensione Prodotti usa la colonna **ProductCategoryKey** come colonna chiave, è possibile specificare la colonna **ProductCategoryName** come colonna del nome dell'attributo.  
  
         Se l'elenco **Colonne chiave** contiene più colonne chiave, è necessario specificare una colonna del nome che fornisce i valori del membro per l'attributo chiave. A questo scopo, è possibile creare un calcolo denominato nella vista origine dati e utilizzarlo come colonna del nome.  
  
    5.  Scegliere **Avanti**.  
  
4.  Nella pagina **Selezione tabelle correlate** selezionare le tabelle correlate che si vuole includere nella dimensione e quindi fare clic su **Avanti**.  
  
    > [!NOTE]  
    >  La pagina **Selezione tabelle correlate** è visualizzata se la tabella delle dimensioni principale specificata ha relazioni con altre tabelle delle dimensioni.  
  
5.  Nella pagina **Selezione attributi dimensione** selezionare gli attributi che si vuole includere nella dimensione e quindi fare clic su **Avanti**.  
  
     Facoltativamente, è possibile modificare i nomi di attributo, abilitare o disabilitare l'esplorazione e specificare il tipo di attributo.  
  
    > [!NOTE]  
    >  Per rendere attivi i campi **Consenti esplorazione** e **Tipo attributo** , l'attributo deve essere selezionato in modo da essere incluso nella dimensione.  
  
6.  Nella pagina **Funzionalità di Business Intelligence per la contabilità** selezionare il tipo di conto nella colonna **Tipi di conto predefiniti** e quindi fare clic su **Avanti**.  
  
     Il tipo di conto deve corrispondere a quello della tabella di origine elencato nella colonna **Tipi di conto tabella di origine** .  
  
    > [!NOTE]  
    >  La pagina **Funzionalità di Business Intelligence per la contabilità** è visualizzata se è stato definito un attributo di dimensione **Tipo conto** nella pagina **Selezione attributi dimensione** della procedura guidata.  
  
7.  Nella pagina **Completamento procedura guidata** assegnare un nome alla nuova dimensione e quindi esaminare la struttura della dimensione. Per apportare modifiche, fare clic su **Indietro**. In caso contrario, fare clic su **Fine**.  
  
    > [!NOTE]  
    >  È possibile utilizzare Progettazione dimensioni al termine della Creazione guidata dimensione per aggiungere, rimuovere e configurare attributi e gerarchie nella dimensione.  
  
## <a name="see-also"></a>Vedere anche  
 [Creare una dimensione usando una tabella esistente](create-a-dimension-by-using-an-existing-table.md)  
  
  

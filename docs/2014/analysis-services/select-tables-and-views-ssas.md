---
title: Selezione tabelle e viste (SSAS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.seltablesviews.f1
ms.assetid: 5e8121cc-03f0-4168-98cf-63c5c032bb0b
caps.latest.revision: 10
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: dcc5de5cfa1125ee950b9c86e02445f192199439
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37232051"
---
# <a name="select-tables-and-views-ssas"></a>Selezione tabelle e viste (SSAS)
  Questa pagina dell'**Importazione guidata tabella** consente di selezionare le tabelle e le viste da cui si desidera importare dati. Per accedere alla procedura guidata da [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], dal menu **Modello** selezionare **Importa da origine dati**.  
  
 L'aspetto delle tabelle e delle viste in questa pagina non garantisce che l'importazione verrà completata. Se l'utente specificato nella pagina Impostazioni di rappresentazione non dispone di privilegi sufficienti per leggere dal database selezionato, l'importazione non verrà completata.  
  
 Per origini dati in cui viene utilizzata l'autenticazione di Windows, le credenziali dell'utente corrente vengono utilizzate per recuperare le tabelle e le viste nella finestra di dialogo Selezione tabelle e viste. Per altre origini dati, vengono utilizzate le credenziali fornite nella stringa di connessione per il recupero dei dati.  
  
## <a name="uielement-list"></a>Elenco degli elementi di interfaccia  
 **Server**  
 Viene visualizzato il server al quale si è connessi.  
  
 **Database**  
 Visualizza il database selezionato.  
  
 **Tabelle e viste**  
 Elenca le tabelle e le viste presenti nel database. Selezionare la casella di controllo accanto a ciascuna tabella e visualizzare la tabella che si desidera importare.  
  
 **Tabella di origine**  
 Specifica il nome della tabella di origine in base al tipo di origine dati.  
  
 **Schema**  
 Specifica lo schema in cui è contenuta la tabella di origine. A seconda del tipo di database, un schema funziona come un contenitore per altri oggetti, ad esempio tabelle, nonché indicare la proprietà di tali oggetti.  
  
 **Nome descrittivo**  
 Specifica il nome descrittivo della tabella di origine. Per impostazione predefinita, nella colonna viene visualizzato il nome della tabella di origine presente nella colonna **Tabella di origine** . Modificare il nome se si desidera utilizzare un nome diverso da quello utilizzato nel database di origine.  
  
 **Dettagli filtro**  
 Se è stato applicato un filtro ai dati importati, consente di visualizzare il filtro per l'importazione dei dati nella finestra di dialogo **Dettagli filtro**. Per altre informazioni, vedere [Dettagli filtro &#40;DAX&#41;](filter-details-ssas.md).  
  
 **Anteprima e Applica filtro**  
 Visualizza la finestra di dialogo **Anteprima tabella selezionata** usata per applicare un filtro ai dati importati. Per altre informazioni, vedere [Anteprima tabella selezionata &#40;SSAS&#41;](preview-selected-table-ssas.md).  
  
 **Selezione tabelle correlate**  
 Consente di selezionare per l'importazione le tabelle e le viste correlate alle tabelle e alle viste già selezionate.  
  
  

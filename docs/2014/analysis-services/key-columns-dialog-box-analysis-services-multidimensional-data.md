---
title: Finestra di dialogo colonne (Analysis Services - dati multidimensionali) della chiave | Microsoft Docs
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
- sql.asvs.dimensiondesigner.dbv.dataitemCollection.f1
helpviewer_keywords:
- DataItem Collection dialog box
ms.assetid: 585f27f2-d5eb-4516-b29a-2084010b7d51
caps.latest.revision: 19
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3fbd5ef14875e11cef4144286d82c2b733f4fa2c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37220571"
---
# <a name="key-columns-dialog-box-analysis-services---multidimensional-data"></a>Finestra di dialogo Colonne chiave (Analysis Services - Dati multidimensionali)
  Usare la finestra di dialogo **Colonne chiave** per modificare la proprietà **KeyColumns** di un attributo. Per altre informazioni, vedere [Modificare la proprietà KeyColumn di un attributo](multidimensional-models/attribute-properties-modify-the-keycolumn-property.md).  
  
 **Per visualizzare la finestra di dialogo colonne chiave**  
  
-   In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] o in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], selezionare un attributo e nella finestra **Proprietà** fare clic sul pulsante con i puntini di sospensione (**...**) associato alla proprietà **KeyColumns** di quell'attributo.  
  
## <a name="options"></a>Opzioni  
 **Tabella di origine**  
 Selezionare la tabella di origine per la quale si vogliono selezionare le colonne chiave. È possibile selezionare la tabella di origine da un elenco di tutte le tabelle nella Vista origine dati.  
  
 **Colonne disponibili**  
 Selezionare le colonne da utilizzare come colonne chiave. È possibile selezionare le colonne non ancora selezionate come colonne chiave da un elenco di colonne nella **Tabella di origine** specificata.  
  
 Per aggiungere le colonne selezionate all'elenco **Colonne chiave** fare clic sul pulsante **>** .  
  
 **Colonne chiave**  
 Definire l'ordine delle colonne chiave selezionate. L'ordine delle colonne chiave è importante nel definire la chiave composta corretta. Per ordinare o riordinare l'elenco delle colonne chiave, selezionare una colonna, quindi fare clic sul pulsante **Su** o **Giù** .  
  
 Per rimuovere una colonna dall'elenco **Colonne chiave** , selezionare la colonna e fare click sul pulsante **\<** .  
  
 **Su**  
 Fare clic per spostare verso l'alto di una posizione la colonna selezionata in **Colonne chiave** .  
  
> [!NOTE]  
>  Questa opzione è abilitata solo se l'elenco contiene più di una colonna e una colonna è selezionata.  
  
 **Giù**  
 Fare clic per spostare verso il basso di una posizione la colonna selezionata in **Colonne chiave** .  
  
> [!NOTE]  
>  Questa opzione è abilitata solo se l'elenco contiene più di una colonna e una colonna è selezionata.  
  
 **>**  
 Fare clic per aggiungere una nuova colonna alla fine delle colonne elencate in **Colonne chiave**.  
  
 **<**  
 Fare clic per rimuovere la colonna selezionata dalle colonne elencate in **Colonne chiave**.  
  
## <a name="see-also"></a>Vedere anche  
 [Finestre di progettazione e finestre di dialogo di Analysis Services &#40;dati multidimensionali&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  

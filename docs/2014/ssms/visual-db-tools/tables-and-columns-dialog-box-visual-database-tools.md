---
title: Finestra di dialogo Tabelle e colonne (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.tablesandcolumns
ms.assetid: 8cf27be1-e66d-4735-a428-9ab4b33af4f5
caps.latest.revision: 14
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 167015bff4e1b27f7106c3b999069b69ccf01ee7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37293971"
---
# <a name="tables-and-columns-dialog-box-visual-database-tools"></a>Finestra di dialogo Tabelle e colonne (Visual Database Tools)
  Questa finestra di dialogo consente di eseguire il mapping di una chiave primaria in una tabella a una chiave esterna in un'altra tabella. Per accedere a tale finestra di dialogo, scegliere **Relazioni** dal menu **Progettazione tabelle**. Nella finestra di dialogo **Relazioni chiavi esterne** fare clic sul campo **Specifica tabelle e colonne** e quindi sui puntini di sospensione **(…)** a destra della proprietà.  
  
> [!NOTE]  
>  Se la tabella viene pubblicata per la replica, è necessario apportare modifiche allo schema usando l'istruzione [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) di Transact-SQL oppure SMO (SQL Server Management Objects). Quando si apportano modifiche allo schema utilizzando Progettazione tabelle o Progettazione diagrammi di database, viene effettuato il tentativo di rimuovere e rigenerare la tabella. La modifica allo schema non riuscirà, poiché non è consentita la rimozione di oggetti pubblicati.  
  
## <a name="options"></a>Opzioni  
 **Nome relazione**  
 Visualizza il nome della relazione.  
  
 **Tabella chiave primaria**  
 Elenca le tabelle del database. Scegliere la tabella che si troverà sul lato chiave primaria della relazione.  
  
 **Tabella chiave esterna**  
 Visualizza la tabella sul lato chiave esterna della relazione. Corrisponde alla tabella attualmente selezionata in Progettazione tabelle.  
  
 **Griglia al di sotto della tabella di chiave primaria**  
 Elenca le colonne della tabella selezionata nell'elenco **Tabella chiave primaria** . Immettere le colonne che contribuiscono alla chiave primaria della tabella.  
  
 **Griglia al di sotto della tabella di chiave esterna**  
 Elenca le colonne della tabella selezionata nell'elenco **Tabella chiave esterna** . Immettere la colonna chiave esterna della tabella di chiave esterna che corrisponde alla colonna chiave primaria.  
  
> [!NOTE]  
>  Le colonne selezionate per la chiave esterna devono avere lo stesso tipo di dati delle colonne primarie a cui corrispondono. In ogni chiave deve esistere un numero uguale di colonne. Se ad esempio la chiave primaria della tabella sul lato primario della relazione è composta da due colonne, ognuna di queste colonne dovrà corrispondere a una colonna della tabella sul lato chiave esterna della relazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Creare relazioni di chiave esterna](../../relational-databases/tables/create-foreign-key-relationships.md)  
  
  

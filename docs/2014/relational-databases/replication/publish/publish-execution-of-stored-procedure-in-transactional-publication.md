---
title: Pubblicare l'esecuzione di una Stored Procedure in una pubblicazione transazionale (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- publishing [SQL Server replication], stored procedure execution
- stored procedures [SQL Server replication], publishing
ms.assetid: 1d3a3525-0bc5-466f-b097-5359dc74432d
caps.latest.revision: 14
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 55cfa244fa0d4ac5716a2978487b5b4be74ad257
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37274817"
---
# <a name="publish-the-execution-of-a-stored-procedure-in-a-transactional-publication-sql-server-management-studio"></a>Pubblicazione dell'esecuzione di una stored procedure in una pubblicazione transazionale (SQL Server Management Studio)
  Specificare che nella finestra di dialogo **Proprietà articolo - \<Articolo>** deve essere pubblicata l'esecuzione di una stored procedure, anziché la sola definizione. Questa finestra di dialogo è disponibile nella Creazione guidata nuova pubblicazione e nella finestra di dialogo **Proprietà pubblicazione - \<Pubblicazione>**. Per altre informazioni sull'uso della creazione guidata e l'accesso alla finestra di dialogo, vedere [Creare una pubblicazione](create-a-publication.md) e [Visualizzare e modificare le proprietà della pubblicazione](view-and-modify-publication-properties.md).  
  
 La definizione della procedura, ovvero l'istruzione CREATE PROCEDURE, viene replicata nel Sottoscrittore durante l'inizializzazione della sottoscrizione. Quando la procedura viene eseguita nel server di pubblicazione, la replica esegue la procedura corrispondente nel Sottoscrittore.  
  
### <a name="to-publish-the-execution-of-a-stored-procedure"></a>Per pubblicare l'esecuzione di una stored procedure  
  
1.  Nella pagina **Articoli** della Creazione guidata nuova pubblicazione o nella finestra di dialogo **Proprietà pubblicazione - \<Pubblicazione>** selezionare una stored procedure.  
  
2.  Fare clic su **Proprietà articolo**e quindi su **Imposta proprietà dell'articolo di stored procedure evidenziato**.  
  
3.  Nella finestra di dialogo **Proprietà articolo - \<Articolo>** specificare uno dei valori seguenti per l'opzione **Replica**:  
  
    -   **Esecuzione della stored procedure**  
  
    -   **Esecuzione in una transazione serializzata della stored procedure**  
  
         Questa è l'opzione consigliata in quanto replica l'esecuzione della procedura solo se essa viene eseguita all'interno del contesto di una transazione serializzabile. Se viene eseguita in un contesto diverso, le modifiche ai dati delle tabelle pubblicate vengono replicate come una serie di istruzioni DML (Data Manipulation Language).  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  Se è visualizzata la finestra di dialogo **Proprietà pubblicazione - \<Pubblicazione>** fare clic su **OK** per salvare e chiudere la finestra di dialogo.  
  
## <a name="see-also"></a>Vedere anche  
 [Pubblicazione dell'esecuzione delle stored procedure nella replica transazionale](../transactional/publishing-stored-procedure-execution-in-transactional-replication.md)  
  
  

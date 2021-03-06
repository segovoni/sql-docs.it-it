---
title: Finestra di dialogo Aggiorna tabella (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-visual-db
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.updatetable
- vdtsql.chm:69643
ms.assetid: 174c7275-5b15-42a9-b172-5ff30de575a1
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9482391137fa5a1f12fa12defcfde274c0bac680
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33048648"
---
# <a name="update-table-dialog-box-visual-database-tools"></a>Finestra di dialogo Aggiorna tabella (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Questa finestra di dialogo consente di specificare la tabella da aggiornare.  
  
Viene visualizzata quando nel riquadro Diagramma sono aperte più tabelle e si cambia il tipo di query in modo da disporre di una query di aggiornamento (Update).  
  
Selezionare la tabella da aggiornare e scegliere **OK**.\  
  
> [!NOTE]  
> Se la tabella viene pubblicata per la replica, è necessario apportare modifiche allo schema usando l'istruzione [ALTER TABLE](http://msdn.microsoft.com/en-us/f1745145-182d-4301-a334-18f799d361d1) di Transact-SQL oppure SMO (SQL Server Management Objects). Quando si apportano modifiche allo schema utilizzando Progettazione tabelle o Progettazione diagrammi di database, viene effettuato il tentativo di rimuovere e rigenerare la tabella. La modifica allo schema non riuscirà, poiché non è consentita la rimozione di oggetti pubblicati.  
  
## <a name="see-also"></a>Vedere anche  
[Creazione di query di aggiornamento (Visual Database Tools)](../../ssms/visual-db-tools/create-update-queries-visual-database-tools.md)  
  

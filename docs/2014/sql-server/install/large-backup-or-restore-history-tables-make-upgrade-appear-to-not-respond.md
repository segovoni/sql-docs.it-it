---
title: Tabelle di cronologia di backup o ripristino grandi aggiornamento potrebbe apparire non rispondere | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- backup history tables
- history tables
ms.assetid: f88d86ec-324b-4518-b6d7-1af7e7265812
caps.latest.revision: 21
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d01d73f9456d56a8f12698b954213289ab4921d7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37208501"
---
# <a name="large-backup-or-restore-history-tables-make-upgrade-appear-to-not-respond"></a>Se sono presenti tabelle di cronologia di backup o ripristino di grandi dimensioni, l'aggiornamento potrebbe sembrare che non risponde
  In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] sono state aggiunte nuove colonne ad alcune delle tabelle di cronologia di backup e ripristino. Per aggiornare queste tabelle, è necessario modificarle in modo da aggiungere le nuove colonne. Se una o più di queste tabelle contengono un numero elevato di righe, l'aggiornamento richiederà molto tempo per l'istruzione ALTER TABLE che aggiunge colonne a tale tabella.  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 L'aggiornamento potrebbe apparire bloccato se una delle seguenti tabelle di cronologia di backup o ripristino contiene un numero elevato di righe:  
  
-   **backupfile**  
  
-   **backupmediafamily**  
  
-   **backupmediaset**  
  
-   **backupset**  
  
-   **restorefile**  
  
-   **restorefilegroup**  
  
-   **restorehistory**  
  
 Se una di queste tabelle contiene almeno 10.000 righe, verrà segnalato un errore di non conformità. La tabella che supera il numero consentito di righe non viene indicata. La prima tabella che supera le 10.000 righe genera l'errore.  
  
## <a name="corrective-action"></a>Azione correttiva  
 Prima di aggiornare un database, se una di queste tabelle supera le 10.000 righe, si consiglia di ridurre questo numero. Per ridurre le righe in tutte queste tabelle, è possibile eseguire la **sp_delete_backuphistory** stored procedure. Questa procedura elimina le voci in tutte le tabelle di cronologia di backup e ripristino relative a set di backup precedenti a una data specificata. Per altre informazioni, vedere [sp_delete_backuphistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql).  
  
> [!NOTE]  
>  È possibile aggiornare un database le cui tabelle di cronologia di backup e ripristino contengono più di 10.000 righe, ma il processo potrebbe sembrare bloccato durante la modifica di tabelle di grandi dimensioni. Le dimensioni delle tabelle influiscono sul tempo richiesto per completare il programma di installazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento del motore di database](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Preparazione aggiornamento a SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  

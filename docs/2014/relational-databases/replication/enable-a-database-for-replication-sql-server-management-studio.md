---
title: Abilitare un database per la replica (SQL Server Management Studio) | Microsoft Docs
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
- databases [SQL Server replication]
ms.assetid: 8092faa3-9cff-4f81-926c-6a0070d1ce2c
caps.latest.revision: 31
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9be2fcfab6582aa801db160e45aa2968f7f65ff0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37210981"
---
# <a name="enable-a-database-for-replication-sql-server-management-studio"></a>Abilitazione di un database per la replica (SQL Server Management Studio)
  Un database viene implicitamente abilitato per la replica quando un membro del ruolo predefinito del server **sysadmin** crea una pubblicazione mediante la Creazione guidata nuova pubblicazione. Il membro del ruolo predefinito del server **sysadmin** può inoltre abilitare esplicitamente un database per la replica, in modo che un membro del ruolo predefinito del database **db_owner** possa creare una o più pubblicazioni in tale database. A tale scopo, usare la pagina **Database di pubblicazione** della finestra di dialogo **Proprietà server di pubblicazione - \<ServerPubblicazione>**. Per ulteriori informazioni sull'accesso a questa finestra di dialogo, vedere [Create a Publication](publish/create-a-publication.md).  
  
### <a name="to-enable-a-database-for-replication"></a>Per abilitare un database per la replica  
  
1.  Nella pagina **Database di pubblicazione** della finestra di dialogo **Proprietà server di pubblicazione - \<ServerPubblicazione>** selezionare la casella di controllo **Transazionale** e/o **Merge** per ogni database da replicare. Selezionare **Transazionale** per abilitare il database per la replica snapshot.  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
  

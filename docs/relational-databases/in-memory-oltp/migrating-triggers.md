---
title: Migrazione di trigger | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: in-memory-oltp
ms.reviewer: ''
ms.suite: sql
ms.technology: in-memory-oltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ad5385c5-5a50-40ca-a319-97d5606b8511
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 81f631999a3cf9867c4668f108f4cebdc7a03fe1
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2018
ms.locfileid: "34326712"
---
# <a name="migrating-triggers"></a>Migrazione di trigger
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  In questo argomento vengono illustrati i trigger DDL e le tabelle ottimizzate per la memoria.  
  
 I trigger DML sono supportati nelle tabelle ottimizzate per la memoria, ma solo con l'evento trigger FOR | AFTER. Ad esempio, vedere [Implementing UPDATE with FROM or Subqueries](../../relational-databases/in-memory-oltp/implementing-update-with-from-or-subqueries.md)(Implementazione di UPDATE con FROM o sottoquery). 
  
 I trigger LOGON sono trigger definiti per l'attivazione in corrispondenza di eventi LOGON. I trigger LOGON non influiscono sulle tabelle ottimizzate per la memoria.  
  
## <a name="ddl-triggers"></a>Trigger DDL  
 I trigger DDL sono trigger definiti per l'attivazione quando un'istruzione CREATE, ALTER, DROP, GRANT, DENY, REVOKE o UPDATE STATISTICS viene eseguita nel database o nel server in cui è definita.  
  
 Non è possibile creare tabelle ottimizzate per la memoria se nel database o nel server sono definiti uno o più trigger DDL per l'evento CREATE_TABLE o per qualsiasi gruppo di eventi in cui questo sia incluso. Non è possibile eliminare una tabella ottimizzata per la memoria se nel database o nel server sono definiti uno o più trigger DDL per l'evento DROP_TABLE o per qualsiasi gruppo di eventi in cui questo sia incluso.  
  
 Non è possibile creare stored procedure compilate in modo nativo se sono presenti uno o più trigger DDL per gli eventi CREATE_PROCEDURE, DROP_PROCEDURE o per qualsiasi gruppo di eventi in cui questi siano inclusi.  
  
## <a name="see-also"></a>Vedere anche  
 [Migrazione a OLTP in memoria](../../relational-databases/in-memory-oltp/migrating-to-in-memory-oltp.md)  
  
  

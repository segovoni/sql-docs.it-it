---
title: Visualizzare gli eventi per i pacchetti registrati | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- viewing events
- extended events [SQL Server], viewing events
ms.assetid: 9a90b1a2-aa69-43f6-bdeb-cc5f57a26c6f
caps.latest.revision: 16
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0610697d8e5b743729985d4a7fe3dbec5a2743f2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37213371"
---
# <a name="view-the-events-for-registered-packages"></a>Visualizzare gli eventi per i pacchetti registrati
  Prima di creare una sessione degli eventi estesi di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], è utile individuare gli eventi disponibili nei pacchetti registrati. Per ulteriori informazioni, vedere [SQL Server Extended Events Packages](../relational-databases/extended-events/sql-server-extended-events-packages.md).  
  
 Il completamento di questa attività comporta l'utilizzo dell'editor di query in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] per effettuare la procedura descritta di seguito.  
  
 Al termine delle istruzioni in questa procedura, nella scheda **Results** dell'editor di query vengono visualizzate le colonne seguenti:  
  
-   name. Nome del pacchetto.  
  
-   event. Nome dell'evento.  
  
-   keyword. Parola chiave derivata da una tabella di mapping numerica interna.  
  
-   channel. Gruppo di destinatari per un evento.  
  
-   description. Descrizione dell'evento.  
  
## <a name="to-view-the-events-for-registered-packages-using-query-editor"></a>Per visualizzare gli eventi per i pacchetti registrati utilizzando l'editor di query  
  
-   Nell'editor di query eseguire le istruzioni indicate di seguito.  
  
    ```  
    USE msdb  
    SELECT p.name, c.event, k.keyword, c.channel, c.description FROM  
    (  
    SELECT event_package=o.package_guid, o.description,   
    event=c.object_name, channel=v.map_value  
    FROM sys.dm_xe_objects o  
    LEFT JOIN sys.dm_xe_object_columns c ON o.name=c.object_name  
    INNER JOIN sys.dm_xe_map_values v ON c.type_name=v.name   
    AND c.column_value=cast(v.map_key AS nvarchar)  
    WHERE object_type='event' AND (c.name='CHANNEL' or c.name IS NULL)  
  
    ) c LEFT JOIN   
    (  
    SELECT event_package=c.object_package_guid, event=c.object_name,   
    keyword=v.map_value  
    FROM sys.dm_xe_object_columns c INNER JOIN sys.dm_xe_map_values v   
    ON c.type_name=v.name AND c.column_value=v.map_key   
    AND c.type_package_guid=v.object_package_guid  
    INNER JOIN sys.dm_xe_objects o ON o.name=c.object_name   
    AND o.package_guid=c.object_package_guid  
    WHERE object_type='event' AND c.name='KEYWORD'   
    ) k  
    ON  
    k.event_package=c.event_package AND (k.event=c.event or k.event IS NULL)  
    INNER JOIN sys.dm_xe_packages p ON p.guid=c.event_package  
    ORDER BY keyword desc, channel, event  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Pacchetti degli eventi estesi di SQL Server](../relational-databases/extended-events/sql-server-extended-events-packages.md)   
 [sys.dm_xe_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql)   
 [sys.dm_xe_packages &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-packages-transact-sql)  
  
  

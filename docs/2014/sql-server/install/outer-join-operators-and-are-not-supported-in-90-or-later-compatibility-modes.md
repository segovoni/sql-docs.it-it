---
title: Operatori outer join *= e =* non sono supportati in modalità di compatibilità 90 o versioni successive | Microsoft Docs
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
- outer joins
- =* join
- '*= join'
- joins [SQL Server]
ms.assetid: ca4aa11f-1048-411f-9c6c-3d0a8e319f2f
caps.latest.revision: 12
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 579565320855694166f57039402e3fbef14183d5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37255443"
---
# <a name="outer-join-operators--and--are-not-supported-in-90-or-later-compatibility-modes"></a>Operatori outer join *= e =* non sono supportati nella modalità di compatibilità 90 o successiva
  Preparazione aggiornamento è stato rilevato l'utilizzo di operatori outer join * = e =\*. Tali operatori non sono supportati nella modalità di compatibilità 90 o successiva Quando si esegue l'aggiornamento, la modalità di compatibilità dei database utente non cambia. Le istruzioni in cui sono utilizzati questi operatori non riusciranno.  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Azione correttiva  
 Prima di impostare la modalità di compatibilità del database su 90 o successiva, modificare le istruzioni che utilizzano gli operatori outer join * = e =\* usare parole chiave OUTER JOIN equivalenti. Nell'esempio seguente vengono illustrate una query che utilizza l'operatore `*=` e una query equivalente che utilizza le parole chiave `LEFT OUTER JOIN`.  
  
```  
-- This query uses an old-style outer join operator.  
USE pubs  
SELECT employee.job_id, employee.emp_id,  
   employee.fname, employee.minit, jobs.job_desc  
FROM employee, jobs   
WHERE employee.job_id *= jobs.job_id  
ORDER BY employee.job_id  
  
-- This query uses the ANSI standard keywords LEFT OUTER JOIN.  
USE pubs;  
SELECT employee.job_id, employee.emp_id,  
   employee.fname, employee.minit, jobs.job_desc  
FROM employee LEFT OUTER JOIN jobs ON   
    employee.job_id = jobs.job_id  
ORDER BY employee.job_id  
```  
  
 Per ulteriori informazioni sugli outer join, vedere "Utilizzo di outer join" nella documentazione online di SQL Server.  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento del motore di database](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Preparazione aggiornamento a SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  

---
title: MSSQLSERVER_10537 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 10537 (Database Engine error)
ms.assetid: 728469a4-6523-4a37-925f-a950d75420fa
caps.latest.revision: 9
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6fa0fbe4e0881c82ce58fc259401846b3f321837
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37411636"
---
# <a name="mssqlserver10537"></a>MSSQLSERVER_10537
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|10537|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|PG_DUP_ENABLED|  
|Testo del messaggio|Impossibile abilitare la guida di pano '%.*ls' perché la guida di piano '%.\*ls' abilitata contiene lo stesso ambito e lo stesso valore di offset iniziale dell'istruzione. Disabilitare la guida di piano esistente prima di abilitare la guida di piano specificata.|  
  
## <a name="explanation"></a>Spiegazione  
 Una guida di piano esistente abilitata contiene lo stesso ambito e lo stesso valore di offset iniziale dell'istruzione presente nella guida di piano specificata.  
  
## <a name="user-action"></a>Azione dell'utente  
 Disabilitare la guida di piano esistente prima di abilitare la guida di piano specificata.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [Guide di piano](../performance/plan-guides.md)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  

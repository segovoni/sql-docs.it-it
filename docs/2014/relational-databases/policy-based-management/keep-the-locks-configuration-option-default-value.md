---
title: Mantenere il valore predefinito per l'opzione di configurazione dei blocchi | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: f214f05b-5f0b-4786-b2ad-b8b4b6e58d72
caps.latest.revision: 12
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d2ef15536a79b5e67de7907ce6a8bdf5595c49f4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37280862"
---
# <a name="keep-the-locks-configuration-option-default-value"></a>Impostazione dell'opzione di configurazione dei blocchi sul valore predefinito
  Questa regola consente di controllare il valore dell'opzione di configurazione dei blocchi, che determina il numero massimo di blocchi disponibili. Tale valore limita la quantità di memoria utilizzata dal [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] per i blocchi. L'impostazione predefinita 0 consente al [!INCLUDE[ssDE](../../includes/ssde-md.md)] di allocare e deallocare strutture di blocco in modo dinamico in base alle variazioni dei requisiti di sistema.  
  
 Se il valore relativo ai blocchi è diverso da zero, i processi batch si arresteranno e verrà generato un messaggio di errore indicante un numero insufficiente di blocchi quando viene superato il valore specificato.  
  
## <a name="best-practices-recommendations"></a>Procedure consigliate  
 Utilizzare la stored procedure di sistema sp_configure per impostare l'opzione relativa ai blocchi sul valore predefinito tramite l'istruzione seguente:  
  
```  
EXEC sp_configure 'locks', 0;  
```  
  
## <a name="for-more-information"></a>Ulteriori informazioni  
 [Configurare l'opzione di configurazione del server locks](../../database-engine/configure-windows/configure-the-locks-server-configuration-option.md)  
  
 [sys.dm_tran_locks &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql)  
  
 [sys.dm_os_wait_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql)  
  
 [Articolo 271509 della Microsoft Knowledge Base](http://go.microsoft.com/fwlink/?linkid=117788)  
  
## <a name="see-also"></a>Vedere anche  
 [Monitorare e applicare le procedure consigliate tramite la gestione basata su criteri](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  

---
title: L'aggiornamento verrà modificato l'Account Proxy utente di SQL Server Agent dall'account temporaneo UpgradedProxyAccount | Microsoft Docs
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
- log shipping [SQL Server Agent]
ms.assetid: cd2d08c3-4e56-4034-8b68-0c78df8b5471
caps.latest.revision: 18
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 14b79ad393db1360520e060b118c8a4e280e358b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37292091"
---
# <a name="upgrading-will-change-the-sql-server-agent-user-proxy-account-to-the-temporary-upgradedproxyaccount"></a>In seguito all'aggiornamento l'account proxy utente per SQL Server Agent verrà sostituito dall'account temporaneo UpgradedProxyAccount
  I piani di manutenzione del database con il log shipping abilitato non verranno abilitati dopo l'aggiornamento.  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent  
  
## <a name="description"></a>Description  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è disponibile un nuovo set di funzioni di log shipping che non sono direttamente compatibili con i piani di manutenzione del database.  
  
## <a name="corrective-action"></a>Azione correttiva  
 Gli utenti di [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] i cui piani di manutenzione del database contengono funzioni di log shipping devono configurare il log shipping utilizzando le nuove funzioni. Per ulteriori informazioni, cercare "log shipping" nella documentazione online di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Categoria di processi di SQL Server Agent log shipping comporta l'aggiornamento di](../../../2014/sql-server/install/sql-server-agent-log-shipping-job-category-causes-upgrade-to-fail.md)   
 [Il log shipping non verrà eseguito dopo l'aggiornamento](../../../2014/sql-server/install/log-shipping-will-not-run-after-upgrading.md)  
  
  

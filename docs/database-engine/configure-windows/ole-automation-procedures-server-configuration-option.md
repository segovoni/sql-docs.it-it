---
title: Opzione di configurazione del server Ole Automation Procedures | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.suite: sql
ms.technology: configuration
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Ole Automation Procedures option
ms.assetid: e8982e05-4984-4406-9760-285e8c028ddf
caps.latest.revision: 20
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 55e0cd91d46f560de2c5cee204158bc4076273ec
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32864266"
---
# <a name="ole-automation-procedures-server-configuration-option"></a>Opzione di configurazione del server Ole Automation Procedures
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Usare l'opzione **Ole Automation Procedures** per specificare se è possibile creare un'istanza degli oggetti di automazione OLE all'interno di batch [!INCLUDE[tsql](../../includes/tsql-md.md)] . Questa opzione può essere configurata usando anche la gestione basata su criteri o la stored procedure **sp_configure** . Per ulteriori informazioni, vedere [Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md).  
  
 L'opzione **Ole Automation Procedures** può essere impostata su uno dei valori seguenti.  
  
 0  
 L'opzione Ole Automation Procedures è disabilitata. Impostazione predefinita per le nuove istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 1  
 L'opzione Ole Automation Procedures è abilitata.  
  
 Quando l'opzione Ole Automation Procedures è abilitata, l'ambiente di esecuzione condiviso OLE viene avviato mediante una chiamata a **sp_OACreate** .  
  
 È possibile visualizzare e modificare il valore corrente dell'opzione **Ole Automation Procedures** mediante la stored procedure di sistema **sp_configure** .  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene illustrata la procedura per la visualizzazione dell'impostazione corrente dell'opzione Ole Automation Procedures.  
  
```  
EXEC sp_configure 'Ole Automation Procedures';  
GO  
```  
  
 Nell'esempio seguente viene illustrata la procedura per l'abilitazione dell'opzione Ole Automation Procedures.  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'Ole Automation Procedures', 1;  
GO  
RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Configurazione superficie di attacco](../../relational-databases/security/surface-area-configuration.md)   
 [Opzioni di configurazione del server &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
  

---
title: sysmail_stop_sp (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sysmail_stop_sp_TSQL
- sysmail_stop_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_stop_sp
ms.assetid: 045ee36f-5bf0-4626-b5ee-e84db06ce16f
caps.latest.revision: 28
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8f304337470d0117b6f44d03bf7e459c6b9f51d5
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33257783"
---
# <a name="sysmailstopsp-transact-sql"></a>sysmail_stop_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Arresta l'esecuzione di Posta elettronica database mediante l'arresto degli oggetti di [!INCLUDE[ssSB](../../includes/sssb-md.md)] utilizzati dal programma esterno.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sysmail_stop_sp  
```  
  
## <a name="arguments"></a>Argomenti  
 Nessuno  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 Questa stored procedure è nel **msdb** database.  
  
 Questa stored procedure arresta la coda di Posta elettronica database contenente le richieste dei messaggi in uscita e disabilita [!INCLUDE[ssSB](../../includes/sssb-md.md)] per il programma esterno.  
  
 Se le code vengono arrestate, il programma esterno Posta elettronica database non elabora i messaggi. Questa stored procedure consente di arrestare l'esecuzione di Posta elettronica database per motivi di manutenzione o risoluzione dei problemi.  
  
 Per avviare posta elettronica Database, utilizzare **sysmail_start_sp**. Si noti che **sp_send_dbmail** continua ad accettare posta elettronica quando il [!INCLUDE[ssSB](../../includes/sssb-md.md)] gli oggetti vengono arrestati.  
  
> [!NOTE]  
>  Questa stored procedure arresta solo le code di Posta elettronica database e non disattiva il recapito dei messaggi di [!INCLUDE[ssSB](../../includes/sssb-md.md)] nel database. Questa stored procedure non disabilita le stored procedure estese di Posta elettronica database per ridurre la superficie di attacco. Per disabilitare le stored procedure estese, vedere il [opzione Database Mail XPs](../../database-engine/configure-windows/database-mail-xps-server-configuration-option.md) del **sp_configure** stored procedure di sistema.  
  
## <a name="permissions"></a>Autorizzazioni  
 Autorizzazioni di esecuzione per questa routine per impostazione predefinita ai membri del **sysadmin** ruolo predefinito del server.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene illustrato l'arresto di posta elettronica Database nel **msdb** database. Nell'esempio si presuppone che il programma esterno Posta elettronica database sia stato abilitato.  
  
```  
USE msdb ;  
GO  
  
EXECUTE dbo.sysmail_stop_sp ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Posta elettronica database](../../relational-databases/database-mail/database-mail.md)   
 [sysmail_start_sp &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-start-sp-transact-sql.md)   
 [Stored procedure di posta elettronica database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  

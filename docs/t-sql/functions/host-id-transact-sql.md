---
title: HOST_ID (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- HOST_ID
- HOST_ID_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IDs [SQL Server], workstations
- HOST_ID function
- workstation IDs [SQL Server]
- identification numbers [SQL Server], workstations
ms.assetid: 36ba56d4-20d7-4cd1-aa2a-e40a6c0a4e39
caps.latest.revision: 22
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2595affaab1b4ad214d727e3b3a8dda12c52a4fe
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/04/2018
ms.locfileid: "37790772"
---
# <a name="hostid-transact-sql"></a>HOST_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce il numero di identificazione della workstation. Questo numero corrisponde all'ID di processo (PID) dell'applicazione nel computer client che si connette a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
HOST_ID ()  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 **char(10)**  
  
## <a name="remarks"></a>Remarks  
 Se il parametro per una funzione di sistema è facoltativo, vengono utilizzati il database, il computer host, l'utente del server o l'utente del database correnti. Le funzioni predefinite devono essere sempre seguite da parentesi.  
  
 È possibile utilizzare funzioni di sistema nell'elenco di selezione, nella clausola WHERE e in tutti i casi in cui è consentita un'espressione.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene creata una tabella che utilizza `HOST_ID()` in una definizione `DEFAULT` per registrare gli ID dei terminali dei computer che inseriscono righe in una tabella di registrazione degli ordini.  
  
```  
CREATE TABLE Orders  
   (OrderID     int       PRIMARY KEY,  
    CustomerID  nchar(5)  REFERENCES Customers(CustomerID),  
    TerminalID  char(8)   NOT NULL DEFAULT HOST_ID(),  
    OrderDate   datetime  NOT NULL,  
    ShipDate    datetime  NULL,  
    ShipperID   int       NULL REFERENCES Shippers(ShipperID));  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Espressioni &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Funzioni di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)  
  
  

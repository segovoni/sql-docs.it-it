---
title: Numeri di errori nativi | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ODBC error handling, native error numbers
- SQL Server Native Client ODBC driver, errors
- native error numbers [SQL Server Native Client]
- messages [ODBC], native error numbers
- errors [ODBC], native error numbers
ms.assetid: 77cbc826-f47f-4803-8e7a-223d6df069b1
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 7b69031278c26fcc06463195d41bcd12a71ce84d
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37409900"
---
# <a name="native-error-numbers"></a>Numeri di errori nativi
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Per gli errori che si verificano nell'origine dati (restituiti da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]), il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client restituisce il numero di errori nativi restituito da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per gli errori rilevati dal driver, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client restituisce un numero di errori nativi pari a 0. Per altre informazioni su un elenco di numeri di errori nativi, vedere la colonna degli errori di **sysmessages** tabella di sistema il **master** del database in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Per informazioni sui codici di errore di stato, vedere [SQLSTATE &#40;codici di errore ODBC&#41;](../../relational-databases/native-client-odbc-error-messages/sqlstate-odbc-error-codes.md). Per gli errori restituiti dalla libreria di rete, il numero di errori nativi viene derivato dal software di rete sottostante.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione di errori e messaggi](../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  

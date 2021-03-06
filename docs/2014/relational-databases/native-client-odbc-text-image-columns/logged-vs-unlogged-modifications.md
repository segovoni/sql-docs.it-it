---
title: Visual Studio connesso. Le modifiche registrate | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- text columns [ODBC]
- SQL Server Native Client ODBC driver, image columns
- SQL Server Native Client ODBC driver, text columns
- data types [ODBC], image
- data types [ODBC], text
- logged vs. nonlogged modifications [SQL Server Native Client]
- columns [ODBC]
- ODBC data types, image columns
- nonlogged vs. logged modifications
- ODBC data types, text columns
- image columns [ODBC]
ms.assetid: 20aa5b27-4a2c-46e7-8356-beb0eebf4b7e
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 34064aaa2e96a7d610f8709c1f5750bddd62b766
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37420291"
---
# <a name="logged-vs-unlogged-modifications"></a>Visual Studio connesso. Registrate e non registrate
  Un'applicazione può richiedere che il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client non registro **testo**, **ntext**, e **immagine** le modifiche. Questa opzione deve essere utilizzata con una certa cautela e Deve essere usato solo per quelle situazioni in cui il **testo**, **ntext**, o **immagine** dati non critici e i proprietari sono disposti a rinunciare alla possibilità di ripristinare i dati per prestazioni più elevate.  
  
 La registrazione delle **testo**, **ntext**, e **immagine** le modifiche vengono controllate chiamando [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) con i  *Attributo* parametro è impostato su sql_sopt_ss _ TEXTPTR_LOGGING e *ValuePtr* impostato su SQL_TL_ON o SQL_TL_OFF.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione di colonne di tipo text e image](managing-text-and-image-columns.md)  
  
  

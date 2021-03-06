---
title: SQLGetInfo (Driver di File di testo) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLGetInfo function [ODBC], Text File Driver
- text file driver [ODBC], SQLGetInfo
ms.assetid: 6b7a630e-47f8-4ee1-b2a7-476bc1d0b0d4
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9645b3148c3a3a391a65f158a4d8d28471239d36
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32904566"
---
# <a name="sqlgetinfo-text-file-driver"></a>SQLGetInfo (Driver di File di testo)
> [!NOTE]  
>  In questo argomento fornisce informazioni specifiche del Driver File di testo. Per informazioni generali su questa funzione, vedere l'argomento appropriato in [riferimento all'API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **SQLGetInfo** supporta il tipo di informazioni SQL_FILE_USAGE. Il valore restituito è un valore integer a 16 bit che indica il modo in cui il driver considera direttamente i file in un'origine dati:  
  
-   SQL_FILE_NOT_SUPPORTED, Il driver non è un driver a un solo livello.  
  
-   SQL_FILE_TABLE, ovvero Un driver a un solo livello considera i file in un'origine dati come tabelle.  
  
-   SQL_FILE_QUALIFIER, I file in un'origine dati un driver a un solo livello vengono considerati un qualificatore.  
  
 Il driver ODBC restituisce SQL_FILE_TABLE per Textdriver, poiché ogni file è una tabella.  
  
## <a name="sqldbmsver"></a>SQL_DBMS_VER  
  
|ISAM|Versione|Formato dei numeri di versione|  
|----------|-------------|-------------------------------|  
|Text|1,0|01.00.0000|  
  
## <a name="sqlcatalogusage"></a>SQL_CATALOG_USAGE  
 SQL_QU_DML_STATEMENTS &AMP;#124; SQL_QU_TABLE_DEFINITION  
  
## <a name="sqltimedatefunctions"></a>SQL_TIMEDATE_FUNCTIONS  
 SQL_FN_TD_CURDATE &AMP;#124; SQL_FN_TD_CURTIME &AMP;#124; SQL_FN_TD_DAYOFMONTH &AMP;#124; SQL_FN_TD_DAYOFWEEK &AMP;#124; SQL_FN_TD_DAYOFYEAR &AMP;#124; SQL_FN_TD_HOUR &AMP;#124; SQL_FN_TD_MINUTE &AMP;#124; SQL_FN_TD_MONTH &AMP;#124; SQL_FN_TD_NOW &AMP;#124; SQL_FN_TD_SECOND &AMP;#124; SQL_FN_TD_WEEK &AMP;#124; SQL_FN_TD_YEAR

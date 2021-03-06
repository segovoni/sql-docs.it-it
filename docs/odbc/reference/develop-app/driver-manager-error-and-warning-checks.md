---
title: Errore di Gestione driver e i controlli di avviso | Documenti Microsoft
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
- diagnostic information [ODBC], driver manager error checking
- driver manager [ODBC], error checking
ms.assetid: eeb5ab3f-987d-4f30-87d2-7425a81ad1d7
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 20b411544e4d4ac54dc32cdbd126868f313b75c5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32908946"
---
# <a name="driver-manager-error-and-warning-checks"></a>Errore di Gestione driver e i controlli di avviso
Gestione Driver completamente o parzialmente implementa una serie di funzioni e pertanto verifica la presenza di tutti o alcuni degli errori e avvisi in tali funzioni.  
  
-   Gestione Driver implementa **SQLDataSources** e **SQLDrivers** e le verifiche per tutti gli errori e avvisi di queste funzioni.  
  
-   Gestione Driver verifica se un driver implementa **SQLGetFunctions**. Se il driver non implementa **SQLGetFunctions**, gestione Driver implementa e verifica la presenza di tutti gli errori e avvisi in essa contenuti.  
  
-   Gestione Driver implementa parzialmente **SQLAllocHandle**, **SQLConnect**, **SQLDriverConnect**, **SQLBrowseConnect**,  **SQLFreeHandle**, **SQLGetDiagRec**, e **SQLGetDiagField** e le verifiche per alcuni errori di queste funzioni. Può restituire gli stessi errori perché il driver per alcune di queste funzioni perché entrambi eseguire operazioni simili. Ad esempio, il Driver Manager o il driver può restituire IM008 SQLSTATE (finestra di dialogo non riuscita) se uno è in grado di visualizzare una finestra di dialogo di accesso per **SQLDriverConnect**.

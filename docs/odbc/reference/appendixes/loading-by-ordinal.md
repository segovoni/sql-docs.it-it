---
title: Caricamento tramite l'ordinale | Documenti Microsoft
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
- backward compatibility [ODBC], loading by ordinal
- compatibility [ODBC], loading by ordinal
- loading by ordinal [ODBC]
ms.assetid: 337d90ab-68eb-4940-a2f3-f7d5693ee766
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e37cd9754b402960ca12b0dbdbeaf43a5f2aee61
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32906246"
---
# <a name="loading-by-ordinal"></a>Caricamento da ordinale
In ODBC 2. *x*, è possibile eseguire il caricamento da numero ordinale per migliorare le prestazioni del processo di connessione. Un database ODBC 2. *x* driver Esporta una funzione fittizia con l'ordinale 199; quando Gestione Driver rileva, risolve gli indirizzi delle funzioni ODBC per ordinale e non per nome. Questa funzionalità è ancora supportata per l'API ODBC 2. *x* driver ma non è supportata per ODBC 3*x* driver.

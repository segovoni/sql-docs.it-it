---
title: Tipi di dati supportati | Documenti Microsoft
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
- data types [ODBC], DBMS support
- interoperability [ODBC], data types
ms.assetid: a89d4bab-ef3c-45c2-aa72-2639b3e0f856
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0b11c3df36ba36153f71721d9a10dee702ef745d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32915146"
---
# <a name="supported-data-types"></a>Tipi di dati supportati
I tipi di dati supportati da DBMS variano notevolmente. Un'applicazione può determinare i nomi e le caratteristiche dei tipi di dati supportati chiamando **SQLGetTypeInfo**. A causa delle ampie differenze nei nomi di tipi di dati, l'applicazione deve utilizzare i nomi dei tipi di dati restituiti da **SQLGetTypeInfo** in **CREATE TABLE** istruzioni. Per ulteriori informazioni, vedere [tipi di dati ODBC](../../../odbc/reference/develop-app/data-types-in-odbc.md).

---
title: "Passaggio 1: Connettersi all'origine dati | Documenti Microsoft"
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
- application process [ODBC], connecting to data source
- data sources [ODBC], connections
- connecting to data source [ODBC], steps
ms.assetid: 84298664-4523-4149-b821-7b2e42c85281
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 98fff3a58b7bc191b275d4f887f5856700f7fa91
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32915606"
---
# <a name="step-1-connect-to-the-data-source"></a>Passaggio 1: Connettersi all'origine dati
Il primo passaggio in qualsiasi applicazione consiste nella connessione all'origine dati. Questa fase, incluse le funzioni che richiesti, è illustrata nella figura seguente.  
  
 ![Connessione all'origine dei dati in un'applicazione ODBC](../../../odbc/reference/develop-app/media/pr11.gif "pr11")  
  
 È il primo passaggio per la connessione all'origine dati per caricare il Driver Manager e allocare l'handle di ambiente con **SQLAllocHandle**. Per ulteriori informazioni, vedere [allocare l'Handle di ambiente](../../../odbc/reference/develop-app/allocating-the-environment-handle.md).  
  
 L'applicazione quindi registra la versione di ODBC in cui è conforme chiamando **SQLSetEnvAttr** con l'attributo di ambiente SQL_ATTR_APP_ODBC_VER. Per ulteriori informazioni, vedere [la dichiarazione ODBC versione dell'applicazione](../../../odbc/reference/develop-app/declaring-the-application-s-odbc-version.md) e [compatibilità e conformità agli standard](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).  
  
 Successivamente, l'applicazione viene allocato un handle di connessione con **SQLAllocHandle** e si connette all'origine dati con **SQLConnect**, **SQLDriverConnect**, o **SQLBrowseConnect**. Per ulteriori informazioni, vedere [allocare un Handle di connessione](../../../odbc/reference/develop-app/allocating-a-connection-handle-odbc.md) e [stabilire una connessione](../../../odbc/reference/develop-app/establishing-a-connection.md).  
  
 Quindi, l'applicazione imposta gli attributi di connessione, ad esempio se manualmente il commit delle transazioni. Per ulteriori informazioni, vedere [gli attributi di connessione](../../../odbc/reference/develop-app/connection-attributes.md).

---
title: Connessione a origini dati | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- connections [ADO]
ms.assetid: 82770486-37bd-4c90-885f-6817a7c77ad7
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4262088b9f7bdf629f5ced8b7916359e3062227d
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35270840"
---
# <a name="connecting-to-data-sources"></a>Connessione a origini dati
Un oggetto ADO **connessione** oggetto rappresenta una sessione univoca con un'origine dati, tra cui un DBMS, un archivio di file o un file di testo delimitato da virgole. Nel caso di un sistema di database client/server, la connessione ADO può essere una connessione di rete effettiva al server.  
  
 Il **connessione** oggetto supporta vari [proprietà e metodi](../../../ado/reference/ado-api/connection-object-properties-methods-and-events.md) per specificare le configurazioni di connessione, apertura e chiusura delle connessioni, la creazione e l'esecuzione di comandi sull'origine dati e fornire informazioni sulla progettazione dell'origine dati sottostante sotto forma di set di righe dello schema, e così via. A seconda della funzionalità supportata dal provider, alcuni insiemi, metodi o proprietà di un **connessione** oggetto potrebbe non essere disponibile.  
  
 È possibile connettersi a un'origine dati tramite un **connessione** dell'oggetto o usando un **Recordset** oggetto.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Uso di un oggetto Connection](../../../ado/guide/data/using-a-connection-object.md)  
  
-   [Uso di un oggetto Recordset](../../../ado/guide/data/using-a-recordset-object.md)  
  
-   [Creazione di una stringa di connessione](../../../ado/guide/data/creating-a-connection-string.md)  
  
-   [Specificazione delle proprietà della connessione](../../../ado/guide/data/specifying-connection-properties.md)  
  
-   [Controllo delle transazioni](../../../ado/guide/data/controlling-transactions-ado.md)

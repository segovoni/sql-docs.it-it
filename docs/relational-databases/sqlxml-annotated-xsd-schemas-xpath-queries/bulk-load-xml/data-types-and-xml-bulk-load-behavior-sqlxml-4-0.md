---
title: Tipi di dati e XML in blocco il comportamento di caricamento (SQLXML 4.0) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- bulk load [SQLXML], data types
- data types [SQLXML], XML Bulk Load
- XML Bulk Load [SQLXML], data types
ms.assetid: d1ac1939-1f6c-4398-b7a7-a79ca608a4f1
caps.latest.revision: "20"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ffe103926663fd3b4c514921551c1b40598001e5
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="data-types-and-xml-bulk-load-behavior-sqlxml-40"></a>Tipi di dati e comportamento del caricamento bulk XML (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]I tipi di dati che vengono specificati nello schema di mapping (tipo XSD o XDR e **SQL: DataType**) vengono in genere ignorati ad eccezione dei casi seguenti:  
  
 In XSD:  
  
-   Se il tipo è **dateTime** o **ora**, è necessario specificare il **SQL: DataType** perché il caricamento Bulk XML esegue la conversione dei dati prima di inviarli a Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Quando si esegue un caricamento bulk in una colonna di **uniqueidentifier** digitare [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] e il valore XSD è un GUID che include parentesi graffe ({e}), è necessario specificare **SQL: DataType = "uniqueidentifier"** per rimuovere le parentesi graffe prima che il valore venga inserito nella colonna. Se **SQL: DataType** viene omesso, il valore viene inviato con le parentesi graffe e l'inserimento ha esito negativo.  
  
 Per ulteriori informazioni su **SQL: DataType**, vedere [coercizioni dei tipi di dati e l'annotazione SQL: DataType &#40; SQLXML 4.0 &#41; ](../../../relational-databases/sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md).  
  
 In XDR:  
  
-   Se il **dt: Type** è **datetime**, **ora**, **dateTime.tz**, o **time.tz**, è necessario specificare sia il **dt: Type** e **SQL: DataType** perché il caricamento Bulk XML esegue la conversione dei dati prima di inviare i dati per i tipi di dati [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Se i dati XML sono di tipo **uuid**, **SQL: DataType** deve essere specificata. **dt: Type = "uuid"** è obbligatorio, a meno che i dati sono dati di tipo stringa. Se non si specifica **dt:uuid**, caricamento Bulk XML accetta stringhe con parentesi graffe (e di rimuoverli se necessario).  
  
-   Se i dati XML sono **bin. Base64** o **bin.hex**, è necessario specificare il tipo di dati XML con **dt: Type**. Il caricamento bulk XML carica quindi i dati in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] come rappresentazione esadecimale dei dati.  
  
  
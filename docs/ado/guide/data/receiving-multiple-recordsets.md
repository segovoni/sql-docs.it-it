---
title: Ricezione di più recordset | Documenti Microsoft
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
- receiving multiple Recordsets [ADO]
- Recordset object [ADO], receiving multiple Recordsets
ms.assetid: 2a7ad7a6-f00d-4355-b0b5-d0ab957b0566
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 73bf5b086b82f1accdcb34f4e75c4101e324e532
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35272260"
---
# <a name="receiving-multiple-recordsets"></a>Ricezione di più recordset
Il [il Provider Microsoft OLE DB per SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md) supporta la restituzione di più **Recordset** oggetti per un unico comando che contiene più istruzioni SQL, uno **Recordset**per ogni istruzione SQL. L'ordine in cui il **Recordset**s vengono restituiti seguendo l'ordine in cui le istruzioni SQL vengono inserite nel testo del comando.  
  
 Il Provider Microsoft OLE DB per SQL Server anche restituisce più set di risultati di ADO quando il comando contiene una clausola COMPUTE. Ad esempio, un comando contenente l'istruzione SQL seguente restituisce i risultati in due **Recordset** oggetti: uno per il set di righe di (*ProductID*, *ProductName*, *UnitPrice*) e l'altro per il prezzo medio di tutti i prodotti nella tabella.  
  
```  
SELECT ProductID, ProductName, UnitPrice   
  FROM PRODUCTS   
  COMPUTE AVG(UnitPrice)  
```  
  
 È possibile utilizzare il **NextRecordset** metodo per enumerare i due oggetti.  
  
 Per ulteriori informazioni, vedere [NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md).

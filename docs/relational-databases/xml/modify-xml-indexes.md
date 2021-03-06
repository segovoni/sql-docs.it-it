---
title: Modificare indici XML | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: xml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- XML indexes [SQL Server], modifying
- modifying indexes
ms.assetid: 24d50fe1-c6ec-49e6-91a3-9791851ba53d
caps.latest.revision: 12
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 87e16b7c52a01b3755a5e7fb7d232f937470953c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33014258"
---
# <a name="modify-xml-indexes"></a>Modifica di indici XML
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  È possibile usare l’istruzione DDL di [ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md)[!INCLUDE[tsql](../../includes/tsql-md.md)] per modificare gli indici XML e non XML esistenti. Per gli indici XML, tuttavia, non sono disponibili tutte le opzioni ALTER INDEX. Per la modifica degli indici XML non sono valide le opzioni seguenti:  
  
-   Per gli indici XML non è valida l'opzione di ricompilazione e impostazione IGNORE_DUP_KEY. Per gli indici XML secondari è necessario impostare l'opzione di ricompilazione ONLINE su OFF. Nell'istruzione ALTER INDEX non è consentita l'opzione DROP_EXISTING.  
  
-   Le modifiche al vincolo di chiave primaria nella tabella utente non vengono automaticamente propagate agli indici XML. L'utente deve prima eliminare gli indici XML e quindi ricrearli.  
  
-   Se viene specificata l'opzione ALTER INDEX ALL, questa viene applicata agli indici sia XML che non XML. È possibile che vengano specificate opzioni di indicizzazione che non sono valide per entrambi i tipi di indici. In tal caso, l'intera istruzione ha esito negativo.  
  
## <a name="example-modifying-an-xml-index"></a>Esempio: modifica di un indice XML  
 Nell'esempio seguente viene creato, e quindi modificato, un indice XML impostando l'opzione `ALLOW_ROW_LOCKS` su `OFF`. Quando l'opzione `ALLOW_ROW_LOCKS` è impostata su `OFF`, le righe non sono bloccate ed è possibile ottenere l'accesso agli indici specificati tramite blocchi a livello di pagina e di tabella.  
  
```  
CREATE TABLE T (Col1 INT PRIMARY KEY, XmlCol XML)  
GO  
-- Create primary XML index.   
CREATE PRIMARY XML INDEX PIdx_T_XmlCol   
ON T(XmlCol)  
GO  
-- Note the type 3 is index on XML type.  
SELECT *  
FROM sys.xml_indexes  
WHERE object_id = object_id('T')  
AND name='PIdx_T_XmlCol'  
  
-- Modify and set an index option.  
ALTER INDEX PIdx_T_XmlCol on T   
SET (ALLOW_ROW_LOCKS = OFF)  
```  
  
## <a name="example-disabling-and-enabling-an-xml-index"></a>Esempio: disabilitazione e attivazione di un indice XML  
 Per impostazione predefinita, viene attivato un indice XML. Se si disabilita un indice XML, per le query in esecuzione sulla colonna XML non viene utilizzato l'indice XML. Per abilitare un indice XML, utilizzare `ALTER INDEX` con l'opzione `REBUILD` .  
  
```  
CREATE TABLE T (Col1 INT PRIMARY KEY, XmlCol XML)  
GO  
CREATE PRIMARY XML INDEX PIdx_T_XmlCol ON T(XmlCol)  
GO  
ALTER INDEX PIdx_T_XmlCol on T DISABLE  
Go  
-- Verify index is disabled.  
SELECT *  
FROM sys.xml_indexes  
WHERE object_id = object_id('T')  
AND name='PIdx_T_XmlCol'  
-- Rebuild the index.  
ALTER INDEX PIdx_T_XmlCol on T REBUILD  
Go  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Indici XML &#40;SQL Server&#41;](../../relational-databases/xml/xml-indexes-sql-server.md)  
  
  

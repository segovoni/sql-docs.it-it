---
title: Uso del Provider SQLXMLOLEDB (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- sample applications [SQLXML]
- SQLXMLOLEDB Provider, samples
- ClientSideXML property
ms.assetid: fbcefac5-29c9-478b-b0e0-d510b593f446
caps.latest.revision: 26
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: e2c9d60c84cde37eeef80dd5c916544a0ca83e6f
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38053809"
---
# <a name="using-the-sqlxmloledb-provider-sqlxml-40"></a>Utilizzo del provider SQLXMLOLEDB (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Negli argomenti di questa sezione vengono fornite applicazioni ADO di esempio che illustrano l'utilizzo delle proprietà specifiche del provider SQLXMLOLEDB.  
  
## <a name="application-requirements-for-sqlxmloledb-40-provider"></a>Requisiti dell'applicazione per il provider SQLXMLOLEDB 4.0  
 Per creare esempi reali che utilizzano SQLXMLOLEDB 4.0, è necessario effettuare le operazioni seguenti:  
  
1.  Creare un'applicazione Microsoft Visual Basic con estensione exe e aggiungere uno dei riferimenti seguenti:  
  
    -   Libreria Microsoft ActiveX Data Objects 2.6  
  
    -   Libreria Microsoft ActiveX Data Objects 2.7  
  
    -   Libreria Microsoft ActiveX Data Objects 2.8  
  
2.  Distribuire e installare SQLXML 4.0 e [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  
  
     Per altre informazioni, vedere sul [concetti relativi alla programmazione SQLXML 4.0](../../../relational-databases/sqlxml/sqlxml-4-0-programming-concepts.md) e [installazione di SQL Server Native Client](../../../relational-databases/native-client/applications/installing-sql-server-native-client.md).  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 [Esecuzione di query SQL &#40;Provider SQLXMLOLEDB&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/executing-sql-queries-sqlxmloledb-provider.md)  
 Viene illustrato l'utilizzo delle proprietà radice ClientSideXML e xml per eseguire query SQL.  
  
 [Esecuzione di modelli che contengono query SQL &#40;Provider SQLXMLOLEDB&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/executing-templates-that-contain-sql-queries-sqlxmloledb-provider.md)  
 Viene illustrato l'utilizzo della proprietà ClientSideXML.  
  
 [Esecuzione di query XPath &#40;Provider SQLXMLOLEDB&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/executing-xpath-queries-sqlxmloledb-provider.md)  
 Viene illustrato l'utilizzo delle proprietà ClientSideXML, il percorso di Base e Mapping dello Schema.  
  
 [Esecuzione di query XPath con spazi dei nomi &#40;Provider SQLXMLOLEDB&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/executing-xpath-queries-with-namespaces-sqlxmloledb-provider.md)  
 Viene illustrato come eseguire una query sugli schemi qualificati con lo spazio dei nomi.  
  
 [Esecuzione di modelli che contengono query XPath &#40;Provider SQLXMLOLEDB&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/executing-templates-that-contain-xpath-queries-sqlxmloledb-provider.md)  
 Viene illustrato come eseguire modelli con query SQL usando le proprietà ClientSideXML, il percorso di Base e Mapping dello Schema.  
  
 [Applicare una trasformazione XSL &#40;Provider SQLXMLOLEDB&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/data-access-components-provider/applying-an-xsl-transformation-sqlxmloledb-provider.md)  
 Viene illustrato l'utilizzo delle proprietà ClientSideXML e xsl nell'applicazione di una trasformazione XSL.  
  
## <a name="see-also"></a>Vedere anche  
 [Requisiti di sistema per SQL Server Native Client](../../../relational-databases/native-client/system-requirements-for-sql-server-native-client.md)  
  
  

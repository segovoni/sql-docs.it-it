---
title: Creare, modificare o eliminare indici XML selettivi | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: xml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c398f396-f630-4a2d-a264-f243c5346de1
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c3d819ce2d83df4be1337129b9425dfe0c21498f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="create-alter-and-drop-selective-xml-indexes"></a>Creare, modificare o eliminare indici XML selettivi
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Viene descritto come creare un nuovo indice XML selettivo oppure modificarne o eliminarne uno esistente.  
  
 Per altre informazioni sugli indici XML selettivi, vedere [Indici XML selettivi &#40;SXI&#41;](../../relational-databases/xml/selective-xml-indexes-sxi.md).  
  
##  <a name="create"></a> Creazione di un indice XML selettivo  
  
### <a name="how-to-create-a-selective-xml-index"></a>Procedura: creare un indice XML selettivo  
 **Creare un indice XML selettivo tramite Transact-SQL**  
 Creare un indice XML selettivo chiamando l'istruzione CREATE SELECTIVE XML INDEX. Per altre informazioni, vedere [CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-selective-xml-index-transact-sql.md).  
  
 **Esempio**  
  
 Nell'esempio seguente viene illustrata la sintassi per la creazione di un indice XML selettivo. Vengono inoltre mostrate diverse varianti della sintassi per la descrizione dei percorsi che si desidera indicizzare, con hint di ottimizzazione facoltativi.  
  
```sql  
CREATE SELECTIVE XML INDEX sxi_index  
ON Tbl(xmlcol)  
  
FOR(  
    pathab   = '/a/b' as XQUERY 'node()'  
    pathabc  = '/a/b/c' as XQUERY 'xs:double',   
    pathdtext = '/a/b/d/text()' as XQUERY 'xs:string' MAXLENGTH(200) SINGLETON  
    pathabe = '/a/b/e' as SQL NVARCHAR(100)  
)  
```  
  
  
##  <a name="alter"></a> Modifica di un indice XML selettivo  
  
### <a name="how-to-alter-a-selective-xml-index"></a>Procedura: modificare un indice XML selettivo  
 **Modificare un indice XML selettivo tramite Transact-SQL**  
 Modificare un indice XML selettivo esistente chiamando l'istruzione ALTER INDEX. Per altre informazioni, vedere [ALTER INDEX &#40;indici XML selettivi&#41;](../../t-sql/statements/alter-index-selective-xml-indexes.md).  
  
 **Esempio**  
  
 Nell'esempio seguente viene illustrata un'istruzione ALTER INDEX. Con questa istruzione il percorso `'/a/b/m'` viene aggiunto alla parte XQuery dell'indice e il percorso `'/a/b/e'` viene eliminato dalla parte SQL dell'indice creato nell'esempio nell'argomento [CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-selective-xml-index-transact-sql.md). Il percorso da eliminare viene identificato dal nome fornito al momento della creazione.  
  
```sql  
ALTER INDEX sxi_index  
ON Tbl  
FOR   
(  
    ADD pathm = '/a/b/m' as XQUERY 'node()' ,  
    REMOVE pathabe  
)  
```  
  
  
##  <a name="drop"></a> Eliminazione di un indice XML selettivo  
  
### <a name="how-to-drop-a-selective-xml-index"></a>Procedura: eliminare un indice XML selettivo  
 **Eliminare un indice XML selettivo tramite Transact-SQL**  
 Eliminare un indice XML selettivo chiamando l'istruzione DROP INDEX. Per altre informazioni, vedere [DROP INDEX &#40;indici XML selettivi&#41;](../../t-sql/statements/drop-index-selective-xml-indexes.md).  
  
 **Esempio**  
  
 Nell'esempio seguente viene illustrata un'istruzione DROP INDEX.  
  
```sql  
DROP INDEX sxi_index ON tbl  
```  
  
  
  

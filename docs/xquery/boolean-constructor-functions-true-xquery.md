---
title: true (funzione) (XQuery) | Microsoft Docs
ms.custom: ''
ms.date: 08/10/2016
ms.prod: sql
ms.prod_service: sql
ms.component: xquery
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- fn:true function
- true function
ms.assetid: 318e370d-0444-4812-afe4-307df7ef9f3b
caps.latest.revision: 17
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 349b2f99f5db35ca9d44e3ac8459030b7f7ba55f
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38014031"
---
# <a name="boolean-constructor-functions---true-xquery"></a>Funzioni costruttore booleane - true (XQuery)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce il valore di tipo xs:boolean True, che equivale a `xs:boolean("1")`.  
  
## <a name="syntax"></a>Sintassi  
  
```  
fn:true() as xs:boolean  
```  
  
## <a name="examples"></a>Esempi  
 In questo argomento vengono forniti esempi di XQuery sulle istanze XML archiviate in diverse **xml** colonne di tipo nel database AdventureWorks.  
  
### <a name="a-using-the-true-xquery-boolean-function"></a>A. Utilizzo della funzione booleana true() di XQuery  
 Nell'esempio seguente esegue una query non tipizzato **xml** variabile. L'espressione nel **Value ()** metodo viene restituito booleano **true ()** se "aaa" è il valore dell'attributo. Il **Value ()** metodo per il **xml** tipo di dati converte il valore booleano in un bit e lo restituisce.  
  
```  
DECLARE @x XML  
SET @x= '<ROOT><elem attr="aaa">bbb</elem></ROOT>'  
select @x.value(' if ( (/ROOT/elem/@attr)[1] eq "aaa" ) then fn:true() else fn:false() ', 'bit')  
go  
-- result = 1  
```  
  
 Nell'esempio seguente, la query viene eseguita su un oggetto tipizzato **xml** colonna. L'espressione `if` verifica il valore booleano tipizzato dell'elemento <`ROOT`> e restituisce il relativo codice XML creato. Nell'esempio vengono eseguite le operazioni seguenti:  
  
-   Viene creata una raccolta di XML Schema che definisce l'elemento <`ROOT`> di tipo xs:boolean.  
  
-   Crea una tabella con un oggetto tipizzato **xml** colonna usando la raccolta di XML schema.  
  
-   Viene salvata un'istanza XML della colonna, sulla quale viene eseguita una query.  
  
```  
-- Drop table if exist  
--DROP TABLE T  
--go  
DROP XML SCHEMA COLLECTION SC  
go  
CREATE XML SCHEMA COLLECTION SC AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema"  
targetNamespace="QNameXSD" >  
      <element name="ROOT" type="boolean" nillable="true"/>  
</schema>'  
go  
CREATE TABLE T (xmlCol XML(SC))  
go  
-- following OK  
insert into T values ('<ROOT xmlns="QNameXSD">true</ROOT>')  
 go  
-- Retrieve the local name.   
SELECT xmlCol.query('declare namespace a="QNameXSD";   
   if (/a:ROOT[1] eq true()) then  
       <result>Found boolean true</result>  
   else  
       <result>Found boolean false</result>')  
  
FROM T  
-- result = <result>Found boolean true</result>  
-- Clean up  
DROP TABLE T  
go  
DROP XML SCHEMA COLLECTION SC  
go  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni costruttore booleane &#40;XQuery&#41;](http://msdn.microsoft.com/library/fa907f39-d4b7-4495-b829-c788928e0f64)  
  
  

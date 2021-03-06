---
title: Metodo query() (tipo di dati xml) | Microsoft Docs
ms.custom: ''
ms.date: 07/26/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- query method
- query() method
ms.assetid: f48f6f7b-219f-463a-bf36-bc10f21afaeb
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: dedb594cbded10d17e93f1ed52dddf858b2fa67f
ms.sourcegitcommit: a6596c62f607041c4402f7d5b41a232fca257c14
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36250913"
---
# <a name="query-method-xml-data-type"></a>Metodo query() con tipo di dati XML
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Specifica una query XQuery su un'istanza con tipo di dati **xml**. Il risultato è di tipo **xml**. Il metodo restituisce un'istanza XML non tipizzata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
query ('XQuery')  
```  
  
## <a name="arguments"></a>Argomenti  
 XQuery  
 Stringa costituita da un'espressione XQuery che esegue query su nodi XML, ad esempio elementi o attributi, in un'istanza XML.  
  
## <a name="examples"></a>Esempi  
 In questa sezione sono disponibili esempi di uso del metodo query() con tipo di dati **xml**.  
  
### <a name="a-using-the-query-method-against-an-xml-type-variable"></a>A. Utilizzo del metodo query() in una variabile di tipo XML  
 Nell'esempio seguente viene dichiarata una variabile **@myDoc** di tipo **xml** a cui viene assegnata un'istanza XML. In seguito viene usato il metodo **query()** per specificare una query XQuery sul documento.  
  
 La query recupera l'elemento figlio <`Features`> dell'elemento <`ProductDescription`>:  
  
```  
declare @myDoc xml  
set @myDoc = '<Root>  
<ProductDescription ProductID="1" ProductName="Road Bike">  
<Features>  
  <Warranty>1 year parts and labor</Warranty>  
  <Maintenance>3 year parts and labor extended maintenance is available</Maintenance>  
</Features>  
</ProductDescription>  
</Root>'  
SELECT @myDoc.query('/Root/ProductDescription/Features')  
```  
  
 Risultato:  
  
```  
<Features>  
  <Warranty>1 year parts and labor</Warranty>  
  <Maintenance>3 year parts and labor extended maintenance is available</Maintenance>  
</Features>        
```  
  
### <a name="b-using-the-query-method-against-an-xml-type-column"></a>B. Utilizzo del metodo query() in una colonna di tipo XML  
 Nell'esempio seguente viene usato il metodo **query()** per specificare una query XQuery sulla colonna **CatalogDescription** di tipo **xml** nel database **AdventureWorks**:  
  
```  
SELECT CatalogDescription.query('  
declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
<Product ProductModelID="{ /PD:ProductDescription[1]/@ProductModelID }" />  
') as Result  
FROM Production.ProductModel  
where CatalogDescription.exist('  
declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
declare namespace wm="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain";  
     /PD:ProductDescription/PD:Features/wm:Warranty ') = 1  
```  
  
 Dalla query precedente si noti quanto segue:  
  
-   La colonna CatalogDescription è una colonna **xml** tipizzata. Pertanto, è disponibile il relativo schema associato. Nel [prologo di una query XQuery](../../xquery/modules-and-prologs-xquery-prolog.md), la parola chiave **namespace** viene usata per definire il prefisso incluso in seguito nel corpo della query.  
  
-   Il metodo **query()** consente di costruire una struttura XML, un elemento <`Product`> con un attributo **ProductModelID** in cui il valore dell'attributo **ProductModelID** viene recuperato dal database. Per altre informazioni sulla costruzione di strutture XML, vedere [XML Construction &#40;XQuery&#41;](../../xquery/xml-construction-xquery.md) (Costruzione XML &#40;XQuery&#41;).  
  
-   Il [metodo exist() (tipo di dati XML)](../../t-sql/xml/exist-method-xml-data-type.md) nella clausola WHERE viene usato per trovare solo le righe che contengono l'elemento <`Warranty`> nella struttura XML. Anche qui la parola chiave **namespace** per definire due prefissi dello spazio dei nomi.  
  
 Risultato parziale:  
  
```  
<Product ProductModelID="19"/>   
<Product ProductModelID="23"/>   
...  
```  
  
 Si noti che i metodi query() ed exist() dichiarano entrambi il prefisso PD. In tali casi, è possibile utilizzare WITH XMLNAMESPACES per definire innanzitutto i prefissi e utilizzarli nella query.  
  
```  
WITH XMLNAMESPACES 
(  
   'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS PD,  
   'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain' AS WM
)  
SELECT CatalogDescription.query('<Product ProductModelID="{ /PD:ProductDescription[1]/@ProductModelID }" />')
       AS Result  
FROM Production.ProductModel  
WHERE CatalogDescription.exist('/PD:ProductDescription/PD:Features/WM:Warranty ') = 1;

```  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiungere spazi dei nomi alle query con WITH XMLNAMESPACES](../../relational-databases/xml/add-namespaces-to-queries-with-with-xmlnamespaces.md)   
 [Confronto dati XML tipizzati con dati XML non tipizzati](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [Creare istanze di dati XML](../../relational-databases/xml/create-instances-of-xml-data.md)   
 [metodi con tipo di dati XML](../../t-sql/xml/xml-data-type-methods.md)   
 [Linguaggio XML di manipolazione dei dati &#40;XML DML&#41;](../../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  

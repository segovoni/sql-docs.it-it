---
title: 'Specifica di relazioni tramite SQL: Relationship (SQLXML 4.0) | Documenti Microsoft'
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
- IDREFS relationships [SQLXML]
- parent attribute [SQLXML]
- element relationships [SQLXML]
- multiple element relationships
- attribute relationships [SQLXML]
- sql:relationship
- relationship chains [SQLXML]
- IDREF relationships [SQLXML]
- parent-child relationships [SQLXML]
- relationship annotation
- XSD schemas [SQLXML], relationships
- annotated XSD schemas, relationships
- relationships [SQLXML], specifying
- unnamed relationships
- ID relationships [SQLXML]
- hierarchical relationships [SQLXML]
- named relationships [SQLXML]
ms.assetid: 98820afa-74e1-4e62-b336-6111a3dede4c
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 5d9846c90dc6b95d83c3e647aaee1f388cd0ea86
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32973856"
---
# <a name="specifying-relationships-using-sqlrelationship-sqlxml-40"></a>Definizione di relazioni tramite sql:relationship (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Gli elementi in un documento XML possono essere correlati. È possibile nidificare gerarchicamente gli elementi e specificare relazioni ID, IDREF o IDREFS tra gli elementi.  
  
 Ad esempio, in uno schema XSD, una  **\<cliente >** elemento contiene  **\<ordine >** gli elementi figlio. Quando viene eseguito il mapping dello schema nel database AdventureWorks, il  **\<cliente >** elemento viene mappato alla tabella Sales. Customer e  **\<ordine >** elemento viene mappato al Tabella Sales. SalesOrderHeader. Queste tabelle sottostanti, Sales.Customer e Sales.SalesOrderHeader, sono correlate in quanto i clienti effettuano ordini. L'elemento CustomerID nella tabella Sales.SalesOrderHeader è una chiave esterna che fa riferimento alla chiave primaria CustomerID nella tabella Sales.Customer. È possibile stabilire queste relazioni fra elementi dello schema di mapping tramite il **SQL:Relationship** annotazione.  
  
 Nello schema XSD con annotazioni, il **SQL:Relationship** annotazione viene utilizzata per nidificare gerarchicamente, gli elementi dello schema sulla base di chiave primaria e le relazioni di chiave esterna tra le tabelle sottostanti a cui mappare gli elementi. Quando si specifica il **SQL:Relationship** annotazione, è necessario identificare le operazioni seguenti:  
  
-   Tabella padre (Sales.Customer) e tabella figlio (Sales.SalesOrderHeader).  
  
-   Colonna o colonne che costituiscono la relazione tra le tabelle padre e figlio, ad esempio la colonna CustomerID, visualizzata sia nella tabella padre che nella tabella figlio.  
  
 Queste informazioni vengono utilizzate per generare la gerarchia appropriata.  
  
 Per fornire i nomi delle tabelle e le informazioni necessarie join, vengono specificati gli attributi seguenti sul **SQL:Relationship** annotazione. Questi attributi sono validi solo con il  **\<SQL: Relationship >** elemento:  
  
 **Nome**  
 Specifica il nome univoco della relazione,  
  
 **Parent**  
 Specifica la relazione padre (tabella). Si tratta di un attributo facoltativo. Se non è specificato, il nome della tabella padre viene ottenuto dalle informazioni presenti nella gerarchia padre-figlio del documento. Se lo schema specifica due gerarchie padre-figlio che utilizzano la stessa  **\<SQL: Relationship >** ma elementi padre diversi, non si specifica l'attributo parent in  **\<sql: relazione >**. Queste informazioni vengono ottenute dalla gerarchia nello schema.  
  
 **parent-key**  
 Specifica la chiave padre dell'elemento padre. Se la chiave padre è costituita da più colonne, i valori vengono specificati con uno spazio tra l'uno e l'altro. Tra i valori specificati per la chiave multicolonna e la chiave figlio corrispondente viene applicato un mapping posizionale.  
  
 **Figlio**  
 Specifica la relazione figlio (tabella).  
  
 **child-key**  
 Specifica la chiave figlio nell'elemento figlio che fa riferimento alla chiave padre nell'elemento padre. Se la chiave figlio è costituita da più attributi (colonne), i valori di chiave figlio vengono specificati con uno spazio tra l'uno e l'altro. Tra i valori specificati per la chiave multicolonna e la chiave padre corrispondente viene applicato un mapping posizionale.  
  
 **Inverso**  
 Questo attributo specificato in  **\<SQL: Relationship >** viene utilizzato dagli Updategram. Per ulteriori informazioni, vedere [specificando l'attributo SQL: inverse in SQL: Relationship](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-the-sql-inverse-attribute-on-sql-relationship-sqlxml-4-0.md).  
  
 Il **SQL: Key-campi** annotazione deve essere specificata in un elemento che contiene un elemento figlio, con un  **\<SQL: Relationship >** definito tra l'elemento e il figlio e che esegue non fornisce la chiave primaria della tabella specificata nell'elemento padre. Anche se lo schema non specifica  **\<SQL: Relationship >**, è necessario specificare **SQL: Key-campi** per produrre la gerarchia appropriata. Per ulteriori informazioni, vedere [identificazione di colonne chiave mediante SQL: Key-campi](../../relational-databases/sqlxml-annotated-xsd-schemas-using/identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md).  
  
 Per produrre la nidificazione appropriata nel risultato, è consigliabile che **SQL:Key-campi** specificato in tutti gli schemi.  
  
## <a name="examples"></a>Esempi  
 Per creare esempi reali utilizzando gli esempi seguenti, è necessario soddisfare alcuni requisiti. Per ulteriori informazioni, vedere [requisiti per esecuzione esempi SQLXML](../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-the-sqlrelationship-annotation-on-an-element"></a>A. Specifica dell'annotazione sql:relationship in un elemento  
 Include lo schema XSD con annotazioni seguente  **\<cliente >** e  **\<ordine >** elementi. Il  **\<ordine >** elemento è un elemento figlio del  **\<cliente >** elemento.  
  
 Nello schema, il **SQL: Relationship** annotazione viene specificata per il  **\<ordine >** elemento figlio. La relazione stessa è definita nel  **\<xsd: appinfo >** elemento.  
  
 Il  **\<relazione >** elemento identifica CustomerID nella tabella Sales. SalesOrderHeader come chiave esterna che fa riferimento alla chiave primaria CustomerID nella tabella Sales. Customer. Di conseguenza, gli ordini appartenenti a un cliente vengono visualizzati come elemento figlio di tale  **\<cliente >** elemento.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustOrders"  
          parent="Sales.Customer"  
          parent-key="CustomerID"  
          child="Sales.SalesOrderHeader"  
          child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customer" sql:relation="Sales.Customer" type="CustomerType" />  
   <xsd:complexType name="CustomerType" >  
     <xsd:sequence>  
        <xsd:element name="Order"   
                     sql:relation="Sales.SalesOrderHeader"  
                    sql:relationship="CustOrders" >  
           <xsd:complexType>  
              <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
              <xsd:attribute name="CustomerID" type="xsd:string" />  
           </xsd:complexType>  
        </xsd:element>  
     </xsd:sequence>  
        <xsd:attribute name="CustomerID"   type="xsd:string" />   
    </xsd:complexType>  
  
</xsd:schema>  
```  
  
 Lo schema precedente utilizza una relazione denominata. È inoltre possibile specificare una relazione priva di nome. I risultati sono identici.  
  
 Di seguito viene fornito lo schema corretto in cui è specificata una relazione priva di nome:  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  
  <xsd:element name="Customer" sql:relation="Sales.Customer"  type="CustomerType" />  
   <xsd:complexType name="CustomerType" >  
     <xsd:sequence>  
        <xsd:element name="Order"   
                     sql:relation="Sales.SalesOrderHeader">  
           <xsd:annotation>  
            <xsd:appinfo>  
              <sql:relationship   
                parent="Sales.Customer"  
                parent-key="CustomerID"  
                child="Sales.SalesOrderHeader"  
                child-key="CustomerID" />  
            </xsd:appinfo>  
           </xsd:annotation>  
           <xsd:complexType>  
              <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
              <xsd:attribute name="CustomerID" type="xsd:string" />  
           </xsd:complexType>  
        </xsd:element>  
     </xsd:sequence>  
        <xsd:attribute name="CustomerID"   type="xsd:string" />   
    </xsd:complexType>  
  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Per testare una query Xpath di esempio sullo schema  
  
1.  Copiare il codice dello schema precedente e incollarlo in un file di testo. Salvare il file con il nome sql-relationship.xml.  
  
2.  Copiare il modello seguente e incollarlo in un file di testo. Salvare il file con il nome sql-relationshipT.xml nella stessa directory in cui è stato salvato il file sql-relationship.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="sql-relationship.xml">  
            /Customer[@CustomerID=1]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Il percorso di directory specificato per lo schema di mapping (sql-relationship.xml) è relativo alla directory in cui è salvato il modello. È possibile specificare anche un percorso assoluto, ad esempio:  
  
    ```  
    mapping-schema="C:\MyDir\sql-relationship.xml"  
    ```  
  
3.  Creare e utilizzare lo script di test SQLXML 4.0 (Sqlxml4test.vbs) per eseguire il modello.  
  
     Per ulteriori informazioni, vedere [utilizzando ADO per eseguire query SQLXML](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Set di risultati:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
  <Customer CustomerID="1">   
    <Order OrderID="43860" CustomerID="1" />   
    <Order OrderID="44501" CustomerID="1" />   
    <Order OrderID="45283" CustomerID="1" />   
    <Order OrderID="46042" CustomerID="1" />   
  </Customer>   
</ROOT>  
```  
  
### <a name="b-specifying-a-relationship-chain"></a>B. Definizione di una catena di relazioni  
 Per questo esempio, si supponga di voler fare in modo che il documento XML seguente utilizzi dati ottenuti dal database di AdventureWorks:  
  
```  
<Order SalesOrderID="43659">  
  <Product Name="Mountain Bike Socks, M"/>   
  <Product Name="Sport-100 Helmet, Blue"/>  
  ...  
</Order>  
...  
```  
  
 Per ogni ordine nella tabella Sales. SalesOrderHeader, il documento XML ha uno  **\<ordine >** elemento. E ogni  **\<ordine >** elemento include un elenco di  **\<prodotto >** gli elementi figlio, uno per ogni prodotto richiesto nell'ordine.  
  
 Per specificare uno schema XSD che produrrà questa gerarchia, è necessario definire due relazioni: OrderOD e ODProduct. La relazione OrderOD specifica la relazione padre-figlio tra le tabelle Sales.SalesOrderHeader e Sales.SalesOrderDetail. La relazione ODProduct specifica la relazione tra le tabelle Sales.SalesOrderDetail e Production.Product.  
  
 Nello schema seguente, il **msdata: Relationship** annotazione nel  **\<prodotto >** elemento specifica due valori: OrderOD e ODProduct. L'ordine in cui sono elencati gli attributi è importante.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:msdata="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <msdata:relationship name="OrderOD"  
          parent="Sales.SalesOrderHeader"  
          parent-key="SalesOrderID"  
          child="Sales.SalesOrderDetail"  
          child-key="SalesOrderID" />  
  
    <msdata:relationship name="ODProduct"  
          parent="Sales.SalesOrderDetail"  
          parent-key="ProductID"  
          child="Production.Product"  
          child-key="ProductID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Order" msdata:relation="Sales.SalesOrderHeader"   
               msdata:key-fields="SalesOrderID" type="OrderType" />  
   <xsd:complexType name="OrderType" >  
     <xsd:sequence>  
        <xsd:element name="Product" msdata:relation="Production.Product"   
                     msdata:key-fields="ProductID"  
                     msdata:relationship="OrderOD ODProduct">  
          <xsd:complexType>  
             <xsd:attribute name="Name" type="xsd:string" />  
          </xsd:complexType>  
        </xsd:element>  
     </xsd:sequence>  
        <xsd:attribute name="SalesOrderID"   type="xsd:integer" />   
    </xsd:complexType>  
</xsd:schema>  
```  
  
 Anziché specificare una relazione denominata, è possibile specificare una relazione anonima. In questo caso, l'intero contenuto di  **\<annotazione >**...  **\</annotation >**, che descrive le due relazioni, viene visualizzato come un elemento figlio di  **\<prodotto >**.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:msdata="urn:schemas-microsoft-com:mapping-schema">  
  
  <xsd:element name="Order" msdata:relation="Sales.SalesOrderHeader"   
               msdata:key-fields="SalesOrderID" type="OrderType" />  
  
   <xsd:complexType name="OrderType" >  
     <xsd:sequence>  
        <xsd:element name="Product" msdata:relation="Production.Product"   
                     msdata:key-fields="ProductID" >  
         <xsd:annotation>  
          <xsd:appinfo>  
           <msdata:relationship   
               parent="Sales.SalesOrderHeader"  
               parent-key="SalesOrderID"  
               child="Sales.SalesOrderDetail"  
               child-key="SalesOrderID" />  
  
           <msdata:relationship   
               parent="Sales.SalesOrderDetail"  
               parent-key="ProductID"  
               child="Production.Product"  
               child-key="ProductID" />  
         </xsd:appinfo>  
       </xsd:annotation>  
       <xsd:complexType>  
          <xsd:attribute name="Name" type="xsd:string" />  
       </xsd:complexType>  
     </xsd:element>  
   </xsd:sequence>  
   <xsd:attribute name="SalesOrderID"   type="xsd:integer" />   
  </xsd:complexType>  
 </xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Per testare una query Xpath di esempio sullo schema  
  
1.  Copiare il codice dello schema precedente e incollarlo in un file di testo. Salvare il file con il nome relationshipChain.xml.  
  
2.  Copiare il modello seguente e incollarlo in un file di testo. Salvare il file con il nome relationshipChainT.xml nella stessa directory in cui è stato salvato il file relationshipChain.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="relationshipChain.xml">  
            /Order  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Il percorso di directory specificato per lo schema di mapping (relationshipChain.xml) è relativo alla directory in cui è salvato il modello. È possibile specificare anche un percorso assoluto, ad esempio:  
  
    ```  
    mapping-schema="C:\MyDir\relationshipChain.xml"  
    ```  
  
3.  Creare e utilizzare lo script di test SQLXML 4.0 (Sqlxml4test.vbs) per eseguire il modello.  
  
     Per ulteriori informazioni, vedere [utilizzando ADO per eseguire query SQLXML](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Set di risultati:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
  <Order SalesOrderID="43659">  
    <Product Name="Mountain Bike Socks, M" />   
    <Product Name="Sport-100 Helmet, Blue" />   
    <Product Name="AWC Logo Cap" />   
    <Product Name="Long-Sleeve Logo Jersey, M" />   
    <Product Name="Long-Sleeve Logo Jersey, XL" />   
    ...  
  </Order>  
  ...  
</ROOT>  
```  
  
### <a name="c-specifying-the-relationship-annotation-on-an-attribute"></a>C. Definizione dell'annotazione sql:relationship in un attributo  
 In questo esempio lo schema include un \<cliente > elemento con un \<CustomerID > elemento figlio e un attributo OrderIDList di tipo IDREFS. Il \<cliente > elemento viene mappato alla tabella Sales. Customer nel database AdventureWorks. Per impostazione predefinita, l'ambito di questo mapping si applica a tutti gli elementi figlio o attributi a meno che non **SQL: relation** specificato per l'elemento figlio o un attributo, nel qual caso, la relazione primaria-chiave/chiave esterna appropriata deve essere definito tramite il \<relazione > elemento. E l'elemento figlio o un attributo che specifica la tabella diversa utilizzando il **relazione** annotazione, è necessario specificare anche il **relazione** annotazione.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustOrders"  
          parent="Sales.Customer"  
          parent-key="CustomerID"  
          child="Sales.SalesOrderHeader"  
          child-key="CustomerID" />  
     </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customer" sql:relation="Sales.Customer" type="CustomerType" />  
   <xsd:complexType name="CustomerType" >  
     <xsd:sequence>  
        <xsd:element name="CustomerID"   type="xsd:string" />   
     </xsd:sequence>  
     <xsd:attribute name="OrderIDList"   
                     type="xsd:IDREFS"   
                     sql:relation="Sales.SalesOrderHeader"   
                     sql:field="SalesOrderID"  
                     sql:relationship="CustOrders" >  
        </xsd:attribute>  
    </xsd:complexType>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Per testare una query Xpath di esempio sullo schema  
  
1.  Copiare il codice dello schema precedente e incollarlo in un file di testo. Salvare il file con il nome relationship-on-attribute.xml.  
  
2.  Copiare il modello seguente e incollarlo in un file. Salvare il file con il nome relationship-on-attributeT.xml nella stessa directory in cui è stato salvato il file relationship-on-attribute.xml. La query nel modello seleziona un cliente con CustomerID 1.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="relationship-on-attribute.xml">  
        /Customer[CustomerID=1]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Il percorso di directory specificato per lo schema di mapping (relationship-on-attribute.xml) è relativo alla directory in cui è salvato il modello. È possibile specificare anche un percorso assoluto, ad esempio:  
  
    ```  
    mapping-schema="C:\MyDir\relationship-on-attribute.xml"  
    ```  
  
3.  Creare e utilizzare lo script di test SQLXML 4.0 (Sqlxml4test.vbs) per eseguire il modello.  
  
     Per ulteriori informazioni, vedere [utilizzando ADO per eseguire query SQLXML](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Set di risultati:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
  <Customer OrderIDList="43860 44501 45283 46042">  
    <CustomerID>1</CustomerID>   
  </Customer>  
</ROOT>  
```  
  
### <a name="d-specifying-sqlrelationship-on-multiple-elements"></a>D. Specifica di sql:relationship in più elementi  
 In questo esempio, contiene lo schema XSD con annotazioni di  **\<cliente >**,  **\<ordine >**, e  **\<OrderDetail >** elementi.  
  
 Il  **\<ordine >** elemento è un elemento figlio del  **\<cliente >** elemento. **\<SQL: Relationship >** specificato nel  **\<ordine >** elemento figlio; pertanto, gli ordini appartenenti a un cliente vengono visualizzati come elementi figlio di  **\<cliente >**.  
  
 Il  **\<ordine >** elemento include il  **\<OrderDetail >** elemento figlio. **\<SQL: Relationship >** viene specificato in  **\<OrderDetail >** elemento figlio, i dettagli dell'ordine che riguardano un ordine vengono visualizzati come elementi figlio di tale **\<ordine >** elemento.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustOrders"  
        parent="Sales.Customer"  
        parent-key="CustomerID"  
        child="Sales.SalesOrderHeader"  
        child-key="CustomerID" />  
  
    <sql:relationship name="OrderOrderDetail"  
        parent="Sales.SalesOrderHeader"  
        parent-key="SalesOrderID"  
        child="Sales.SalesOrderDetail"  
        child-key="SalesOrderID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customer" sql:relation="Sales.Customer" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader"    
              sql:relationship="CustOrders" maxOccurs="unbounded" >  
          <xsd:complexType>  
              <xsd:sequence>  
                <xsd:element name="OrderDetail"   
                             sql:relation="Sales.SalesOrderDetail"   
                             sql:relationship="OrderOrderDetail"   
                             maxOccurs="unbounded" >  
                  <xsd:complexType>  
                    <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
                    <xsd:attribute name="ProductID" type="xsd:string" />  
                    <xsd:attribute name="OrderQty" type="xsd:integer" />  
                  </xsd:complexType>  
                </xsd:element>  
              </xsd:sequence>  
              <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
              <xsd:attribute name="OrderDate" type="xsd:date" />  
              <xsd:attribute name="CustomerID" type="xsd:string" />  
          </xsd:complexType>  
        </xsd:element>  
      </xsd:sequence>  
      <xsd:attribute name="CustomerID" type="xsd:string" />  
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Per testare una query Xpath di esempio sullo schema  
  
1.  Copiare il codice dello schema precedente e incollarlo in un file di testo. Salvare il file con il nome relationship-multiple-elements.xml.  
  
2.  Copiare il modello seguente e incollarlo in un file di testo. Salvare il file con il nome relationship-multiple-elementsT.xml nella stessa directory in cui è stato salvato il file relationship-multiple-elements.xml. La query nel modello restituisce informazioni sull'ordine per un cliente con CustomerID 1 e SalesOrderID 43860.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="relationship-multiple-elements.xml">  
        /Customer[@CustomerID=1]/Order[@SalesOrderID=43860]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Il percorso di directory specificato per lo schema di mapping (relationship-multiple-elements.xml) è relativo alla directory in cui è salvato il modello. È possibile specificare anche un percorso assoluto, ad esempio:  
  
    ```  
    mapping-schema="C:\MyDir\relationship-multiple-elements.xml"  
    ```  
  
3.  Creare e utilizzare lo script di test SQLXML 4.0 (Sqlxml4test.vbs) per eseguire il modello.  
  
     Per ulteriori informazioni, vedere [utilizzando ADO per eseguire query SQLXML](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Set di risultati:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Order SalesOrderID="43860" OrderDate="2001-08-01" CustomerID="1">  
     <OrderDetail SalesOrderID="43860" ProductID="761" OrderQty="2" />   
     <OrderDetail SalesOrderID="43860" ProductID="770" OrderQty="1" />   
     <OrderDetail SalesOrderID="43860" ProductID="758" OrderQty="2" />   
     <OrderDetail SalesOrderID="43860" ProductID="765" OrderQty="2" />   
     <OrderDetail SalesOrderID="43860" ProductID="732" OrderQty="1" />   
     <OrderDetail SalesOrderID="43860" ProductID="762" OrderQty="1" />   
     <OrderDetail SalesOrderID="43860" ProductID="738" OrderQty="1" />   
     <OrderDetail SalesOrderID="43860" ProductID="768" OrderQty="1" />   
     <OrderDetail SalesOrderID="43860" ProductID="753" OrderQty="2" />   
     <OrderDetail SalesOrderID="43860" ProductID="729" OrderQty="1" />   
     <OrderDetail SalesOrderID="43860" ProductID="763" OrderQty="1" />   
     <OrderDetail SalesOrderID="43860" ProductID="756" OrderQty="1" />   
  </Order>  
</ROOT>  
```  
  
### <a name="e-specifying-the-sqlrelationship-without-the-parent-attribute"></a>E. Specifica il \<SQL: Relationship > senza l'attributo parent  
 In questo esempio viene illustrato come specificare il  **\<SQL: Relationship >** senza il **padre** attributo. Si supponga, ad esempio, di disporre delle tabelle relative ai dipendenti seguenti:  
  
```  
Emp1(SalesPersonID, FirstName, LastName, ReportsTo)  
Emp2(SalesPersonID, FirstName, LastName, ReportsTo)  
```  
  
 La vista XML seguente è il  **\<Emp1 >** e  **\<Emp2 >** elementi mapping di tabelle a emp1 e Sales. emp2:  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="EmpOrders"  
          parent-key="SalesPersonID"  
          child="Sales.SalesOrderHeader"  
          child-key="SalesPersonID" />  
     </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Emp1" sql:relation="Sales.Emp1" type="EmpType" />  
  <xsd:element name="Emp2" sql:relation="Sales.Emp2" type="EmpType" />  
   <xsd:complexType name="EmpType" >  
     <xsd:sequence>  
        <xsd:element name="Order"   
                     sql:relation="Sales.SalesOrderHeader"   
                     sql:relationship="EmpOrders" >  
          <xsd:complexType>  
             <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
             <xsd:attribute name="CustomerID" type="xsd:string" />  
          </xsd:complexType>  
        </xsd:element>  
     </xsd:sequence>  
        <xsd:attribute name="SalesPersonID"   type="xsd:integer" />   
        <xsd:attribute name="LastName"   type="xsd:string" />   
    </xsd:complexType>  
  
</xsd:schema>  
```  
  
 Nello schema, sia il  **\<Emp1 >** elemento e  **\<Emp2 >** elemento sono di tipo **EmpType**. Il tipo **EmpType** descrive un  **\<ordine >** elemento figlio e i corrispondenti  **\<SQL: Relationship >**. In questo caso, non è presente alcun singolo elemento padre che possa essere identificato in  **\<SQL: Relationship >** utilizzando il **padre** attributo. In questo caso, non si specifica il **padre** attributo  **\<SQL: Relationship >**; **padre** attributo informazioni vengono ottenute dal gerarchia dello schema.  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Per testare una query Xpath di esempio sullo schema  
  
1.  Creare le tabelle seguenti nel database AdventureWorks:  
  
    ```  
    USE AdventureWorks  
    CREATE TABLE Sales.Emp1 (  
           SalesPersonID int primary key,   
           FirstName  varchar(20),   
           LastName   varchar(20),   
           ReportsTo int)  
    Go  
    CREATE TABLE Sales.Emp2 (  
           SalesPersonID int primary key,   
           FirstName  varchar(20),   
           LastName   varchar(20),   
           ReportsTo int)  
    Go  
    ```  
  
2.  Aggiungere i dati di esempio seguenti nelle tabelle:  
  
    ```  
    INSERT INTO Sales.Emp1 values (279, 'Nancy', 'Devolio',NULL)  
    INSERT INTO Sales.Emp1 values (282, 'Andrew', 'Fuller',1)  
    INSERT INTO Sales.Emp1 values (276, 'Janet', 'Leverling',1)  
    INSERT INTO Sales.Emp2 values (277, 'Margaret', 'Peacock',3)  
    INSERT INTO Sales.Emp2 values (283, 'Steven', 'Devolio',4)  
    INSERT INTO Sales.Emp2 values (275, 'Nancy', 'Buchanan',5)  
    INSERT INTO Sales.Emp2 values (281, 'Michael', 'Suyama',6)  
    ```  
  
3.  Copiare il codice dello schema precedente e incollarlo in un file di testo. Salvare il file con il nome relationship-noparent.xml.  
  
4.  Copiare il modello seguente e incollarlo in un file di testo. Salvare il file con il nome relationship-noparentT.xml nella stessa directory in cui è stato salvato il file relationship-noparent.xml. La query nel modello seleziona tutti i \<Emp1 > elementi (di conseguenza, l'elemento padre è Emp1).  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="relationship-noparent.xml">  
            /Emp1  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Il percorso di directory specificato per lo schema di mapping (relationship-noparent.xml) è relativo alla directory in cui è salvato il modello. È possibile specificare anche un percorso assoluto, ad esempio:  
  
    ```  
    mapping-schema="C:\MyDir\relationship-noparent.xml"  
    ```  
  
5.  Creare e utilizzare lo script di test SQLXML 4.0 (Sqlxml4test.vbs) per eseguire il modello.  
  
     Per ulteriori informazioni, vedere [utilizzando ADO per eseguire query SQLXML](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Di seguito viene fornito un set di risultati parziale:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
<Emp1 SalesPersonID="276" LastName="Leverling">  
  <Order SalesOrderID="43663" CustomerID="510" />   
  <Order SalesOrderID="43666" CustomerID="511" />   
  <Order SalesOrderID="43859" CustomerID="259" />  
  ...  
</Emp1>  
```  
  
  

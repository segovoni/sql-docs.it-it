---
title: CircularString | Microsoft Docs
ms.custom: ''
ms.date: 06/02/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: spatial
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-spatial
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 9fe06b03-d98c-4337-9f89-54da98f49f9f
caps.latest.revision: 27
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 5de99f558b60fb2657542d6c9352bc3b7ce24f66
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32971097"
---
# <a name="circularstring"></a>CircularString
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  **CircularString** è una raccolta di zero o più segmenti di arco circolare continui. Un segmento di arco circolare è un segmento curvo definito da tre punti su un piano bidimensionale. Il primo punto non può corrispondere al terzo punto. Se tutti e tre i punti di un segmento di arco circolare sono collineari, il segmento di arco verrà gestito come un segmento di linea.  
  
> [!IMPORTANT]  
>  Per una descrizione dettagliata ed esempi delle nuove funzionalità spaziali introdotte in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], tra cui il sottotipo **CircularString** , scaricare il white paper relativo alle [nuove funzionalità spaziali in SQL Server 2012](http://go.microsoft.com/fwlink/?LinkId=226407).  
  
## <a name="circularstring-instances"></a>Istanze CircularString  
 Nel disegno seguente vengono illustrate le istanze **CircularString** valide:  
  
 ![5ff17e34-b578-4873-9d33-79500940d0bc](../../relational-databases/spatial/media/5ff17e34-b578-4873-9d33-79500940d0bc.gif)
  
### <a name="accepted-instances"></a>Istanze accettate  
 Un'istanza **CircularString** viene accettata se è vuota o contiene un numero dispari di punti, n, dove n > 1. Le istanze **CircularString** seguenti vengono accettate.  
  
```  
DECLARE @g1 geometry = 'CIRCULARSTRING EMPTY';  
DECLARE @g2 geometry = 'CIRCULARSTRING(1 1, 2 0, -1 1)';  
DECLARE @g3 geometry = 'CIRCULARSTRING(1 1, 2 0, 2 0, 2 0, 1 1)';  
```  
  
 `@g3` mostra che l'istanza **CircularString** può essere accettata, ma non è valida. La dichiarazione dell'istanza CircularString seguente non viene accettata. Questa dichiarazione genera un'eccezione `System.FormatException`.  
  
```  
DECLARE @g geometry = 'CIRCULARSTRING(1 1, 2 0, 2 0, 1 1)';  
```  
  
### <a name="valid-instances"></a>Istanze valide  
 Un'istanza **CircularString** valida deve essere vuota o disporre degli attributi seguenti:  
  
-   Deve contenere almeno un segmento di arco circolare, cioè avere un minimo di tre punti.  
  
-   L'ultimo endpoint per ogni segmento di arco circolare nella sequenza, a eccezione dell'ultimo segmento, deve essere il primo endpoint per il segmento successivo nella sequenza.  
  
-   Deve contenere un numero di punti dispari.  
  
-   Non deve sovrapporsi a un intervallo.  
  
-   Anche se è possibile che le istanze **CircularString** contengano segmenti di linea, questi ultimi devono essere definiti da tre punti collineari.  
  
 Nell'esempio seguente vengono illustrate le istanze **CircularString** valide.  
  
```  
DECLARE @g1 geometry = 'CIRCULARSTRING EMPTY';  
DECLARE @g2 geometry = 'CIRCULARSTRING(1 1, 2 0, -1 1)';  
DECLARE @g3 geometry = 'CIRCULARSTRING(1 1, 2 0, 2 0, 1 1, 0 1)';  
DECLARE @g4 geometry = 'CIRCULARSTRING(1 1, 2 2, 2 2)';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(),@g4.STIsValid();  
```  
  
 Un'istanza **CircularString** deve contenere almeno due segmenti di arco circolare per definire un cerchio completo. Un'istanza **CircularString** non può usare un singolo segmento di arco circolare, ad esempio (1 1, 3 1, 1 1), per definire un cerchio completo. Utilizzare (1 1, 2 2, 3 1, 2 0, 1 1) per definire il cerchio.  
  
 Nell'esempio seguente vengono illustrate le istanze CircularString non valide.  
  
```  
DECLARE @g1 geometry = 'CIRCULARSTRING(1 1, 2 0, 1 1)';  
DECLARE @g2 geometry = 'CIRCULARSTRING(0 0, 0 0, 0 0)';  
SELECT @g1.STIsValid(), @g2.STIsValid();  
```  
  
### <a name="instances-with-collinear-points"></a>Istanze con punti collineari  
 Nei casi seguenti un segmento di arco circolare sarà considerato come un segmento di linea:  
  
-   Quando tutti e i tre punti sono collineari, ad esempio, (1 3, 4 4, 7 5).  
  
-   Quando il primo punto e il punto medio sono gli stessi, ma il terzo punto è diverso, ad esempio, (1 3, 1 3, 7 5).  
  
-   Quando il punto medio e l'ultimo punto sono gli stessi, ma il primo punto è diverso, ad esempio, (1 3, 4 4, 4 4).  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-instantiating-a-geometry-instance-with-an-empty-circularstring"></a>A. Creazione di un'istanza Geometry con un'istanza CircularString vuota  
 In questo esempio viene illustrato come creare un'istanza **CircularString** vuota:  
  
```sql  
DECLARE @g geometry;  
SET @g = geometry::Parse('CIRCULARSTRING EMPTY');  
```  
  
### <a name="b-instantiating-a-geometry-instance-using-a-circularstring-with-one-circular-arc-segment"></a>B. Creazione di un'istanza Geometry utilizzando un'istanza CircularString con un segmento di arco circolare  
 L'esempio seguente mostra come creare un'istanza **CircularString** con un singolo segmento di arco circolare (mezzo cerchio):  
  
```sql  
DECLARE @g geometry;  
SET @g = geometry:: STGeomFromText('CIRCULARSTRING(2 0, 1 1, 0 0)', 0);  
SELECT @g.ToString();  
```  
  
### <a name="c-instantiating-a-geometry-instance-using-a-circularstring-with-multiple-circular-arc-segments"></a>C. Creazione di un'istanza Geometry utilizzando un'istanza CircularString con più segmenti di arco circolare  
 L'esempio seguente mostra come creare un'istanza **CircularString** con più segmenti di arco circolare (cerchio completo):  
  
```sql  
DECLARE @g geometry;  
SET @g = geometry::Parse('CIRCULARSTRING(2 1, 1 2, 0 1, 1 0, 2 1)');  
SELECT 'Circumference = ' + CAST(@g.STLength() AS NVARCHAR(10));    
```  
  
 Viene prodotto l'output seguente:  
  
```  
Circumference = 6.28319  
```  
  
 Confrontare l'output quando viene utilizzata **LineString** anziché **CircularString**:  
  
```sql  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(2 1, 1 2, 0 1, 1 0, 2 1)', 0);  
SELECT 'Perimeter = ' + CAST(@g.STLength() AS NVARCHAR(10));  
```  
  
 Viene prodotto l'output seguente:  
  
```  
Perimeter = 5.65685  
```  
  
 Si noti che il valore per l'esempio **CircularString** è vicino a 2∏, che è la circonferenza effettiva del cerchio.  
  
### <a name="d-declaring-and-instantiating-a-geometry-instance-with-a-circularstring-in-the-same-statement"></a>D. Dichiarazione e creazione di un'istanza Geometry utilizzando un'istanza CircularString nella stessa istruzione  
 In questo frammento viene illustrato come dichiarare e creare un'istanza **geometry** con un'istanza **CircularString** nella stessa istruzione:  
  
```sql  
DECLARE @g geometry = 'CIRCULARSTRING(0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0)';  
```  
  
### <a name="e-instantiating-a-geography-instance-with-a-circularstring"></a>E. Creazione di un'istanza Geometry con un'istanza CircularString  
 Nell'esempio seguente viene illustrato come dichiarare e creare un'istanza **geography** con un'istanza **CircularString**:  
  
```sql  
DECLARE @g geography = 'CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
```  
  
### <a name="f-instantiating-a-geometry-instance-with-a-circularstring-that-is-a-straight-line"></a>F. Creazione di un'istanza Geometry con un'istanza CircularString che corrisponde a una linea retta  
 Nell'esempio seguente viene illustrato come creare un'istanza **CircularString** che corrisponde a una linea retta:  
  
```sql  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('CIRCULARSTRING(0 0, 1 2, 2 4)', 0);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica dei tipi di dati spaziali](../../relational-databases/spatial/spatial-data-types-overview.md)   
 [CompoundCurve](../../relational-databases/spatial/compoundcurve.md)   
 [MakeValid &#40;tipo di dati geography&#41;](../../t-sql/spatial-geography/makevalid-geography-data-type.md)   
 [MakeValid &#40;tipo di dati geometry&#41;](../../t-sql/spatial-geometry/makevalid-geometry-data-type.md)   
 [STIsValid &#40;tipo di dati geometry&#41;](../../t-sql/spatial-geometry/stisvalid-geometry-data-type.md)   
 [STIsValid &#40;tipo di dati geography&#41;](../../t-sql/spatial-geography/stisvalid-geography-data-type.md)   
 [STLength &#40;tipo di dati geometry&#41;](../../t-sql/spatial-geometry/stlength-geometry-data-type.md)   
 [STStartPoint &#40;tipo di dati geometry&#41;](../../t-sql/spatial-geometry/ststartpoint-geometry-data-type.md)   
 [STEndpoint &#40;tipo di dati geometry&#41;](../../t-sql/spatial-geometry/stendpoint-geometry-data-type.md)   
 [STPointN &#40;tipo di dati geometry&#41;](../../t-sql/spatial-geometry/stpointn-geometry-data-type.md)   
 [STNumPoints &#40;geometry Data Type&#41; (STNumPoints &#40;tipo di dati geometry&#41;)](../../t-sql/spatial-geometry/stnumpoints-geometry-data-type.md)   
 [STIsRing &#40;tipo di dati geometry&#41;](../../t-sql/spatial-geometry/stisring-geometry-data-type.md)   
 [STIsClosed &#40;tipo di dati geometry&#41;](../../t-sql/spatial-geometry/stisclosed-geometry-data-type.md)   
 [STPointOnSurface &#40;tipo di dati geometry&#41;](../../t-sql/spatial-geometry/stpointonsurface-geometry-data-type.md)   
 [LineString](../../relational-databases/spatial/linestring.md)  
  
  

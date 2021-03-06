---
title: MultiLineString | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: spatial
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-spatial
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- MultiLineString geometry subtype [SQL Server]
- geometry subtypes [SQL Server]
ms.assetid: 95deeefe-d6c5-4a11-b347-379e4486e7b7
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: afb12ee323ca4ddec2e569a127fe90b80f359e40
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32971639"
---
# <a name="multilinestring"></a>MultiLineString
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Un'istanza **MultiLineString** è una raccolta di zero o più istanze di tipo **geometry** o **geographyLineString** .  
  
## <a name="multilinestring-instances"></a>Istanze MultiLineString  
 La figura seguente illustra esempi di istanze **MultiLineString** .  
  
 ![Esempi di istanze di geometria MultiLineString](../../relational-databases/spatial/media/multilinestring.gif "Esempi di istanze di geometria MultiLineString")  
  
 Come indicato nell'illustrazione:  
  
-   La figura 1 è un'istanza **MultiLineString** di tipo semplice il cui limite sono i quattro endpoint dei due elementi **LineString** .  
  
-   La figura 2 è un'istanza di tipo semplice **MultiLineString** perché si intersecano solo gli endpoint degli elementi **LineString** . Il limite è rappresentato dai due endpoint non sovrapposti.  
  
-   La figura 3 è un'istanza di tipo non semplice **MultiLineString** perché l'interno di uno dei suoi elementi **LineString** è intersecato. Il limite di questa istanza **MultiLineString** è rappresentato dai quattro endpoint.  
  
-   La figura 4 rappresenta un'istanza **MultiLineString** non semplice e non chiusa.  
  
-   La figura 5 rappresenta un'istanza **MultiLineString**semplice non chiusa. Non è chiusa perché gli elementi **LineString** non sono chiusi. È semplice perché nessuna delle parti interne di alcuna istanza **LineString** si interseca.  
  
-   La figura 6 rappresenta un'istanza **MultiLineString** semplice e chiusa. È chiusa perché tutti i suoi elementi sono chiusi. È semplice perché nessuno dei suoi elementi si interseca con le parti interne.  
  
### <a name="accepted-instances"></a>Istanze accettate  
 Per poter essere accettata, un'istanza **MultiLineString** deve essere vuota o comprendere esclusivamente istanze **LineString** accettate. Per altre informazioni sulle istanze **LineString** accettate, vedere [LineString](../../relational-databases/spatial/linestring.md). Gli esempi seguenti illustrano alcune istanze **MultiLineString** accettate.  
  
```  
DECLARE @g1 geometry = 'MULTILINESTRING EMPTY';  
DECLARE @g2 geometry = 'MULTILINESTRING((1 1, 3 5), (-5 3, -8 -2))';  
DECLARE @g3 geometry = 'MULTILINESTRING((1 1, 5 5), (1 3, 3 1))';  
DECLARE @g4 geometry = 'MULTILINESTRING((1 1, 3 3, 5 5),(3 3, 5 5, 7 7))';  
```  
  
 L'esempio seguente genera un'eccezione `System.FormatException` , perché la seconda istanza **LineString** non è valida.  
  
```  
DECLARE @g geometry = 'MULTILINESTRING((1 1, 3 5),(-5 3))';  
```  
  
### <a name="valid-instances"></a>Istanze valide  
 Per poter essere valida, un'istanza **MultiLineString** deve soddisfare i criteri seguenti:  
  
1.  Tutte le istanze che comprendono l'istanza **MultiLineString** devono essere istanze **LineString** valide.  
  
2.  Due istanze **LineString** che comprendono l'istanza **MultiLineString** possono sovrapporsi a un intervallo. Le istanze **LineString** possono solo intersecarsi oppure toccarsi reciprocamente o con altre istanze **LineString** in un numero finito di punti.  
  
 L'esempio seguente indica tre istanze **MultiLineString** valide e un'istanza **MultiLineString** non valida.  
  
```  
DECLARE @g1 geometry = 'MULTILINESTRING EMPTY';  
DECLARE @g2 geometry = 'MULTILINESTRING((1 1, 3 5), (-5 3, -8 -2))';  
DECLARE @g3 geometry = 'MULTILINESTRING((1 1, 5 5), (1 3, 3 1))';  
DECLARE @g4 geometry = 'MULTILINESTRING((1 1, 3 3, 5 5),(3 3, 5 5, 7 7))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(), @g4.STIsValid();  
```  
  
 `@g4` non è valida, perché la seconda istanza **LineString** si sovrappone alla prima istanza **LineString** in un intervallo. Si toccano in un numero infinito di punti.  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente crea un'istanza `geometry``MultiLineString` che contiene due elementi `LineString` con SRID 0.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('MULTILINESTRING((0 2, 1 1), (1 0, 1 1))');  
```  
  
 Per creare un'istanza di questa istanza con un diverso SRID, utilizzare `STGeomFromText()` o `STMLineStringFromText()`. È anche possibile utilizzare `Parse()` e quindi modificare l'identificatore SRID, come mostrato dall'esempio seguente.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('MULTILINESTRING((0 2, 1 1), (1 0, 1 1))');  
SET @g.STSrid = 13;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [STLength &#40;tipo di dati geometry&#41;](../../t-sql/spatial-geometry/stlength-geometry-data-type.md)   
 [STIsClosed &#40;tipo di dati geometry&#41;](../../t-sql/spatial-geometry/stisclosed-geometry-data-type.md)   
 [LineString](../../relational-databases/spatial/linestring.md)   
 [Dati spaziali &#40;SQL Server&#41;](../../relational-databases/spatial/spatial-data-sql-server.md)  
  
  

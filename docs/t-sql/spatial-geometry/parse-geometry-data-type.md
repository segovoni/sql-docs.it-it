---
title: Parse (tipo di dati geometry) | Documenti Microsoft
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- Parse (geometry Data Type)
ms.assetid: 6e080919-4b64-46cd-8dd2-254a9c232e53
caps.latest.revision: 19
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 64adf9398a6ea63203f75714aa97ccf2653e947b
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="parse-geometry-data-type"></a>Parse (tipo di dati geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce un **geometry** istanza da una rappresentazione di Open Geospatial Consortium (OGC) Well-Known Text (WKT). `Parse()`equivale a [stgeomfromtext ()](../../t-sql/spatial-geometry/parse-geometry-data-type.md), con l'eccezione che assume un riferimento a ID SRID 0 come parametro. All'input possono appartenere valori Z (innalzamento) e M (misura) facoltativi.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Parse ( 'geometry_tagged_text' )  
```  
  
## <a name="arguments"></a>Argomenti  
 *geometry_tagged_text*  
 È la rappresentazione WKT del **geometry** istanza da restituire. *geometry_tagged_text* è un **nvarchar** espressione.  
  
## <a name="return-types"></a>Tipi restituiti  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo restituito: **geometry**  
  
 Tipo CLR restituito: **SqlGeometry**  
  
## <a name="remarks"></a>Osservazioni  
 Il tipo OGC del **geometry** istanza restituita dalla `Parse()` è impostato sull'input WKT corrispondente.  
  
 La stringa 'Null' verrà interpretata come un valore null **geometry** istanza.  
  
 Questo metodo genererà un **FormatException** se l'input non è formattata correttamente.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene utilizzato il metodo `Parse()` per creare un'istanza `geometry`.  
  
```  
DECLARE @g geometry;   
SET @g = geometry::Parse('LINESTRING (100 100, 20 180, 180 180)');  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [STGeomFromText](../../t-sql/spatial-geometry/parse-geometry-data-type.md)   
 [Metodi di geometria statici estesi](../../t-sql/spatial-geometry/extended-static-geometry-methods.md)  
  
  


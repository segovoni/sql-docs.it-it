---
title: STGeomCollFromText (tipo di dati geometry) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- STGeomCollFromText_TSQL
- STGeomCollFromText (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STGeomCollFromText (geometry Data Type)
ms.assetid: 19e757b3-cb2e-4852-87b9-40a815ab707e
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f014f37142e82cc1c0bbcd85e35b09fa3215cbe8
ms.sourcegitcommit: a6596c62f607041c4402f7d5b41a232fca257c14
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36240103"
---
# <a name="stgeomcollfromtext-geometry-data-type"></a>STGeomCollFromText (tipo di dati geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce un'istanza **geometry** da una rappresentazione WKT (Well-Known Text) OGC (Open Geospatial Consortium) integrata con qualsiasi valore Z (innalzamento) e M (misura) appartenente all'istanza.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
STGeomCollFromText ( 'geometrycollection_tagged_text' , SRID )  
```  
  
## <a name="arguments"></a>Argomenti  
 *geometrycollection_tagged_text*  
 Rappresentazione WKT dell'istanza **geometry** da restituire. *geometry_tagged_text* è un'espressione **nvarchar(max)**.  
  
 *SRID*  
 Espressione **int** che rappresenta l'identificatore SRID dell'istanza **geometry** da restituire.  
  
## <a name="return-types"></a>Tipi restituiti  
 Tipo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituito: **geometry**  
  
 Tipo CLR restituito: **SqlGeometry**  
  
## <a name="remarks"></a>Remarks  
 Il tipo OGC dell'istanza **geometry** restituita da `STGeomCollFromText()` è impostato sull'input WKT corrispondente.  
  
 Questo metodo genererà un'eccezione se l'input non è valido.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene utilizzato il metodo `STGeomCollFromText()` per creare un'istanza di geometria.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomCollFromText('GEOMETRYCOLLECTION ( POLYGON((5 5, 10 5, 10 10, 5 5)), POINT(10 10) )', 0);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di geometria statici OGC](../../t-sql/spatial-geometry/ogc-static-geometry-methods.md)  
  
  


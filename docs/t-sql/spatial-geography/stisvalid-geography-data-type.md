---
title: STIsValid (tipo di dati geography) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- STIsValid method (geography)
ms.assetid: 1bfe787f-ddf0-4fc7-af6a-570a58faab23
caps.latest.revision: 11
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: aea666f53a2693f5809e32efb67d172dfd263897
ms.sourcegitcommit: a6596c62f607041c4402f7d5b41a232fca257c14
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36258303"
---
# <a name="stisvalid-geography-data-type"></a>STIsValid (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Restituisce true se un'istanza **geography** è in formato corretto e riconosciuta come oggetto geografico valido in base al relativo tipo OGC (Open Geospatial Consortium). Restituisce false se il formato di un'istanza **geography** non è corretto. Il metodo è preciso.  
  
 Questo metodo con tipo di dati geography supporta le istanze **FullGlobe** o le istanze spaziali con dimensioni maggiori di un emisfero.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STIsValid ( )  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 Tipo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituito: **bit**  
  
 Tipo CLR restituito: **SqlBoolean**  
  
## <a name="remarks"></a>Remarks  
 Il tipo OGC di un'istanza **geography** può essere determinato richiamando [STGeometryType()](../../t-sql/spatial-geography/stgeometrytype-geography-data-type.md).  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] produce solo istanze **geography** valide, ma consente l'archiviazione e il recupero di istanze non valide. Un'istanza valida che rappresenta lo stesso set di punti di un'istanza non valida può essere recuperata utilizzando il metodo `MakeValid()`.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene creata un'istanza `geography` e viene utilizzato `STIsValid()` per verificare se l'istanza è valida.  
  
```  
DECLARE @g geography = geography::STGeomFromText('LINESTRING(0 0, 2 2, 1 0)', 4326);  
SELECT @g.STIsValid();  
DECLARE @g geography  
```  
  
## <a name="see-also"></a>Vedere anche  
 [STGeometryType &#40;tipo di dati geography&#41;](../../t-sql/spatial-geography/stgeometrytype-geography-data-type.md)   
 [MakeValid &#40;tipo di dati geography&#41;](../../t-sql/spatial-geography/makevalid-geography-data-type.md)   
 [Metodi OGC sulle istanze geografiche](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  

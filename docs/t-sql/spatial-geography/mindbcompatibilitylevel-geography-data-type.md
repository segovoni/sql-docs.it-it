---
title: MinDbCompatibilityLevel (tipo di dati geography) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- MinDbCompatibilityLevel
- MinDbCompatibilityLevel_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MinDbCompatibilityLevel method (geography)
ms.assetid: a9e44748-4a9e-4179-abc4-7631597be5a7
caps.latest.revision: 17
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 1b3409d88f516bb59f67912acbf40b2c82b0275b
ms.sourcegitcommit: a6596c62f607041c4402f7d5b41a232fca257c14
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36249143"
---
# <a name="mindbcompatibilitylevel-geography-data-type"></a>MinDbCompatibilityLevel (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Restituisce la compatibilità del database minima che riconosce il tipo di dati **geography**.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
. MinDbCompatibilityLevel ( )  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 Tipo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituito: **int**  
  
 Tipo CLR restituito: **int**  
  
## <a name="remarks"></a>Remarks  
 Utilizzare `MinDbCompatibilityLevel()` per verificare la compatibilità di un oggetto spaziale prima di modificare il livello di compatibilità in un database. Un tipo **geography** non valido restituisce 110.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-testing-circularstring-type-for-compatibility-with-compatibility-level-110"></a>A. Verifica della compatibilità del tipo CircularString con livello di compatibilità 110  
 Nell'esempio seguente viene verificata la compatibilità di un'istanza `CircularString` con una versione precedente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
```  
DECLARE @g geometry = 'CIRCULARSTRING(-120.533 46.566, -118.283 46.1, -122.3 47.45)';  
IF @g.MinDbCompatibilityLevel() <= 110  
BEGIN  
    SELECT @g.ToString();  
END  
  
```  
  
### <a name="b-testing-linestring-type-for-compatibility-with-compatibility-level-100"></a>B. Verifica della compatibilità del tipo LineString con livello di compatibilità 100  
 Nell'esempio seguente viene verificata la compatibilità di un'istanza `LineString` con [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]:  
  
```  
DECLARE @g geometry = 'LINESTRING(-120.533 46.566, -118.283 46.1, -122.3 47.45)';  
IF @g.MinDbCompatibilityLevel() <= 100  
BEGIN  
    SELECT @g.ToString();  
END  
  
```  
  
### <a name="c-testing-the-value-of-a-geography-instance-for-compatibility"></a>C. Verifica della compatibilità del valore di un'istanza Geography  
 Nell'esempio seguente vengono illustrati i livelli di compatibilità per due istanze `geography`. Una è più piccola di un emisfero e l'altra è più grande di un emisfero:  
  
```  
DECLARE @g geography = geography::Parse('POLYGON((0 -10, 120 -10, 240 -10, 0 -10))');  
DECLARE @h geography = geography::Parse('POLYGON((0 10, 120 10, 240 10, 0 10))');  
IF (@g.EnvelopeAngle() >= 90)  
BEGIN  
SELECT @g.MinDbCompatibilityLevel();  
END     
IF (@h.EnvelopeAngle() < 90)  
BEGIN  
SELECT @h.MinDbCompatibilityLevel();  
END  
  
```  
  
 La prima istruzione SELECT restituisce 110, mentre la seconda istruzione SELECT restituisce 100.  
  
## <a name="see-also"></a>Vedere anche  
 [Livello di compatibilità ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)   
 [Compatibilità con le versioni precedenti del motore di database di SQL Server](../../database-engine/sql-server-database-engine-backward-compatibility.md)  
  
  

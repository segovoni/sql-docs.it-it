---
title: MinDbCompatibilityLevel (tipo di dati geometry) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
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
- MinDbCompatibilityLevel method (geometry)
ms.assetid: c848b974-8ccb-4c5c-a7eb-b019a9538d99
caps.latest.revision: 17
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ca5eacc943ff45cb8615f376a95a911355868541
ms.sourcegitcommit: a6596c62f607041c4402f7d5b41a232fca257c14
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36242643"
---
# <a name="mindbcompatibilitylevel-geometry-data-type"></a>MinDbCompatibilityLevel (tipo di dati geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Restituisce il livello minimo di compatibilità del database che riconosce l'istanza del tipo di dati **geometry**.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.MinDbCompatibilityLevel ( )  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 Tipo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituito: **int**  
  
 Tipo CLR restituito: **int**  
  
## <a name="remarks"></a>Remarks  
 Utilizzare `MinDbCompatibilityLevel()` per verificare la compatibilità di un oggetto spaziale prima di modificare il livello di compatibilità in un database.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-testing-circularstring-type-for-compatibility-with-compatibility-level-110"></a>A. Verifica della compatibilità del tipo CircularString con livello di compatibilità 110  
 Nell'esempio seguente viene verificata la compatibilità di un'istanza `CircularString` con una versione precedente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
```
 DECLARE @g geometry = 'CIRCULARSTRING(3 4, 8 9, 5 6)'; 
 IF @g.MinDbCompatibilityLevel() <= 110 
 BEGIN 
 SELECT @g.ToString(); 
 END
 ```  
  
### <a name="b-testing-linestring-type-for-compatibility-with-compatibility-level-100"></a>B. Verifica della compatibilità del tipo LineString con livello di compatibilità 100  
 Nell'esempio seguente viene verificata la compatibilità di un'istanza `LineString` con [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]:  
  
```
 DECLARE @g geometry = 'LINESTRING(3 4, 8 9, 5 6)'; 
 IF @g.MinDbCompatibilityLevel() <= 100 
 BEGIN 
 SELECT @g.ToString(); 
 END
``` 
  
## <a name="see-also"></a>Vedere anche  
 [Livello di compatibilità ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)  
  
  


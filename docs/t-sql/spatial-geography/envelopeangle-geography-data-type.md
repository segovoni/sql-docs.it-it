---
title: EnvelopeAngle (tipo di dati geography) | Microsoft Docs
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
- EnvelopeAngle
- EnvelopeAngle_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- EnvelopeAngle method
ms.assetid: 14a7ba15-168c-4b08-ba3d-951d73092ac7
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f3cb8a8722436880bdc1d347631cfe2e932315b6
ms.sourcegitcommit: a6596c62f607041c4402f7d5b41a232fca257c14
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36254023"
---
# <a name="envelopeangle-geography-data-type"></a>EnvelopeAngle (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce l'angolo massimo, espresso in gradi, tra il punto restituito dal metodo `EnvelopeCenter()` e un punto nell'istanza **geography**.  
  
 Questo metodo con tipo di dati **geography** supporta le istanze **FullGlobe** o le istanze spaziali con dimensioni maggiori di un emisfero.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
EnvelopeAngle( )  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 Tipo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituito: **float**  
  
 Tipo CLR restituito: **SqlDouble**  
  
## <a name="remarks"></a>Remarks  
 Questo metodo restituisce un punto nell'istanza **geography** espresso in gradi. Se usato con EnvelopeCenter(), `EnvelopeAngle()` restituisce un cerchio di delimitazione di un'istanza **geography**.  
  
 In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] questo metodo è stato esteso alle istanze **FullGlobe**.  
  
 La limitazione di emisfero applicata a `EnvelopeAngle()` in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] è stata rimossa. Tuttavia, per le istanze con angoli più ampi di 90 gradi, verrà restituito 180 gradi. `EnvelopeAngle()` non è preciso per le istanze **geography** estese a più di un emisfero.  
  
## <a name="examples"></a>Esempi  
  
```  
DECLARE @g geography = 'LINESTRING(-120 45, -120 0, -90 0)';   
SELECT @g.EnvelopeAngle();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi estesi sulle istanze di geografia](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [EnvelopeCenter &#40;tipo di dati geography&#41;](../../t-sql/spatial-geography/envelopecenter-geography-data-type.md)  
  
  

---
title: ShortestLineTo (tipo di dati geometry) | Microsoft Docs
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
- ShortestLineTo method (geometry)
ms.assetid: 39a2d0e4-4f93-4e94-a27e-6ad9537cfe74
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b5722110fc1ae00e8174078c735b15be0d0006bf
ms.sourcegitcommit: a6596c62f607041c4402f7d5b41a232fca257c14
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36250973"
---
# <a name="shortestlineto-geometry-data-type"></a>ShortestLineTo (tipo di dati geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Restituisce un'istanza **LineString** con due punti che rappresentano la distanza più breve tra le due istanze **geometry**. La lunghezza dell'istanza **LineString** restituita è la distanza tra le due istanze **geometry**.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.ShortestLineTo ( geometry_other )  
```  
  
## <a name="arguments"></a>Argomenti  
 *geometry_other*  
 Seconda istanza **geometry** da cui l'istanza **geometry** chiamante prova a determinare la distanza più breve.  
  
## <a name="return-types"></a>Tipi restituiti  
 Tipo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituito: **geometry**  
  
 Tipo CLR restituito: **SqlGeometry**  
  
## <a name="remarks"></a>Remarks  
 Il metodo restituisce un'istanza **LineString** con endpoint che si trovano sui bordi delle due istanze **geometry** non intersecate messe a confronto. La lunghezza dell'istanza **LineString** restituita corrisponde alla distanza minore tra le due istanze **geometry**. Viene restituita un'istanza **LineString** vuota quando le due istanze **geometry** si intersecano.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-calling-shortestlineto-on-non-intersecting-instances"></a>A. Chiamata di ShortestLineTo() in istanze non intersecate  
 In questo esempio viene individuata la distanza più breve tra un'istanza `CircularString` e un'istanza `LineString` e viene restituita l'istanza `LineString` che collega i due punti:  
  
```
 DECLARE @g1 geometry = 'CIRCULARSTRING(0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0)';  
 DECLARE @g2 geometry = 'LINESTRING(-4 7, 7 10, 3 7)';  
 SELECT @g1.ShortestLineTo(@g2).ToString();
 ```  
  
### <a name="b-calling-shortestlineto-on-intersecting-instances"></a>B. Chiamata di ShortestLineTo() in istanze intersecate  
 In questo esempio viene restituita un'istanza `LineString` vuota perché l'istanza `LineString` interseca l'istanza `CircularString`:  
  
```
 DECLARE @g1 geometry = 'CIRCULARSTRING(0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0)';  
 DECLARE @g2 geometry = 'LINESTRING(0 5, 7 10, 3 7)';  
 SELECT @g1.ShortestLineTo(@g2).ToString();
 ```  
  
## <a name="see-also"></a>Vedere anche  
 [ShortestLineTo &#40;tipo di dati geography&#41;](../../t-sql/spatial-geography/shortestlineto-geography-data-type.md)  
  
  


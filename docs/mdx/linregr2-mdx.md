---
title: LinRegR2 (MDX) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- LINREGR2
dev_langs:
- kbMDX
helpviewer_keywords:
- LinRegR2 function
ms.assetid: 770d1e1e-d034-43f1-82b1-3f91d52c86be
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 8f136ba9ed71fbdde7c9f7b797f3caae8bcc27da
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="linregr2-mdx"></a>LinRegR2 (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Calcola la regressione lineare di un set e restituisce il coefficiente di determinazione R<sup>2</sup>.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
LinRegR2(Set_Expression, Numeric_Expression_y [ ,Numeric_Expression_x ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Numeric_Expression_y*  
 Espressione numerica valida che in genere è un'espressione MDX (Multidimensional Expression) di coordinate di celle che restituisce un numero che rappresenta i valori per l'asse Y.  
  
 *Numeric_Expression_x*  
 Espressione numerica valida che in genere è un'espressione MDX (Multidimensional Expression) di coordinate di celle che restituisce un numero che rappresenta i valori per l'asse X.  
  
## <a name="remarks"></a>Osservazioni  
 La regressione lineare, che utilizza il metodo dei minimi quadrati, calcola l'equazione di una retta di regressione, ovvero la retta di migliore approssimazione per una serie di punti. Retta di regressione è l'equazione seguente, in cui un viene definito inclinazione e b viene definito intercetta:  
  
 y = ax+b  
  
 Il **LinRegR2** funzione valuta il setagainst specificato il primo expressionto numerico ottenere i valori per l'asse y. La funzione valuta quindi il set specificato in base alla seconda espressione numerica, se specificata, per ottenere i valori per l'asse X. Se il secondo expressionis numerica non specificata, la funzione utilizza il contesto corrente delle celle nel set specificato come valori per l'asse x. Non specificare la x-axisargument viene spesso utilizzato con la dimensione temporale.  
  
 Dopo aver ottenuto il set di punti, il **LinRegR2** funzione restituisce il coefficiente statistico R<sup>2</sup> che descrive l'adattamento dell'equazione lineare ai punti.  
  
> [!NOTE]  
>  Il **LinRegR2** funzione ignora le celle vuote o che contengono testo o valori logici. Tuttavia, la funzione include celle con valori zero.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente restituisce il coefficiente statistico R<sup>2</sup> che descrive l'adeguatezza dell'equazione di regressione lineare ai punti per le vendite unitarie e le misure delle vendite di archivio.  
  
```  
LinRegR2(LastPeriods(10), [Measures].[Unit Sales],[Measures].[Store Sales])  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

---
title: Proprietà Ordinal (ADO MD Cell) | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Cell::Ordinal
- Ordinal
helpviewer_keywords:
- Ordinal property [ADO MD]
ms.assetid: a6001168-b954-47f0-ba0d-c05c4cc40c58
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cbcbfce4a4d4fe8b5603cada49a224d7ea0b8992
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35284730"
---
# <a name="ordinal-property-ado-md-cell"></a>Proprietà Ordinal (ADO MD Cell)
Identifica in modo univoco un [cella](../../../ado/reference/ado-md-api/cell-object-ado-md.md) la posizione all'interno di un set di celle.  
  
## <a name="return-values"></a>Valori restituiti  
 Restituisce un **lungo** integer ed è di sola lettura.  
  
## <a name="remarks"></a>Remarks  
 Valore ordinale della cella identifica in modo univoco la cella all'interno di un set di celle. Concettualmente, le celle sono numerate in un set di celle come se fosse il set di celle un *p*-matrice dimensionale, dove *p* è il numero di [assi](../../../ado/reference/ado-md-api/axes-collection-ado-md.md). Le celle sono numerate a partire da zero in ordine crescente di riga. Di seguito è riportata la formula per calcolare il numero ordinale di una cella:  
  
 Valore ordinale della cella può essere utilizzato con il [elemento](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md) proprietà del [set di celle](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) oggetto da recuperare rapidamente il [cella](../../../ado/reference/ado-md-api/cell-object-ado-md.md).  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Cell (ADO MD)](../../../ado/reference/ado-md-api/cell-object-ado-md.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di asse (VBScript)](../../../ado/reference/ado-md-api/axis-example-vbscript.md)   
 [Oggetto Cellset (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)   
 [Proprietà dell'elemento (ADO MD Cellset)](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md)   
 [Proprietà Ordinal (Position - ADO MD)](../../../ado/reference/ado-md-api/ordinal-property-ado-md-position.md)

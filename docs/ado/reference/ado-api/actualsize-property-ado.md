---
title: Proprietà ActualSize (ADO) | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 03/20/2018
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Field20::ActualSize
helpviewer_keywords:
- ActualSize property [ADO]
ms.assetid: 722803d0-cef5-4d4c-b79d-3f2f58052229
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f71de5881975eb9ba38b2d21ef8f1590aae95d90
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35275100"
---
# <a name="actualsize-property-ado"></a>Proprietà ActualSize (ADO)
Indica la lunghezza effettiva del valore del campo espressa in byte.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Restituisce un **lungo** valore.  
  
## <a name="remarks"></a>Remarks  
 Utilizzare il **ActualSize** proprietà per restituire la lunghezza effettiva di un [campo](../../../ado/reference/ado-api/field-object.md) valore dell'oggetto. Per tutti i campi, il **ActualSize** proprietà è di sola lettura. Se ADO non è possibile determinare la lunghezza del **campo** il valore dell'oggetto, il **ActualSize** restituisce proprietà **adUnknown**.  
  
 Il **ActualSize** e [DefinedSize](../../../ado/reference/ado-api/definedsize-property.md) le proprietà sono diverse, come illustrato nell'esempio seguente. Oggetto **campo** oggetto con un tipo dichiarato di **adVarChar** e una lunghezza massima di 50 caratteri restituisce un **DefinedSize** valore della proprietà di 50, ma la  **ActualSize** valore restituito della proprietà è la lunghezza dei dati archiviati nel campo del record corrente. **I campi** con un **DefinedSize** maggiori di 255 byte sono considerati come colonne a lunghezza variabile.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Field](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio ActualSize e DefinedSize proprietà (Visual Basic)](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vb.md)   
 [Esempio ActualSize e DefinedSize proprietà (VC + +)](../../../ado/reference/ado-api/actualsize-and-definedsize-properties-example-vc.md)   
 [Proprietà DefinedSize](../../../ado/reference/ado-api/definedsize-property.md)

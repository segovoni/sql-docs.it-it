---
title: Proprietà NumericScale (ADO) | Documenti Microsoft
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
- _Parameter::NumericScale
- Field20::NumericScale
helpviewer_keywords:
- NumericScale property [ADO]
ms.assetid: 29a02992-64be-4fcd-be13-445cba205893
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5ad1cceb73749530faf08e96eecef235905971e5
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35279930"
---
# <a name="numericscale-property-ado"></a>Proprietà NumericScale (ADO)
Indica la scala di valori numerici in un [parametro](../../../ado/reference/ado-api/parameter-object.md) o [campo](../../../ado/reference/ado-api/field-object.md) oggetto.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Restituisce o imposta un **Byte** valore che indica il numero di posizioni decimali in cui i valori numerici verranno risolte.  
  
## <a name="remarks"></a>Remarks  
 Utilizzare il **NumericScale** proprietà per determinare il numero di cifre a destra del separatore decimale da utilizzare per rappresentare i valori per un valore numerico **parametro** o **campo** oggetto.  
  
 Per **parametro** oggetti, il **NumericScale** proprietà è di lettura/scrittura.  
  
 Per un **campo**oggetto **NumericScale** è di sola lettura. Tuttavia, per i nuovi **campo** gli oggetti che sono stati accodati per il [campi](../../../ado/reference/ado-api/fields-collection-ado.md) raccolta di un [Record](../../../ado/reference/ado-api/record-object-ado.md), **NumericScale** è lettura/scrittura solo dopo che il [valore](../../../ado/reference/ado-api/value-property-ado.md) proprietà per il **campo** è stato specificato e il provider di dati è stato aggiunto il nuovo **campo** chiamando il [ Aggiornamento](../../../ado/reference/ado-api/update-method.md) metodo il [campi](../../../ado/reference/ado-api/fields-collection-ado.md) insieme.  
  
## <a name="applies-to"></a>Si applica a  
  
|||  
|-|-|  
|[Oggetto Parameter](../../../ado/reference/ado-api/parameter-object.md)|[Oggetto Field](../../../ado/reference/ado-api/field-object.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [NumericScale e Precision (VB)](../../../ado/reference/ado-api/numericscale-and-precision-properties-example-vb.md)   
 [NumericScale e Precision (VC + +)](../../../ado/reference/ado-api/numericscale-and-precision-properties-example-vc.md)   
 [Proprietà Precision (ADO)](../../../ado/reference/ado-api/precision-property-ado.md)

---
title: Proprietà Precision (ADO) | Documenti Microsoft
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
- _Parameter::Precision
- Field20::Precision
helpviewer_keywords:
- Precision property [ADO]
ms.assetid: 1fa38e78-6b5b-414d-ba0a-3dd26b29b766
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 630bae40ab9e473656abeb3fa8cdb79de89e258c
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35280640"
---
# <a name="precision-property-ado"></a>Proprietà Precision (ADO)
Indica il grado di precisione per i valori numerici in un [parametro](../../../ado/reference/ado-api/parameter-object.md) oggetto o per valori numerici [campo](../../../ado/reference/ado-api/field-object.md) oggetti.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Restituisce o imposta un **Byte** valore che indica il numero massimo di cifre utilizzate per rappresentare i valori.  
  
## <a name="remarks"></a>Remarks  
 Utilizzare il **precisione** proprietà per determinare il numero massimo di cifre utilizzate per rappresentare i valori per un valore numerico **parametro** o **campo** oggetto.  
  
 Il valore è di lettura/scrittura in un **parametro** oggetto.  
  
 Per un **campo**oggetto **precisione** è di sola lettura. Tuttavia, per i nuovi **campo** gli oggetti che sono stati accodati per il [campi](../../../ado/reference/ado-api/fields-collection-ado.md) raccolta di un [Record](../../../ado/reference/ado-api/record-object-ado.md), **precisione** è di sola lettura/scrittura Dopo il [valore](../../../ado/reference/ado-api/value-property-ado.md) proprietà per il **campo** è stato specificato e il provider di dati è stato aggiunto il nuovo **campo** chiamando il [Aggiornamento](../../../ado/reference/ado-api/update-method.md) metodo il **campi** insieme.  
  
## <a name="applies-to"></a>Si applica a  
  
|||  
|-|-|  
|[Oggetto Field](../../../ado/reference/ado-api/field-object.md)|[Oggetto Parameter](../../../ado/reference/ado-api/parameter-object.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [NumericScale e Precision (VB)](../../../ado/reference/ado-api/numericscale-and-precision-properties-example-vb.md)   
 [NumericScale e Precision (VC + +)](../../../ado/reference/ado-api/numericscale-and-precision-properties-example-vc.md)   
 [Proprietà NumericScale (ADO)](../../../ado/reference/ado-api/numericscale-property-ado.md)

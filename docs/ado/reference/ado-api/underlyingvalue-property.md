---
title: Proprietà | Documenti Microsoft
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
- Field20::GetUnderlyingValue
- Field20::get_UnderlyingValue
- Field20::UnderlyingValue
helpviewer_keywords:
- UnderlyingValue property
ms.assetid: 00a0c8b8-8b63-433f-95b8-020ab05874a0
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4f0548dd9c42e18b988cc848ebd214dd191f8489
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35282790"
---
# <a name="underlyingvalue-property"></a>Proprietà
Indica il valore corrente di un [campo](../../../ado/reference/ado-api/field-object.md) oggetto nel database.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un **Variant** valore che indica il valore di **campo**.  
  
## <a name="remarks"></a>Remarks  
 Utilizzare il **UnderlyingValue** proprietà per restituire il valore del campo corrente dal database. Il valore del campo nel **UnderlyingValue** proprietà è il valore che è visibile alla transazione e potrebbe essere il risultato di un recente aggiornamento da un'altra transazione. Questo può differire dal [OriginalValue](../../../ado/reference/ado-api/originalvalue-property-ado.md) proprietà, che riflette il valore restituito in origine per il [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
 È simile all'utilizzo di [Resync](../../../ado/reference/ado-api/resync-method.md) (metodo), ma la **UnderlyingValue** proprietà restituisce solo il valore per un campo specifico del record corrente. Questo è lo stesso valore che il [Resync](../../../ado/reference/ado-api/resync-method.md) metodo utilizzato per sostituire il [valore](../../../ado/reference/ado-api/value-property-ado.md) proprietà.  
  
 Quando si utilizza questa proprietà con il **OriginalValue** proprietà, è possibile risolvere i conflitti generati dagli aggiornamenti in batch.  
  
## <a name="record"></a>Record  
 Per [Record](../../../ado/reference/ado-api/record-object-ado.md) oggetti, questa proprietà sarà vuota per i campi aggiunti prima [aggiornamento](../../../ado/reference/ado-api/update-method.md) viene chiamato.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Field](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio OriginalValue e UnderlyingValue proprietà (Visual Basic)](../../../ado/reference/ado-api/originalvalue-and-underlyingvalue-properties-example-vb.md)   
 [Esempio OriginalValue e UnderlyingValue proprietà (VC + +)](../../../ado/reference/ado-api/originalvalue-and-underlyingvalue-properties-example-vc.md)   
 [Proprietà OriginalValue (ADO)](../../../ado/reference/ado-api/originalvalue-property-ado.md)   
 [Metodo Resync](../../../ado/reference/ado-api/resync-method.md)

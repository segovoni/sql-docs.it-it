---
title: Aggiornare risincronizzazione proprietà dinamica (ADO) | Documenti Microsoft
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
helpviewer_keywords:
- Update Resync property [ADO]
ms.assetid: 8a3bb608-66d7-4128-a3ef-84cb0556de0d
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ae21cd46a181a3541dedb663dafef845ec162930
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35282678"
---
# <a name="update-resync-property-dynamic-ado"></a>Aggiornamento risincronizzazione proprietà dinamica (ADO)
Specifica se il [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) metodo è seguito da implicita [Resync](../../../ado/reference/ado-api/resync-method.md) operazione del metodo e in tal caso, l'ambito dell'operazione.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Imposta o restituisce uno o più di [ADCPROP_UPDATERESYNC_ENUM](../../../ado/reference/ado-api/adcprop-updateresync-enum.md) valori.  
  
## <a name="remarks"></a>Remarks  
 I valori di ADCPROP_UPDATERESYNC_ENUM possono essere combinati, ad eccezione di adResyncAll che già rappresenta una combinazione di altri valori.  
  
 La costante **adResyncConflicts** archivia i valori di risincronizzazione come valori sottostanti, ma non esegue l'override delle modifiche in sospeso.  
  
 **Aggiornare risincronizzazione** viene aggiunta una proprietà dinamica per il [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto [delle proprietà](../../../ado/reference/ado-api/properties-collection-ado.md) raccolta quando il [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) è impostata su **adUseClient**.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)

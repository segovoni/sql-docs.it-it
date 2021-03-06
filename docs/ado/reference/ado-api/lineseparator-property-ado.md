---
title: Proprietà LineSeparator (ADO) | Documenti Microsoft
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
- _Stream::LineSeparator
helpviewer_keywords:
- LineSeparator property [ADO]
ms.assetid: 0b20fbb8-6b83-48ec-b442-f96c8a4bafbb
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 76534a2925954c18d54ca7b14a3811d2544e233f
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35279290"
---
# <a name="lineseparator-property-ado"></a>Proprietà LineSeparator (ADO)
Indica il carattere binario da utilizzare come separatore di riga nel testo [flusso](../../../ado/reference/ado-api/stream-object-ado.md) oggetti.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Restituisce o imposta un [LineSeparatorsEnum](../../../ado/reference/ado-api/lineseparatorsenum.md) valore che indica il carattere separatore di riga utilizzato nel **flusso**. Il valore predefinito è **adCRLF**.  
  
## <a name="remarks"></a>Remarks  
 **LineSeparator** viene utilizzato per interpretare le righe durante la lettura del contenuto del testo di una **flusso**. È possibile ignorare le righe con la [SkipLine](../../../ado/reference/ado-api/skipline-method.md) metodo.  
  
 **LineSeparator** viene utilizzato solo con il testo **flusso** oggetti ([tipo](../../../ado/reference/ado-api/type-property-ado-stream.md) è **adTypeText**). Questa proprietà viene ignorata se **tipo** è **adTypeBinary**.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)

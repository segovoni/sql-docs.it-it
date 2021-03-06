---
title: Proprietà MaxRecords (ADO) | Documenti Microsoft
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
- Recordset15::MaxRecords
helpviewer_keywords:
- MaxRecords property [ADO]
ms.assetid: 20c76571-8c9a-482c-a99e-726ab1d93f8b
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b83fad35d6bc237e932dad9ed40ab2ae6f4ea279
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35279240"
---
# <a name="maxrecords-property-ado"></a>Proprietà MaxRecords (ADO)
Indica il numero massimo di record da restituire per una [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) da una query.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Restituisce o imposta un **lungo** valore che indica il numero massimo di record da restituire. Valore predefinito è zero (**0**), che indica nessun limite.  
  
## <a name="remarks"></a>Remarks  
 Utilizzare il **MaxRecords** proprietà per limitare il numero di record che il provider restituisce dall'origine dati. L'impostazione predefinita di questa proprietà è zero, ovvero che il provider restituisce che tutti i record richiesti.  
  
 Il **MaxRecords** proprietà è di lettura/scrittura quando il **Recordset** è chiuso e di sola lettura quando è aperto.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà MaxRecords (VB)](../../../ado/reference/ado-api/maxrecords-property-example-vb.md)   
 [Esempio di proprietà MaxRecords (VC++)](../../../ado/reference/ado-api/maxrecords-property-example-vc.md)   

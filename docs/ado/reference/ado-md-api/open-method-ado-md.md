---
title: Open (metodo) (ADO MD) | Documenti Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Open
- Cellset::Open
helpviewer_keywords:
- Open method [ADO MD]
ms.assetid: a87d8080-a238-45e5-bc80-9a8625b3810f
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 35faf0a1217f5b558c9781644cb9ea115e602584
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="open-method-ado-md"></a>Open (metodo) (ADO MD)
Recupera i risultati di una query multidimensionale e restituisce i risultati in un [set di celle](../../../ado/reference/ado-md-api/cellset-object-ado-md.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Cellset.Open Source, ActiveConnection  
```  
  
#### <a name="parameters"></a>Parametri  
 *Origine*  
 Facoltativa. Oggetto **Variant** che restituisce una query multidimensionale valida, ad esempio una query MDX (Multidimensional Expression). Il *origine* argomento corrisponde alla [origine](../../../ado/reference/ado-md-api/source-property-ado-md.md) proprietà. Per ulteriori informazioni su MDX, vedere il [OLE DB per l'elaborazione OLAP (Online Analytical)](http://msdn.microsoft.com/en-us/8a7673c6-3ca1-4411-9f1e-adf1e47df4f3) documentazione di Microsoft Data Access Components SDK.  
  
 *ActiveConnection*  
 Facoltativa. Oggetto **Variant** che restituisce una stringa che specifica un valido ADO [connessione](../../../ado/reference/ado-api/connection-object-ado.md) nome di variabile o una definizione per una connessione dell'oggetto. Il *ActiveConnection* argomento specifica la connessione in cui aprire il [set di celle](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) oggetto. Se si passa una definizione di connessione per questo argomento, ADO apre una nuova connessione utilizzando i parametri specificati. Il *ActiveConnection* argomento corrisponde alla [ActiveConnection](../../../ado/reference/ado-md-api/activeconnection-property-ado-md.md) proprietà.  
  
## <a name="remarks"></a>Osservazioni  
 Il **aprire** metodo genera un errore se uno dei relativi parametri viene omesso e il valore della proprietà corrispondente non è stata impostata prima di tentare di aprire il **set di celle**.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Cellset (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di set di celle (VB)](../../../ado/reference/ado-md-api/cellset-example-vb.md)   
 [Proprietà ActiveConnection (ADO MD)](../../../ado/reference/ado-md-api/activeconnection-property-ado-md.md)   
 [Close (metodo) (ADO MD)](../../../ado/reference/ado-md-api/close-method-ado-md.md)   
 [Oggetto di connessione (ADO.NET)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Proprietà Source (ADO MD)](../../../ado/reference/ado-md-api/source-property-ado-md.md)   
 [Proprietà state (ADO MD)](../../../ado/reference/ado-md-api/state-property-ado-md.md)
---
title: Metodo Recover (SQLServerXAResource) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerXAResource.recover
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 840ecfcf-0dd3-4b7b-976f-dc9a96cd1464
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d2e30fa3b1fc9d5ab419cd0f8f8b2b7bbcf018b2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32840476"
---
# <a name="recover-method-sqlserverxaresource"></a>Metodo recover (SQLServerXAResource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ottiene un elenco di rami di transazioni preparati da uno strumento di gestione delle risorse.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public javax.transaction.xa.Xid[] recover(int flags)  
```  
  
#### <a name="parameters"></a>Parametri  
 *flags*  
  
 Un **int** valore che può assumere uno dei seguenti valori: XAResource.TMSTARTRSCAN o XAResource.TMENDRSCAN o XAResource.TMNOFLAGS o XAResource.TMSTARTTRSCAN | XAResource.TMENDRSCAN.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto Xid.  
  
## <a name="exceptions"></a>Eccezioni  
 javax.transaction.xa.XAException  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo di ripristino viene specificato dal metodo nell'interfaccia javax Ripristina.  
  
 Se il parametro **flag** non XAResource.TMSTARTRSCAN o XAResource.TMSTARTRSCAN | XAResource.TMENDRSCAN, un'analisi di ripristino deve essere in corso.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-methods.md)   
 [Membri di SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [Classe SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  

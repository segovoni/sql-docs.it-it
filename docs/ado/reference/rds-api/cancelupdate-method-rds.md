---
title: Metodo CancelUpdate (RDS) | Documenti Microsoft
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
helpviewer_keywords:
- CancelUpdate method [RDS]
ms.assetid: 76d8a6e9-bc6c-4ea0-8e7a-2bae5ed06650
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9b8e41e0cd963b87b73fc65b3f149f22f3a67b76
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="cancelupdate-method-rds"></a>Metodo CancelUpdate (RDS)
Annulla le modifiche apportate alla riga corrente o nuova di un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DataControl.CancelUpdate  
```  
  
#### <a name="parameters"></a>Parametri  
 *DataControl*  
 Una variabile oggetto che rappresenta un [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) oggetto.  
  
## <a name="remarks"></a>Osservazioni  
 Il servizio di cursore per OLE DB mantiene una copia dei valori originali e una cache delle modifiche. Quando si chiama **CancelUpdate**, la cache delle modifiche viene reimpostata e tutti i controlli associati vengono aggiornati i dati originali.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto DataControl (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di metodo CancelUpdate (VBScript)](../../../ado/reference/rds-api/cancelupdate-method-example-vbscript.md)   
 [Pulsanti di Address Book comando](../../../ado/guide/remote-data-service/address-book-command-buttons.md)   
 [Cancel (metodo) (ADO)](../../../ado/reference/ado-api/cancel-method-ado.md)   
 [Metodo Cancel (RDS)](../../../ado/reference/rds-api/cancel-method-rds.md)   
 [Metodo CancelBatch (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [Metodo CancelUpdate (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [Metodo Refresh (RDS)](../../../ado/reference/rds-api/refresh-method-rds.md)   
 [Metodo SubmitChanges (RDS)](../../../ado/reference/rds-api/submitchanges-method-rds.md)



---
title: 'IRowsetFastLoad:: Commit (OLE DB) | Documenti Microsoft'
description: IRowsetFastLoad::Commit (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-interfaces
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRowsetFastLoad::Commit (OLE DB)
apitype: COM
helpviewer_keywords:
- Commit method
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 8f4baa2339105e8dac65c29e5efc35663b7c4b8d
ms.sourcegitcommit: 03ba89937daeab08aa410eb03a52f1e0d212b44f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/16/2018
ms.locfileid: "35689854"
---
# <a name="irowsetfastloadcommit-ole-db"></a>IRowsetFastLoad::Commit (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Contrassegna la fine di un batch di righe inserite e scrive le righe nella tabella di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Per esempi, vedere [Bulk copia i dati mediante IRowsetFastLoad &#40;OLE DB&#41; ](../../oledb/ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md) e [inviare dati BLOB a SQL SERVER utilizzando IROWSETFASTLOAD e ISEQUENTIALSTREAM &#40;OLE DB&#41;](../../oledb/ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
HRESULT Commit(  
      BOOL fDone);  
```  
  
## <a name="arguments"></a>Argomenti  
 *fDone*[in]  
 Se impostato su FALSE, il set di righe resta valido e può essere utilizzato dal consumer per l'inserimento di altre righe. Se impostato su TRUE, il set di righe non è più valido e il consumer non può inserire altre righe.  
  
## <a name="return-code-values"></a>Valori restituiti  
 S_OK  
 Il metodo è riuscito e tutti i dati inseriti sono stati scritti nella tabella [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 E_FAIL  
 Si è verificato un errore specifico del provider. Recuperare informazioni relative al testo dell'errore specifico dal provider.  
  
 E_UNEXPECTED  
 Il metodo è stato chiamato su un set di righe copia bulk precedentemente invalidato dal **IRowsetFastLoad:: commit** metodo.  
  
## <a name="remarks"></a>Remarks  
 Un Driver OLE DB per set di righe copia bulk SQL Server si comporta come un set di righe di modalità di aggiornamento ritardato. Quando l'utente inserisce i dati di riga nel set di righe, le righe inserite vengono trattate nello stesso modo come inserimenti in sospeso di un set di righe che supportano **IRowsetUpdate**.  
  
 Il consumer deve chiamare il **Commit** (metodo) nel set di righe di copia bulk per scrivere le righe inserite il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tabella esattamente come il **IRowsetUpdate:: Update** metodo viene utilizzato per inviare le righe a in sospeso un istanza di SQL Server.  
  
 Se il consumer rilascia il riferimento al set di righe di copia bulk senza chiamare il **Commit** (metodo), inserita tutte le righe non scritte in precedenza andranno perse.  
  
 Il consumer può raggruppare le righe inserite chiamando il **Commit** metodo con il *fDone* argomento impostato su FALSE. Quando si *fDone*è impostata su TRUE, il set di righe diventa non valido. Un set di righe copia bulk non valido supporta solo il **ISupportErrorInfo** interfaccia e **IRowsetFastLoad:: Release** metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [IRowsetFastLoad &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/irowsetfastload-ole-db.md)  
  
  

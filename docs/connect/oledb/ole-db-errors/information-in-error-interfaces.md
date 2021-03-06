---
title: Le informazioni nelle interfacce di errore | Documenti Microsoft
description: Informazioni nelle interfacce di errore
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-errors
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, errors
- IErrorRecords interface
- IErrorInfo interface
- OLE DB error handling, error interfaces
- ISQLErrorInfo interface
- errors [OLE DB], error interfaces
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 514b2328fce0f400315be4d21539f766f8715890
ms.sourcegitcommit: e1bc8c486680e6d6929c0f5885d97d013a537149
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/15/2018
ms.locfileid: "35666141"
---
# <a name="information-in-error-interfaces"></a>Informazioni nelle interfacce di errore
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Il Driver OLE DB per SQL Server riporta alcune informazioni di errore e di stato nelle interfacce di errore definite da OLE DB **IErrorInfo**, **IErrorRecords**, e **ISQLErrorInfo**.  
  
 Il Driver OLE DB per SQL Server supporta **IErrorInfo** membro funziona nel modo seguente.  
  
|Funzione membro|Description|  
|---------------------|-----------------|  
|**GetDescription**|Stringa descrittiva del messaggio di errore.|  
|**GetGUID**|GUID dell'interfaccia che ha definito l'errore.|  
|**GetHelpContext**|Non supportato. Restituisce sempre zero.|  
|**GetHelpFile**|Non supportato. Viene restituito sempre NULL.|  
|**GetSource**|Stringa "Microsoft OLE DB Driver per SQL Server".|  
  
 Il Driver OLE DB per SQL Server supporta disponibili per il consumer **IErrorRecords** membro funziona nel modo seguente.  
  
|Funzione membro|Description|  
|---------------------|-----------------|  
|**GetBasicErrorInfo**|Inserisce in una struttura ERRORINFO le informazioni di base su un errore. Una struttura ERRORINFO contiene membri che identificano il valore restituito HRESULT per l'errore nonché il provider e l'interfaccia alle quali si applica l'errore.|  
|**GetCustomErrorObject**|Restituisce un riferimento nelle interfacce **ISQLErrorInfo** e [ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1).|  
|**GetErrorInfo**|Restituisce un riferimento in un **IErrorInfo** interfaccia.|  
|**GetErrorParameters**|Il Driver OLE DB per SQL Server non restituisce parametri al consumer tramite **GetErrorParameters**.|  
|**GetRecordCount**|Conteggio dei record di errore disponibili.|  
  
 Il Driver OLE DB per SQL Server supporta **ISQLErrorInfo:: Getsqlinfo** parametri come indicato di seguito.  
  
|Parametro|Description|  
|---------------|-----------------|  
|*pbstrSQLState*|Restituisce un valore SQLSTATE per l'errore. I valori SQLSTATE vengono definiti nelle specifiche API, SQL-92, ODBC e ISO SQL. Né [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] né il Driver OLE DB per SQL Server definite valori SQLSTATE specifici dell'implementazione.|  
|*plNativeError*|Restituisce il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] numero di errore **master.dbo** quando disponibile. Gli errori nativi sono disponibili dopo un tentativo riuscito di inizializzare un Driver OLE DB per l'origine dati di SQL Server. Prima del tentativo, il Driver OLE DB per SQL Server restituisce sempre zero.|  
  
## <a name="see-also"></a>Vedere anche  
 [errori](../../oledb/ole-db-errors/errors.md)  
  
  

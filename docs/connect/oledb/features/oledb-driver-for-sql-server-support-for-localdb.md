---
title: Driver OLE DB per SQL Server Support for LocalDB | Documenti Microsoft
description: Driver OLE DB per il supporto di SQL Server per LocalDB
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: c66855285d9912b8a818b5e270f38880c7828ebc
ms.sourcegitcommit: 354ed9c8fac7014adb0d752518a91d8c86cdce81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/14/2018
ms.locfileid: "35612316"
---
# <a name="ole-db-driver-for-sql-server-support-for-localdb"></a>Driver OLE DB per SQL Server Support for LocalDB
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  A partire da [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], sarà disponibile una versione lightweight di SQL Server, chiamato Database locale. In questo argomento viene discussa la modalità di connessione a un database in un'istanza del database locale.  
  
## <a name="remarks"></a>Remarks  
 Per ulteriori informazioni sul database locale inclusa la modalità di installazione del database locale e di configurazione della relativa istanza, vedere:  
  
-   [Riferimento al database locale SQL Server Express](../../../relational-databases/sql-server-express-localdb-reference.md)  
  
-   [SQL Server 2016 Express LocalDB](../../../database-engine/configure-windows/sql-server-2016-express-localdb.md)  
  
 Riepilogando, il database locale consente di:  
  
-   Utilizzare **sqllocaldb.exe è** per individuare il nome dell'istanza predefinita.  
  
-   Utilizzare il **AttachDBFilename** parola chiave di stringa di connessione per specificare quale file di database il server deve essere connesso. Quando si utilizza **AttachDBFilename**, se non si specifica il nome del database con il **Database** parola chiave di stringa di connessione, verrà rimosso dal database dell'istanza del database locale quando l'applicazione chiude.  
  
-   Specificare un'istanza del database locale nella stringa di connessione:  
  
```  
SERVER=(localdb)\v11.0  
```  
  
 Se necessario, è possibile creare un'istanza del database locale con sqllocaldb.exe. È possibile utilizzare anche sqlcmd.exe per aggiungere e modificare i database in un'istanza del database locale. Ad esempio, **sqlcmd -S (localdb) \v11.0**.  
  
## <a name="see-also"></a>Vedere anche  
 [Driver OLE DB per funzionalità di SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)  
  
  

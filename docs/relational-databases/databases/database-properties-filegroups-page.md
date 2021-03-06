---
title: Proprietà database (pagina Filegroup) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: databases
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.swb.databaseproperties.filegroups.f1
ms.assetid: 8d06e859-73dd-4019-b6e8-99c5c5297697
caps.latest.revision: 31
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d8902da97f015bad1f548fb3aaf3d23b7d108aec
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32925286"
---
# <a name="database-properties-filegroups-page"></a>Proprietà database (pagina Filegroup)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Utilizzare questa pagina per visualizzare i filegroup o aggiungere un nuovo filegroup al database selezionato. I tipi di filegroup sono suddivisi in filegroup di *righe*, in filegroup di dati FILESTREAM e in filegroup ottimizzati per la memoria.  
  
 I filegroup di righe contengono file di dati e di log standard. I filegroup di dati FILESTREAM contengono file di dati FILESTREAM. Questi file di dati archiviano informazioni sulle modalità con cui i dati BLOB (binary large object) vengono archiviati nel file system quando si utilizza l'archiviazione FILESTREAM. Le opzioni sono le stesse per entrambi tipi di filegroup.  
  
 Se FILESTREAM non è stato abilitato, la sezione **Filestream** non sarà disponibile. È possibile abilitare l'archiviazione FILESTREAM usando la finestra di dialogo [Proprietà server (pagina Avanzate)](../../database-engine/configure-windows/server-properties-advanced-page.md).  
  
 Per altre informazioni sul modo in cui [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usa i filegroup righe, vedere [Filegroup e file di database](../../relational-databases/databases/database-files-and-filegroups.md). Per altre informazioni sui filegroup e i dati FILESTREAM, vedere [FILESTREAM &#40;SQL Server&#41;](../../relational-databases/blob/filestream-sql-server.md).  
  
 I filegroup ottimizzati per la memoria sono necessari per consentire ai database di contenere una o più tabelle ottimizzate per la memoria.  
  
## <a name="row-and-filestream-data-filegroup-options"></a>Opzioni di filegroup di righe e di dati FILESTREAM  
 **Nome**  
 Consente di immettere il nome del filegroup.  
  
 **File**  
 Visualizza il numero dei file contenuti nel filegroup.  
  
 **Sola lettura**  
 Consente di impostare il filegroup sullo stato di sola lettura.  
  
 **Default**  
 Consente di impostare il filegroup come filegroup predefinito. È possibile avere un filegroup predefinito per le righe e un filegroup predefinito per i dati FILESTREAM.  
  
 **Aggiungi**  
 Consente di aggiungere una nuova riga vuota alla griglia in cui sono elencati i filegroup per il database.  
  
 **Rimuovi**  
 Consente di rimuovere il filegroup selezionato dalla griglia.  
  
## <a name="memory-optimized-data-filegroup-options"></a>Opzioni di filegroup di dati con ottimizzazione per la memoria  
 **Nome**  
 Consente di immettere il nome del filegroup ottimizzato per la memoria.  
  
 **File FILESTREAM**  
 Visualizza il numero di file (contenitori) nel filegroup di dati ottimizzato per la memoria. È possibile aggiungere contenitori nella pagina **File** .  
  
 **Aggiungi**  
 Consente di aggiungere una nuova riga vuota alla griglia in cui sono elencati i filegroup per il database.  
  
 **Rimuovi**  
 Consente di rimuovere il filegroup selezionato dalla griglia.  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)  
  
  

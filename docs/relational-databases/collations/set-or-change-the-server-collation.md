---
title: Impostare o modificare le regole di confronto del server | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- server collations [SQL Server]
- collations [SQL Server], server
ms.assetid: 3242deef-6f5f-4051-a121-36b3b4da851d
caps.latest.revision: 34
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a1aa7c772b5a204f51a863f8c22780261156929f
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2018
ms.locfileid: "35698782"
---
# <a name="set-or-change-the-server-collation"></a>Impostazione o modifica di regole di confronto del server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Le regole di confronto del server costituiscono le regole di confronto predefinite per tutti i database di sistema installati con l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]e per ogni database utente creato successivamente. Le regole di confronto del server vengono specificate durante l'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Per altre informazioni, vedere [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md).  
  
## <a name="changing-the-server-collation"></a>Modifica di regole di confronto del server  
 La modifica delle regole di confronto predefinite per un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] può essere un'operazione complessa e richiede i passaggi seguenti:  
  
-   Assicurarsi che siano disponibili tutte le informazioni o gli script necessari per ricreare i database utente e tutti gli oggetti in essi contenuti.  
  
-   Esportare tutti i dati usando uno strumento come [l'utilità bcp](../../tools/bcp-utility.md). Per altre informazioni, vedere [Importazione ed esportazione bulk di dati &#40;SQL Server&#41;](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md).  
  
-   Eliminare tutti i database utente.  
  
-   Ricompilare il database master specificando le nuove regole di confronto nella proprietà SQLCOLLATION del comando **setup** . Ad esempio  
  
    ```  
    Setup /QUIET /ACTION=REBUILDDATABASE /INSTANCENAME=InstanceName   
    /SQLSYSADMINACCOUNTS=accounts /[ SAPWD= StrongPassword ]   
    /SQLCOLLATION=CollationName  
    ```  
  
     Per altre informazioni, vedere [Ricompilare database di sistema](../../relational-databases/databases/rebuild-system-databases.md).  
  
-   Creare tutti i database e tutti gli oggetti in essi contenuti.  
  
-   Importare tutti i dati.  
  
> [!NOTE]  
>  Anziché modificare le regole di confronto predefinite di un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è possibile specificare regole di confronto predefinite per ogni nuovo database creato.  
  
## <a name="see-also"></a>Vedere anche  
 [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md)   
 [Impostare o modificare le regole di confronto del database](../../relational-databases/collations/set-or-change-the-database-collation.md)   
 [Impostare o modificare le regole di confronto delle colonne](../../relational-databases/collations/set-or-change-the-column-collation.md)   
 [Ricompilare database di sistema](../../relational-databases/databases/rebuild-system-databases.md)  
  
  

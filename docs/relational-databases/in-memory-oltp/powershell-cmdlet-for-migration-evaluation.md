---
title: Cmdlet di PowerShell per la valutazione della migrazione | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: in-memory-oltp
ms.reviewer: ''
ms.suite: sql
ms.technology: in-memory-oltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 117250d3-9982-47fe-94fd-6f29f6159940
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 1903907268847f2d8e84a338f8bc3cf2135aba17
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2018
ms.locfileid: "34327103"
---
# <a name="powershell-cmdlet-for-migration-evaluation"></a>Cmdlet di PowerShell per la valutazione della migrazione
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Il cmdlet Save-SqlMigrationReport è uno strumento che valuta l'idoneità per la migrazione di più oggetti in un database di SQL Server. Attualmente è limitato alla valutazione di OLTP in memoria. Il cmdlet può essere eseguito sia in un ambiente Windows PowerShell con privilegi elevati che in sqlps.  
  
## <a name="syntax"></a>Sintassi  
  
```powershell  
Save-SqlMigrationReport [ -MigrationType OLTP ] [ -Server server -Database database [ -Object object_name ] ]  |  [ -InputObject smo_object ] -FolderPath path  
```  
  
#### <a name="parameters"></a>Parametri  
 I parametri sono descritti nella tabella riportata di seguito.  
  
|Parametri|Descrizione|  
|----------------|-----------------|  
|MigrationType|Tipo di scenario di migrazione specificato come destinazione dal cmdlet. Attualmente l'unico valore è il valore predefinito OLTP. Facoltativo.|  
|Server|Nome dell'istanza di SQL Server di destinazione. Obbligatorio nell'ambiente Windows Powershell se non viene specificato il parametro -InputObject. Facoltativo in SQLPS.|  
|Database|Nome del database di SQL Server di destinazione. Obbligatorio nell'ambiente Windows Powershell se non viene specificato il parametro -InputObject. Facoltativo in SQLPS.|  
|Object|Nome dell'oggetto di database di destinazione. Può essere una tabella o una stored procedure.|  
|InputObject|Oggetto SMO a cui il cmdlet deve fare riferimento. Obbligatorio nell'ambiente Windows Powershell se non vengono specificati -Server e -Database. Facoltativo in SQLPS.|  
|FolderPath|Cartella in cui il cmdlet deve depositare i report generati. Obbligatorio.|  
  
## <a name="results"></a>Risultati  
 La cartella specificata nel parametro -FolderPath conterrà due nomi di cartella: Tables e Stored procedures. Se l'oggetto di destinazione è una tabella, il report sarà all'interno della cartella Tables. In caso contrario, sarà all'interno della cartella Stored procedures.  
  
  

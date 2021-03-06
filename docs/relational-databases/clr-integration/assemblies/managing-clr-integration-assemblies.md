---
title: La gestione degli assembly dell'integrazione CLR | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
helpviewer_keywords:
- database objects [CLR integration], assemblies
- common language runtime [SQL Server], assemblies
- assemblies [CLR integration], managing
ms.assetid: bdbbf325-14f6-460e-a35a-d3861d3c961e
caps.latest.revision: 56
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: fba26bd48f94fb76f44c423297e9f2bc0d2f86cb
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37350183"
---
# <a name="managing-clr-integration-assemblies"></a>Gestione degli assembly dell'integrazione con CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Il codice gestito viene compilato e quindi distribuito in unità denominate assembly. Un assembly viene compresso come DLL o file eseguibile (con estensione exe). Mentre un file eseguibile può essere eseguito in modo autonomo, una DLL deve essere ospitata in un'applicazione esistente. Gli assembly DLL gestiti possono essere caricati e ospitati da [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] richiede che si registri l'assembly in un database [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilizzando l'istruzione CREATE ASSEMBLY, prima che possa essere caricato nel processo e usato. Gli assembly possono inoltre essere aggiornati a una versione più recente tramite l'istruzione ALTER ASSEMBLY o rimossi da [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tramite l'istruzione DROP ASSEMBLY.  
  
 Informazioni sull'assembly vengono archiviati nel **Sys. assembly_files** tabella del database in cui è stato installato l'assembly. Il **Sys. assembly_files** tabella contiene le colonne seguenti.  
  
|colonna|Description|  
|------------|-----------------|  
|assembly_id|Identificatore definito per l'assembly. Questo numero viene assegnato a tutti gli oggetti relativi allo stesso assembly.|  
|NAME|Nome dell'oggetto .|  
|file_id|Numero che identifica ogni oggetto, con il primo oggetto associato un determinato **assembly_id** viene assegnato il valore pari a 1. Se più oggetti sono associati allo stesso **assembly_id**, quindi ogni successivo **file_id** valore viene incrementato di 1.|  
|content|Rappresentazione esadecimale dell'assembly o del file.|  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 [Creazione di un assembly](../../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)  
 Viene descritta la creazione di assembly CLR SAFE, EXTERNAL_ACCESS e UNSAFE in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Modifica di un assembly](../../../relational-databases/clr-integration/assemblies/altering-an-assembly.md)  
 Viene descritto l'aggiornamento di assembly CLR in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Eliminazione di un assembly](../../../relational-databases/clr-integration/assemblies/dropping-an-assembly.md)  
 Viene descritta l'eliminazione di assembly CLR da [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza dell'integrazione CLR](../../../relational-databases/clr-integration/security/clr-integration-security.md)   
 [Sicurezza dall'accesso di codice dell'integrazione con CLR](../../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)  
  
  

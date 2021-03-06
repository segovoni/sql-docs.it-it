---
title: Ospitare gli attributi di protezione e programmazione dell'integrazione con Common Language Runtime | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: clr
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- host protection attributes [CLR integration]
- HostProtectionAttribute [CLR integration]
- common language runtime [SQL Server], host protection attributes
- disallowed types and members [CLR integration]
- common language runtime [SQL Server], disallowed types and members
- HPAs [CLR integration]
ms.assetid: 268078df-63ca-4c03-a8e7-7108bcea9697
caps.latest.revision: 28
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 501c85065f0519987a7837042bec45b5d5b4db9d
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37350313"
---
# <a name="host-protection-attributes-and-clr-integration-programming"></a>Attributi di protezione host e programmazione dell'integrazione con CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Common Language Runtime (CLR) fornisce un meccanismo di annotazione delle API gestite che fanno parte di .NET Framework con determinati attributi che possono interessare un host di CLR, ad esempio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], a partire da [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Di seguito sono riportati alcuni esempi di attributi di protezione host:  
  
-   **SharedState**, che indica se l'API espone la possibilità di creare o gestire lo stato (ad esempio campi classe statici) condiviso.  
  
-   **Sincronizzazione**, che indica se l'API espone la possibilità di eseguire la sincronizzazione tra thread.  
  
-   **ExternalProcessMgmt**, che indica se l'API espone una modalità per controllare il processo host.  
  
 Sulla base di tali attributi, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] specifica un elenco di attributi di protezione host non consentiti nell'ambiente host attraverso la sicurezza da accesso di codice. I requisiti di autorità di certificazione sono specificati da uno di tre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] set di autorizzazioni: **sicuri**, **EXTERNAL_ACCESS**, oppure **UNSAFE**. Uno dei tre livelli di sicurezza viene specificato quando l'assembly viene registrato nel server, usando il **CREATE ASSEMBLY** istruzione. Codice in esecuzione all'interno di **sicura** o **EXTERNAL_ACCESS** set di autorizzazioni devono evitare alcuni tipi o membri che hanno il **System.Security.Permissions.HostProtectionAttribute** attributo viene applicato. Per altre informazioni, vedere [creazione di un Assembly](../../relational-databases/clr-integration/assemblies/creating-an-assembly.md) e [restrizioni del modello di programmazione integrazione CLR](../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md).  
  
 Il **HostProtectionAttribute** non è un'autorizzazione di sicurezza come un modo per migliorare l'affidabilità, in quanto identifica specifici codice costruisce, tipi o metodi, che l'host possono essere disattivati. L'utilizzo dei **HostProtectionAttribute** applica un modello di programmazione che consente di proteggere la stabilità dell'host.  
  
## <a name="host-protection-attributes"></a>Attributi di protezione host  
 Gli attributi di protezione host identificano i tipi o i membri non inclusi nel modello di programmazione host e rappresentano i livelli di pericolo per l'affidabilità, riportati di seguito in ordine crescente di gravità:  
  
-   Sono altrimenti innocui.  
  
-   Possono determinare la destabilizzazione del codice utente gestito dal server.  
  
-   Possono determinare la destabilizzazione del processo del server stesso.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non consente l'utilizzo di un tipo o membro che dispone di un **HostProtectionAttribute** che specifica un **System.Security.Permissions.HostProtectionResource** con un valore di enumerazione ** ExternalProcessMgmt**, **ExternalThreading**, **MayLeakOnAbort**, **SecurityInfrastructure**, ** SelfAffectingProcessMgmnt**, **SelfAffectingThreading**, **SharedState**, **sincronizzazione**, o **interfacciautente**. In questo modo si impedisce agli assembly di chiamare membri che attivano la condivisione dello stato, eseguono la sincronizzazione, possono determinare una perdita di risorse al termine del processo o compromettere l'integrità del processo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### <a name="disallowed-types-and-members"></a>Tipi e membri non consentiti  
 Gli argomenti seguenti identificano i tipi e membri il cui **HostProtectionResource** i valori non sono consentiti da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Gli elenchi presenti in questi argomenti sono stati generati dagli assembly supportati.  Per altre informazioni, vedere [librerie di .NET Framework supportate](../../relational-databases/clr-integration/database-objects/supported-net-framework-libraries.md).  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 [Tipi e membri non consentiti in Microsoft.VisualBasic.dll](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-microsoft-visualbasic-dll.md)  
 Vengono elencati i tipi e i membri di Microsoft.VisualBasic.dll, i cui valori degli attributi di protezione host non sono consentiti.  
  
 [Tipi e membri non consentiti in mscorlib.dll](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-mscorlib-dll.md)  
 Elenca i tipi e i membri in mscorlib.dll, i cui valori degli attributi di protezione host non sono consentiti.  
  
 [Tipi e membri non consentiti in System.dll](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-system-dll.md)  
 Elenca i tipi e i membri in System.dll, i cui valori degli attributi di protezione host non sono consentiti.  
  
 [Tipi e membri non consentiti in System.Data.dll](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-system-data-dll.md)  
 Elenca i tipi e i membri in System.Data.dll, i cui valori degli attributi di protezione host non sono consentiti.  
  
 [Tipi e membri non consentiti in System.Core.dll](../../relational-databases/clr-integration-security-host-protection-attributes/disallowed-types-and-members-in-system-core-dll.md)  
 Elenca i tipi e i membri in System.Core.dll, i cui valori degli attributi di protezione host non sono consentiti.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza dall'accesso di codice integrazione CLR](../../relational-databases/clr-integration/security/clr-integration-code-access-security.md)   
 [Restrizioni relative al modello programmazione CLR Integration](../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md)   
 [Creazione di un assembly](../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)  
  
  

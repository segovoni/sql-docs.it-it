---
title: I file e numeri di versione | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, versions
- components [SMO]
- files [SMO], components
- SMO [SQL Server], versions
- versions [SMO]
ms.assetid: 510907b6-e7a9-41bd-b892-d6d99a5118e1
caps.latest.revision: 32
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: dfd73cbcb236c30f9a88a236ee87bf5cedecc7f8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37169044"
---
# <a name="files-and-version-numbers"></a>File e numeri di versione
  Tutte le necessarie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] componenti Management Objects (SMO) vengono installati come parte di un'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client o server. SMO viene implementato in diversi assembly gestiti. È possibile sviluppare applicazioni SMO in un client o in un server.  
  
|Directory|File|Description|  
|---------------|----------|-----------------|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|Microsoft.SqlServer.ConnectionInfo.dll|Contiene supporto per la connessione a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|Microsoft.SqlServer.ServiceBrokerEnum.dll|Contiene supporto per la programmazione di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Service Broker. È richiesto solo in programmi che accedono a Service Broker.|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|Microsoft.SqlServer.Smo.dll|Contiene la maggior parte delle classi SMO.|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|Microsoft.SqlServer.SmoExtended.dll<br /><br /> Microsoft.SqlServer.Management.Sdk.Sfc.dll<br /><br /> Microsoft.SqlServer.SqlEnum.dll|Contiene il supporto per le classi SMO.|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|Microsoft.SqlServer.WmiEnum.dll|Contiene le classi del provider Strumentazione gestione Windows (WMI, Windows Management Instrumentation). È richiesto solo per programmi che utilizzano le classi del Provider WMI.|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|Microsoft.SqlServer.RegSvrEnum.dll|Contiene le classi del server registrato. È richiesto solo per programmi che utilizzano le classi del server registrato.|  
  
  

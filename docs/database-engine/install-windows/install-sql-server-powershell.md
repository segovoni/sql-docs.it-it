---
title: Installare SQL Server PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/05/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: install
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 854c0b2f-02d2-46a4-a8cc-6b7a5d191cf8
caps.latest.revision: 9
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 11cbbd4c1dac33600330b504be11329051e371e6
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34770547"
---
# <a name="install-sql-server-powershell"></a>Installare SQL Server PowerShell
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Il programma di installazione configura automaticamente i componenti di PowerShell.  

Per installare il software che fornisce il supporto [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per Windows PowerShell utilizzare l'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Quando si seleziona qualsiasi funzionalità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che richiede il supporto di PowerShell, vengono installati i componenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell seguenti:  
  
- Gli snap-in di PowerShell per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Gli snap-in sono file DLL che implementano due tipi di supporto di Windows PowerShell per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
  - Set di cmdlet di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . I cmdlet sono comandi che implementano un'azione specifica, ad esempio **Invoke-Sqlcmd** esegue uno script [!INCLUDE[tsql](../../includes/tsql-md.md)] o XQuery che può essere eseguito anche con l'utilità **sqlcmd** , mentre **Invoke-PolicyEvaluation** segnala se gli oggetti [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sono conformi ai criteri di gestione basata su criteri.  
  
  - Provider di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Il provider consente di spostarsi nella gerarchia degli oggetti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizzando un percorso simile a un percorso del file system. Ciascun oggetto è associato a una classe dei modelli SMO ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects). È possibile utilizzare i metodi e le proprietà della classe per eseguire azioni sugli oggetti. Utilizzando il comando cd per un oggetto di database in un percorso, ad esempio, è possibile utilizzare i metodi e le proprietà della classe Microsoft.SqlServer.Management.SMO.Database per gestire il database.  
 
- Modulo **sqlps** importato nelle sessioni di Windows PowerShell 2.0 per caricare gli snap-in di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
 
- [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] supporta l'avvio delle sessioni di Windows PowerShell dall'albero di Esplora oggetti. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent supporta i passaggi del processo di Windows PowerShell.  
  
Windows Server 2012 e versioni successive e Windows 8 e versioni successive vengono forniti con PowerShell installato e configurato. Per informazioni sull'installazione di Windows PowerShell, vedere [Installazione di Windows PowerShell](http://docs.microsoft.com/powershell/scripting/setup/installing-windows-powershell).  

Per altre informazioni, vedere:   

- [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md)  
  
  

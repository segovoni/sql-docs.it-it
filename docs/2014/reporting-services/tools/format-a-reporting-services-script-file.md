---
title: Formattare un file script di Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- scripts [Reporting Services], formats
- formats [Reporting Services], script files
ms.assetid: 85a207dd-4e0f-4d40-a41e-0c75f65d719c
caps.latest.revision: 42
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: f54fb06c849655b8fbb7c60fd2b20117dff610f7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37276047"
---
# <a name="format-a-reporting-services-script-file"></a>Formattare un file script di Reporting Services
  Uno script [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] è un file di codice [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .NET, specificato su un proxy compilato in WSDL (Web Service Description Language), che definisce l'API SOAP di Reporting Services. Un file script viene archiviato come file di testo Unicode o UTF-8 con estensione .rss.  
  
 Il file script funge da modulo [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] e può contenere procedure definite dall'utente e variabili a livello del modulo. Per una corretta esecuzione, il file script deve contenere una routine Main. La routine Main è la prima routine alla quale viene eseguito l'accesso quando si esegue il file script. Nella routine Main è possibile aggiungere le operazioni del servizio Web ed eseguire le sottoroutine definite dall'utente. Nel codice seguente viene creata una routine Main:  
  
```  
Public Sub Main()  
    ' Your code goes here.  
End Sub  
```  
  
 L'ambiente di script si connette automaticamente al server di report, crea la classe proxy Web e genera una variabile di riferimento (*rs*) nell'oggetto proxy del servizio Web. Le singole istruzioni che vengono create devono solo fare riferimento alla variabile a livello di modulo *rs* per eseguire una delle operazioni del servizio Web disponibili nella libreria del servizio Web. Il codice [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] seguente chiama il metodo <xref:ReportService2010.ReportingService2010.ListChildren%2A> del servizio Web dall'interno di un file script:  
  
```  
Public Sub Main()  
    Dim items() As CatalogItem  
    items = rs.ListChildren("/", True)  
  
    Dim item As CatalogItem  
    For Each item In items  
        Console.WriteLine(item.Name)  
    Next item  
End Sub   
```  
  
> [!IMPORTANT]  
>  Le credenziali dell'utente vengono gestite dall'ambiente di script e vengono passate agli argomenti del prompt dei comandi tramite RS.exe. Anche se è possibile usare la variabile *rs* per impostare l'autenticazione del servizio Web, si consiglia di usare l'ambiente di script. Non è necessario autenticare il servizio Web nel file script. Per altre informazioni sull'autenticazione degli ambienti di script, vedere [RS.exe utilità &#40;SSRS&#41;](rs-exe-utility-ssrs.md).  
  
 Non dichiarare gli spazi dei nomi all'interno del file script. L'ambiente di scripting rende disponibili molti spazi dei nomi [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] utili: **System.Web.Services**, **System.Web.Services.Protocols**, **System.Xml** e **System.IO**.  
  
 Per esempi di script, vedere [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889)(Esempi del prodotto SQL Server Reporting Services).  
  
## <a name="see-also"></a>Vedere anche  
 [Servizio Web ReportServer](../report-server-web-service/report-server-web-service.md)   
 [Riferimento tecnico &#40;SSRS&#41;](../technical-reference-ssrs.md)   
 [Utilità RS.exe &#40;SSRS&#41;](rs-exe-utility-ssrs.md)  
  
  

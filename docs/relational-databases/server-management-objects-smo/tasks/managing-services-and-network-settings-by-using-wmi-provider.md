---
title: Gestione dei servizi e le impostazioni di rete con il Provider WMI | Documenti Microsoft
ms.custom: 
ms.date: 08/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: smo
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- WMI provider [SMO]
- services [SQL Server], SMO
- network settings [SMO]
- monitoring [SMO]
ms.assetid: ef8c3986-1098-4f21-b03a-f1f6bdb51c26
caps.latest.revision: "40"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d5f236d7726d2c45de16d8ac2a79dd2c4a4e4525
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="managing-services-and-network-settings-by-using-wmi-provider"></a>Gestione di servizi e di impostazioni di rete tramite il provider WMI
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Il provider WMI è un'interfaccia pubblicata utilizzata da [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Management Console (MMC) per gestire il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] servizi e protocolli di rete. In SMO la <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> oggetto rappresenta il Provider WMI.  
  
 Il <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> oggetto funziona indipendentemente dalla connessione stabilita con il <xref:Microsoft.SqlServer.Management.Smo.Server> oggetto a un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]e utilizza le credenziali di Windows per connettersi al servizio WMI.  
  
## <a name="example"></a>Esempio  
Per usare qualsiasi esempio di codice fornito, è necessario scegliere l'ambiente di programmazione, il modello di programmazione e il linguaggio di programmazione per la creazione dell'applicazione. Per ulteriori informazioni, vedere [crea un Visual C &#35; Progetto SMO in Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  

  
 Per programmi che utilizzano il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] provider WMI, è necessario includere il **importazioni** istruzione per qualificare lo spazio dei nomi WMI. Inserire l'istruzione dopo le altre istruzioni **Imports** , ma prima di qualsiasi dichiarazione nell'applicazione, ad esempio:  
  
 `Imports Microsoft.SqlServer.Management.Smo`  
  
 `Imports Microsoft.SqlServer.Management.Common`  
  
 `Imports Microsoft.SqlServer.Management.Smo.Wmi`  
  
## <a name="stopping-and-restarting-the-microsoft-sql-server-service-to-the-instance-of-sql-server-in-visual-basic"></a>Arresto e riavvio del servizio Microsoft SQL Server nell'istanza di SQL Server in Visual Basic  
 In questo esempio di codice viene illustrato come arrestare e avviare servizi tramite l'oggetto <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> SMO. Viene fornita un'interfaccia al provider WMI per la gestione della configurazione.  
  
```VBNET
'Declare and create an instance of the ManagedComputer object that represents the WMI Provider services.
Dim mc As ManagedComputer
mc = New ManagedComputer()
'Iterate through each service registered with the WMI Provider.
Dim svc As Service
For Each svc In mc.Services
    Console.WriteLine(svc.Name)
Next
'Reference the Microsoft SQL Server service.
svc = mc.Services("MSSQLSERVER")
'Stop the service if it is running and report on the status continuously until it has stopped.
If svc.ServiceState = ServiceState.Running Then
    svc.Stop()

    Console.WriteLine(String.Format("{0} service state is {1}", svc.Name, svc.ServiceState))
    Do Until String.Format("{0}", svc.ServiceState) = "Stopped"
        Console.WriteLine(String.Format("{0}", svc.ServiceState))
        svc.Refresh()
    Loop
    Console.WriteLine(String.Format("{0} service state is {1}", svc.Name, svc.ServiceState))
    'Start the service and report on the status continuously until it has started.
    svc.Start()
    Do Until String.Format("{0}", svc.ServiceState) = "Running"
        Console.WriteLine(String.Format("{0}", svc.ServiceState))
        svc.Refresh()
    Loop
    Console.WriteLine(String.Format("{0} service state is {1}", svc.Name, svc.ServiceState))

Else
    Console.WriteLine("SQL Server service is not running.")
End If
```
  
## <a name="enabling-a-server-protocol-using-a-urn-string-in-visual-basic"></a>Abilitazione di un protocollo server utilizzando una stringa URN in Visual Basic  
 Nell'esempio di codice viene illustrato come identificare un protocollo server utilizzando un oggetto URN e quindi abilitare il protocollo.  
  
```VBNET  
'This program must run with administrator privileges.  
        'Declare the ManagedComputer WMI interface.  
        Dim mc As New ManagedComputer()  
  
        'Create a URN object that represents the TCP server protocol.  
        Dim u As New Urn("ManagedComputer[@Name='V-ROBMA3']/ServerInstance[@Name='MSSQLSERVER']/ServerProtocol[@Name='Tcp']")  
  
        'Declare the serverProtocol variable and return the ServerProtocol object.  
        Dim sp As ServerProtocol  
        sp = mc.GetSmoObject(u)  
  
        'Enable the protocol.  
        sp.IsEnabled = True  
  
        'propagate back to the service  
        sp.Alter()  
```  
  
## <a name="enabling-a-server-protocol-using-a-urn-string-in-powershell"></a>Abilitazione di un protocollo server utilizzando una stringa URN in PowerShell  
 Nell'esempio di codice viene illustrato come identificare un protocollo server utilizzando un oggetto URN e quindi abilitare il protocollo.  
  
```powershell  
#This example shows how to identify a server protocol using a URN object, and then enable the protocol  
#This program must run with administrator privileges.  
  
#Load the assembly containing the classes used in this example  
[reflection.assembly]::LoadWithPartialName("Microsoft.SqlServer.SqlWmiManagement")  
  
#Get a managed computer instance  
$mc = New-Object -TypeName Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer  
  
#Create a URN object that represents the TCP server protocol  
#Change 'MyPC' to the name of the your computer   
$urn = New-Object -TypeName Microsoft.SqlServer.Management.Sdk.Sfc.Urn -argumentlist "ManagedComputer[@Name='MyPC']/ServerInstance[@Name='MSSQLSERVER']/ServerProtocol[@Name='Tcp']"  
  
#Get the protocol object  
$sp = $mc.GetSmoObject($urn)  
  
#enable the protocol on the object  
$sp.IsEnabled = $true  
  
#propagate back to actual service  
$sp.Alter()  
```  
  
## <a name="starting-and-stopping-a-service-in-visual-c"></a>Avvio e arresto di un servizio in Visual C#  
 In questo esempio di codice viene illustrato come arrestare e avviare un'istanza di SQL Server.  
  
```csharp  
{   
   //Declare and create an instance of the ManagedComputer   
   //object that represents the WMI Provider services.   
   ManagedComputer mc;   
   mc = new ManagedComputer();   
   //Iterate through each service registered with the WMI Provider.   
  
   foreach (Service svc in mc.Services)  
   {   
      Console.WriteLine(svc.Name);   
   }   
//Reference the Microsoft SQL Server service.   
  Service Mysvc = mc.Services["MSSQLSERVER"];   
//Stop the service if it is running and report on the status  
// continuously until it has stopped.   
   if (Mysvc.ServiceState == ServiceState.Running) {   
      Mysvc.Stop();   
      Console.WriteLine(string.Format("{0} service state is {1}", Mysvc.Name, Mysvc.ServiceState));   
      while (!(string.Format("{0}", Mysvc.ServiceState) == "Stopped")) {   
         Console.WriteLine(string.Format("{0}", Mysvc.ServiceState));   
          Mysvc.Refresh();   
      }   
      Console.WriteLine(string.Format("{0} service state is {1}", Mysvc.Name, Mysvc.ServiceState));   
//Start the service and report on the status continuously   
//until it has started.   
      Mysvc.Start();   
      while (!(string.Format("{0}", Mysvc.ServiceState) == "Running")) {   
         Console.WriteLine(string.Format("{0}", Mysvc.ServiceState));   
         Mysvc.Refresh();   
      }   
      Console.WriteLine(string.Format("{0} service state is {1}", Mysvc.Name, Mysvc.ServiceState));  
      Console.ReadLine();  
   }   
   else {   
      Console.WriteLine("SQL Server service is not running.");  
      Console.ReadLine();  
   }   
}  
```  
  
## <a name="starting-and-stopping-a-service-in-powershell"></a>Avvio e arresto di un servizio in PowerShell  
 In questo esempio di codice viene illustrato come arrestare e avviare un'istanza di SQL Server.  
  
```powershell  
#Load the assembly containing the objects used in this example  
[reflection.assembly]::LoadWithPartialName("Microsoft.SqlServer.SqlWmiManagement")  
  
#Get a managed computer instance  
$mc = New-Object -TypeName Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer  
  
#List out all sql server instnces running on this mc  
foreach ($Item in $mc.Services){$Item.Name}  
  
#Get the default sql server datbase engine service  
$svc = $mc.Services["MSSQLSERVER"]  
  
# for stopping and starting services PowerShell must run as administrator  
  
#Stop this service  
$svc.Stop()  
$svc.Refresh()  
while ($svc.ServiceState -ne "Stopped")  
{  
$svc.Refresh()  
$svc.ServiceState  
}  
"Service" + $svc.Name + " is now stopped"  
"Starting " + $svc.Name  
$svc.Start()  
$svc.Refresh()  
while ($svc.ServiceState -ne "Running")  
{  
$svc.Refresh()  
$svc.ServiceState  
}  
$svc.ServiceState  
"Service" + $svc.Name + "is now started"  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Concetti relativi al provider WMI per Gestione configurazione](../../../relational-databases/wmi-provider-configuration/wmi-provider-for-configuration-management.md)  
  
  
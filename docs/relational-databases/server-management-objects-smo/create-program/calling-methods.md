---
title: Chiamata di metodi | Microsoft Docs
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: smo
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- methods [SMO]
- calling methods
- SQL Server Management Objects, method calling
- SMO [SQL Server], method calling
ms.assetid: c88d5c5f-9ff0-4f84-b2b6-24c6b90fa15e
caps.latest.revision: 46
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: a3629f2f5d5905ce17df7a5aa15936edaa876ef4
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38005831"
---
# <a name="calling-methods"></a>Chiamata di metodi
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  Metodi di eseguono attività specifiche correlate all'oggetto, ad esempio emissione di un **Checkpoint** in un database o la richiesta di un elenco enumerato di account di accesso per l'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 I metodi eseguono un'operazione su un oggetto. I metodi possono accettare parametri e spesso restituiscono un valore. Il valore restituito può essere un tipo di dati semplice, un oggetto complesso o una struttura che contiene molti membri.  
  
 Utilizzare la gestione delle eccezioni per determinare se il metodo è stato eseguito correttamente. Per altre informazioni, vedere [Handling SMO Exceptions](../../../relational-databases/server-management-objects-smo/create-program/handling-smo-exceptions.md).  
  
## <a name="examples"></a>Esempi  
Per usare qualsiasi esempio di codice fornito, è necessario scegliere l'ambiente di programmazione, il modello di programmazione e il linguaggio di programmazione per la creazione dell'applicazione. Per altre informazioni, vedere [creare un Visual C&#35; progetto SMO in Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
 
  
## <a name="using-a-simple-smo-method-in-visual-basic"></a>Utilizzo di un metodo SMO semplice in Visual Basic  
 In questo esempio il metodo <xref:Microsoft.SqlServer.Management.Smo.Database.Create%2A> non accetta parametri e non restituisce alcun valore.  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Define a Database object variable by supplying the parent server and the database name arguments in the constructor.
Dim db As Database
db = New Database(srv, "Test_SMO_Database")
'Call the Create method to create the database on the instance of SQL Server. 
db.Create()
```
  
## <a name="using-a-simple-smo-method-in-visual-c"></a>Utilizzo di un metodo SMO semplice in Visual C#  
 In questo esempio il metodo <xref:Microsoft.SqlServer.Management.Smo.Database.Create%2A> non accetta parametri e non restituisce alcun valore.  
  
```csharp  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Define a Database object variable by supplying the parent server and the database name arguments in the constructor.   
Database db;   
db = new Database(srv, "Test_SMO_Database");   
//Call the Create method to create the database on the instance of SQL Server.   
db.Create();   
```  
  
 }  
  
## <a name="using-an-smo-method-with-a-parameter-in-visual-basic"></a>Utilizzo di un metodo SMO con un parametro in Visual Basic  
 Il <xref:Microsoft.SqlServer.Management.Smo.Table> oggetto ha un metodo denominato <xref:Microsoft.SqlServer.Management.Smo.Table.RebuildIndexes%2A>. Questo metodo richiede un parametro numerico che specifica **FillFactor**.  
  
```VBNET
Dim srv As Server  
srv = New Server  
Dim tb As Table  
tb = srv.Databases("AdventureWorks2012").Tables("Employee", "HumanResources")  
tb.RebuildIndexes(70)  
```  
  
## <a name="using-an-smo-method-with-a-parameter-in-visual-c"></a>Utilizzo di un metodo SMO con un parametro in Visual C#  
 Il <xref:Microsoft.SqlServer.Management.Smo.Table> oggetto ha un metodo denominato <xref:Microsoft.SqlServer.Management.Smo.Table.RebuildIndexes%2A>. Questo metodo richiede un parametro numerico che specifica `FillFactor`.  
  
```csharp  
{   
Server srv = default(Server);   
srv = new Server();   
Table tb = default(Table);   
tb = srv.Databases("AdventureWorks2012").Tables("Employee", "HumanResources");   
tb.RebuildIndexes(70);   
}   
```  
  
## <a name="using-an-enumeration-method-that-returns-a-datatable-object-in-visual-basic"></a>Utilizzo di un metodo di enumerazione che restituisce un oggetto DataTable in Visual Basic  
 Questa sezione descrive come chiamare un metodo di enumerazione e come gestire i dati nell'oggetto restituito <xref:System.Data.DataTable> oggetto.  
  
 Il metodo <xref:Microsoft.SqlServer.Management.Smo.Server.EnumCollations%2A> restituisce un oggetto <xref:System.Data.DataTable>, che richiede ulteriore navigazione per accedere a tutte le informazioni sulle regole di confronto disponibili relative all'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
```VBNET
'Connect to the local, default instance of SQL Server.  
Dim srv As Server  
srv = New Server  
'Call the EnumCollations method and return collation information to DataTable variable.  
Dim d As DataTable  
'Select the returned data into an array of DataRow.  
d = srv.EnumCollations  
'Iterate through the rows and display collation details for the instance of SQL Server.  
Dim r As DataRow  
Dim c As DataColumn  
For Each r In d.Rows  
    Console.WriteLine("==")  
    For Each c In r.Table.Columns  
        Console.WriteLine(c.ColumnName + " = " + r(c).ToString)  
    Next  
Next  
```  
  
## <a name="using-an-enumeration-method-that-returns-a-datatable-object-in-visual-c"></a>Utilizzo di un metodo di enumerazione che restituisce un oggetto DataTable in Visual C#  
 Questa sezione descrive come chiamare un metodo di enumerazione e come gestire i dati nell'oggetto restituito <xref:System.Data.DataTable> oggetto.  
  
 Il <xref:Microsoft.SqlServer.Management.Smo.Server.EnumCollations%2A> metodo viene restituito un sistema <xref:System.Data.DataTable> oggetto. Il <xref:System.Data.DataTable> oggetto richiede ulteriore navigazione per accedere a tutte le regole di confronto disponibili informazioni sull'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
```csharp  
//Connect to the local, default instance of SQL Server.   
{   
Server srv = default(Server);   
srv = new Server();   
//Call the EnumCollations method and return collation information to DataTable variable.   
DataTable d = default(DataTable);   
//Select the returned data into an array of DataRow.   
d = srv.EnumCollations;   
//Iterate through the rows and display collation details for the instance of SQL Server.   
DataRow r = default(DataRow);   
DataColumn c = default(DataColumn);   
foreach ( r in d.Rows) {   
  Console.WriteLine("=========");   
  foreach ( c in r.Table.Columns) {   
    Console.WriteLine(c.ColumnName + " = " + r(c).ToString);   
  }   
}   
}   
```  
  
## <a name="constructing-an-object-in-visual-basic"></a>Costruzione di un oggetto in Visual Basic  
 È possibile chiamare il costruttore di qualsiasi oggetto utilizzando l'operatore **New** . Viene eseguito l'overload del costruttore dell'oggetto <xref:Microsoft.SqlServer.Management.Smo.Database> e la versione del costruttore dell'oggetto <xref:Microsoft.SqlServer.Management.Smo.Database> usata nell'esempio accetta due parametri: l'oggetto <xref:Microsoft.SqlServer.Management.Smo.Server> padre cui appartiene il database e una stringa che rappresenta il nome del nuovo database.  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Declare and define a Database object by supplying the parent server and the database name arguments in the constructor.
Dim d As Database
d = New Database(srv, "Test_SMO_Database")
'Create the database on the instance of SQL Server.
d.Create()
Console.WriteLine(d.Name)
```
  
## <a name="constructing-an-object-in-visual-c"></a>Costruzione di un oggetto in Visual C#  
 È possibile chiamare il costruttore di qualsiasi oggetto utilizzando l'operatore **New** . Viene eseguito l'overload del costruttore dell'oggetto <xref:Microsoft.SqlServer.Management.Smo.Database> e la versione del costruttore dell'oggetto <xref:Microsoft.SqlServer.Management.Smo.Database> usata nell'esempio accetta due parametri: l'oggetto <xref:Microsoft.SqlServer.Management.Smo.Server> padre cui appartiene il database e una stringa che rappresenta il nome del nuovo database.  
  
```csharp  
{   
Server srv;   
srv = new Server();   
Table tb;   
tb = srv.Databases("AdventureWorks2012").Tables("Employee", "HumanResources");   
tb.RebuildIndexes(70);   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Declare and define a Database object by supplying the parent server and the database name arguments in the constructor.   
Database d;   
d = new Database(srv, "Test_SMO_Database");   
//Create the database on the instance of SQL Server.   
d.Create();   
Console.WriteLine(d.Name);   
}  
```  
  
## <a name="copying-an-smo-object-in-visual-basic"></a>Copia di un oggetto SMO in Visual Basic  
 Questo esempio di codice Usa il <xref:Microsoft.SqlServer.Management.Common.ServerConnection.Copy%2A> metodo per creare una copia del <xref:Microsoft.SqlServer.Management.Smo.Server> oggetto. Il <xref:Microsoft.SqlServer.Management.Smo.Server> oggetto rappresenta una connessione a un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
```VBNET  
'Connect to the local, default instance of SQL Server.
Dim srv1 As Server
srv1 = New Server()
'Modify the default database and the timeout period for the connection.
srv1.ConnectionContext.DatabaseName = "AdventureWorks2012"
srv1.ConnectionContext.ConnectTimeout = 30
'Make a second connection using a copy of the ConnectionContext property and verify settings.
Dim srv2 As Server
srv2 = New Server(srv1.ConnectionContext.Copy)
Console.WriteLine(srv2.ConnectionContext.ConnectTimeout.ToString)
```
  
## <a name="copying-an-smo-object-in-visual-c"></a>Copia di un oggetto SMO in Visual C#  
 Questo esempio di codice Usa il <xref:Microsoft.SqlServer.Management.Common.ServerConnection.Copy%2A> metodo per creare una copia del <xref:Microsoft.SqlServer.Management.Smo.Server> oggetto. Il <xref:Microsoft.SqlServer.Management.Smo.Server> oggetto rappresenta una connessione a un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
```csharp  
{   
//Connect to the local, default instance of SQL Server.   
Server srv1;   
srv1 = new Server();   
//Modify the default database and the timeout period for the connection.   
srv1.ConnectionContext.DatabaseName = "AdventureWorks2012";   
srv1.ConnectionContext.ConnectTimeout = 30;   
//Make a second connection using a copy of the ConnectionContext property and verify settings.   
Server srv2;   
srv2 = new Server(srv1.ConnectionContext.Copy);   
Console.WriteLine(srv2.ConnectionContext.ConnectTimeout.ToString);   
}  
```  
  
## <a name="monitoring-server-processes-in-visual-basic"></a>Monitoraggio di processi server in Visual Basic  
 È possibile ottenere le informazioni sul tipo di stato corrente relative all'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tramite i metodi di enumerazione. Nell'esempio di codice viene utilizzato il metodo <xref:Microsoft.SqlServer.Management.Smo.Server.EnumProcesses%2A> per individuare informazioni sui processi correnti. Viene inoltre illustrato come utilizzare le colonne e le righe nell'oggetto <xref:System.Data.DataTable> restituito.  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Call the EnumCollations method and return collation information to DataTable variable.
Dim d As DataTable
'Select the returned data into an array of DataRow.
d = srv.EnumProcesses
'Iterate through the rows and display collation details for the instance of SQL Server.
Dim r As DataRow
Dim c As DataColumn
For Each r In d.Rows
    Console.WriteLine("============================================")
    For Each c In r.Table.Columns
        Console.WriteLine(c.ColumnName + " = " + r(c).ToString)
    Next
Next
```
  
## <a name="monitoring-server-processes-in-visual-c"></a>Monitoraggio di processi server in Visual C#  
 È possibile ottenere le informazioni sul tipo di stato corrente relative all'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tramite i metodi di enumerazione. Nell'esempio di codice viene utilizzato il metodo <xref:Microsoft.SqlServer.Management.Smo.Server.EnumProcesses%2A> per individuare informazioni sui processi correnti. Viene inoltre illustrato come utilizzare le colonne e le righe nell'oggetto <xref:System.Data.DataTable> restituito.  
  
```csharp  
//Connect to the local, default instance of SQL Server.   
{   
Server srv = default(Server);   
srv = new Server();   
//Call the EnumCollations method and return collation information to DataTable variable.   
DataTable d = default(DataTable);   
//Select the returned data into an array of DataRow.   
d = srv.EnumProcesses;   
//Iterate through the rows and display collation details for the instance of SQL Server.   
DataRow r = default(DataRow);   
DataColumn c = default(DataColumn);   
foreach ( r in d.Rows) {   
  Console.WriteLine("=====");   
  foreach ( c in r.Table.Columns) {   
    Console.WriteLine(c.ColumnName + " = " + r(c).ToString);   
  }   
}   
}   
```  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.SqlServer.Management.Smo.Server>   
 <xref:Microsoft.SqlServer.Management.Common.ServerConnection>  
  
  

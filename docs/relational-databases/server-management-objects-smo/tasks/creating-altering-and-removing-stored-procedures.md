---
title: Creazione, modifica e rimozione di Stored procedure | Microsoft Docs
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
- stored procedures [SMO]
ms.assetid: 2a072f9c-8f11-4364-ab71-3990735a8d66
caps.latest.revision: 47
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 37eaf9824ac36333208ba538f36a5016ca6b87c8
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39084103"
---
# <a name="creating-altering-and-removing-stored-procedures"></a>Creazione, modifica e rimozione di stored procedure
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  Nelle [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO), stored procedure sono rappresentate dal <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> oggetto.  
  
 La creazione di un <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> oggetti in SMO richiede l'impostazione di <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure.TextBody%2A> proprietà per il [!INCLUDE[tsql](../../../includes/tsql-md.md)] script che definisce la stored procedure. I parametri richiedono il \@ prefissi e devono essere creati singolarmente utilizzando <xref:Microsoft.SqlServer.Management.Smo.StoredProcedureParameter> gli oggetti e l'aggiunta al <xref:Microsoft.SqlServer.Management.Smo.StoredProcedureParameter> insieme del <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> oggetto.  
  
## <a name="example"></a>Esempio  
 Per usare qualsiasi esempio di codice fornito, è necessario scegliere l'ambiente di programmazione, il modello di programmazione e il linguaggio di programmazione per la creazione dell'applicazione. Per altre informazioni, vedere [creare un Visual C&#35; progetto SMO in Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-altering-and-removing-a-stored-procedure-in-visual-basic"></a>Creazione, modifica e rimozione di una stored procedure in Visual Basic  
 Questo esempio di codice viene illustrato come creare una stored procedure per la [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database. Nell'esempio viene restituito il cognome di un dipendente quando viene fornito il numero ID del dipendente. La stored procedure richiede un parametro di input per specificare il numero ID del dipendente e un parametro di output per restituire il cognome del dipendente.  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Reference the AdventureWorks2012 2008R2 database.
Dim db As Database
db = srv.Databases("AdventureWorks2012")
'Define a StoredProcedure object variable by supplying the parent database and name arguments in the constructor.
Dim sp As StoredProcedure
sp = New StoredProcedure(db, "GetLastNameByEmployeeID")
'Set the TextMode property to false and then set the other object properties.
sp.TextMode = False
sp.AnsiNullsStatus = False
sp.QuotedIdentifierStatus = False
'Add two parameters.
Dim param As StoredProcedureParameter
param = New StoredProcedureParameter(sp, "@empval", DataType.Int)
sp.Parameters.Add(param)
Dim param2 As StoredProcedureParameter
param2 = New StoredProcedureParameter(sp, "@retval", DataType.NVarChar(50))
param2.IsOutputParameter = True
sp.Parameters.Add(param2)
'Set the TextBody property to define the stored procedure.
Dim stmt As String
stmt = " SELECT @retval = (SELECT LastName FROM Person.Person AS p JOIN HumanResources.Employee AS e ON p.BusinessEntityID = e.BusinessEntityID AND e.BusinessEntityID = @empval )"
sp.TextBody = stmt
'Create the stored procedure on the instance of SQL Server.
sp.Create()
'Modify a property and run the Alter method to make the change on the instance of SQL Server.   
sp.QuotedIdentifierStatus = True
sp.Alter()
'Remove the stored procedure.
sp.Drop()
``` 
  
## <a name="creating-altering-and-removing-a-stored-procedure-in-visual-c"></a>Creazione, modifica e rimozione di una stored procedure in Visual C#  
 Questo esempio di codice viene illustrato come creare una stored procedure per la [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database. Nell'esempio viene restituito il cognome di un dipendente quando viene fornito il numero ID del dipendente (`BusinessEntityID`). La stored procedure richiede un parametro di input per specificare il numero ID del dipendente e un parametro di output per restituire il cognome del dipendente.  
  
```csharp  
{  
            //Connect to the local, default instance of SQL Server.   
            Server srv;  
            srv = new Server();  
            //Reference the AdventureWorks2012 database.   
            Database db;  
            db = srv.Databases["AdventureWorks2012"];  
            //Define a StoredProcedure object variable by supplying the parent database and name arguments in the constructor.   
            StoredProcedure sp;  
            sp = new StoredProcedure(db, "GetLastNameByBusinessEntityID");  
            //Set the TextMode property to false and then set the other object properties.   
            sp.TextMode = false;  
            sp.AnsiNullsStatus = false;  
            sp.QuotedIdentifierStatus = false;  
            //Add two parameters.   
            StoredProcedureParameter param;  
            param = new StoredProcedureParameter(sp, "@empval", DataType.Int);  
            sp.Parameters.Add(param);  
            StoredProcedureParameter param2;  
            param2 = new StoredProcedureParameter(sp, "@retval", DataType.NVarChar(50));  
            param2.IsOutputParameter = true;  
            sp.Parameters.Add(param2);  
            //Set the TextBody property to define the stored procedure.   
            string stmt;  
            stmt = " SELECT @retval = (SELECT LastName FROM Person.Person,HumanResources.Employee WHERE Person.Person.BusinessEntityID = HumanResources.Employee.BusinessentityID AND HumanResources.Employee.BusinessEntityID = @empval )";  
            sp.TextBody = stmt;  
            //Create the stored procedure on the instance of SQL Server.   
            sp.Create();  
            //Modify a property and run the Alter method to make the change on the instance of SQL Server.   
            sp.QuotedIdentifierStatus = true;  
            sp.Alter();  
            //Remove the stored procedure.   
            sp.Drop();  
        }  
```  
  
## <a name="creating-altering-and-removing-a-stored-procedure-in-powershell"></a>Creazione, modifica e rimozione di una stored procedure in PowerShell  
 Questo esempio di codice viene illustrato come creare una stored procedure per la [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database. Nell'esempio viene restituito il cognome di un dipendente quando viene fornito il numero ID del dipendente (`BusinessEntityID`). La stored procedure richiede un parametro di input per specificare il numero ID del dipendente e un parametro di output per restituire il cognome del dipendente.  
  
```powershell  
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = get-item Adventureworks2012  
  
# Define a StoredProcedure object variable by supplying the parent database and name arguments in the constructor.   
$sp  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.StoredProcedure `  
-argumentlist $db, "GetLastNameByBusinessEntityID"  
  
#Set the TextMode property to false and then set the other object properties.   
$sp.TextMode = $false  
$sp.AnsiNullsStatus = $false  
$sp.QuotedIdentifierStatus = $false  
  
# Add two parameters  
$type = [Microsoft.SqlServer.Management.SMO.Datatype]::Int  
$param  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.StoredProcedureParameter `  
-argumentlist $sp,"@empval",$type  
$sp.Parameters.Add($param)  
  
$type = [Microsoft.SqlServer.Management.SMO.DataType]::NVarChar(50)  
$param2  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.StoredProcedureParameter `  
-argumentlist $sp,"@retval",$type  
$param2.IsOutputParameter = $true  
$sp.Parameters.Add($param2)  
  
#Set the TextBody property to define the stored procedure.   
$sp.TextBody =  " SELECT @retval = (SELECT LastName FROM Person.Person,HumanResources.Employee WHERE Person.Person.BusinessEntityID = HumanResources.Employee.BusinessentityID AND HumanResources.Employee.BusinessEntityID = @empval )"  
  
# Create the stored procedure on the instance of SQL Server.   
$sp.Create()  
  
# Modify a property and run the Alter method to make the change on the instance of SQL Server.   
$sp.QuotedIdentifierStatus = $true  
$sp.Alter()  
  
#Remove the stored procedure.   
$sp.Drop()  
```  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure>  
  
  

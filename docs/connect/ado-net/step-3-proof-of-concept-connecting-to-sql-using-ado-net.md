---
title: 'Passaggio 3: Modello di verifica per la connessione a SQL mediante ADO.NET | Documenti Microsoft'
ms.custom: ''
ms.date: 08/08/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: aebe3dc6-3ee4-4d11-8e43-5d32b3f91490
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6933fb1690b11d373974892672b43fe8df218860
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35288890"
---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-adonet"></a>Passaggio 3: Modello di verifica per la connessione a SQL mediante ADO.NET

- Articolo precedente:&nbsp;&nbsp;&nbsp;[passaggio 2: creare un database SQL per lo sviluppo di ADO.NET](step-2-create-a-sql-database-for-ado-net-development.md)  
- L'articolo successivo:&nbsp;&nbsp;&nbsp;[passaggio 4: connettere in modo resiliente a SQL con ADO.NET](step-4-connect-resiliently-to-sql-with-ado-net.md)  

  
Questo esempio di codice c# deve essere considerato un modello solo di prova. Il codice di esempio è semplificato per maggiore chiarezza e non rappresenta necessariamente le procedure consigliate da Microsoft.  
  
## <a name="step-1-connect"></a>Passaggio 1: connettersi
  
Il metodo **SqlConnection.Open** viene utilizzato per connettersi al database SQL.  


```CSharp  
    // C# , ADO.NET  
    using System;
    using QC = System.Data.SqlClient;  // System.Data.dll  
      
    namespace ProofOfConcept_SQL_CSharp  
    {  
        public class Program  
        {  
            static public void Main()  
            {  
                using (var connection = new QC.SqlConnection(  
                    "Server=tcp:YOUR_SERVER_NAME_HERE.database.windows.net,1433;" +
                    "Database=AdventureWorksLT;User ID=YOUR_LOGIN_NAME_HERE;" +
                    "Password=YOUR_PASSWORD_HERE;Encrypt=True;" +
                    "TrustServerCertificate=False;Connection Timeout=30;"  
                    ))  
                {  
                    connection.Open();  
                    Console.WriteLine("Connected successfully.");  
  
                    Console.WriteLine("Press any key to finish...");  
                    Console.ReadKey(true);  
                }  
            }  
        }  
    }  
    /**** Actual output:  
    Connected successfully.  
    Press any key to finish...  
    ****/  
```  


## <a name="step-2--execute-a-query"></a>Passaggio 2: Eseguire una query  
  
Il metodo SqlCommand. ExecuteReader:  
  
- Esegue l'istruzione SQL SELECT per il sistema SQL.  
- Restituisce un'istanza di SqlDataReader per fornire l'accesso alle righe di risultati.  
  
  
  
```CSharp  
    using System;  // C# , ADO.NET  
    using DT = System.Data;            // System.Data.dll  
    using QC = System.Data.SqlClient;  // System.Data.dll  
      
    namespace ProofOfConcept_SQL_CSharp  
    {  
        public class Program  
        {  
            static public void Main()  
            {  
                using (var connection = new QC.SqlConnection(  
                    "Server=tcp:YOUR_SERVER_NAME_HERE.database.windows.net,1433;" +
                    "Database=AdventureWorksLT;User ID=YOUR_LOGIN_NAME_HERE;" +
                    "Password=YOUR_PASSWORD_HERE;Encrypt=True;" +
                    "TrustServerCertificate=False;Connection Timeout=30;"  
                    ))  
                {  
                    connection.Open();  
                    Console.WriteLine("Connected successfully.");  
      
                    Program.SelectRows(connection);  
      
                    Console.WriteLine("Press any key to finish...");  
                    Console.ReadKey(true);  
                }  
            }  
      
            static public void SelectRows(QC.SqlConnection connection)  
            {  
                using (var command = new QC.SqlCommand())  
                {  
                    command.Connection = connection;  
                    command.CommandType = DT.CommandType.Text;  
                    command.CommandText = @"  
    SELECT  
        TOP 5  
            COUNT(soh.SalesOrderID) AS [OrderCount],  
            c.CustomerID,  
            c.CompanyName  
        FROM  
                            SalesLT.Customer         AS c  
            LEFT OUTER JOIN SalesLT.SalesOrderHeader AS soh  
                ON c.CustomerID = soh.CustomerID  
        GROUP BY  
            c.CustomerID,  
            c.CompanyName  
        ORDER BY  
            [OrderCount] DESC,  
            c.CompanyName; ";  
      
                    QC.SqlDataReader reader = command.ExecuteReader();  
      
                    while (reader.Read())  
                    {  
                        Console.WriteLine("{0}\t{1}\t{2}",  
                            reader.GetInt32(0),  
                            reader.GetInt32(1),  
                            reader.GetString(2));  
                    }  
                }  
            }  
        }  
    }  
    /**** Actual output:  
    Connected successfully.  
    1       29736   Action Bicycle Specialists  
    1       29638   Aerobic Exercise Company  
    1       29546   Bulk Discount Store  
    1       29741   Central Bicycle Specialists  
    1       29612   Channel Outlet  
    Press any key to finish...  
    ****/  
```  
  
  
  
## <a name="step-3-insert-a-row"></a>Passaggio 3: Inserire una riga  
  
  
In questo esempio viene illustrato come:  
  
- Eseguire un'istruzione SQL INSERT in modo sicuro, passando i parametri.  
  - Utilizzo dei parametri consente di proteggere da attacchi SQL injection.  
- Recuperare il valore generato automaticamente.  
  
  
  
```CSharp  
    using System;  // C# , ADO.NET  
    using DT = System.Data;            // System.Data.dll  
    using QC = System.Data.SqlClient;  // System.Data.dll  
      
    namespace ProofOfConcept_SQL_CSharp  
    {  
        public class Program  
        {  
            static public void Main()  
            {  
                using (var connection = new QC.SqlConnection(  
                    "Server=tcp:YOUR_SERVER_NAME_HERE.database.windows.net,1433;" +
                    "Database=AdventureWorksLT;User ID=YOUR_LOGIN_NAME_HERE;" +
                    "Password=YOUR_PASSWORD_HERE;Encrypt=True;" +
                    "TrustServerCertificate=False;Connection Timeout=30;"  
                    ))  
                {  
                    connection.Open();  
                    Console.WriteLine("Connected successfully.");  
      
                    Program.InsertRows(connection);  
      
                    Console.WriteLine("Press any key to finish...");  
                    Console.ReadKey(true);  
                }  
            }  
      
            static public void InsertRows(QC.SqlConnection connection)  
            {  
                QC.SqlParameter parameter;  
      
                using (var command = new QC.SqlCommand())  
                {  
                    command.Connection = connection;  
                    command.CommandType = DT.CommandType.Text;  
                    command.CommandText = @"  
    INSERT INTO SalesLT.Product  
            (Name,  
            ProductNumber,  
            StandardCost,  
            ListPrice,  
            SellStartDate  
            )  
        OUTPUT  
            INSERTED.ProductID  
        VALUES  
            (@Name,  
            @ProductNumber,  
            @StandardCost,  
            @ListPrice,  
            CURRENT_TIMESTAMP  
            ); ";  
      
                    parameter = new QC.SqlParameter("@Name", DT.SqlDbType.NVarChar, 50);  
                    parameter.Value = "SQL Server Express 2014";  
                    command.Parameters.Add(parameter);  
      
                    parameter = new QC.SqlParameter("@ProductNumber", DT.SqlDbType.NVarChar, 25);  
                    parameter.Value = "SQLEXPRESS2014";  
                    command.Parameters.Add(parameter);  
      
                    parameter = new QC.SqlParameter("@StandardCost", DT.SqlDbType.Int);  
                    parameter.Value = 11;  
                    command.Parameters.Add(parameter);  
      
                    parameter = new QC.SqlParameter("@ListPrice", DT.SqlDbType.Int);  
                    parameter.Value = 12;  
                    command.Parameters.Add(parameter);  
      
                    int productId = (int)command.ExecuteScalar();  
                    Console.WriteLine("The generated ProductID = {0}.", productId);  
                }  
            }  
        }  
    }  
    /**** Actual output:  
    Connected successfully.  
    The generated ProductID = 1000.  
    Press any key to finish...  
    ****/  
```

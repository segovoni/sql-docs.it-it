---
title: Ordinare l'esempio di proprietà (VB) | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- Sort property [ADO], Visual Basic example
ms.assetid: fc2fd40b-65d6-4023-90a3-90c9a88ef6cf
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 29251f351302fc94c9f55c0ada9c4028408cbe44
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35281886"
---
# <a name="sort-property-example-vb"></a>Esempio di proprietà Sort (VB)
Questo esempio viene utilizzato il [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) dell'oggetto [ordinamento](../../../ado/reference/ado-api/sort-property.md) proprietà per riordinare le righe di un **Recordset** derivato dal ***autori*** tabella di il ***Pubs*** database. Una routine dell'utilità secondaria stampa ogni riga.  
  
```  
'BeginSortVB  
  
    'To integrate this code  
    'replace the data source and initial catalog values  
    'in the connection string  
  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
     ' connection and recordset variables  
    Dim Cnxn As New ADODB.Connection  
    Dim rstAuthors As New ADODB.Recordset  
    Dim strCnxn As String  
    Dim strSQLAuthors As String  
  
    Dim strTitle As String  
  
    ' Open connection  
    Set Cnxn = New ADODB.Connection  
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" & _  
        "Initial Catalog='Pubs';Integrated Security='SSPI';"  
    Cnxn.Open strCnxn  
  
    ' open client-side recordset to enable sort method  
    Set rstAuthors = New ADODB.Recordset  
    rstAuthors.CursorLocation = adUseClient  
    strSQLAuthors = "SELECT * FROM Authors"  
    rstAuthors.Open strSQLAuthors, Cnxn, adOpenStatic, adLockReadOnly, adCmdText  
  
     ' sort the recordset last name ascending  
    rstAuthors.Sort = "au_lname ASC, au_fname ASC"  
     ' show output  
    Debug.Print "Last Name Ascending:"  
    Debug.Print "First Name  Last Name" & vbCr  
  
    rstAuthors.MoveFirst  
    Do Until rstAuthors.EOF  
        Debug.Print rstAuthors!au_fname & " " & rstAuthors!au_lname  
        rstAuthors.MoveNext  
    Loop  
  
     ' sort the recordset last name descending  
    rstAuthors.Sort = "au_lname DESC, au_fname ASC"  
     ' show output  
    Debug.Print "Last Name Descending"  
    Debug.Print "First Name  Last Name" & vbCr  
  
    Do Until rstAuthors.EOF  
        Debug.Print rstAuthors!au_fname & " " & rstAuthors!au_lname  
        rstAuthors.MoveNext  
    Loop  
  
    ' clean up  
    rstAuthors.Close  
    Cnxn.Close  
    Set rstAuthors = Nothing  
    Set Cnxn = Nothing  
    Exit Sub  
  
ErrorHandler:  
    ' clean up  
    If Not rstAuthors Is Nothing Then  
        If rstAuthors.State = adStateOpen Then rstAuthors.Close  
    End If  
    Set rstAuthors = Nothing  
  
    If Not Cnxn Is Nothing Then  
        If Cnxn.State = adStateOpen Then Cnxn.Close  
    End If  
    Set Cnxn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
'EndSortVB  
```  
  
 Questa è la routine dell'utilità secondaria che stampa il titolo e il contenuto dell'oggetto specificato **Recordset**.  
  
```  
Attribute VB_Name = "Sort"  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Recordset ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Proprietà Sort](../../../ado/reference/ado-api/sort-property.md)

---
title: Inviare e ricevere dati in modo incrementale mediante FILESTREAM (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: b82ecf4c-f151-4a99-8717-a73ee5ec994f
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 76a02beccc609c62267594e7f3512e8f0e395157
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37428500"
---
# <a name="send-and-receive-data-incrementally-with-filestream-odbc"></a>Inviare e ricevere dati in modo incrementale mediante FILESTREAM (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  In questo esempio viene illustrato come utilizzare la caratteristica FILESTREAM per inviare e ricevere dati in modo incrementale con SQLPutData e SQLGetData.  
  
 Per altre informazioni sulla caratteristica FILESTREAM, vedere [supporto FILESTREAM &#40;ODBC&#41;](../../relational-databases/native-client/odbc/filestream-support-odbc.md).  
  
## <a name="example"></a>Esempio  
 Prima di compilare ed eseguire questo esempio, abilitare il supporto FILESTREAM ([abilitare e configurare FILESTREAM](../../relational-databases/blob/enable-and-configure-filestream.md)).  
  
 Il primo listato di codice ([!INCLUDE[tsql](../../includes/tsql-md.md)]) consente di creare un database utilizzato dall'esempio. L'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deve disporre di accesso in scrittura per l'esecuzione dello script, che è possibile ottenere, ad esempio, eseguendo l'accesso come account di sistema locale.  
  
 Il secondo listato rappresenta il codice C++. È necessario specificare un server. Nel listato di codice C++, modificare "MyServer" impostando un nome di server valido. Verificare che nella variabile di ambiente INCLUDE sia presente la directory che contiene sqlncli.h. Compilare il listato di codice C++ con odbc32.lib, user32.lib, /D "_UNICODE", /D "UNICODE", odbc32.lib e /EHsc.  
  
 Il terzo listato di codice ([!INCLUDE[tsql](../../includes/tsql-md.md)]) consente di eliminare il database utilizzato dall'esempio.  
  
```  
USE master  
GO  
  
-- enable file stream  
exec sp_configure 'filestream access level', 2  
GO  
  
-- create directory for filestream database  
EXEC sp_configure 'show advanced options', 1  
GO  
RECONFIGURE  
GO  
EXEC sp_configure 'xp_cmdshell', 1  
GO  
RECONFIGURE  
GO  
EXEC xp_cmdshell 'md c:\filestreamdemo'  
GO  
  
-- Drop the filestream demo database  
IF EXISTS (SELECT name FROM master..sysdatabases WHERE name = 'myfilestreamdb')  
    DROP DATABASE [myfilestreamdb]  
GO  
  
-- Create filestream demo database  
CREATE DATABASE [myfilestreamdb] ON PRIMARY  
    (NAME=[myfilestreamdbprimary], FILENAME='c:\filestreamdemo\dbf.mdf'),  
    FILEGROUP [fsgrp] CONTAINS FILESTREAM (NAME=[fscnt],FILENAME='c:\filestreamdemo\fscnt')  
    LOG ON (NAME=[dblog], FILENAME='c:\filestreamdemo\db1.ldf', SIZE=5MB, MAXSIZE=3000MB, FILEGROWTH=5MB)  
GO  
  
-- Create table that contain filestream column  
CREATE TABLE [myfilestreamdb]..[mydocs]  
(  
    id UNIQUEIDENTIFIER ROWGUIDCOL NOT NULL UNIQUE,  
    doc VARBINARY(MAX) FILESTREAM  
)  
GO  
```  
  
```  
// compile with: /D "_UNICODE" /D "UNICODE" odbc32.lib /EHsc  
#pragma once  
#define WIN32_LEAN_AND_MEAN  
#include <tchar.h>  
#include <windows.h>  
#include <stdio.h>  
#include <sql.h>  
#include <sqlext.h>  
  
#define _SQLNCLI_ODBC_  
#include <sqlncli.h>  
  
#define SUCCESS(x) (!((x) & 0xFFFE))  
  
#define CHKRC(stmt) do { \  
                        rc = (stmt); \  
                        if (!SUCCESS(rc)) \  
                            throw (RETCODE) rc; \  
                    } while(0);  
  
void PrintError(SQLSMALLINT HandleType, SQLHANDLE Handle) {  
    RETCODE rc = SQL_SUCCESS;  
    SQLTCHAR szSqlState[6], szMessage[1024];  
    SQLSMALLINT i = 1, msgLen = 0;  
    SQLINTEGER NativeError;  
  
    do {  
       i = 1;  
       while (SQL_NO_DATA != (rc = SQLGetDiagRec(HandleType, Handle, i, szSqlState, &NativeError, szMessage, sizeof(szMessage)/sizeof(SQLTCHAR), &msgLen)) && SUCCESS(rc)) {  
            _tprintf(_T("SQLState=%s, NativeError=%ld, Message=%s\r\n"), szSqlState, NativeError, szMessage);  
            i++;  
        }  
    }   
    while (SQL_NO_DATA != (rc = SQLMoreResults(Handle)) && SUCCESS(rc));  
}  
  
int _tmain(int argc, _TCHAR* argv[]) {  
    RETCODE rc = SQL_SUCCESS;  
    HENV henv = SQL_NULL_HENV;  
    HDBC hdbc = SQL_NULL_HDBC;  
    SQLHSTMT hstmt = SQL_NULL_HSTMT;  
    SQLTCHAR * pszConnection = _T("DRIVER={SQL Server Native Client 10.0};")  
                               _T("Server=MyServer;")  
                               _T("Trusted_Connection=Yes;");  
    SQLLEN cbBuffer = SQL_DATA_AT_EXEC;  
    BYTE rgbDoc[1024];  
    SQLLEN cbDoc;  
  
    try {  
        CHKRC(SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HENV, &henv));  
        CHKRC(SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER)SQL_OV_ODBC3, 0));  
        CHKRC(SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc));  
        CHKRC(SQLDriverConnect(hdbc, NULL, pszConnection, SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT));  
  
        CHKRC(SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt));  
        CHKRC(SQLPrepare(hstmt,  (SQLTCHAR *)_T("INSERT INTO [myfilestreamdb]..[mydocs] VALUES(newid(), ?)"), SQL_NTS));  
        CHKRC(SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_BINARY, SQL_VARBINARY, SQL_SS_LENGTH_UNLIMITED, 0, (SQLPOINTER)1, 0, &cbBuffer));  
  
        rc = ::SQLExecute(hstmt);  
        if (SQL_NEED_DATA == rc) {  
            SQLPOINTER pParam = NULL;  
            while (SQL_NEED_DATA == (rc = ::SQLParamData(hstmt, (SQLPOINTER *)&pParam))) {  
                CHKRC(SQLPutData(hstmt, "Hello ", 6));  
                CHKRC(SQLPutData(hstmt, "World!", 6));  
            }  
        }  
  
        CHKRC(SQLFreeStmt(hstmt, SQL_CLOSE));  
        CHKRC(SQLExecDirect(hstmt, _T("SELECT doc FROM [myfilestreamdb]..[mydocs]"), SQL_NTS));  
        CHKRC(SQLBindCol(hstmt, 1, SQL_C_BINARY, (SQLPOINTER)rgbDoc, sizeof(rgbDoc), &cbDoc));  
        CHKRC(SQLFetch(hstmt));  
  
        rgbDoc[cbDoc] = '\0';  
        printf("%s\r\n", (LPSTR)rgbDoc);  
    }  
    catch (RETCODE retcode) {  
        rc = retcode;  
    }  
  
    if (!SUCCESS(rc))  
        if (hstmt)  
            PrintError(SQL_HANDLE_STMT, hstmt);  
        else if (hdbc)  
            PrintError(SQL_HANDLE_DBC, hdbc);  
        else if(henv)  
            PrintError(SQL_HANDLE_ENV, henv);  
  
    if (hstmt)  
        SQLFreeHandle(SQL_HANDLE_STMT, hstmt);  
  
    if (hdbc) {  
        SQLDisconnect(hdbc);  
        SQLFreeHandle(SQL_HANDLE_DBC, hdbc);  
    }  
  
    if (henv)  
        SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
```  
  
```  
USE master  
GO  
-- Drop the filestream demo database  
sp_detach_db 'myfilestreamdb'  
IF EXISTS (SELECT name FROM master..sysdatabases WHERE name = 'myfilestreamdb')  
    DROP DATABASE [myfilestreamdb]  
EXEC xp_cmdshell 'rd /s /q c:\filestreamdemo'  
GO  
```  
  
  

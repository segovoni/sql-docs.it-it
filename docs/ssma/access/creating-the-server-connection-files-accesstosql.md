---
title: Creazione dei file di connessione del Server (AccessToSQL) | Documenti Microsoft
ms.prod: sql
ms.custom: ''
ms.date: 08/17/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 829153be-aa8e-4162-87e8-69882feecf19
caps.latest.revision: 10
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: c6e46ab77966f6f6f392de64c076c4560c7885ab
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34773627"
---
# <a name="creating-the-server-connection-files-accesstosql"></a>La creazione di file di connessione (AccessToSQL) del server
Informazioni sul server può essere specificato nella sezione del file di script server. Inoltre possibile specificare le informazioni sul server in un file di connessione server separato. Il parametro della riga di comando per il file di connessione del server è `-c <serverconnectionfile>`. Se lo stesso id di server è presente nel file di connessione sia lo script e il server, è considerata la definizione del server nel file di script.  
  
```xml  
<!--Sample of server connection file commands -->  
<!--Connection to SQL Server-->  
  
<sql-server name="target_3">  
  
  <sql-server-authentication>  
  
    <server value="$TargetServerName$"/>  
  
    <database value="$TargetDB$"/>  
  
    <user-id value="$TargetUserName$"/>  
  
    <password value="$TargetPassword$"/>  
  
    <encrypt value="true"/>  
  
    <trust-server-certificate value="true"/>  
  
  </sql-server-authentication>  
  
</sql-server>  
```  
  
```xml  
<!--Connection to SQL Azure-->  
  
<sql-azure name="target_azure">  
  
  <server value="$TargetAzureServerName$"/>  
  
  <database value="$TargetAzureDB$"/>  
  
  <user-id value="$TargetAzureUserName$"/>  
  
  <password value="$TargetAzurePassword$"/>  
  
</sql-azure>  
```  
  
## <a name="server-connection-file-validation"></a>Convalida del file di connessione di server  
L'utente può facilmente convalidare il file di connessione del server nel file di definizione dello schema **'A2SSConsoleScriptServersSchema.xsd'** disponibile nella cartella 'Schemi'.  
  
## <a name="next-step"></a>Passaggio successivo  
Il passaggio successivo nella console di gestione viene [in esecuzione la Console di SSMA &#40;AccessToSQL&#41;](../../ssma/access/executing-the-ssma-console-accesstosql.md)  
  
## <a name="see-also"></a>Vedere anche  
[L'esecuzione la Console SSMA (Access)](http://msdn.microsoft.com/aa1bf665-8dc0-4259-b36f-46ae67197a43)  
  

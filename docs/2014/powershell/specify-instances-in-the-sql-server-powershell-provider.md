---
title: Specificare istanze nel provider SQL Server PowerShell| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 9373de68-fd43-45f2-b9a6-149c96610aeb
caps.latest.revision: 7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b34db68006ab06d5e0f3346f567542005d2dd7a8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37175898"
---
# <a name="specify-instances-in-the-sql-server-powershell-provider"></a>Specifica di istanze nel provider SQL Server PowerShell
  I percorsi specificati per il provider SQL Server PowerShell devono identificare l'istanza di [!INCLUDE[ssDE](../includes/ssde-md.md)] e il computer sulla quale è in esecuzione. La sintassi per la specifica del computer e l'istanza devono conformarsi sia alle regole per gli identificatori di SQL Server che ai percorsi di Windows PowerShell.  
  
1.  **Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions)  
  
2.  **Per specificare un'istanza:**  [Esempi](#Examples)  
  
## <a name="before-you-begin"></a>Prima di iniziare  
 Il primo nodo che segue SQLSERVER:\SQL in un percorso del provider SQL Server è il nome del computer che esegue l'istanza di [!INCLUDE[ssDE](../includes/ssde-md.md)], ad esempio:  
  
```  
SQLSERVER:\SQL\MyComputer  
```  
  
 Se si esegue Windows PowerShell nello stesso computer dell'istanza del [!INCLUDE[ssDE](../includes/ssde-md.md)], è possibile utilizzare localhost o (local) al posto del nome del computer. Gli script che utilizzano localhost o (local) possono essere eseguiti in qualsiasi computer senza che debbano essere modificati per riflettere i diversi nomi dei computer.  
  
 È possibile eseguire più istanze del programma eseguibile [!INCLUDE[ssDE](../includes/ssde-md.md)] sullo stesso computer. Il nodo che segue il nome del computer in un percorso del provider SQL Server identifica l'istanza; ad esempio:  
  
```  
SQLSERVER:\SQL\MyComputer\MyInstance  
```  
  
 Ciascun computer può disporre di un'istanza predefinita di [!INCLUDE[ssDE](../includes/ssde-md.md)]. Non viene specificato un nome per l'istanza predefinita quando viene installata. Specificando solo un nome del computer in una stringa di connessione si è connessi all'istanza predefinita nel computer. Tutte le altre istanze nel computer devono essere istanze denominate. Il nome dell'istanza viene specificato durante l'installazione e nelle stringhe di connessione è necessario specificare il nome del computer e il nome dell'istanza.  
  
###  <a name="LimitationsRestrictions"></a> Limitazioni e restrizioni  
 Non è possibile utilizzare il punto (.) per specificare il computer locale negli script di PowerShell. Il punto non è supportato perché viene interpretato da PowerShell come un comando.  
  
 I caratteri parentesi in (local) vengono in genere gestiti da Windows PowerShell come comandi. È necessario codificarli o utilizzare caratteri di escape per l'utilizzo in un percorso o racchiudere il percorso tra doppie virgolette. Per ulteriori informazioni, vedere Codifica e decodifica degli identificatori di SLQ Server.  
  
 Il provider di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] richiede di specificare sempre un nome dell'istanza. Per le istanze predefinite, è necessario specificare un nome dell'istanza DEFAULT.  
  
##  <a name="Examples"></a> Esempi, nomi del computer e dell'istanza  
 In questo esempio viene utilizzato localhost e DEFAULT per specificare l'istanza predefinita nel computer locale.  
  
```  
Set-Location SQLSERVER:\SQL\localhost\DEFAULT   
```  
  
 I caratteri parentesi in (local) vengono in genere gestiti da Windows PowerShell come comandi. È necessario:  
  
-   Racchiudere la stringa del percorso tra virgolette.  
  
    ```  
    Set-Location "SQLSERVER:\SQL\(local)\DEFAULT"  
    ```  
  
-   Utilizzare caratteri di escape per la parentesi utilizzando il carattere apice inverso (`).  
  
    ```  
    Set-Location SQLSERVER:\SQL\`(local`)\DEFAULT  
    ```  
  
-   Codificare le parentesi utilizzando la rappresentazione esadecimale.  
  
    ```  
    Set-Location SQLSERVER:\SQL\%28local%29\DEFAULT  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Identificatori di SQL Server in PowerShell](sql-server-identifiers-in-powershell.md)   
 [Provider PowerShell per SQL Server](sql-server-powershell-provider.md)   
 [SQL Server PowerShell](sql-server-powershell.md)  
  
  

---
title: Caricare dati XML | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- XML data [SQL Server], loading
- loading XML data
ms.assetid: d1741e8d-f44e-49ec-9f14-10208b5468a7
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a5048132c50460475ffe9c04f0f03a75cf6368b7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37166302"
---
# <a name="load-xml-data"></a>Caricamento dati XML
  È possibile trasferire dati XML in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] in diversi modi. Esempio:  
  
-   Se i dati si trovano in una colonna di tipo [n]text o image in un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , è possibile importare la tabella utilizzando [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Modificare il tipo di colonna in XML utilizzando l'istruzione ALTER TABLE.  
  
-   È possibile eseguire una copia bulk dei dati da un altro database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usando bcp out e quindi eseguire un inserimento bulk dei dati nel database di una versione successiva usando bcp in.  
  
-   Se i dati si trovano in colonne relazionali in un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , creare una nuova tabella con una colonna di tipo [n]text e, facoltativamente, una colonna chiave primaria per un identificatore di riga. Uso di programmazione per recuperare il XML generato nel server con FOR XML sul lato client e scriverli nella `[n]text` colonna. Usare quindi le tecniche illustrate in precedenza per trasferire i dati in un database di una versione successiva. È possibile scegliere di scrivere i dati XML direttamente in una colonna XML nel database di una versione successiva.  
  
## <a name="bulk-loading-xml-data"></a>Caricamento bulk di dati XML  
 È possibile eseguire un caricamento bulk dei dati XML nel server utilizzando le funzionalità per il caricamento bulk disponibili in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ad esempio bcp. OPENROWSET consente di caricare dati in una colonna XML da uno o più file, come illustrato nell'esempio seguente.  
  
##### <a name="example-loading-xml-from-files"></a>Esempio: caricamento di dati XML da un file  
 In questo esempio viene illustrato l'inserimento di una riga nella tabella T. Il valore della colonna XML viene caricato dal file C:\MyFile\xmlfile.xml come CLOB e alla colonna di tipo integer viene fornito il valore 10.  
  
```  
INSERT INTO T  
SELECT 10, xCol  
FROM    (SELECT *      
    FROM OPENROWSET (BULK 'C:\MyFile\xmlfile.xml', SINGLE_CLOB)   
 AS xCol) AS R(xCol)  
```  
  
## <a name="text-encoding"></a>Codifica del testo  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] archivia i dati XML in formato Unicode (UTF-16). I dati XML recuperati dal server vengono restituiti con la codifica UTF-16. Se si desidera una codifica diversa, sarà necessario eseguire la conversione appropriata sui dati recuperati. Per i dati XML viene talvolta utilizzata una codifica diversa. In questo caso è necessario prestare particolare attenzione durante il caricamento dei dati. Esempio:  
  
-   Se il testo XML è in formato Unicode (UCS-2, UTF-16), sarà possibile assegnarlo senza problemi a una colonna, una variabile o un parametro XML.  
  
-   Se viene utilizzata una codifica implicita diversa da Unicode, a causa della tabella codici di origine, la tabella codici per le stringhe nel database dovrà essere uguale o compatibile con i punti di codice da caricare. Se necessario, utilizzare COLLATE. Se tale tabella codici non esiste sul server, sarà necessario aggiungere una dichiarazione XML esplicita con la codifica appropriata.  
  
-   Per usare una codifica esplicita, usare il `varbinary()` digitare, che non ha alcuna interazione con le tabelle codici, oppure utilizzare un tipo di stringa della tabella codici appropriata. Assegnare quindi i dati a una colonna, a una variabile o a un parametro XML.  
  
### <a name="example-explicitly-specifying-an-encoding"></a>Esempio: impostazione di una codifica in modo esplicito  
 Si consideri un documento XML di nome vcdoc, archiviato come `varchar(max)` e che non include una dichiarazione XML esplicita. L'istruzione seguente aggiunge una dichiarazione XML con codifica "iso8859-1", concatena il documento XML, viene eseguito il cast del risultato a `varbinary(max)` in modo che la rappresentazione dei byte viene mantenuta e infine esegue il cast in formato XML. Questo consente al processore XML di analizzare i dati in base alla codifica specificata, "iso8859-1", e di generare la rappresentazione UTF-16 corrispondente per i valori stringa.  
  
```  
SELECT CAST(   
CAST (('<?xml version="1.0" encoding="iso8859-1"?>'+ vcdoc) AS VARBINARY (MAX))   
 AS XML)  
```  
  
### <a name="string-encoding-incompatibilities"></a>Stringa che codifica le incompatibilità  
 Se si copia e si incolla XML come un valore letterale stringa nella finestra dell'editor di query di [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], potrebbero verificarsi incompatibilità di codifica delle stringhe [N]VARCHAR, che dipendono dalla codifica dell'istanza XML utilizzata. In molti casi, è possibile rimuovere la dichiarazione XML. Esempio:  
  
```  
<?xml version="1.0" encoding="UTF-8"?>  
  <xsd:schema …  
```  
  
 È quindi consigliabile inserire una N per rendere l'istanza XML un'istanza di Unicode. Esempio:  
  
```  
-- Assign XML instance to a variable.  
DECLARE @X XML  
SET @X = N'…'  
-- Insert XML instance into an xml type column.  
INSERT INTO T VALUES (N'…')  
-- Create an XML schema collection  
CREATE XML SCHEMA COLLECTION XMLCOLL1 AS N'<xsd:schema … '  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Dati XML &#40;SQL Server&#41;](xml-data-sql-server.md)  
  
  

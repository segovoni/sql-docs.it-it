---
title: Specificare i formati di dati per la compatibilità con bcp (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: data-movement
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- bulk exporting [SQL Server], compatibility
- bulk importing [SQL Server], compatibility
- compatibility [SQL Server], data formats
- data formats [SQL Server], compatibility
- bcp utility [SQL Server], compatibility
ms.assetid: cd5fc8c8-eab1-4165-9468-384f31e53f0a
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 42266e1f4ab136045c16d1e0f41d6ae802c3f1c7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37154542"
---
# <a name="specify-data-formats-for-compatibility-when-using-bcp-sql-server"></a>Impostazione dei formati di dati per la compatibilità mediante bcp (SQL Server)
  In questo argomento viene descritto l'attributi del formato dati, prompt specifici di campo e l'archiviazione dei dati di campo per campo in un file in formato non xml di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `bcp` comando. La comprensione di questi concetti può risultare utile per l'esportazione bulk di dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a fini di importazione in un altro programma, ad esempio un altra applicazione di database. I formati di dati predefiniti (native, character o Unicode) nella tabella di origine potrebbero non essere compatibili con il layout di dati previsto dall'altra applicazione. In questo caso, quando si esportano i dati è necessario descriverne il layout.  
  
> [!NOTE]  
>  Se non si ha familiarità con i formati di dati per l'importazione o esportazione di dati, vedere [Formati di dati per l'importazione o l'esportazione bulk &#40;SQL Server&#41;](data-formats-for-bulk-import-or-bulk-export-sql-server.md).  
  
 **Contenuto dell'argomento:**  
  
-   [Attributi del formato dati BCP](#bcpDataFormatAttr)  
  
-   [Panoramica dei prompt specifici di campo](#FieldSpecificPrompts)  
  
-   [L'archiviazione dei dati di campo per campo in un File di formato Non XML](#FieldByFieldNonXmlFF)  
  
-   [Attività correlate](#RelatedTasks)  
  
##  <a name="bcpDataFormatAttr"></a> Attributi di formato e dati di bcp  
 Il comando `bcp` consente di specificare la struttura di tutti i campi di un file di dati mediante i seguenti attributi di formato dati:  
  
-   tipo di archiviazione di file  
  
     Il *tipo di archiviazione di file* indica la modalità con la quale vengono archiviati i dati in un file. Dati possono essere esportati in un file di dati come tipo di tabella di database (formato nativo), nella relativa rappresentazione di caratteri (formato carattere) o come qualsiasi tipo di dati in cui è supportata la conversione implicita; ad esempio, la copia una `smallint` come un `int`. I tipi di dati definiti dall'utente vengono esportati utilizzando il tipo di dati di base corrispondente. Per altre informazioni, vedere [Specifica del tipo di archiviazione di file tramite bcp &#40;SQL Server&#41;](specify-file-storage-type-by-using-bcp-sql-server.md).  
  
-   Lunghezza del prefisso  
  
     Per implementare il tipo di archiviazione più compatto durante l'esportazione bulk dei dati in formato nativo in un file di dati, il comando `bcp` inserisce davanti a ogni campo uno o più caratteri che ne indicano la lunghezza. Tali caratteri sono denominati *caratteri per il prefisso di lunghezza*. Per altre informazioni, vedere [Specificare la lunghezza del prefisso nei file di dati tramite bcp &#40;SQL Server&#41;](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md).  
  
-   Lunghezza del campo  
  
     La lunghezza del campo indica il numero massimo di caratteri necessari per rappresentare i dati in formato carattere. Se i dati sono archiviati in formato nativo, la lunghezza del campo è già nota. Per altre informazioni, vedere [Definizione della lunghezza di campo tramite bcp &#40;SQL Server&#41;](specify-field-length-by-using-bcp-sql-server.md).  
  
-   Carattere di terminazione del campo  
  
     Nei campi dati di tipo carattere, i caratteri di terminazione facoltativi consentono di indicare la fine di ogni campo nel file di dati (tramite un *carattere di terminazione del campo*) e di ogni riga (tramite un *carattere di terminazione della riga*). I caratteri di terminazione indicano ai programmi che leggono il file il punto in cui termina il campo o la riga e inizia il campo o la riga successiva. Per altre informazioni, vedere [Impostazione dei caratteri di terminazione del campo e della riga &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md).  
  
##  <a name="FieldSpecificPrompts"></a> Panoramica dei prompt specifici dei campi  
 Se un oggetto interattivo `bcp` comando contiene il **nelle** o **out** opzione ma non contiene entrambi l'opzione del file di formato (**-f**) o un formato di dati passa ( **- n**, **- c**, **-w**, oppure **-N**), ogni colonna nella tabella di origine o destinazione, il comando richiede per ognuno dei precedenti attributi, a sua volta. In ogni prompt, il `bcp` comando fornisce un valore predefinito in base il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipo di dati della colonna della tabella. Accettare il valore predefinito per tutti i prompt equivale a specificare il formato nativo (**-n**) nella riga di comando. Ogni prompt mostra un valore predefinito fra parentesi: [*predefinito*]. Per accettare i valori predefiniti, premere INVIO. Per specificare un valore diverso da quello predefinito, immettere il valore desiderato al prompt.  
  
### <a name="example"></a>Esempio  
 L'esempio seguente usa il `bcp` comando per eseguire bulk esportare dati dal `HumanResources.myTeam` tabella in modo interattivo al `myTeam.txt` file. Prima di eseguire l'esempio è necessario creare questa tabella. Per informazioni sulla modalità di creazione e sulla tabella, vedere [Tabella di esempio HumanResources.myTeam &#40;SQL Server&#41;](humanresources-myteam-sample-table-sql-server.md).  
  
 Il comando specifica un file di formato né un tipo di dati, causando `bcp` per la richiesta di informazioni sul formato di dati. Al prompt dei comandi di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows digitare:  
  
```  
bcp AdventureWorks.HumanResources.myTeam out myTeam.txt -T  
```  
  
 Per ogni colonna, bcp richiede valori specifici del campo. Nell'esempio seguente vengono illustrati i prompt specifici di campo per le colonne `EmployeeID` e `Name` della tabella e viene suggerito il tipo di archiviazione file predefinito (il formato nativo) per ogni colonna. Le lunghezze del prefisso delle colonne `EmployeeID` e `Name` sono rispettivamente 0 e 2. L'utente specifica una virgola (`,`) come carattere di terminazione di ogni campo.  
  
 `Enter the file storage type of field EmployeeID [smallint]:`  
  
 `Enter prefix-length of field EmployeeID [0]:`  
  
 `Enter field terminator [none]:,`  
  
 `Enter the file storage type of field Name [nvarchar]:`  
  
 `Enter prefix length of field Name [2]:`  
  
 `Enter field terminator [none]:,`  
  
 `.`  
  
 `.`  
  
 `.`  
  
 Per ogni colonna della tabella, in ordine e se necessario, vengono visualizzati prompt equivalenti.  
  
##  <a name="FieldByFieldNonXmlFF"></a> Archiviazione di dati campo per campo in un file di formato non XML  
 Dopo che tutti in cui vengono specificate le colonne della tabella, la `bcp` prompt dei comandi si vuole generare un file di formato non XML che archivia l'appena inserite informazioni campo per campo (vedere l'esempio precedente). Se si sceglie di generare un file di formato, è possibile utilizzarlo ogni volta che si esportano dati da quella tabella o si importano dati di struttura simile in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Il file di formato può essere utilizzato per eseguire l'importazione bulk dal file di dati a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o per eseguire l'esportazione bulk di dati dalla tabella senza dover nuovamente specificare il formato. Per altre informazioni, vedere [File di formato per l'importazione o l'esportazione di dati &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md).  
  
 Nell'esempio seguente viene creato un file di formato non XML denominato `myFormatFile.fmt`:  
  
 `Do you want to save this format information in a file? [Y/n] y`  
  
 `Host filename: [bcp.fmt]myFormatFile.fmt`  
  
 Il nome predefinito per il file di formato è bcp.fmt, ma è possibile specificare un nome diverso.  
  
> [!NOTE]  
>  Per un file di dati che usa un unico formato dati per il tipo di archiviazione, ad esempio il formato carattere o nativo, è possibile creare rapidamente un file di formato senza esportare o importare dati usando l'opzione **format** . Questo approccio ha il vantaggio della semplicità e consente di creare un file di formato XML o non XML. Per altre informazioni, vedere [Creazione di un file di formato &#40;SQL Server&#41;](create-a-format-file-sql-server.md).  
  
##  <a name="RelatedTasks"></a> Attività correlate  
  
-   [Specifica del tipo di archiviazione di file tramite bcp &#40;SQL Server&#41;](specify-file-storage-type-by-using-bcp-sql-server.md)  
  
-   [Specificare la lunghezza del prefisso nei file di dati tramite bcp &#40;SQL Server&#41;](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)  
  
-   [Definizione della lunghezza di campo tramite bcp &#40;SQL Server&#41;](specify-field-length-by-using-bcp-sql-server.md)  
  
-   [Impostazione dei caratteri di terminazione del campo e della riga &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md)  
  
## <a name="related-content"></a>Contenuto correlato  
 nessuna.  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sull'importazione ed esportazione in blocco di dati &#40;SQL Server&#41;](bulk-import-and-export-of-data-sql-server.md)   
 [Formati di dati per l'importazione o l'esportazione bulk &#40;SQL Server&#41;](data-formats-for-bulk-import-or-bulk-export-sql-server.md)   
 [Utilità bcp](../../tools/bcp-utility.md)   
 [Tipi di dati &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)  
  
  

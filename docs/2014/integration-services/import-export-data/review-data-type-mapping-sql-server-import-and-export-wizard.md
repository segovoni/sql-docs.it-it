---
title: Verifica mapping tra i tipi di dati (Importazione/Esportazione guidata SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.reviewissues.f1
ms.assetid: 0625c4f9-b8ff-4593-b884-39398b9d43af
caps.latest.revision: 18
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: cbfaab44f1b7c40a912eec0c6c6cef8a6b00c51f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37158912"
---
# <a name="review-data-type-mapping-sql-server-import-and-export-wizard"></a>Verifica mapping tra i tipi di dati (Importazione/Esportazione guidata SQL Server)
  Usare la **rivedere Data Type Mapping** pagina per esaminare le informazioni dettagliate sulle conversioni di tipi di dati che la procedura guidata deve eseguire per rendere i dati di origine compatibili con la destinazione. Queste informazioni includono segnali visivi per distinguere le conversioni per cui si prevede un esito positivo da quelle che potrebbero provocare errori o troncamenti. Per ogni conversione, è possibile decidere se accettare la conversione suggerita dalla procedura guidata e specificare come gestire gli eventuali errori restituiti.  
  
 Per altre informazioni su questa procedura guidata, vedere [SQL Server importazione / esportazione guidata](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Per altre informazioni sulle opzioni per l'avvio della procedura guidata e sulle autorizzazioni necessarie per eseguire correttamente la procedura guidata, vedere [esecuzione di SQL Server importazione / esportazione guidata](start-the-sql-server-import-and-export-wizard.md).  
  
 Lo scopo del [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] importazione / esportazione guidata consiste nella copia dei dati da un'origine a una destinazione. La procedura guidata può inoltre creare automaticamente un database di destinazione e le tabelle di destinazione. Se tuttavia è necessario copiare più database o tabelle, o altri tipi di oggetti di database, è preferibile utilizzare Copia guidata database. Per altre informazioni, vedere [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="options"></a>Opzioni  
 La pagina **Verifica mapping tra i tipi di dati** è costituita da un elenco **Tabella** , un elenco **Mapping dei tipi di dati** e da opzioni per la gestione degli errori.  
  
### <a name="table-list"></a>Elenco Tabella  
 La parte superiore del **verifica problemi dei tipi Data** pagina è un **tabella** elenco contenente le tabelle da trasferire dall'origine alla destinazione. Nella tabella seguente vengono descritte le colonne presenti nell'elenco.  
  
|colonna|Description|  
|------------|-----------------|  
|Icona di origine dati|Indica la probabilità di esito positivo per le conversioni dei tipi di dati:<br /><br /> Un'icona raffigurante un segno di spunta verde indica che la procedura guidata prevede l'esito positivo per tutte le conversioni dei tipi di dati per la tabella.<br /><br /> Un'icona di avviso gialla indica che è consigliabile verificare le singole conversioni eseguite dalla procedura guidata. Per verificare tali conversioni, selezionare la tabella, quindi controllare le conversioni per singole colonne nell'elenco **Mapping dei tipi di dati** .<br /><br /> Un'icona di errore rossa indica che la procedura guidata non è in grado di eseguire in modo affidabile alcune delle conversioni per la tabella.|  
|**Origine**|Visualizza il nome della tabella di origine.|  
|Icona di destinazione|Indica se la destinazione è già presente o se verrà creata dalla procedura guidata:<br /><br /> Un'icona di tabella indica che la destinazione è costituita da una tabella esistente.<br /><br /> Un'icona di tabella con un riflesso di luce indica che la destinazione è costituita da una nuova tabella che verrà creata dalla procedura guidata.|  
|**Destinazione**|Visualizza il nome della tabella di destinazione.|  
  
 Per visualizzare informazioni di conversione su una singola tabella, selezionare una tabella in questo **tabella** griglia. Le informazioni sulla conversione per la tabella selezionata verranno visualizzate nelle colonne della griglia **Mapping dei tipi di dati** nella parte inferiore della pagina.  
  
### <a name="data-type-mapping-list"></a>Elenco Mapping dei tipi di dati  
 La parte inferiore del **verifica problemi dei tipi Data** pagina è la **mapping dei tipi di dati** elenco. Questa griglia fornisce informazioni dettagliate sulla conversione per le colonne della tabella selezionata nell'elenco **Tabella** . Nella tabella seguente vengono descritte le colonne presenti nell'elenco.  
  
|colonna|Description|  
|------------|-----------------|  
|Icona di conversione|Indica la probabilità di esito positivo per le conversioni dei tipi di dati:<br /><br /> Un'icona raffigurante un segno di spunta verde indica che la procedura guidata prevede l'esito positivo della conversione del tipo di dati per la colonna specifica.<br /><br /> Un'icona di avviso gialla indica che è consigliabile verificare la conversione eseguita dalla procedura guidata. Per verificare la conversione, fare doppio clic sulla colonna per visualizzare la finestra di dialogo **Dettagli conversione colonna** .<br /><br /> Un'icona di errore rossa indica che la procedura guidata non è in grado di eseguire in modo affidabile la conversione.|  
|**Colonna di origine**|Visualizza il nome della colonna di origine.|  
|**Tipo origine**|Visualizza il tipo di dati della colonna di origine.|  
|**Colonna di destinazione**|Visualizza il nome della colonna di destinazione.|  
|**Tipo destinazione**|Visualizza il tipo di dati della colonna di destinazione.|  
|**Converti**|Consente di specificare se la conversione pianificata deve continuare:<br /><br /> Selezionare la casella di controllo per fare in modo che la procedura guidata prosegua con la conversione pianificata.<br /><br /> Deselezionare la casella di controllo per annullare la conversione del tipo di dati.|  
|**In caso di errore**|Consente di specificare la modalità di gestione degli errori utilizzata dalla procedura guidata:<br /><br /> Usare la **in caso di errore (globale)** impostazione.<br /><br /> Generare un errore e arrestare il processo di importazione o esportazione.<br /><br /> Ignorare l'errore.|  
|**In caso di troncamento**|Consente di specificare la modalità di gestione del troncamento utilizzata dalla procedura guidata:<br /><br /> Usare la **in caso di troncamento (globale)** impostazione.<br /><br /> Generare un errore e arrestare il processo di importazione o esportazione.<br /><br /> Ignorare il troncamento.|  
  
 Per visualizzare informazioni dettagliate sulla conversione di una determinata colonna di dati, fare doppio clic su qualsiasi riga nell'elenco. Verrà visualizzata la finestra di dialogo **Dettagli conversione colonna** , che contiene informazioni più dettagliate sulla conversione per la colonna.  
  
### <a name="error-handling-options"></a>Opzioni di gestione degli errori  
 **In caso di errore (globale)**  
 Consente di specificare la modalità di gestione degli errori utilizzata dalla procedura guidata:  
  
-   Generare un errore e arrestare il processo di importazione o esportazione.  
  
-   Ignorare l'errore e continuare il processo di importazione o esportazione.  
  
 Questa impostazione si applica a tutte le conversioni per cui nella colonna **In caso di errore** dell'elenco **Mapping dei tipi di dati** è selezionata l'opzione **Usa valore globale** .  
  
 **In caso di troncamento (globale)**  
 Consente di specificare la modalità di gestione del troncamento utilizzata dalla procedura guidata:  
  
-   Generare un errore e arrestare il processo di importazione o esportazione.  
  
-   Ignorare il troncamento e continuare il processo di importazione o esportazione.  
  
 Questa impostazione si applica a tutte le conversioni per cui nella colonna **In caso di troncamento** dell'elenco **Mapping dei tipi di dati** è selezionata l'opzione **Usa valore globale** .  
  
  

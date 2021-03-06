---
title: Aggiornamento di un'applicazione da SQL Server 2005 Native Client | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client, updating applications
ms.assetid: 1e1e570c-7f14-4e16-beab-c328e3fbdaa8
caps.latest.revision: 42
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: cf7be28b850e7b10f209c6d6194450d3ab8aecaf
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37426850"
---
# <a name="updating-an-application-from-sql-server-2005-native-client"></a>Aggiornamento di un'applicazione da SQL Server 2005 Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  In questo argomento vengono descritte le modifiche di rilievo introdotte in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client rispetto a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
 Quando si esegue l'aggiornamento da Microsoft Data Access Components (MDAC) a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, si potrebbero anche notare alcune differenze di comportamento. Per altre informazioni, vedere [l'aggiornamento di un'applicazione da MDAC a SQL Server Native Client](../../../relational-databases/native-client/applications/updating-an-application-to-sql-server-native-client-from-mdac.md).  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 9.0 forniti con [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 forniti con [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)].  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.5 fornito con [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)]. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 fornito con [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] e [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)].  
  
|Differenze di comportamento in SQL Server Native Client nelle versione successive a [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]|Description|  
|------------------------------------------------------------------------------------|-----------------|  
|In OLE DB viene applicato il riempimento solo in base alla scala definita.|Per le conversioni in cui i dati convertiti vengono inviati al server, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (a partire da [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]) zeri finali nei dati solo fino alla lunghezza massima dei riquadri **datetime** valori. In SQL Server Native Client 9.0 viene applicato un riempimento fino a un massimo di 9 cifre.|  
|Convalida di DBTYPE_DBTIMESTAMP per ICommandWithParameter::SetParameterInfo.|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (a partire [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]) implementa il requisito OLE DB per *bScale* in ICommandWithParameter::SetParameterInfo da impostare per la precisione secondi frazionari per DBTYPE_DBTIMESTAMP.|  
|Il **sp_columns** stored procedure restituisce ora **"NO"** anziché **"NO"** per la colonna IS_NULLABLE.|A partire [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 ([!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]), **sp_columns** stored procedure restituisce ora **"NO"** anziché **"NO"** per una colonna IS_NULLABLE .|  
|SQLBindCol, SQLBindParameter e SQLSetDescRec ora eseguire la verifica coerenza.|Nelle versioni precedenti a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0, impostazione di SQL_DESC_DATA_PTR non produceva una verifica coerenza per qualsiasi tipo di descrittore in SQLBindCol, SQLBindParameter o SQLSetDescRec.|  
|SQLCopyDesc ora esegue la verifica di coerenza del descrittore.|Nelle versioni precedenti a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0, SQLCopyDesc non eseguiva un controllo di consistenza quando il campo SQL_DESC_DATA_PTR veniva impostato su un determinato record.|  
|SQLGetDescRec non è più una descrittore verifica coerenza.|Nelle versioni precedenti a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0, SQLGetDescRec eseguita una verifica coerenza descrittore quando il campo SQL_DESC_DATA_PTR veniva impostato. Tale controllo non è richiesto dalla specifica ODBC e in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 ([!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]) e versioni successive non viene più eseguito.|  
|Quando la data non è inclusa nell'intervallo consentito viene restituito un errore differente.|Per il **data/ora** tipo, verrà restituito un numero di errore diverso dalla [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (a partire da [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]) per un out-of-range data rispetto a quello restituito nelle versioni precedenti.<br /><br /> In particolare [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 9.0 restituiva il numero 22007 per tutti i valori fuori intervallo anno nelle conversioni di stringa per **datetime**, e [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] a partire dalla versione 10.0 Native Client ([!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]) restituisce 22008 quando la data è compresa nell'intervallo supportato dal **datetime2** ma esterna all'intervallo supportato dal **datetime** oppure **smalldatetime**.|  
|**Data/ora** valore tronca i secondi frazionari e non arrotondato se arrotondamento cambierà il giorno.|Nelle versioni precedenti a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0, il comportamento del client per **datetime** valori inviati al server è arrotonda i 1 più vicino/300th di secondo. A partire da [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0, in questo scenario si verifica il troncamento dei secondi frazionari se l'arrotondamento comporta la modifica del giorno.|  
|Possibile troncamento di secondi per **datetime** valore.|In un'applicazione compilata con [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] Native Client (o versioni successive) che si connette a un server [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2005 vengono troncati i secondi e i secondi frazionari per la porzione di tempo dei dati inviati al server se si esegue l'associazione a una colonna datetime con un identificatore di tipo DBTYPE_DBTIMESTAMP (OLE DB) o SQL_TIMESTAMP (ODBC) e una scala di 0.<br /><br /> Esempio:<br /><br /> Dati di input: 1994-08-21 21:21:36.000<br /><br /> Dati inseriti: 1994-08-21 21:21:00.000|  
|La conversione dei dati OLE DB da DBTYPE_DBTIME a DBTYPE_DATE non può più causare la modifica del giorno.|Nelle versioni precedenti a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0, se la parte relativa all'ora di un tipo DBTYPE_DATE è entro mezzo secondo dalla mezzanotte, il codice di conversione OLE DB causa la modifica del giorno. A partire da [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0, il giorno non viene modificato (i secondi frazionari vengono troncati ma non vengono arrotondati).|  
|Modifiche relative alle conversioni IBCPSession::BCColFmt.|A partire da [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0, quando si usa IBCPSession::BCOColFmt per convertire SQLDATETIME o SQLDATETIME in un tipo stringa, un valore frazionario viene esportato. Quando ad esempio si converte il tipo SQLDATETIME nel tipo SQLNVARCHARMAX, le versioni precedenti di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client restituiscono<br /><br /> 1989-02-01 00:00:00. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 e versioni successive restituiscono 1989-02-01 00:00:00.0000000.|  
|Le dimensioni dei dati inviati devono corrispondere alla lunghezza specificata in SQL_LEN_DATA_AT_EXEC.|Quando si utilizza SQL_LEN_DATA_AT_EXEC, le dimensioni dei dati devono corrispondere alla lunghezza specificata con SQL_LEN_DATA_AT_EXEC. È possibile utilizzare SQL_DATA_AT_EXEC ma l'utilizzo di SQL_LEN_DATA_AT_EXEC comporta vantaggi potenziali in termini di prestazioni.|  
|Le applicazioni personalizzate che utilizzano l'API BCP ora possono visualizzare un avviso.|L'API BCP genererà un messaggio di avviso se la lunghezza dei dati di tutti i tipi è superiore a quella specificata per un campo. In precedenza, questo avviso veniva visualizzato solo per i dati di tipo carattere e non per tutti i tipi.|  
|Inserimento di una stringa vuota in un **sql_variant** associato come tipo Data/ora viene generato un errore.|Nelle [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 9.0 l'inserimento di una stringa vuota in un **sql_variant** associato come tipo Data/ora non è stato generato un errore. In questa situazione in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 e versioni successive viene correttamente generato un errore.|  
|Convalida dei parametri SQL_C_TYPE _TIMESTAMP e DBTYPE_DBTIMESTAMP più restrittiva.|Nelle versioni precedenti a [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] Native Client, **datetime** venivano arrotondati i valori in base alla scala delle **datetime** e **smalldatetime** colonne da [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] Native Client (e versioni successive) applica le regole di convalida più restrittive definite nella specifica ODBC per i secondi frazionari. Se non è possibile convertire il valore di un parametro nel tipo SQL utilizzando la scala specificata o implicita dell'associazione client senza causare il troncamento delle cifre finali, viene restituito un errore.|  
|Quando è in esecuzione un trigger, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] potrebbe restituire risultati diversi.|Modifiche introdotte in [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] potrebbe provocare un'applicazione per restituire un'istruzione che ha causato un trigger da eseguire al risultati diversi **NOCOUNT OFF** attivo. In una situazione di questo tipo l'applicazione potrebbe generare un errore. Per risolvere questo problema, impostare **NOCOUNT ON** nel trigger o chiamare SQLMoreResults per passare al risultato successivo.|  
  
## <a name="see-also"></a>Vedere anche  
 [Programmazione in SQL Server Native Client](../../../relational-databases/native-client/sql-server-native-client-programming.md)  
  
  

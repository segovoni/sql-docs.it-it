---
title: Configurare le impostazioni per Data Migration Assistant (SQL Server) | Microsoft Docs
description: Informazioni su come configurare le impostazioni per Data Migration Assistant aggiornando i valori nel file di configurazione
ms.custom: ''
ms.date: 08/31/2017
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.suite: sql
ms.technology: dma
ms.tgt_pltfrm: ''
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Assess
ms.assetid: ''
caps.latest.revision: ''
author: HJToland3
ms.author: jtoland
manager: craigg
ms.openlocfilehash: a8ab80d5e83ef5f7650f87f8c4618466eb3dee74
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/04/2018
ms.locfileid: "37783992"
---
# <a name="configure-settings-for-data-migration-assistant"></a>Configurare le impostazioni per Data Migration Assistant

È possibile ottimizzare determinati comportamenti di Data Migration Assistant impostando i valori di configurazione nel file dma.exe.config. Questo articolo descrive i valori di configurazione della chiave.

È possibile trovare il file dma.exe.config per l'applicazione desktop Data Migration Assistant e l'utilità della riga di comando, nelle cartelle seguenti nel computer.

- Applicazione desktop

  % ProgramFiles %\\Microsoft Data Migration Assistant\\dma.exe.config

- Utilità della riga di comando

  % ProgramFiles %\\Microsoft Data Migration Assistant\\dmacmd.exe.config 

Assicurarsi di salvare una copia del file di configurazione originale prima di apportare alcuna modifica. Dopo aver apportato modifiche, riavviare Data Migration Assistant per i nuovi valori di configurazione per rendere effettive.

## <a name="number-of-databases-to-assess-in-parallel"></a>Numero di database per valutare in parallelo

Data Migration Assistant valuta più database in parallelo. Durante la valutazione Data Migration Assistant estrae dell'applicazione livello dati (dacpac) per comprendere lo schema del database. Questa operazione possibile timeout se valutati in parallelo in più database nello stesso server. 

A partire da v2.0 Data Migration Assistant, è possibile controllo questo impostando parallelDatabases il valore di configurazione. Valore predefinito è 8.

```
<advisorGroup>

<workflowSettings>

<assessment parallelDatabases="8" />

</workflowSettings>

</advisorGroup>
```




## <a name="number-of-databases-to-migrate-in-parallel"></a>Numero di database per eseguire la migrazione in parallelo

Data Migration Assistant esegue la migrazione di più database in parallelo, in precedenza la migrazione di account di accesso. Durante la migrazione, Data Migration Assistant verrà eseguire un backup del database di origine, se lo si desidera copiare il backup e quindi ripristinarlo nel server di destinazione. È possibile riscontrare gli errori di timeout quando sono selezionati più database per la migrazione. 

A partire dalla versione 2.0 Data Migration Assistant, se si verifica questo problema è possibile ridurre il valore di configurazione parallelDatabases. È possibile aumentare il valore per ridurre il tempo complessivo della migrazione.

```
<advisorGroup>

<workflowSettings>

<migration parallelDatabases=”8″ />

</workflowSettings>

</advisorGroup>
```


## <a name="dacfx-settings"></a>Impostazioni di DacFX

Durante la valutazione, Data Migration Assistant estrae dell'applicazione livello dati (dacpac) per comprendere lo schema del database. Questa operazione può non riuscire con i timeout per database molto grandi, o se il server è in condizioni di carico. Iniziare con la versione 1.0 di migrazione dei dati, è possibile modificare i valori di configurazione seguente per evitare errori. 

> [!NOTE]
> L'intera &lt;dacfx&gt; voce è impostata come commento per impostazione predefinita. Rimuovere i commenti e quindi modificare il valore in base alle esigenze.

- commandTimeout

   Questo imposta la proprietà IDbCommand.CommandTimeout *secondi*. (Predefinito = 60)

- databaseLockTimeout

   Ciò equivale a [blocco impostato\_TIMEOUT timeout\_periodo ](../t-sql/statements/set-lock-timeout-transact-sql.md) nelle *millisecondi*. (Predefinito = 5000)

- maxDataReaderDegreeOfParallelism

   Numero di connessioni di pool di connessione SQL da usare. (Predefinito = 8)

```
<advisorGroup>

<advisorSettings>

<dacFx  commandTimeout="60" databaseLockTimeout="5000"
maxDataReaderDegreeOfParallelism="8"/>

</advisorSettings>

</advisorGroup>
```


## <a name="stretch-database-recommendation-threshold"></a>Stretch Database: Soglia di raccomandazione

Con [SQL Server Stretch Database](https://docs.microsoft.com/sql/sql-server/stretch-database/stretch-database), puoi estendere dinamicamente dati usati raramente sia transazionali da Microsoft SQL Server 2016 in Azure. Stretch Database per i database transazionali con grandi quantità di dati ad accesso sporadico. L'indicazione di Stretch Database, nella raccomandazione per funzionalità di archiviazione, identifica innanzitutto le tabelle che ritiene che trarranno vantaggio da questa funzionalità, e quindi identifica le modifiche da apportare per abilitare la tabella per questa funzionalità.

A partire da v2.0 Data Migration Assistant, è possibile controllare questa soglia per una tabella per qualificarsi per la funzionalità di Stretch Database usando il valore di configurazione recommendedNumberOfRows. Valore predefinito è 100.000 righe. Se si desidera analizzare le funzionalità di estensione per le tabelle di dimensioni ancora inferiori, diminuire il valore di conseguenza.

```
<advisorGroup>

<advisorSettings>

<stretchDBAdvisor  recommendedNumberOfRows="100000" />

</advisorSettings>

</advisorGroup>
```


## <a name="sql-connection-timeout"></a>Timeout della connessione SQL

È possibile controllare la [timeout della connessione SQL](https://msdn.microsoft.com/library/system.data.sqlclient.sqlconnection.connectiontimeout(v=vs.110).aspx) per le istanze di origine e destinazione durante l'esecuzione di una valutazione o la migrazione, impostando il valore di timeout di connessione a un numero di secondi specificato. Il valore predefinito è 15 secondi.

```
<appSettings>

<add key="ConnectionTimeout" value="15" />

</appSettings>
```


## <a name="see-also"></a>Vedere anche

[Download di Assistente per la migrazione dei dati](https://www.microsoft.com/download/details.aspx?id=53595)

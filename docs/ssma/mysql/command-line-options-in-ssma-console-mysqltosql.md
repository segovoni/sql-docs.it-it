---
title: Opzioni della riga di comando nella Console SSMA (MySQLToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Command line options, help option
- Command line options, log file option
- Command line options, project environment folder option
- Command line options, script file option
- Command line options, secure password option
- Command line options, SecurePassword help option
- Command line options, server connection file option
- Command line options, variable value file option
- Command line options, XML output option
ms.assetid: a2310b10-68ad-4285-a08b-c8694cf84416
caps.latest.revision: 12
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 83e8fddb94f2c2cdc51131417b589d7c8691a88d
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/12/2018
ms.locfileid: "38985593"
---
# <a name="command-line-options-in-ssma-console-mysqltosql"></a>Opzioni della riga di comando nella Console SSMA (MySQLToSQL)
Microsoft offre un solido set opzioni riga di comando per eseguire e controllare le attività SSMA. Le sezioni che seguono in modo dettagliato lo stesso.  
  
## <a name="command-line-options-in-ssma-console"></a>Opzioni della riga di comando nella Console SSMA  
È qui descritti la console di opzioni del comando.  
  
Ai fini di questa sezione, il termine 'option' è detta anche 'switch'.  
  
Opzioni non sono tra maiuscole e minuscole e può iniziare con '**-**'or,'**/**' caratteri.  
  
Se si specificano opzioni, diventa obbligatorio specificare i parametri di opzione corrispondenti.  
  
I parametri di opzione devono essere separati dal carattere opzione da spazi vuoti.  
  
**Esempi di sintassi:**  
  
`C:\> SSMAforMySQLConsole.EXE -s scriptfile`  
  
`C:\> SSMAforMySQLConsole.EXE -s “C:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\AssessmentReportGenerationSample.xml” –v “C:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\VariableValueFileSample.xml” –c “C:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\ServersConnectionFileSample.xml”`  
  
Devono specificare i nomi di cartella o file contenenti spazi tra virgolette doppie.  
  
L'output di voci di riga di comando e i messaggi di errore vengono archiviati in STDOUT o in un file specificato.  
  
### <a name="script-file-option-sscript"></a>Opzione del File script: – s o script  
Un parametro obbligatorio, il percorso/nome del file script specifica lo script di sequenze di comandi deve essere eseguito da SSMA.  
  
**Esempi di sintassi:**  
  
`C:\>SSMAforMySQLConsole.EXE –s “C:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\ConversionAndDataMigrationSample.xml”`  
  
### <a name="variable-value-file-option-vvariable"></a>Opzione File valore variabile: variabile o – v  
Questo file è costituito da variabili utilizzate nel file di script. Si tratta di un'opzione facoltativa. Se le variabili non dichiarate nel file delle variabili e usate nel file di script, l'applicazione genera un errore e termina l'esecuzione della console.  
  
**Esempi di sintassi:**  
  
Variabili definite in più file di valore della variabile, ad esempio uno con un valore predefinito e l'altra con un valore specifico dell'istanza quando applicabile. L'ultimo file di variabile specificato negli argomenti della riga di comando consideri le preferenze, nel caso in cui è presente una duplicazione delle variabili:  
  
`C:\>SSMAforMySQLConsole.EXE -s`  
  
`“C:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\ConversionAndDataMigrationSample.xml” –v c:\migration`  
  
`projects\global_variablevaluefile.xml –v “c:\migrationprojects\instance_variablevaluefile.xml”`  
  
### <a name="server-connection-file-option-cserverconnection"></a>Opzione di File di connessione server: c: / serverconnection  
Questo file contiene informazioni di connessione server per ogni server. Ogni definizione del server è identificato da un ID Server univoco. Gli ID Server viene fatto riferimento nel file di script per connessione correlati ai comandi.  
  
Definizione di server può essere una parte del file di connessione di server e/o file di script. Id del server nel file di script ha la precedenza sul file di connessione del server, nel caso in cui è presente una duplicazione dell'id del server.  
  
**Esempi di sintassi:**  
  
Gli ID del server vengono usati nel file di script e vengono definite in un file di connessione server separato, file di connessione server usa le variabili definite nel file di valore della variabile:  
  
`C:\>SSMAforMySQLConsole.EXE –s “C:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\ConversionAndDataMigrationSample.xml”  –v`  
  
`c:\SsmaProjects\myvaluefile1.xml –c`  
  
`c:\SsmaProjects\myserverconnectionsfile1.xml`  
  
Definizione del server è incorporato nel file di script:  
  
`C:\>SSMAforMySQLConsole.EXE –s “C:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\ConversionAndDataMigrationSample.xml”`  
  
### <a name="xml-output-option--xxmloutput-xmloutputfile"></a>Opzione di Output XML: - x / xmloutput [xmloutputfile]  
Questo comando viene utilizzato per l'output i messaggi di output del comando in formato xml alla console o in un file xml.  
  
Sono disponibili due opzioni per xmloutput, una visualizzazione dei..,:  
  
-   Se il percorso file non viene fornito dopo il cambio di xmloutput l'output viene reindirizzato al file.  
  
    **Esempio di sintassi:**  
  
    `C:\>SSMAforMySQLConsole.EXE –s`  
  
    `“C:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\ConversionAndDataMigrationSample.xml”  –x d:\xmloutput\project1output.xml`  
  
-   Se non viene specificato alcun percorso di file dopo il cambio di xmloutput il xmlout viene visualizzato nella console di se stesso.  
  
    **Esempio di sintassi:**  
  
    `C:\>SSMAforMySQLConsole.EXE –s “C:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\ConversionAndDataMigrationSample.xml”  –xmloutput`  
  
### <a name="log-file-option-llog"></a>Opzione del File di log: – l/log  
Tutte le operazioni di SSMA nell'applicazione Console ottengano registrate in un file di log. Si tratta di un'opzione facoltativa. Se un file di log e il relativo percorso vengono specificati nella riga di comando, viene generato il log nel percorso specificato. In caso contrario, viene generato nella posizione predefinita.  
  
**Esempio di sintassi:**  
  
`C:\>SSMAforMySQLConsole.EXE`  
  
`“C:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\ConversionAndDataMigrationSample.xml”  –l c:\SsmaProjects\migration1.log`  
  
### <a name="project-environment-folder-option-eprojectenvironment"></a>Opzione di cartella di progetto ambiente:. e – / projectenvironment  
Ciò indica la cartella Impostazioni ambiente di progetto SSMA corrente. Questa opzione è facoltativa.  
  
**Esempio di sintassi:**  
  
`C:\>SSMAforMySQLConsole.EXE –s`  
  
`“C:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\ConversionAndDataMigrationSample.xml”  –e c:\SsmaProjects\CommonEnvironment`  
  
### <a name="secure-password-option-psecurepassword"></a>Opzione Password sicura: – p/securepassword  
Questa opzione indica la password crittografata per le connessioni al server. Differisce da tutte le altre opzioni: l'opzione non viene eseguito qualsiasi script né consente in qualsiasi attività relative alla migrazione, ma consente di gestire la crittografia della password per le connessioni del server usato nel progetto di migrazione.  
  
È possibile immettere qualsiasi altra opzione o la password come parametro della riga di comando. In caso contrario, viene generato un errore. Per altre informazioni, vedere la [la gestione delle password](http://msdn.microsoft.com/4ffbc587-ea3f-49ad-bc42-a654f672325e) sezione.  
  
Le seguenti opzioni secondarie sono supportate per `–p/securepassword`:  
  
-   Per aggiungere password protette archiviazione per un ID del Server specificato o per tutti gli ID del Server definito nel file di connessione del server. -L'opzione di sovrascrittura, di seguito, gli aggiornamenti della password se esiste già:  
  
    `-p|-securepassword -a|add    {"<server_id>[, .n]"|all}` `-c|-serverconnection <server-connection-file> [-v|variable <variable-value-file>]``[-o|overwrite]`  
  
    `-p|-securepassword -a|add    {"<server_id>[, .n]"|all}``-s|-script <server-connection-file> [-v|variable <variable-value-file>] [-o|overwrite]`  
  
-   Per rimuovere la password crittografata dalla risorsa di archiviazione protetta dell'ID del Server specificato o per tutti gli ID del Server:  
  
    `–p/securepassword –r/remove {<server_id> [, …n] | all}`  
  
-   Per visualizzare un elenco di ID Server per cui la password viene crittografata:  
  
    `–p/securepassword –l/list`  
  
-   Per esportare le password archiviate in un archivio protetto a un file crittografato. Questo file è crittografato con la frase di pass specificato dall'utente.  
  
    `–p/securepassword –e/export {<server-id> [, …n] | all} <encrypted-password -file>`  
  
-   Crittografati-che è stato esportato in precedenza viene importato il file nell'archivio locale protetto utilizzando specificato dall'utente-passphrase. Una volta che il file viene decrittografato, questo viene archiviato in un nuovo file, che a sua volta, viene crittografato nel computer locale.  
  
    `–p/securepassword –i/import {<server-id> [, …n] | all} <encrypted-password -file>`  
  
    È possibile specificare più ID Server usando i separatori virgola.  
  
### <a name="help-option-help"></a>Opzione della Guida::? / della Guida  
Visualizza il riepilogo di sintassi delle opzioni della Console SSMA:  
  
`C:\>SSMAforMySQLConsole.EXE -?`  
  
Per una visualizzazione tabulare di opzioni della riga di comando di Console SSMA, consultare [appendice - 1 &#40;MySQLToSQL&#41;](../../ssma/mysql/appendix-1-mysqltosql.md).  
  
### <a name="securepassword-help-option-securepassword--help"></a>Opzione SecurePassword Help: – securepassword-? /Help  
Visualizza il riepilogo di sintassi delle opzioni della Console SSMA:  
  
`C:\>SSMAforMySQLConsole.EXE -securepassword -?`  
  
Per una visualizzazione tabulare di opzioni della riga di comando di Console SSMA, consultare [appendice - 1 &#40;MySQLToSQL&#41;](../../ssma/mysql/appendix-1-mysqltosql.md)  
  
### <a name="next-step"></a>Passaggio successivo  
Il passaggio successivo dipende dai requisiti progetto:  
  
-   Per specificare una password o l'esportazione / importazione per le password, vedere [la gestione delle password &#40;MySQLToSQL&#41;](../../ssma/mysql/managing-passwords-mysqltosql.md).  
  
-   Per la generazione di report, vedere [generazione di report &#40;MySQLToSQL&#41;](../../ssma/mysql/generating-reports-mysqltosql.md).  
  
-   Per risolvere i problemi nella console, vedere [Troubleshooting &#40;MySQLToSQL&#41;](../../ssma/mysql/troubleshooting-mysqltosql.md).  
  

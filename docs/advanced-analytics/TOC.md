# Panoramica

## [Che cos'è SQL Machine Learning Services](what-is-sql-server-machine-learning.md)
### [Analisi nel database](r/sql-server-r-services.md)
### [Server autonomo](r/r-server-standalone.md)
## [Nuove funzionalità](what-s-new-in-sql-server-machine-learning-services.md)
## [Funzionalità in base all'edizione](r/differences-in-r-features-between-editions-of-sql-server.md)

# [Architettura](architecture-overview-machine-learning.md)
## [R](r/architecture-overview-sql-server-r.md)
### [Interoperabilità di R](r/r-interoperability-in-sql-server.md)
### [Componenti che supportano l'integrazione di R](r/new-components-in-sql-server-to-support-r.md)
### [Sicurezza per R](r/security-overview-sql-server-r.md)
## [Python](python/architecture-overview-sql-server-python.md)
### [Python in Machine Learning Services](python/sql-server-python-services.md)
### [Interoperabilità di Python](python/python-interoperability.md)
### [Componenti per il supporto di Python](python/new-components-in-sql-server-to-support-python-integration.md)
### [Sicurezza di Python](python/security-overview-sql-server-python-services.md)
<!-- ### [How To Create a Resource Pool for Python](python/how-to-create-a-resource-pool-for-python.md)-->
<!-- ### [Extended Events for Python](python/extended-events-for-python.md)-->
<!-- ### [DMVs for Python](python/dmvs-for-python.md)-->
<!-- ### [Resource Governance for Python](python/resource-governance-for-python.md)-->

# Install 

## SQL Server 2017
### [Analisi nel database](install/sql-machine-learning-services-windows-install.md)
### [Server autonomo](install/sql-machine-learning-standalone-windows-install.md)
## SQL Server 2016
### [R Services (In-Database)](install/sql-r-services-windows-install.md)
### [R Server (Standalone)](install/sql-r-standalone-windows-install.md)
## [Modelli con training preliminare](r/install-pretrained-models-sql-server.md)
## [Installazione dal prompt dei comandi](install/sql-ml-component-commandline-install.md)
## [Installazione offline (senza Internet)](install/sql-ml-component-install-without-internet-access.md)
## [Aggiornare R e Python](r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)
## [Configurare gli strumenti R](r/set-up-a-data-science-client.md)
## [Configurare gli strumenti Python](python/setup-python-client-tools-sql.md)

# Guide introduttive

## R
### [Hello World in R e SQL](tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
### [Gestire input e output](tutorials/rtsql-working-with-inputs-and-outputs.md)
### [Gestire i tipi di dati e gli oggetti](tutorials/rtsql-r-and-sql-data-types-and-data-objects.md)
### [Creare un modello predittivo](tutorials/rtsql-create-a-predictive-model-r.md)
### [Eseguire la stima e il tracciato da un modello](tutorials/rtsql-predict-and-plot-from-model.md)

# [Esercitazioni](tutorials/machine-learning-services-tutorials.md)
## [R](tutorials/sql-server-r-tutorials.md)
### [Informazioni sull'analisi nel database](tutorials/sqldev-in-database-r-for-sql-developers.md)
#### [1 - Ottenere dati e script](tutorials/sqldev-download-the-sample-data.md)
#### [2 - Configurare l'ambiente](r/sqldev-import-data-to-sql-server-using-powershell.md)
#### [3 - Visualizzare i dati](tutorials/sqldev-explore-and-visualize-the-data.md)
#### [4 - Creare funzionalità di dati](tutorials/sqldev-create-data-features-using-t-sql.md)
#### [5 - Eseguire il training e salvare in SQL](r/sqldev-train-and-save-a-model-using-t-sql.md)
#### [6 - Stimare i risultati](tutorials/sqldev-operationalize-the-model.md)

### [Procedura dettagliata end-to-end di data science](tutorials/walkthrough-data-science-end-to-end-walkthrough.md)
#### [Preparare i dati](tutorials/walkthrough-prepare-the-data.md)
#### [Esplorare i dati usando SQL](tutorials/walkthrough-view-and-explore-the-data.md)
#### [Riepilogare i dati usando R](tutorials/walkthrough-view-and-summarize-data-using-r.md)
#### [Creare grafici e tracciati](tutorials/walkthrough-create-graphs-and-plots-using-r.md)
#### [Creare funzionalità di dati](tutorials/walkthrough-create-data-features.md)
#### [Creare e salvare il modello](tutorials/walkthrough-build-and-save-the-model.md)
#### [Distribuire e usare il modello](tutorials/walkthrough-deploy-and-use-the-model.md)

### [Approfondimento con RevoScaleR](tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)
#### [Creare il database e le autorizzazioni](tutorials/deepdive-work-with-sql-server-data-using-r.md)
#### [Creare oggetti dati usando RxSqlServerData](tutorials/deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md)
#### [Eseguire query e modificare i dati](tutorials/deepdive-query-and-modify-the-sql-server-data.md)
#### [Definire un contesto di calcolo](tutorials/deepdive-define-and-use-compute-contexts.md)
#### [Creare ed eseguire script R](tutorials/deepdive-create-and-run-r-scripts.md)
#### [Visualizzare i dati](tutorials/deepdive-visualize-sql-server-data-using-r.md)
#### [Creare modelli](tutorials/deepdive-create-models.md)
#### [Valutare i nuovi dati](tutorials/deepdive-score-new-data.md)
#### [Trasformare i dati](tutorials/deepdive-transform-data-using-r.md)
#### [Caricare i dati in memoria mediante rxImport](tutorials/deepdive-load-data-into-memory-using-rximport.md)
#### [Creare una tabella usando rxDataStep](tutorials/deepdive-create-new-sql-server-table-using-rxdatastep.md)
#### [Eseguire un'analisi in blocchi tramite rxDataStep](tutorials/deepdive-perform-chunking-analysis-using-rxdatastep.md)
#### [Analizzare i dati in un contesto di calcolo locale](tutorials/deepdive-analyze-data-in-local-compute-context.md)
#### [Spostare i dati tra SQL Server e file XDF](tutorials/deepdive-move-data-between-sql-server-and-xdf-file.md)
#### [Creare una simulazione semplice](tutorials/deepdive-create-a-simple-simulation.md)

## [Python](tutorials/sql-server-python-tutorials.md)
### [Eseguire Python con T-SQL](tutorials/run-python-using-t-sql.md)
#### [Eseguire il wrapping di Python in una stored procedure](tutorials/wrap-python-in-tsql-stored-procedure.md)
#### [Eseguire il training e assegnare un punteggio da un modello di Python in SQL Server](tutorials/train-score-using-python-in-tsql.md)
#### [Creare un modello con revoscalepy in un contesto di calcolo di SQL Server](tutorials/use-python-revoscalepy-to-create-model.md)
### [Informazioni sull'analisi nel database](tutorials/sqldev-in-database-python-for-sql-developers.md)
#### [Ottenere dati e script](tutorials/sqldev-py1-download-the-sample-data.md)
#### [Importare dati](tutorials/sqldev-py2-import-data-to-sql-server-using-powershell.md)
#### [Esplorare e visualizzare i dati](tutorials/sqldev-py3-explore-and-visualize-the-data.md)
#### [Creare funzionalità di dati](tutorials/sqldev-py4-create-data-features-using-t-sql.md)
#### [Training e salvataggio di un modello](tutorials/sqldev-py5-train-and-save-a-model-using-t-sql.md)
#### [Rendere operativo il modello](tutorials/sqldev-py6-operationalize-the-model.md)

# [Esempi](https://github.com/Microsoft/sql-server-samples)

# [Soluzioni](tutorials/data-science-scenarios-and-solution-templates.md)

# [Procedura](r/sql-server-machine-learning-tasks.md)

## Gestione dei pacchetti
### [Pacchetti predefiniti](r/installing-and-managing-r-packages.md)
### [Ottenere informazioni sui pacchetti](r/determine-which-packages-are-installed-on-sql-server.md)
### [Installare nuovi pacchetti Python](python/install-additional-python-packages-on-sql-server.md)
### [Installare nuovi pacchetti R](r/install-additional-r-packages-on-sql-server.md)
#### [Usare i gestori di pacchetti R](r/use-r-package-managers-on-sql-server.md)
#### [Usare T-SQL](r/install-r-packages-tsql.md)
#### [Usare RevoScaleR](r/use-revoscaler-to-manage-r-packages.md)
##### [Abilitare la gestione remota dei pacchetti R](r/r-package-how-to-enable-or-disable.md)
##### [Sincronizzare i pacchetti R](r/package-install-uninstall-and-sync.md)
#### [Creare un repository miniCRAN](r/create-a-local-package-repository-using-minicran.md)
#### [Suggerimenti per l'uso di pacchetti R](r/packages-installed-in-user-libraries.md)

## Esplorazione e modellazione dei dati
### [Librerie e tipi di dati R](r/r-libraries-and-data-types.md)
### [Librerie e tipi di dati Python](python/python-libraries-and-data-types.md)
### [Punteggio nativo](sql-native-scoring.md)
### [Punteggio in tempo reale](real-time-scoring.md)
### [Modellazione predittiva con R](r/data-exploration-and-predictive-modeling-with-r.md)
### [Definire punteggi nativi o in tempo reale](r/how-to-do-realtime-scoring.md)
### [Caricare oggetti R usando ODBC](r/save-and-load-r-objects-from-sql-server-using-odbc.md)
### [Conversione di codice R per l'uso in Machine Learning Services](r/converting-r-code-for-use-in-sql-server.md)
### [Creazione di più modelli usando rxExecBy](r/creating-multiple-models-using-rxexecby.md)
### [Usare dati dai cubi OLAP in R](r/using-data-from-olap-cubes-in-r.md)
### [Creare una stored procedure con sqlrutils](r/how-to-create-a-stored-procedure-using-sqlrutils.md)

## restazioni
### [Ottimizzazione delle prestazioni per R - Panoramica](r/sql-server-r-services-performance-tuning.md)
### [Ottimizzazione delle prestazioni per R - Configurazione di SQL Server](r/sql-server-configuration-r-services.md)
### [Ottimizzazione delle prestazioni per R - R e ottimizzazione dei dati](r/r-and-data-optimization-r-services.md)
### [Ottimizzazione delle prestazioni per R - Risultati](r/performance-case-study-r-services.md)
### [Usare le funzioni di profiling del codice R](r/using-r-code-profiling-functions.md)

## Amministrazione
### [Configurare e gestire R](r/configuration-sql-server-r-services.md)
### [Opzioni di configurazione avanzate per Machine Learning Services](r/configure-and-manage-advanced-analytics-extensions.md)
### [Considerazioni sulla sicurezza per il runtime R in SQL Server](r/security-considerations-for-the-r-runtime-in-sql-server.md)
### [Modificare il pool di account utente per SQL Server Machine Learning Services](r/modify-the-user-account-pool-for-sql-server-r-services.md)
### [Aggiungere SQLRUserGroup come utente del database](r/add-sqlrusergroup-to-database.md)
### [Distribuire e usare i modelli usando i servizi Web](operationalization-with-mrsdeploy.md)
### [Gestione e monitoraggio delle soluzioni](r/managing-and-monitoring-r-solutions.md)
### [Gestione delle risorse per Machine Learning Services](r/resource-governance-for-r-services.md)
### [Creare un pool di risorse per Machine Learning](r/how-to-create-a-resource-pool-for-r.md)
### [Eventi estesi per Machine Learning Services](r/extended-events-for-sql-server-r-services.md)
### [Eventi estesi per il monitoraggio di istruzioni PREDICT](xe-event-predict-tsql.md)
### [DMV per Machine Learning Services](r/dmvs-for-sql-server-r-services.md)
### [Uso delle funzioni di profiling del codice R](r/using-r-code-profiling-functions.md)
### [Monitorare Machine Learning Services con i report personalizzati in Management Studio](r/monitor-r-services-using-custom-reports-in-management-studio.md)

# [Informazioni di riferimento sui pacchetti](r/machine-learning-services-r-reference.md)

## [MicrosoftML in SQL](using-the-microsoftml-package.md)
## [RevoScaleR in SQL](r/revoscaler-overview.md)
## [Elenco delle funzioni RevoScaleR per i dati di SQL Server](r/scaler-functions-for-working-with-sql-server-data.md)
## [sqlrutils in SQL](r/generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md)
## [olapR in SQL](r/how-to-create-mdx-queries-using-olapr.md)
## [revoscalepy in SQL](python/what-is-revoscalepy.md)

# Risorse

## [Problemi noti](known-issues-for-sql-server-machine-learning-services.md)
## [Note sulla versione](https://docs.microsoft.com/sql/sql-server/sql-server-2017-release-notes)
## [Configurare una macchina virtuale](r/installing-sql-server-r-services-on-an-azure-virtual-machine.md)
## [Risoluzione dei problemi](machine-learning-troubleshooting-faq.md)
### [Raccolta dati](data-collection-ml-troubleshooting-process.md)
### [Errori di installazione e aggiornamento](r/upgrade-and-installation-faq-sql-server-r-services.md)
### [Launchpad ed errori di esecuzione di script esterni](common-issues-external-script-execution.md)
### [Errori di scripting R](r-script-execution-errors.md)

## Blog
### [SQL Server](https://blogs.technet.microsoft.com/dataplatforminsider/)
### [R Server](https://blogs.msdn.microsoft.com/microsoftrservertigerteam/)
### [Apprendimento automatico](https://blogs.technet.microsoft.com/machinelearning/)

## Forum
### [SQL Server](https://social.msdn.microsoft.com/Forums/sqlserver/home?category=sqlserver)
### [Machine Learning Server](https://social.msdn.microsoft.com/Forums/home?forum=MicrosoftR)

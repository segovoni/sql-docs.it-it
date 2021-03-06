# [Preparazione aggiornamento a SQL Server 2014](sql-server-2014-upgrade-advisor.md)
# [Installazione di Preparazione aggiornamento](installing-upgrade-advisor.md)
## [Prerequisiti di Preparazione aggiornamento](upgrade-advisor-prerequisites.md)
## [Installazione di Preparazione aggiornamento dal prompt dei comandi](installing-upgrade-advisor-from-the-command-prompt.md)

# [Uso di Preparazione aggiornamento](working-with-upgrade-advisor.md)
# [Panoramica di Preparazione aggiornamento](overview-of-upgrade-advisor.md)
## [Panoramica del processo di aggiornamento](upgrade-process-overview.md)
## [Panoramica di Preparazione aggiornamento](upgrade-advisor-overview.md)
## [Esecuzione di Preparazione aggiornamento (interfaccia utente)](running-upgrade-advisor-user-interface.md)
## [Esecuzione di Preparazione aggiornamento (prompt dei comandi)](running-upgrade-advisor-command-prompt.md)
## [Uso dei report](using-reports.md)
## [Errori di Preparazione aggiornamento](upgrade-advisor-errors.md)
# [Procedure per Preparazione aggiornamento](upgrade-advisor-how-to-topics.md)
## [Procedura: Installare Preparazione aggiornamento](how-to-install-upgrade-advisor.md)
## [Procedura: Avviare Preparazione aggiornamento](how-to-launch-upgrade-advisor.md)
## [Procedura: Eseguire l'Analisi guidata di Preparazione aggiornamento](how-to-run-the-upgrade-advisor-analysis-wizard.md)
## [Procedura: Visualizzare un report di Preparazione aggiornamento](how-to-view-an-upgrade-advisor-report.md)
## [Procedura: Filtrare i report](how-to-filter-reports.md)
## [Procedura: Esportare i report](how-to-export-reports.md)
# [Guida di riferimento all'interfaccia utente](upgrade-advisor-user-interface-reference.md)
## [Componenti di SQL Server](sql-server-components.md)
## [Parametri di connessione](connection-parameters.md)
## [Parametri di SQL Server](sql-server-parameters.md)
## [Parametri di Analysis Services](analysis-services-parameters.md)
## [Parametri di Reporting Services](reporting-services-parameters.md)
## [Parametri di Integration Services](integration-services-parameters.md)
## [Confermare le impostazioni di Preparazione aggiornamento](confirm-upgrade-advisor-settings.md)
## [Stato di Preparazione aggiornamento](upgrade-advisor-progress.md)

# [Risoluzione dei problemi di aggiornamento](resolving-upgrade-issues.md)
## [Problemi di aggiornamento più recenti](late-breaking-upgrade-issues.md)
## [Problemi di aggiornamento del motore di database](database-engine-upgrade-issues.md)
### [Il carattere 0xFFFF non è valido come identificatore di oggetto](0xffff-character-is-not-valid-as-an-object-identifier.md)
### [Dopo l'aggiornamento, le parole chiave riservate non possono essere usate come identificatori](after-upgrade-new-reserved-keywords-cannot-be-used-as-identifiers.md)
### [Modifiche al comportamento di sottostringa e lunghezza stringa](changes-to-behavior-of-string-length-and-substring.md)
### [Modifiche al comportamento in syslockinfo e sp_lock](changes-to-behavior-in-syslockinfo-and-sp-lock.md)
### [Modifiche al comportamento dei flag di traccia](changes-to-behavior-of-trace-flags.md)
### [Modifiche ai limiti di memoria e CPU per SQL Server Reporting Services Standard ed Enterprise](cpu-memory-limits-changes-sql-server-reporting-services-standard-enterprise.md)
### [Modifiche al formato di archiviazione per i tipi xs:dateTime, xs:date e xs:time](changes-to-the-storage-format-for-types-xs-datetime-xs-date-and-xs-time.md)
### [Gli alias di colonna usati nella clausola ORDER BY non possono essere preceduti dall'alias della tabella](column-aliases-in-order-by-clause-cannot-be-prefixed-by-table-alias.md)
### [I comandi DBCC deprecati sono stati rimossi](deprecated-dbcc-commands-have-now-been-removed.md)
### [Scollegare il database con ID 32767](detach-database-id-32767.md)
### [Impossibile aggiornare gli account di accesso di SQL Server 6.5 inattivi](dormant-sql-server-6-5-logins-cannot-be-upgraded.md)
### [FOR BROWSE non consentita nelle viste in modalità di compatibilità 90 o successiva](for-browse-is-not-allowed-in-views-in-90-or-later-compatibility-modes.md)
### [In modalità di compatibilità 90 o successiva le query FOR XML AUTO restituiscono riferimenti a tabelle derivate](for-xml-auto-queries-return-derived-table-references-90-later-compatibility-mode.md)
### [INFORMATION_SCHEMA.SCHEMATA restituisce i nomi degli schemi di un database, non i database di un'istanza](information-schema-schemata-returns-schema-names-not-databases.md)
### [Un nome di named pipe non valido può bloccare l'aggiornamento](invalid-named-pipe-name-can-block-upgrade.md)
### [Se sono presenti tabelle di cronologia di backup o ripristino di grandi dimensioni, l'aggiornamento potrebbe apparire bloccato](large-backup-or-restore-history-tables-make-upgrade-appear-to-not-respond.md)
### [In modalità di compatibilità 90 o successiva per le costanti di grandi dimensioni vengono usati i tipi di dati per valori di grandi dimensioni](large-constants-typed-as-large-value-types-90-later-compatibility-mode.md)
### [Il log shipping non verrà eseguito dopo l'aggiornamento](log-shipping-will-not-run-after-upgrading.md)
### [Modificare le applicazioni in modo da prevedere valori bigint da sysperfinfo.cntr_value](modify-applications-to-expect-bigint-values-from-sysperfinfo-cntr-value.md)
### [Modificare le connessioni che usano i protocolli di rete Banyan VINES Sequenced Packet Protocol (SPP), Multiprotocol, AppleTalk o NWLink IPX/SPX](modify-connections-banyan-vines-spp-multiprotocol-appletalk-nwlink-ipx-spx.md)
### [Modificare gli indici che dipendono dal tipo restituito di HOST_ID](modify-indexes-that-depend-on-the-return-type-of-host-id.md)
### [Modificare le istruzioni UPDATETEXT che eseguono operazioni di lettura e scrittura in oggetti BLOB](modify-updatetext-statements-that-read-and-write-to-binary-large-objects-blobs.md)
### [I trigger AFTER nidificati vengono attivati anche quando l'opzione relativa alla nidificazione dei trigger è disattivata](nested-after-trigger-fires-even-when-trigger-nesting-is-off.md)
### [La nuova colonna nell'output di sp_helptrigger potrebbe influire sulle applicazioni](new-column-in-output-of-sp-helptrigger-may-impact-applications.md)
### [osql non supporta più i comandi ED e !!](osql-no-longer-supports-the-ed-and-commands.md)
### [Gli operatori di outer join *= e =* non sono supportati in modalità di compatibilità 90 o successiva](outer-join-operators-and-are-not-supported-in-90-or-later-compatibility-modes.md)
### [Non è possibile aggiornare database di sola lettura](read-only-databases-cannot-be-upgraded.md)
### [Rimuovere le chiamate al comando DBCC CONCURRENCYVIOLATION deprecato](remove-calls-to-the-deprecated-dbcc-concurrencyviolation-command.md)
### [Rimuovere i due punti dopo la parola chiave riservata](remove-colon-following-reserved-keyword.md)
### [Rimuovere le istruzioni DDL eseguite su tabelle inserite ed eliminate all'interno di trigger DML](remove-ddl-operations-on-the-inserted-and-deleted-tables-inside-dml-triggers.md)
### [Rimuovere i riferimenti alle stored procedure di sistema deprecate](remove-references-to-deprecated-system-stored-procedures.md)
### [Rimuovere i riferimenti alle tabelle di sistema non documentate](remove-references-to-undocumented-system-tables.md)
### [Rimuovere le istruzioni che eliminano oggetti di sistema](remove-statements-that-drop-system-objects.md)
### [Rimuovere le istruzioni che modificano le autorizzazioni a livello di colonna per gli oggetti di sistema](remove-statements-that-modify-column-level-permissions-on-system-objects.md)
### [Rimuovere le istruzioni che modificano oggetti di sistema](remove-statements-that-modify-system-objects.md)
### [Rimuovere lo schema cdc se si intende abilitare Change Data Capture](remove-the-cdc-schema-if-you-plan-to-enable-change-data-capture.md)
### [Rinominare gli account di accesso con nomi uguali a quelli dei ruoli predefiniti del server](rename-logins-matching-fixed-server-role-names.md)
### [Rimuovere i tipi definiti dall'utente (UDT) denominati come i tipi di dati riservati DATE e TIME](remove-udt-s-named-after-the-reserved-date-and-time-data-types.md)
### [Rimuovere i tipi definiti dall'utente (UDT) denominati come il tipo di dati riservato ORDPATH](remove-udt-s-named-after-the-reserved-ordpath-data-type.md)
### [Rimuovere i tipi definiti dall'utente (UDT) denominati come i tipi di dati GEOMETRY e GEOGRAPHY](remove-udts-named-after-the-reserved-geometry-and-geography-data-types.md)
### [Rinominare l'utente sys](rename-user-sys.md)
### [SERVERPROPERTY restituisce il risultato corretto della proprietà LCID in SQL Server 2005](serverproperty-returns-correct-result-for-lcid-property-in-sql-server-2005.md)
### [Requisiti dell'account del servizio per l'aggiornamento a SQL Server 2008 in un controller di dominio](service-account-requirements-upgrade-sql-server-2008-on-domain-controller.md)
### [Specificare la parola chiave WITH quando si usano hint di tabella in modalità di compatibilità 90](specify-the-with-keyword-when-using-table-hints-in-90-compatibility-mode.md)
### [Il supporto SOAP nativo di SQL Server non è più disponibile in questa versione di SQL Server.](sql-server-native-soap-support-is-discontinued-in-this-version-of-sql-server.md)
### [Gli hint di tabella contenuti nelle definizioni delle viste indicizzate vengono ignorati in modalità di compatibilità 80 e non sono consentiti in modalità di compatibilità 90 o successiva](table-hints-indexed-views-ignored-80-compatibility-mode-not-allowed-90-later.md)
### [Aggiornare le espressioni XPath OPENXML in modo da rimuovere le funzioni non supportate](update-openxml-xpath-expressions-to-remove-unsupported-functions.md)
### [Usare sp_rename per rinominare gli indici duplicati](use-sp-rename-to-rename-duplicate-index-name.md)
### [Usare il percorso completo per registrare i nomi delle DLL delle stored procedure estese](use-the-full-path-to-register-extended-stored-procedure-dll-names.md)
### [In system_function_schema non sono consentite funzioni definite dall'utente](user-defined-functions-are-not-allowed-in-system-function-schema.md)
### [Verificare che durante il processo di aggiornamento tutti i filegroup siano scrivibili](verify-all-filegroups-are-writeable-during-the-upgrade-process.md)
### [Verificare che l'aumento di dimensioni automatico sia abilitato per tutti i file di dati e di log durante il processo di aggiornamento](verify-autogrow-turned-on-for-all-data-and-log-files-during-upgrade.md)
### [Verificare che durante il processo di aggiornamento non siano presenti file di database su unità compresse](verify-no-database-files-on-compressed-drives-during-upgrade.md)
### [Avviso relativo all'uso sul lato client di GEOMETRY, GEOGRAPHY e HIERARCHYID](warning-about-client-side-usage-of-geometry-geography-and-hierarchyid.md)
### [Le stored procedure di Pubblicazione guidata sul Web sono state rimosse](web-assistant-stored-procedures-have-been-removed.md)
### [Configurazione proxy WinSock non supportata](winsock-proxy-configuration-not-supported.md)
### [WITH CHECK OPTION non è supportata nelle viste che contengono TOP nella modalità di compatibilità 90 o successiva](with-check-option-not-supported-in-top-views-90-later-compatibility-mode.md)
### [Quando è attiva la modalità di compatibilità 90 o successiva la clausola WITH ROWS non è supportata nelle istruzioni CREATE STATISTICS](with-rows-not-supported-in-create-statistics-statements-90-later-compatibility-mode.md)
### [Altri problemi di aggiornamento del motore di database](other-database-engine-upgrade-issues.md)
#### [Deprecation Announcement di mirroring del database](database-mirroring-deprecation-announcement.md)
## [Problemi di aggiornamento della ricerca full-text](full-text-search-upgrade-issues.md)
### [La ricerca full-text è stata modificata in SQL Server 2008](full-text-search-has-changed-since-sql-server-2008.md)
### [I word breaker e i filtri per la ricerca full-text sono stati migliorati in modo significativo in SQL Server 2005 e SQL Server 2008](full-text-search-word-breakers-filters-improved-sql-server-2005-2008.md)
### [La lunghezza dei nomi di catalogo full-text è limitata a 120 caratteri](length-of-full-text-catalog-names-restricted-to-120-characters.md)
### [Per impostazione predefinita, il motore di ricerca full-text Microsoft per SQL Server non carica componenti di terze parti non firmati](full-text-engine-sql-server-default-will-not-load-third-party-components.md)
### [Modificare le stored procedure che usano proprietà della ricerca full-text obsolete](modify-stored-procedures-that-use-discontinued-full-text-search-properties.md)
### [Gli indici full-text su colonne calcolate non persistenti non sono consentiti](full-text-indexes-on-nonpersisted-computed-columns-are-not-allowed.md)
### [Gli indici full-text nei database master, tempdb e modello non sono supportati](full-text-indexes-on-master-tempdb-and-model-databases-are-not-supported.md)
### [A seguito dell'aggiornamento, per la ricerca full-text verranno usati per impostazione predefinita word breaker e filtri a livello di istanza, non globali](full-text-search-uses-instance-not-global-level-defaults-after-upgrade.md)
### [Dopo l'aggiornamento, nella ricerca full-text non saranno consentiti i predicati nell'espressione OUTPUT INTO](full-text-search-will-not-allow-predicates-in-output-into-expressions-after-upgrade.md)
## [Problemi di aggiornamento della replica](replication-upgrade-issues.md)
### [Il seguito all'aggiornamento le sottoscrizioni ad aggiornamento in coda che usano Accodamento messaggi verranno modificate](upgrading-will-modify-queued-updating-subscriptions-that-use-message-queuing.md)
### [Altri problemi di aggiornamento della replica](other-replication-upgrade-issues.md)
## [Problemi di aggiornamento di Reporting Services (Preparazione aggiornamento)](reporting-services-upgrade-issues-upgrade-advisor.md)
### [Certificati client sul sito Web del server di report (Preparazione aggiornamento)](client-certificates-on-the-report-server-web-site-upgrade-advisor.md)
### [Nel server di report sono state rilevate estensioni personalizzate (Preparazione aggiornamento)](custom-extensions-were-detected-on-the-report-server-upgrade-advisor.md)
### [Nel server di report sono stati rilevati elementi di report personalizzati (Preparazione aggiornamento)](custom-report-items-were-detected-on-the-report-server-upgrade-advisor.md)
### [Non sono stati rilevati componenti di compatibilità con le versioni precedenti di IIS (Preparazione aggiornamento)](iis-backward-compatibility-components-were-not-detected-upgrade-advisor.md)
### [Rilevata restrizione degli indirizzi IP (Preparazione aggiornamento)](ip-address-restriction-detected-upgrade-advisor.md)
### [Nel server di report sono stati rilevati filtri ISAPI (Preparazione aggiornamento)](isapi-filters-detected-on-the-report-server-site-upgrade-advisor.md)
### [Nel computer del server di report sono state rilevate estensioni obsolete (Preparazione aggiornamento)](obsolete-extensions-were-detected-on-the-report-server-computer-upgrade-advisor.md)
### [Il database del server di report non è configurato (Preparazione aggiornamento)](report-server-database-is-not-configured-upgrade-advisor.md)
### [Rilevato un gruppo di servizi Web ReportServer di SQL Server 2005 (Upgrade Advisor)](sql-server-2005-report-server-web-service-group-detected-upgrade-advisor.md)
### [Non sono state specificate directory virtuali (Preparazione aggiornamento)](virtual-directories-are-unspecified-upgrade-advisor.md)
### [Metodo di autenticazione non supportato nella directory virtuale (Preparazione aggiornamento)](virtual-directory-has-unsupported-authentication-method-upgrade-advisor.md)
### [Modifiche ai limiti di memoria e CPU per SQL Server Standard ed Enterprise (Preparazione aggiornamento)](cpu-memory-limits-changes-sql-server-standard-enterprise-upgrade-advisor.md)
### [Account di dominio richiesti per la farm di SharePoint (Preparazione aggiornamento)](domain-accounts-required-for-sharepoint-farm-upgrade-advisor.md)
### [Esplorazione diretta nel server di report (Preparazione aggiornamento)](direct-browsing-to-report-server-upgrade-advisor.md)
### [Microsoft SharePoint 2007 è installato (Preparazione aggiornamento)](microsoft-sharepoint-2007-is-installed-upgrade-advisor.md)
### [Il servizio SharePoint Shared di Microsoft SQL Server Reporting Services è installato in un ambiente side-by-side (Preparazione aggiornamento)](sql-server-reporting-services-sharepoint-shared-service-side-by-side-upgrade-advisor.md)
### [Regole di confronto del server del motore di database incompatibili (Preparazione aggiornamento)](incompatible-database-engine-server-collation-upgrade-advisor.md)
### [Altri problemi di aggiornamento di Reporting Services](other-reporting-services-upgrade-issues.md)
## [Problemi di aggiornamento di SQL Server Agent](sql-server-agent-upgrade-issues.md)
### [Piani di manutenzione del database sostituiti](database-maintenance-plans-superseded.md)
### [Solo gli utenti sysadmin possono scrivere file di log dei passaggi del processo nel file system](only-sysadmin-users-can-write-job-step-log-files-to-the-file-system.md)
### [Al posto della stored procedure estesa xp_sqlagent_proxy_account usare le nuove stored procedure](replace-xp-sqlagent-proxy-account-extended-sp-with-new-stored-procedures.md)
### [La categoria di processi per il log shipping di SQL Server Agent impedisce il completamento dell'aggiornamento](sql-server-agent-log-shipping-job-category-causes-upgrade-to-fail.md)
### [Il servizio SQL Server Agent non può usare l'autenticazione di SQL Server](sql-server-agent-service-cannot-use-sql-server-authentication.md)
### [Aggiornare la sintassi del token nei passaggi del processo di SQL Server Agent](update-token-syntax-in-sql-server-agent-job-steps.md)
### [Aggiornare tutti i server di destinazione prima di aggiornare il server master](upgrade-all-target-servers-before-upgrading-the-master-server.md)
### [In seguito all'aggiornamento l'account proxy utente per SQL Server Agent verrà sostituito dall'account temporaneo UpgradedProxyAccount](upgrading-changes-sql-server-agent-user-proxy-account-to-temporary-account.md)

# [Installazione dei servizi e configurazione](setup-and-servicing-installation.md)
## [Considerazioni sulla gestione delle licenze per SQL Server](licensing-considerations-for-sql-server.md)
# [Panoramica della documentazione del programma di installazione di SQL Server](overview-of-sql-server-setup-documentation.md)
# [Interfaccia utente del programma di installazione di SQL Server 2014](sql-server-2014-setup-user-interface.md)

# [Guida di riferimento all'interfaccia utente del programma di installazione di SQL Server](sql-server-setup-user-interface-reference.md)
## [Accettare le condizioni di licenza](accept-license-terms.md)
## [Aggiungere un nodo del cluster di failover di SQL Server](add-sql-server-failover-cluster-node.md)
## [Configurazione di Analysis Services - Provisioning account](analysis-services-configuration-account-provisioning.md)
## [Configurazione di Analysis Services - Directory dati](analysis-services-configuration-data-directories.md)
## [Selezione dischi cluster](cluster-disk-selection.md)
## [Configurazione di rete cluster](cluster-network-configuration.md)
## [Configurazione nodi cluster](cluster-node-configuration.md)
## [Configurazione nodi cluster (completa)](cluster-node-configuration-complete.md)
## [Gruppo risorse cluster](cluster-resource-group.md)
## [Criteri di sicurezza cluster](cluster-security-policy.md)
## [Operazione completata - Completamento immagine](complete-complete-image.md)
## [Stato completamento immagine](complete-image-progress.md)
## [Regole di completamento immagine](complete-image-rules.md)
## [Operazione completata - Preparazione immagine](complete-prepare-image.md)
## [Operazione completata - Ripristino](complete-repair.md)
## [Operazione completata - Aggiornamento](complete-upgrade.md)
## [Configurazione del motore di database - Provisioning account](database-engine-configuration-account-provisioning.md)
## [Configurazione del motore di database - Directory dati](database-engine-configuration-data-directories.md)
## [Configurazione del motore di database - Filestream](database-engine-configuration-filestream.md)
## [Configurazione del motore di database - Istanza utente](database-engine-configuration-user-instance.md)
## [Configurazione del controller di Riesecuzione distribuita](distributed-replay-controller-configuration.md)
## [Configurazione del client di Riesecuzione distribuita](distributed-replay-client-configuration.md)
## [Regole di aggiornamento delle edizioni](edition-upgrade-rules.md)
## [Report cluster di failover](failover-cluster-report.md)
## [Esame funzionalità](feature-review.md)
## [Regole di installazione](installation-rules.md)
## [Regole di funzionalità](feature-rules.md)
## [Selezione funzionalità](feature-selection.md)
## [Selezione funzionalità (disinstallazione)](feature-selection-uninstall.md)
## [Selezione funzionalità (aggiornamento)](select-features-upgrade.md)
## [Opzioni di aggiornamento della ricerca full-text](full-text-search-upgrade-options.md)
## [Operazione completata - Installazione](complete-installation.md)
## [Prerequisiti di installazione](installation-prerequisites.md)
## [Stato dell'installazione](installation-progress.md)
## [Tipo di installazione](installation-type.md)
## [Configurazione dell'istanza](instance-configuration.md)
## [Selezione istanza (disinstallazione)](instance-selection-uninstall.md)
## [Selezione istanza (aggiornamento)](instance-selection-upgrade.md)
## [Selezione istanza](select-instance.md)
## [Post-disinstallazione](post-uninstall.md)
## [Avanzamento preparazione immagine](prepare-image-progress.md)
## [Regole di preparazione immagine](prepare-image-rules.md)
## [Prepara tipo di immagine](prepare-image-type.md)
## [Codice Product Key](product-key.md)
## [Stato (disinstallazione)](progress-uninstall.md)
## [Inizio completamento immagine](ready-to-complete-image.md)
## [Inizio installazione](ready-to-install.md)
## [Inizio preparazione immagine](ready-to-prepare-image.md)
## [Ripristino](ready-to-repair.md)
## [Rimuovere un nodo da un cluster di failover di SQL Server](remove-sql-server-failover-cluster-node.md)
## [Stato del ripristino](repair-progress.md)
## [Opzioni di configurazione di Reporting Services](reporting-services-configuration-options-ssrs.md)
## [Aggiornamento modalità SharePoint di Reporting Services](reporting-services-sharepoint-mode-upgrade-ssrs.md)
## [Autenticazione modalità SharePoint di Reporting Services](reporting-services-sharepoint-mode-authentication.md)
## [Selezionare un'istanza predisposta](select-a-prepared-instance.md)
## [Configurazione server - Regole di confronto](server-configuration-collation.md)
## [Configurazione server - Account di servizio](server-configuration-service-accounts.md)
## [Impostazione ruolo](setup-role.md)
## [Creazione guidata cluster di failover.di SQL Server 2008 (completamento)](sql-server-failover-cluster-wizard-complete.md)
## [Creazione guidata cluster di failover.di SQL Server 2008 (installazione)](sql-server-failover-cluster-wizard-install.md)
## [Creazione guidata cluster di failover.di SQL Server 2008 (preparazione)](sql-server-failover-cluster-wizard-prepare.md)
## [Inizio aggiornamento](ready-to-upgrade.md)
## [Regole di installazione](install-rules.md)
## [Regole di disinstallazione](uninstallation-rules.md)
## [Stato aggiornamento](upgrade-progress.md)
## [Regole di funzionalità (aggiornamento)](feature-rules-upgrade.md)
## [Verificare le opzioni di disinstallazione](verify-uninstall-options.md)

# [Installazione della manutenzione di SQL Server](sql-server-servicing-installation.md)
## [Installazione degli aggiornamenti dal prompt dei comandi](../../database-engine/install-windows/installing-updates-from-the-command-prompt.md)
## [Procedura: Convalidare la corretta installazione di un aggiornamento di SQL Server](how-to-validate-successful-installation-of-a-sql-server-update.md)
## [Panoramica sull'installazione dei servizi SQL Server](overview-of-sql-server-servicing-installation.md)
## [Pagina iniziale](welcome.md)
## [Condizioni di licenza](license-terms.md)
## [Seleziona funzionalità](select-features.md)
## [Controllo file in uso](check-files-in-use.md)
## [Inizio aggiornamento](ready-to-update.md)
## [Stato dell'aggiornamento](update-progress.md)
## [Operazione completata](complete.md)

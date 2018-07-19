# Übersicht

## [Was sind SQL Server-Machine Learning Services?](what-is-sql-server-machine-learning.md)
### [Datenbankinterne Analyse](r/sql-server-r-services.md)
### [Eigenständiger Server](r/r-server-standalone.md)
## [Neue Funktionen](what-s-new-in-sql-server-machine-learning-services.md)
## [Funktionen nach Edition](r/differences-in-r-features-between-editions-of-sql-server.md)

# [Aufbau](architecture-overview-machine-learning.md)
## [R](r/architecture-overview-sql-server-r.md)
### [Interoperabilität mit R](r/r-interoperability-in-sql-server.md)
### [Komponenten mit Unterstützung für die R-Integration](r/new-components-in-sql-server-to-support-r.md)
### [Sicherheit für R](r/security-overview-sql-server-r.md)
## [Python](python/architecture-overview-sql-server-python.md)
### [Python in Machine Learning Services](python/sql-server-python-services.md)
### [Interoperabilität mit Python](python/python-interoperability.md)
### [Komponenten zur Unterstützung für Python](python/new-components-in-sql-server-to-support-python-integration.md)
### [Python-Sicherheit](python/security-overview-sql-server-python-services.md)
<!-- ### [How To Create a Resource Pool for Python](python/how-to-create-a-resource-pool-for-python.md)-->
<!-- ### [Extended Events for Python](python/extended-events-for-python.md)-->
<!-- ### [DMVs for Python](python/dmvs-for-python.md)-->
<!-- ### [Resource Governance for Python](python/resource-governance-for-python.md)-->

# Install 

## SQL Server 2017
### [Datenbankinterne Analyse](install/sql-machine-learning-services-windows-install.md)
### [Eigenständiger Server](install/sql-machine-learning-standalone-windows-install.md)
## SQL Server 2016
### [R Services (In-Database)](install/sql-r-services-windows-install.md)
### [R Server (eigenständig)](install/sql-r-standalone-windows-install.md)
## [Vorgefertigtes Modell](r/install-pretrained-models-sql-server.md)
## [Einrichtung der Befehlszeile](install/sql-ml-component-commandline-install.md)
## [Offlineeinrichtung (kein Internet)](install/sql-ml-component-install-without-internet-access.md)
## [Upgrade von R und Python ausführen](r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)
## [Einrichten von R-Tools](r/set-up-a-data-science-client.md)
## [Einrichten von Python-Tools](python/setup-python-client-tools-sql.md)

# Schnellstarts

## R
### [Hallo Welt in R und SQL](tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
### [Arbeiten mit Eingaben und Ausgaben](tutorials/rtsql-working-with-inputs-and-outputs.md)
### [Arbeiten mit Datentypen und Objekten](tutorials/rtsql-r-and-sql-data-types-and-data-objects.md)
### [Erstellen eines Vorhersagemodells](tutorials/rtsql-create-a-predictive-model-r.md)
### [Vorhersagen und Zeichnen ausgehend vom Modell](tutorials/rtsql-predict-and-plot-from-model.md)

# [Tutorials](tutorials/machine-learning-services-tutorials.md)
## [R](tutorials/sql-server-r-tutorials.md)
### [Informationen zur datenbankinternen Analyse](tutorials/sqldev-in-database-r-for-sql-developers.md)
#### [1: Abrufen von Daten und Skripts](tutorials/sqldev-download-the-sample-data.md)
#### [2: Einrichten der Umgebung](r/sqldev-import-data-to-sql-server-using-powershell.md)
#### [3: Visualisieren von Daten](tutorials/sqldev-explore-and-visualize-the-data.md)
#### [4: Erstellen von Datenfeatures](tutorials/sqldev-create-data-features-using-t-sql.md)
#### [5: Trainieren und Speichern in SQL](r/sqldev-train-and-save-a-model-using-t-sql.md)
#### [6: Vorhersagen von Ergebnissen](tutorials/sqldev-operationalize-the-model.md)

### [Lückenlose exemplarische Vorgehensweise für Data Science](tutorials/walkthrough-data-science-end-to-end-walkthrough.md)
#### [Vorbereiten von Daten](tutorials/walkthrough-prepare-the-data.md)
#### [Durchsuchen der Daten mithilfe von SQL](tutorials/walkthrough-view-and-explore-the-data.md)
#### [Zusammenfassen der Daten mithilfe von R](tutorials/walkthrough-view-and-summarize-data-using-r.md)
#### [Erstellen von Graphen und Plots](tutorials/walkthrough-create-graphs-and-plots-using-r.md)
#### [Erstellen von Datenfeatures](tutorials/walkthrough-create-data-features.md)
#### [Erstellen und Speichern des Modells](tutorials/walkthrough-build-and-save-the-model.md)
#### [Bereitstellen und Verwenden des Modells](tutorials/walkthrough-deploy-and-use-the-model.md)

### [Tieferer Einblick in RevoScaleR](tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)
#### [Erstellen von Datenbanken und Berechtigungen](tutorials/deepdive-work-with-sql-server-data-using-r.md)
#### [Erstellen von Datenobjekten mithilfe von RxSqlServerData](tutorials/deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md)
#### [Abfragen und Ändern von Daten](tutorials/deepdive-query-and-modify-the-sql-server-data.md)
#### [Definieren eines Computekontexts](tutorials/deepdive-define-and-use-compute-contexts.md)
#### [Erstellen und Ausführen von R-Skripts](tutorials/deepdive-create-and-run-r-scripts.md)
#### [Visualisieren von Daten](tutorials/deepdive-visualize-sql-server-data-using-r.md)
#### [Erstellen von Modellen](tutorials/deepdive-create-models.md)
#### [Auswertung neuer Daten](tutorials/deepdive-score-new-data.md)
#### [Transformieren von Daten](tutorials/deepdive-transform-data-using-r.md)
#### [Laden von Daten in den Arbeitsspeicher mit rxImport](tutorials/deepdive-load-data-into-memory-using-rximport.md)
#### [Erstellen einer Tabelle mit rxDataStep](tutorials/deepdive-create-new-sql-server-table-using-rxdatastep.md)
#### [Blockweises Analysieren mithilfe von rxDataStep](tutorials/deepdive-perform-chunking-analysis-using-rxdatastep.md)
#### [Analysieren von Daten in einem lokalen Rechenkontext](tutorials/deepdive-analyze-data-in-local-compute-context.md)
#### [Verschieben von Daten zwischen SQL Server und einer XDF-Datei](tutorials/deepdive-move-data-between-sql-server-and-xdf-file.md)
#### [Erstellen einer einfachen Simulation](tutorials/deepdive-create-a-simple-simulation.md)

## [Python](tutorials/sql-server-python-tutorials.md)
### [Ausführen von Python mit T-SQL](tutorials/run-python-using-t-sql.md)
#### [Umschließen von Python in einer gespeicherten Prozedur](tutorials/wrap-python-in-tsql-stored-procedure.md)
#### [Trainieren und Bewerten über ein Python-Modell in SQL Server](tutorials/train-score-using-python-in-tsql.md)
#### [Erstellen eines Modells in einem SQL Server-Computekontext mithilfe von Revoscalepy](tutorials/use-python-revoscalepy-to-create-model.md)
### [Informationen zur datenbankinternen Analyse](tutorials/sqldev-in-database-python-for-sql-developers.md)
#### [Abrufen von Daten und Skripts](tutorials/sqldev-py1-download-the-sample-data.md)
#### [Importieren von Daten](tutorials/sqldev-py2-import-data-to-sql-server-using-powershell.md)
#### [Durchsuchen und Visualisieren von Daten](tutorials/sqldev-py3-explore-and-visualize-the-data.md)
#### [Erstellen von Datenfeatures](tutorials/sqldev-py4-create-data-features-using-t-sql.md)
#### [Trainieren und Speichern des Modells](tutorials/sqldev-py5-train-and-save-a-model-using-t-sql.md)
#### [Operationalisieren des Modells](tutorials/sqldev-py6-operationalize-the-model.md)

# [Beispiele](https://github.com/Microsoft/sql-server-samples)

# [Lösungen](tutorials/data-science-scenarios-and-solution-templates.md)

# [Vorgehensweise](r/sql-server-machine-learning-tasks.md)

## Paketverwaltung
### [Standardpakete](r/installing-and-managing-r-packages.md)
### [Paketinformationen abrufen](r/determine-which-packages-are-installed-on-sql-server.md)
### [Neue Python-Pakete installieren](python/install-additional-python-packages-on-sql-server.md)
### [Neue R-Pakete installieren](r/install-additional-r-packages-on-sql-server.md)
#### [Verwenden des R-Paket-Managers](r/use-r-package-managers-on-sql-server.md)
#### [Verwenden von T-SQL](r/install-r-packages-tsql.md)
#### [Verwenden von RevoScaleR](r/use-revoscaler-to-manage-r-packages.md)
##### [Remoteverwaltung für R-Pakete aktivieren](r/r-package-how-to-enable-or-disable.md)
##### [Synchronisieren von R-Paketen](r/package-install-uninstall-and-sync.md)
#### [Erstellen eines miniCRAN-Repositorys](r/create-a-local-package-repository-using-minicran.md)
#### [Tipps für die Verwendung von R-Paketen](r/packages-installed-in-user-libraries.md)

## Durchsuchen und Modellieren von Daten
### [R-Bibliotheken und -Datentypen](r/r-libraries-and-data-types.md)
### [Python-Bibliotheken und -Datentypen](python/python-libraries-and-data-types.md)
### [Native Bewertung](sql-native-scoring.md)
### [Echtzeitbewertung](real-time-scoring.md)
### [Vorhersagemodellierung mit R](r/data-exploration-and-predictive-modeling-with-r.md)
### [Informationen zum Durchführen von Echtzeit- oder nativen Bewertungen](r/how-to-do-realtime-scoring.md)
### [Laden von R-Objekten mithilfe der ODBC](r/save-and-load-r-objects-from-sql-server-using-odbc.md)
### [Konvertieren des R-Codes für die Verwendung in Machine Learning Services](r/converting-r-code-for-use-in-sql-server.md)
### [Erstellen von mehreren Modellen mit rxExecBy](r/creating-multiple-models-using-rxexecby.md)
### [Verwenden von Daten aus OLAP-Cubes in R](r/using-data-from-olap-cubes-in-r.md)
### [Erstellen einer gespeicherten Prozedur mithilfe von sqlrutils](r/how-to-create-a-stored-procedure-using-sqlrutils.md)

## Leistung
### [Leistungsoptimierung für R – Übersicht](r/sql-server-r-services-performance-tuning.md)
### [Leistungsoptimierung für R – SQL Server-Konfiguration](r/sql-server-configuration-r-services.md)
### [Leistungsoptimierung für R – R und Datenoptimierung](r/r-and-data-optimization-r-services.md)
### [Leistungsoptimierung für R – Ergebnisse](r/performance-case-study-r-services.md)
### [Verwenden von R-Code-Profilerstellungsfunktionen](r/using-r-code-profiling-functions.md)

## Verwaltung
### [Konfigurieren und Verwalten von R](r/configuration-sql-server-r-services.md)
### [Erweiterte Konfigurationsoptionen für Machine Learning Services](r/configure-and-manage-advanced-analytics-extensions.md)
### [Überlegungen zur Sicherheit der R-Laufzeitumgebung in SQL Server](r/security-considerations-for-the-r-runtime-in-sql-server.md)
### [Ändern des Benutzerkontenpools für SQL Server Machine Learning Services](r/modify-the-user-account-pool-for-sql-server-r-services.md)
### [Hinzufügen der SQLRUserGroup als Datenbankbenutzer](r/add-sqlrusergroup-to-database.md)
### [Bereitstellen und Verarbeiten von Modellen mithilfe von Webdiensten](operationalization-with-mrsdeploy.md)
### [Verwalten und Überwachen von Lösungen](r/managing-and-monitoring-r-solutions.md)
### [Ressourcenkontrolle bei Machine Learning Services](r/resource-governance-for-r-services.md)
### [Erstellen eines Ressourcenpools für Machine Learning](r/how-to-create-a-resource-pool-for-r.md)
### [Erweiterte Ereignisse bei Machine Learning Services](r/extended-events-for-sql-server-r-services.md)
### [Erweiterte Ereignisse für die Überwachung von PREDICT-Anweisungen](xe-event-predict-tsql.md)
### [DMVs für Machine Learning Services](r/dmvs-for-sql-server-r-services.md)
### [Verwenden von R-Code-Profilerstellungsfunktionen](r/using-r-code-profiling-functions.md)
### [Überwachung von Machine Learning Services mithilfe von benutzerdefinierten Berichten in Management Studio](r/monitor-r-services-using-custom-reports-in-management-studio.md)

# [Referenz zu Paketen](r/machine-learning-services-r-reference.md)

## [MicrosoftML in SQL](using-the-microsoftml-package.md)
## [RevoScaleR in SQL](r/revoscaler-overview.md)
## [Liste der RevoScaleR-Funktionen für SQL Server-Daten](r/scaler-functions-for-working-with-sql-server-data.md)
## [sqlrutils in SQL](r/generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md)
## [olapR in SQL](r/how-to-create-mdx-queries-using-olapr.md)
## [revoscalepy in SQL](python/what-is-revoscalepy.md)

# Ressourcen

## [Bekannte Probleme](known-issues-for-sql-server-machine-learning-services.md)
## [Versionsanmerkungen](https://docs.microsoft.com/sql/sql-server/sql-server-2017-release-notes)
## [Einrichten eines virtuellen Computers](r/installing-sql-server-r-services-on-an-azure-virtual-machine.md)
## [Problembehandlung](machine-learning-troubleshooting-faq.md)
### [Datensammlung](data-collection-ml-troubleshooting-process.md)
### [Installations- und Upgradefehler](r/upgrade-and-installation-faq-sql-server-r-services.md)
### [Fehler bei der Ausführung von Launchpads und externen Skripts](common-issues-external-script-execution.md)
### [Skripterstellungsfehler bei R](r-script-execution-errors.md)

## Blogs
### [SQL Server](https://blogs.technet.microsoft.com/dataplatforminsider/)
### [R Server](https://blogs.msdn.microsoft.com/microsoftrservertigerteam/)
### [Machine Learning](https://blogs.technet.microsoft.com/machinelearning/)

## Foren
### [SQL Server](https://social.msdn.microsoft.com/Forums/sqlserver/home?category=sqlserver)
### [Machine Learning Server](https://social.msdn.microsoft.com/Forums/home?forum=MicrosoftR)

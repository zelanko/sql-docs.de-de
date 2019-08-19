---
title: SQL Server 2019-CTP-Ankündigungsarchiv | Microsoft-Dokumentation
ms.date: 07/24/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: release-landing
ms.topic: article
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 9f881367442cfa2e24921300ba7595bdbf28ce27
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2019
ms.locfileid: "69028867"
---
# <a name="sql-server-2019-ctp-announcement-archive"></a>SQL Server 2019-CTP-Ankündigungsarchiv

[!INCLUDE[tsql-appliesto-ss-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dieser Artikel bietet ein Archiv von Featureankündigungen von [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]-Releases (CTP). Es wird zu historischen Zwecken bereitgestellt, gilt aber nicht für die Produktion oder aktuelle Vorabversionen von [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)].

Dieser Artikel wird entfernt, sobald [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] für die Produktion freigegeben ist.

Aktuelle Informationen finden Sie unter [Neues in SQL Server 2019](what-s-new-in-sql-server-ver15.md).

## <a name="ctp-31-june-2019"></a>CTP 3.1, Juni 2019

### <a name="big-data-clusters"></a>Big Data-Cluster

| Neue Funktion oder Update | Details |
|:---|:---|
| Änderungen am Befehl `mssqlctl` | Die `mssqlctl cluster`-Befehle wurden in `mssqlctl bdc` umbenannt. Weitere Informationen finden Sie in der [Referenz zu `mssqlctl`](../big-data-cluster/reference-azdata.md). |
|Neue Statusbefehle für `mssqlsctl`|`mssqlctl` fügt neue Befehle zur Ergänzung der vorhandenen Überwachungsbefehle hinzu. Diese ersetzen das Clusterverwaltungsportal, das mit diesem Release entfernt wird.|
| Spark-Computepools | Erstellen Sie zusätzliche Knoten, um die Spark-Rechenleistung zu erhöhen, ohne den Speicher zentral hochskalieren zu müssen. Zudem können Sie Speicherpoolknoten starten, die nicht für Spark verwendet werden. Spark wird vom Speicher entkoppelt. Weitere Informationen finden Sie unter [Configure storage without spark (Konfigurieren des Speichers ohne Spark)](../big-data-cluster/deployment-custom-configuration.md#sparkstorage). |
| MSSQL-Spark-Connector | Ab jetzt werden Lese- und Schreibvorgänge in externen Datenpooltabellen unterstützt. In vorherigen Releases wurden Lese- und Schreibvorgänge nur für Tabellen der MASTER-Instanz unterstützt. Weitere Informationen finden Sie unter [How to read and write to SQL Server from Spark using the MSSQL Spark Connector (Lesen und Schreiben in SQL Server über Spark mithilfe des MSSQL-Spark-Connectors)](../big-data-cluster/spark-mssql-connector.md). |
| Machine Learning mit MLeap | [Trainieren Sie ein MLeap-Machine-Learning-Modell in Spark, und bewerten Sie es mit der Java-Spracherweiterung in SQL Server.](../big-data-cluster/spark-create-machine-learning-model.md) |
| &nbsp; | &nbsp; |

### <a name="database-engine"></a>Datenbank-Engine

| Neue Funktion oder Update | Details |
|:---|:---|
|Indizieren verschlüsselter Spalten|Erstellen Sie Indizes für Spalten, die mit einer zufälligen Verschlüsselung und Enclave-fähigen Schlüsseln verschlüsselt wurden, um die Leistung umfangreicher Abfragen (mit `LIKE` und Vergleichsoperatoren) zu verbessern. Weitere Informationen finden Sie unter [Always Encrypted mit Secure Enclaves](../relational-databases/security/encryption/always-encrypted-enclaves.md).
|Festlegen der Serverarbeitsspeicherwerte `MIN` und `MAX` beim Setup |Während des Setups können Sie die Serverarbeitsspeicherwerte festlegen. Verwenden Sie die Standardwerte, die berechneten empfohlenen Werte, oder geben Sie manuell eigene Werte an, wenn Sie die **empfohlene** Option [Serverkonfigurationsoptionen für den Serverarbeitsspeicher](../database-engine/configure-windows/server-memory-server-configuration-options.md#setting-the-memory-options-manually) ausgewählt haben.
|Neue Graphfunktion: `SHORTEST_PATH` | Verwenden Sie `SHORTEST_PATH` in `MATCH`, um den kürzesten Pfad zwischen zwei Knoten in einem Graph zu ermitteln oder beliebige Längentraversierungen durchzuführen.|
|Partitionstabellen und Indizes für Graphdatenbanken|Die Daten partitionierter Tabellen und Indizes werden in Einheiten aufgeteilt, die über mehrere Dateigruppen in einer Graphdatenbank verteilt sein können. |
|Neue Option für Indizes: `OPTIMIZE_FOR_SEQUENTIAL_KEY`|Diese Option aktiviert eine Optimierung in der Datenbank-Engine, die den Durchsatz für Einfügevorgänge mit hoher Parallelität in den Index verbessert. Diese Option ist für Indizes vorgesehen, die anfällig für Konflikte durch Einfügevorgänge auf der letzten Seite sind. Dieser Fall tritt häufig bei Indizes mit fortlaufendem Schlüssel auf. Dazu zählen beispielsweise Identitätsspalten, Sequenzspalten oder Spalten für Datum und Uhrzeit. Weitere Informationen finden Sie unter [CREATE INDEX](../t-sql/statements/create-index-transact-sql.md#sequential-keys).|
| &nbsp; | &nbsp; |

### <a name="sql-server-on-linux"></a>SQL Server unter Linux

| Neue Funktion oder Update | Details |
|:-----|:-----|
| Tempdb-Verbesserungen | Standardmäßig erstellt eine neue Installation von SQL Server für Linux mehrere tempdb-Datendateien, deren Anzahl sich nach der Anzahl der logischen Kerne richtet (bis zu acht Datendateien). Das gilt nicht für direkte Upgrades der Neben- oder Hauptversion. Jede tempdb-Datei ist 8 MB groß und wird automatisch um 64 MB vergrößert. Dieses Verhalten ähnelt dem der SQL Server-Standardinstallation unter Windows. |
| &nbsp; | &nbsp; |

## <a name="ctp-30-may-2019"></a>CTP 3.0 (Mai 2019)

### <a name="big-data-clusters"></a>Big Data-Cluster

| Neue Funktion oder Update | Details |
|:---|:---|
| **mssqlctl**-Updates | Mehrere [Updates für den Befehl **mssqlctl** und seine Parameter](../big-data-cluster/reference-mssqlctl.md). Dies umfasst ein Update für den Befehl **mssqlctl login**, der nun den Controllerbenutzernamen und -endpunkt zum Ziel hat. |
| Speichererweiterungen | Unterstützung für verschiedene Speicherkonfigurationen für Protokolle und Daten. Darüber hinaus wurde die Anzahl der Ansprüche von persistentem Volume für einen Big Data-Cluster gesenkt. |
| Mehrere Computepoolinstanzen | Unterstützung für mehrere Computepoolinstanzen. |
| Neues Poolverhalten und neue Poolfunktionen | Der Computepool wird jetzt standardmäßig für Speicherpool- und Datenpoolvorgänge ausschließlich in einer **ROUND_ROBIN**-Verteilung verwendet. Der Datenpool kann nun einen neuen Verteilungstyp **REPLICATED** verwenden, was bedeutet, dass dieselben Daten in allen Datenpoolinstanzen vorhanden sind. |
| Verbesserungen externer Tabellen | Externe Tabellen des HADOOP-Datenquellentyps unterstützen nun das Lesen von Zeilen mit einer Größe von bis zu 1 MB. Externe Tabellen (ODBC, Speicherpool, Datenpool) unterstützen jetzt Zeilen mit der Breite einer SQL Server-Tabelle. |
| &nbsp; | &nbsp; |

### <a name="database-engine"></a>Datenbank-Engine

| Neue Funktion oder Update | Details |
|:---|:---|
|SQL Server-Spracherweiterungen – [Java-Spracherweiterung](https://docs.microsoft.com/sql/language-extensions/language-extensions-overview)|Das [Microsoft-SDK für Java-Erweiterung für Microsoft SQL Server](https://docs.microsoft.com/sql/language-extensions/how-to/extensibility-sdk-java-sql-server) ist jetzt Open Source und [auf GitHub verfügbar](https://github.com/microsoft/sql-server-language-extensions).|
|Registrieren externer Sprachen|In einer neuen DDL, `CREATE EXTERNAL LANGUAGE`, werden externe Sprachen (z.B. Java) in SQL Server registriert. Informationen finden Sie unter [CREATE EXTERNAL LANGUAGE](../t-sql/statements/create-external-language-transact-sql.md). |
|Mehr unterstützte Datentypen für Java|Informationen finden Sie unter [Java-Datentypen](../language-extensions/how-to/java-to-sql-data-types.md).|
|Angepasste Erfassungsrichtlinie für den Abfragespeicher|Bei Aktivierung stehen zusätzliche Abfragespeicherkonfigurationen unter einer neuen Einstellung für die Erfassungsrichtlinie des Abfragespeichers zur Verfügung, um die Datensammlung auf einem bestimmten Server zu optimieren. Weitere Informationen finden Sie unter [ALTER DATABASE SET-Optionen](../t-sql/statements/alter-database-transact-sql-set-options.md).|
|[In-Memory-Datenbank](../relational-databases/in-memory-database.md) fügt neue DDL-Syntax zum Steuern des hybriden Pufferpools hinzu. <sup>2</sup>|Mit dem [hybriden Pufferpool](../database-engine/configure-windows/hybrid-buffer-pool.md) kann bei Bedarf direkt auf Datenbankseiten in Datenbankdateien zugegriffen werden, die sich auf einem Gerät mit beständigem Arbeitsspeicher (PMEM) befinden.|
|Neue In-Memory-Datenbankfunktion, speicheroptimierte tempdb-Metadaten hinzugefügt.|Informationen finden Sie unter [Speicheroptimierte TempDB-Metadaten](../relational-databases/databases/tempdb-database.md#memory-optimized-tempdb-metadata).|
|Verbindungsserver unterstützen UTF-8-Zeichencodierung. |[Collation and Unicode Support](../relational-databases/collations/collation-and-unicode-support.md) |
|Der Sortierungsname „BIN2_UTF8“ wurde in „Latin1_General_100_BIN2_UTF8“ geändert. |[Collation and Unicode Support](../relational-databases/collations/collation-and-unicode-support.md) |
|Das SQL Server-Setup umfasst MaxDOP-Empfehlungen, die auf dokumentierten Richtlinien basieren. |[Konfigurieren der Serverkonfigurationsoption Max. Grad an Parallelität](../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md#Guidelines)|
|`sys.dm_exec_query_plan_stats` gibt mehr Informationen zum Grad der Parallelität und Speicherzuweisungen für Abfragepläne zurück. |[sys.dm_exec_query_plan_stats](../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-stats-transact-sql.md)<sup>1</sup>|
| &nbsp; | &nbsp; |

><sup>1</sup> Dies ist eine optionale Funktion, für die das [Ablaufverfolgungsflag](../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 2451 aktiviert sein muss.
>
><sup>2</sup> Es ist kein Ablaufverfolgungsflag mehr zum Aktivieren des hybriden Pufferpools erforderlich.

### [!INCLUDE[master-data-services](../includes/ssmdsshort-md.md)]

| Neue Funktion oder Update | Details |
|:---|:---|
|[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] [!INCLUDE[master-data-services](../includes/ssmdsshort-md.md)] unterstützt Datenbanken mit verwalteter Azure SQL-Datenbank-Instanz.| Hosten von [!INCLUDE[master-data-services](../includes/ssmdsshort-md.md)] auf einer verwalteten Instanz. Informationen finden Sie unter [[!INCLUDE[master-data-services](../includes/ssmdsshort-md.md)]-Installation und -Konfiguration](../master-data-services/master-data-services-installation-and-configuration.md#SetUpWeb).
| &nbsp; | &nbsp; |

### <a name="analysis-services"></a>Analysis Services

| Neue Funktion oder Update | Details |
|:---|:---|
|Unterstützung von MDX-Abfragen für tabellarische Modelle mit Berechnungsgruppen |In dieser Version wird die frühere Beschränkung in [Berechnungsgruppen](#calc-ctp24) aufgehoben. |
|Dynamische Formatierung von Measures mithilfe von Berechnungsgruppen |Mit dieser Funktion können Sie Formatzeichenfolgen für Measures mit [Berechnungsgruppen](#calc-ctp24) bedingt ändern. Beispielsweise kann mit der Währungsumrechnung ein Measure in verschiedenen Fremdwährungsformaten angezeigt werden.|
| &nbsp; | &nbsp; |

## <a name="ctp-25-april-2019"></a>CTP 2.5 (April 2019)

### <a name="big-data-clusters"></a>Big Data-Cluster

| Neue Funktion oder Update | Details |
|:---|:---|
| Bereitstellungsprofile | Verwenden Sie für die Bereitstellung von Big Data-Clustern standardmäßige und benutzerdefinierte [Konfigurationsdateien für die JSON-Bereitstellung](../big-data-cluster/deployment-guidance.md#configfile) anstelle von Umgebungsvariablen. |
| Bereitstellungen mit Aufforderung | `mssqlctl cluster create` ruft jetzt zu allen erforderlichen Einstellungen für Standardbereitstellungen auf. |
| Änderungen bei Dienstendpunkten und Podnamen | Weitere Informationen finden Sie unter [Versionshinweise zu Big Data-Clustern](../big-data-cluster/release-notes-big-data-cluster.md). |
| Verbesserungen bei **mssqlctl** | Verwenden Sie **mssqlctl** zum [Auflisten externer Endpunkte](../big-data-cluster/deployment-guidance.md#endpoints) und zum Überprüfen der Version von **mssqlctl** mithilfe des Parameters `--version`. |
| Offlineinstallation | [Anleitung für Offlinebereitstellungen von Big Data-Clustern](../big-data-cluster/deploy-offline.md) |
| Verbesserungen bei HDFS-Tiering | HDFS-Tiering für Amazon S3-Speicher. OAuth-Unterstützung für ADLS Gen2. Zwischenspeicherfunktionen für eine bessere Leistung. Weitere Informationen finden Sie unter [HDFS-Tiering](../big-data-cluster/hdfs-tiering.md). |
| Connector zu SQL Server aus Spark | [Read and write to SQL Server from Spark using the MSSQL JDBC Connector (Lesen und Schreiben in SQL Server aus Spark mithilfe des MSSQL JDBC-Connectors)](../big-data-cluster/spark-mssql-connector.md) |
| &nbsp; | &nbsp; |

### <a name="database-engine"></a>Datenbank-Engine

| Neue Funktion oder Update | Details |
|:---|:---|
| PolyBase unter Linux | [Installieren Sie PolyBase](../relational-databases/polybase/polybase-linux-setup.md) für Nicht-Hadoop-Connectors unter Linux.<br/><br/>[PolyBase type mapping (Typzuordnung mit PolyBase)](../relational-databases/polybase/polybase-type-mapping.md) |
| Neues Java SDK für SQL Server | Vereinfacht die Entwicklung von Java-Programmen, die von SQL Server ausgeführt werden können. Weitere Informationen finden Sie unter [What's new in SQL Server Machine Learning Services (Neuerungen in SQL Server-Machine Learning Services)](../advanced-analytics/what-s-new-in-sql-server-machine-learning-services.md). |
| Bereich der Pläne wurde erweitert, die in der DMF `sys.dm_exec_query_plan_stats` verfügbar sind |Weitere Informationen finden Sie unter [sys.dm_exec_query_plan_stats](../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-stats-transact-sql.md)<sup>1</sup>.|
| Neue datenbankweite Konfiguration von `LAST_QUERY_PLAN_STATS` zur Aktivierung von `sys.dm_exec_query_plan_stats` |Weitere Informationen finden Sie unter [ALTER DATABASE SCOPED CONFIGURATION](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md).|
| Neue SRIDs (Spatial Reference Identifiers) |Das [australische GDA2020](http://www.ga.gov.au/scientific-topics/positioning-navigation/geodesy/datums-projections/gda2020) stellt robustere und genauere Datumsangaben bereit, die stärker an GPS-Systemen ausgerichtet sind. Die neuen SRIDs sind:<br/><br/> 7843: geografisches 2D-CRS<br/> 7844: geografisches 3D-CRS <br/><br/>Die Ansicht von [sys.spatial_reference_systems](../relational-databases/system-catalog-views/sys-spatial-reference-systems-transact-sql.md) enthält die Definitionen der neuen SRIDs. |
| &nbsp; | &nbsp; |

><sup>1</sup> Dies ist eine optionale Funktion, für die das [Ablaufverfolgungsflag](../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 2451 aktiviert oder die datenbankweite Konfiguration von `LAST_QUERY_PLAN_STATS` auf ON festgelegt sein muss.

## <a name="ctp-24-march-2019"></a>CTP 2.4 (März 2019)

### <a name="big-data-clusters"></a>Big Data-Cluster

| Neue Funktion oder Update | Details |
|:---|:---|
| Anleitung für die GPU-Unterstützung zum Ausführen von Deep Learning mit TensorFlow in Spark | Weitere Informationen finden Sie unter [Deploy a big data cluster with GPU support and run TensorFlow (Bereitstellen eines Big Data-Clusters mit GPU-Unterstützung und Ausführen von TensorFlow)](../big-data-cluster/spark-gpu-tensorflow.md). |
| Die Datenquellen **SqlDataPool** und **SqlStoragePool** werden nicht mehr standardmäßig erstellt. | Erstellen Sie diese nach Bedarf manuell. Weitere Informationen finden Sie im Abschnitt [Bekannte Probleme](../big-data-cluster/release-notes-big-data-cluster.md#externaltablesctp24). |
| Unterstützung von `INSERT INTO SELECT` für den Datenpool | Ein Beispiel finden Sie unter [Tutorial: Ingest data into a SQL Server data pool with Transact-SQL (Tutorial: Erfassen von Daten in einem SQL Server-Datenpool mit Transact-SQL)](../big-data-cluster/tutorial-data-pool-ingest-sql.md). |
| Optionen `FORCE SCALEOUTEXECUTION` und `DISABLE SCALEOUTEXECUTION` | Weitere Informationen finden Sie unter [Versionshinweise zu Big Data-Clustern](../big-data-cluster/release-notes-big-data-cluster.md#whats-new).|
| Aktualisierte Bereitstellungsempfehlungen für AKS | Für die Auswertung von Big Data-Clustern in AKS wird die Verwendung eines einzelnen Knotens der Größe **Standard_L8s** empfohlen. |
| Upgrade der Spark-Runtime auf Spark 2.4 | |
| &nbsp; | &nbsp; |

### <a name="database-engine"></a>Datenbank-Engine

| Neue Funktion oder Update | Details |
|:-----|:-----|
|Fehlermeldungen für die Kürzung enthalten standardmäßig die Tabellen- und Spaltennamen sowie den gekürzten Wert.|[VERBOSE_TRUNCATION_WARNINGS](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md#verbose-truncation)|
|Die neue dynamische Verwaltungsfunktion `sys.dm_exec_query_plan_stats` gibt das Äquivalent des letzten bekannten tatsächlichen Ausführungsplans für die meisten Abfragen zurück. |[sys.dm_exec_query_plan_stats](../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-stats-transact-sql.md)<sup>1</sup>|
|Im Gegensatz zum Ereignis `query_post_execution_showplan`, das die Standardprofilerstellung nutzt, erfasst das neue erweiterte Ereignis `query_post_execution_plan_profile` das Äquivalent eines tatsächlichen Ausführungsplans mithilfe einfacher Profilerstellung. |[Query profiling infrastructure (Profilerstellungsinfrastruktur für Abfragen)](../relational-databases/performance/query-profiling-infrastructure.md)|
|Anhalten und Fortsetzen des TDE-Scans (Transparent Data Encryption)|[TDE-Überprüfung (Transparent Data Encryption): Anhalten und Fortsetzen](../relational-databases/security/encryption/transparent-data-encryption.md#scan-suspend-resume)|
| &nbsp; | &nbsp; |

><sup>1</sup> Dies ist eine optionale Funktion, für die das [Ablaufverfolgungsflag](../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 2451 aktiviert sein muss.

### <a name="sql-server-analysis-services-ssas"></a>SQL Server Analysis Services (SSAS)

| Neue Funktion oder Update | Details |
|:-----|:-----|
|m:n-Beziehungen in tabellarischen Modellen|[m:n-Beziehungen in tabellarischen Modellen](#many-to-many-ctp24)|
|Eigenschafteneinstellungen für die Ressourcenkontrolle|[Eigenschafteneinstellungen für die Ressourcenkontrolle](#property-ctp24)|
| &nbsp; | &nbsp; |

## <a name="ctp-23-february-2019"></a>CTP 2.3 (Februar 2019)

### <a name="big-data-clusters"></a>Big Data-Cluster

| Neue Funktion oder Update | Details |
| :---------- | :------ |
| Übermitteln von Spark-Aufträgen an Big Data-Cluster in IntelliJ | [Submit Spark jobs on SQL Server big data clusters in IntelliJ (Übermitteln von Spark-Aufträgen an Big Data-Cluster von SQL Server in IntelliJ)](../big-data-cluster/spark-submit-job-intellij-tool-plugin.md) |
| Allgemeine CLI für die Anwendungsbereitstellung und Clusterverwaltung | [How to deploy an app on SQL Server 2019 big data cluster (preview) (Vorgehensweise: Bereitstellen einer App in Big Data-Clustern von SQL Server 2019 (Vorschau))](../big-data-cluster/big-data-cluster-create-apps.md) |
| VS Code-Erweiterung zum Bereitstellen von Anwendungen in einem Big Data-Cluster | [How to use VS Code to deploy applications to SQL Server big data clusters (Vorgehensweise: Verwenden von VS Code zum Bereitstellen von Anwendungen in Big Data-Clustern von SQL Server)](../big-data-cluster/app-deployment-extension.md) |
| Änderungen an der Befehlssyntax des Tools **mssqlctl** | Weitere Informationen finden Sie unter [Bekannte Probleme bei „mssqlctl“](../big-data-cluster/release-notes-big-data-cluster.md ). |
| Verwenden von „Sparklyr“ in Big Data-Clustern | [Use Sparklyr in SQL Server 2019 big data cluster (Verwenden von Sparklyr in Big Data-Clustern von SQL Server 2019)](../big-data-cluster/sparklyr-from-RStudio.md) |
| Einbinden von externen HDFS-kompatiblen Speichern (Hadoop Distributed File System) in Big Data-Clustern mit dem **HDFS-Tiering** | Weitere Informationen finden Sie unter [HDFS-Tiering](../big-data-cluster/hdfs-tiering.md). |
| Neue einheitliche Verbindungsoberfläche für die SQL Server-Masterinstanz und das HDFS-/Spark-Gateway | Weitere Informationen finden Sie unter [SQL Server master instance and the HDFS/Spark Gateway (Die SQL Server-Masterinstanz und das HDFS-/Spark-Gateway)](../big-data-cluster/connect-to-big-data-cluster.md). |
| Beim Löschen eines Clusters mit **mssqlctl cluster delete** werden jetzt nur noch die Objekte im Namespace gelöscht, die Teil des Big Data-Clusters waren. | Der Namespace wird nicht gelöscht. In früheren Releases wurde mit diesem Befehl jedoch nicht der gesamte Namespace gelöscht. |
| Namen von _Sicherheitsendpunkten_ wurden geändert und zusammengefasst | **service-security-lb** und **service-security-nodeport** wurden im Endpunkt **endpoint-security** zusammengefasst. |
| Namen von _Proxyendpunkten_ wurden geändert und zusammengefasst | **service-proxy-lb** und **service-proxy-nodeport** wurden im Endpunkt **endpoint-service-proxy** zusammengefasst. |
| Namen von _Controllerendpunkten_ wurden geändert und zusammengefasst | **service-mssql-controller-lb** und **service-mssql-controller-nodeport** wurden im Endpunkt **endpoint-controller** zusammengefasst. |
| &nbsp; | &nbsp; |

### <a name="database-engine"></a>Datenbank-Engine

| Neue Funktion oder Update | Details |
|:-----|:-----|
|Verbesserte Wiederherstellung von Datenbanken kann für einzelne Datenbanken aktiviert werden| [Verbesserte Wiederherstellung von Datenbanken](../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md#adr)|
|Durch den Abfragespeicherplan erzwungene Unterstützung für schnelle Vorwärts- und statische Cursor|[Erzwingen eines Plans für schnelle Vorwärts- und statische Cursor](../relational-databases/performance/monitoring-performance-by-using-the-query-store.md#ctp23) |
|Weniger Neukompilierungen für Workloads mit temporären Tabellen für mehrere Bereiche |[Weniger Neukompilierungen für Workloads](../relational-databases/tables/tables.md#ctp23) |
|Verbesserte Skalierbarkeit indirekter Prüfpunkte |[Verbesserte Skalierbarkeit indirekter Prüfpunkte](../relational-databases/logs/database-checkpoints-sql-server.md#ctp23)|
|Unterstützung für die Verwendung von UTF-8-Zeichencodierung mit BIN2-Sortierung (`UTF8_BIN2`) wurde hinzugefügt |[Collation and Unicode Support](../relational-databases/collations/collation-and-unicode-support.md) |
|Definieren von kaskadierenden Löschaktionen für eine Edgeeinschränkung in einer Graphdatenbank |[Edgeeinschränkungen](../relational-databases/tables/graph-edge-constraints.md) |
|Aktivieren oder Deaktivieren von `LIGHTWEIGHT_QUERY_PROFILING` mit der neuen datenbankweiten Konfiguration |[`LIGHTWEIGHT_QUERY_PROFILING`](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md#lqp) |
| &nbsp; | &nbsp; |

### <a name="tools"></a>Tools

| Neue Funktion oder Update | Details |
|:-----|:-----|
|Azure Data Studio unterstützt Azure Active Directory |[Azure Data Studio](../azure-data-studio/what-is.md) |
|Die Benutzeroberfläche für das Anzeigen von Notebooks wurde in Azure Data Studio verschoben. |[How to manage notebooks in Azure Data Studio (Vorgehensweise: Verwalten von Notebooks in Azure Data Studio)](../big-data-cluster/notebooks-how-to-manage.md) |
|Ein neuer Assistent zum Erstellen externer Datenquellen von HDFS (Hadoop Distributed File System) in Big Data-Clustern von SQL Server wurde hinzugefügt. | [Tools](#tools-ctp23)|
|Verbesserte Benutzeroberfläche für das Anzeigen von Notebooks. | [Tools](#tools-ctp23) |
|Neue Notebook-APIs wurden hinzugefügt.| [Tools](#tools-ctp23) |
|Der Befehl „“ wurde zur Unterstützung beim Aktualisieren von Python-Paketen hinzugefügt. | [Tools](#tools-ctp23) |
|Ermöglicht das Starten von Azure Data Studio über SSMS| [Tools](#tools-ctp23) |
| &nbsp; | &nbsp; |

### <a name="analysis-services"></a>Analysis Services

| Neue Funktion oder Update | Details |
|:-----|:-----|
|Berechnungsgruppen in einem tabellarischen Modell| [Berechnungsgruppen in einem tabellarischen Modell](#calc-ctp24) |
| &nbsp; | &nbsp; |

## <a name="ctp-22-december-2018"></a>CTP 2.2 (Dezember 2018)

### <a name="big-data-clusters"></a>Big Data-Cluster

| Neue Funktion oder Update | Details |
|:-----|:-----|
|Verwenden von SparkR von Azure Data Studio in einem Big Data-Cluster | |
|Bereitstellen von Python- und R-Apps|[Deploy applications using mssqlctl (Bereitstellen von Anwendungen mit „mssqlctl“)](../big-data-cluster/big-data-cluster-create-apps.md) |
| &nbsp; | &nbsp; |

### <a name="database-engine"></a>Datenbank-Engine

| Neue Funktion oder Update | Details |
|:-----|:-----|
|Unterstützung für die Verwendung von UTF-8-Zeichencodierung mit SQL Server-Replikation wurde hinzugefügt |[Collation and Unicode Support](../relational-databases/collations/collation-and-unicode-support.md#ctp23) |
| &nbsp; | &nbsp; |


### <a name="sql-server-on-linux"></a>SQL Server unter Linux

| Neue Funktion oder Update | Details |
|:-----|:-----|
|Always On-Verfügbarkeitsgruppe in Docker-Containern mit Kubernetes |[Always On Availability Groups for containers (Always On-Verfügbarkeitsgruppen für Container)](../linux/sql-server-ag-kubernetes.md) |
| &nbsp; | &nbsp; |

## <a name="ctp-21-november-2018"></a>CTP 2.1 (November 2018)

### <a name="database-engine"></a>Datenbank-Engine

| Neue Funktion oder Update | Details |
|:-----|:-----|
|Unterstützung für die Auswahl der UTF-8-Sortierung als Standard während des Setups von [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] wurde hinzugefügt |[Collation and Unicode Support](../relational-databases/collations/collation-and-unicode-support.md#ctp23) |
|Inlining benutzerdefinierter Skalarfunktionen wandelt die entsprechenden Funktionen automatisch in relationale Ausdrücke um und bettet sie in die aufrufende SQL-Abfrage ein |[Inlining benutzerdefinierter Skalarfunktionen](../relational-databases/user-defined-functions/scalar-udf-inlining.md) |
|Die Spalte `command` der dynamischen Verwaltungssicht `sys.dm_exec_requests` zeigt `SELECT (STATMAN)` an, wenn ein `SELECT`-Objekt darauf wartet, dass ein synchroner Statistikupdatevorgang abgeschlossen wird, bevor die Abfrage weiter ausgeführt wird. | [`sys.dm_exec_requests`](../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md) |
|Neuer Wartetyp `WAIT_ON_SYNC_STATISTICS_REFRESH` wird in der dynamischen Verwaltungssicht `sys.dm_os_wait_stats` angezeigt. Er zeigt die kumulierte Zeit auf Instanzebene für synchrone Statistikaktualisierungen an.|[`sys.dm_os_wait_stats`](../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md) |
|Der hybride Pufferpool ist eine neue Funktion der SQL Server-Datenbank-Engine, mit der Sie bei Bedarf direkt auf Datenbankseiten in Datenbankdateien zugreifen können, die sich auf einem Gerät mit beständigem Arbeitsspeicher (PMEM) befinden.|[Hybrider Pufferpool](../database-engine/configure-windows/hybrid-buffer-pool.md) |
|Verwenden von abgeleiteten Tabellen- oder Ansichtsaliasen in Graphabgleichsabfragen |[Graph-Edgeeinschränkungen](../relational-databases/tables/graph-edge-constraints.md) |
| &nbsp; | &nbsp; |

### <a name="sql-server-on-linux"></a>SQL Server unter Linux

| Neue Funktion oder Update | Details |
|:-----|:-----|
|Neue Containerregistrierung für SQL Server |[Get started with SQL Server containers on Docker (Erste Schritte mit SQL Server-Containern unter Docker)](../linux/quickstart-install-connect-docker.md) |
| &nbsp; | &nbsp; |

### <a name="tools"></a>Tools

| Neue Funktion oder Update | Details |
|:-----|:-----|
|[Azure Data Studio](../azure-data-studio/what-is.md) unterstützt das Verbinden und Verwalten von Big Data-Clustern von [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]. | |
| &nbsp; | &nbsp; |

## <a name="ctp-20-october-2018"></a>CTP 2.0 (Oktober 2018)

### <a name="big-data-clusters"></a>Big Data-Cluster

| Neue Funktion oder Update | Details |
|:-----|:-----|
|Bereitstellen eines Big Data-Clusters mit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]- und Spark-Linux-Containern in Kubernetes | |
|Zugriff auf Big Data über HDFS | |
|Ausführen von erweiterten Analysen und Machine Learning-Vorgängen mit Spark | |
|Streamen von Daten an SQL Server-Datenpools mit Spark | |
|Ausführen von Abfragebüchern zur Bereitstellung einer Notebookumgebung in **Azure Data Studio**|[Datentechnik](../azure-data-studio/what-is.md#data-engineering)|
| &nbsp; | &nbsp; |

### <a name="database-engine"></a>Datenbank-Engine

| Neue Funktion oder Update | Details |
|:-----|:-----|
|Die Datenbank **COMPATIBILITY_LEVEL 150** wurde hinzugefügt. |[ALTER DATABASE-Kompatibilitätsgrad (Transact-SQL)](../t-sql/statements/alter-database-transact-sql-compatibility-level.md) |
|Erstellen von fortsetzbaren Onlineindizes|[CREATE INDEX (Transact-SQL)](../t-sql/statements/create-index-transact-sql.md#resumable-indexes) |
|Feedback zur Speicherzuweisung im Zeilenmodus |[Feedback zur Speicherzuweisung im Zeilenmodus](../relational-databases/performance/intelligent-query-processing.md#row-mode-memory-grant-feedback) |
|Geschätzte `COUNT DISTINCT`-Werte|[Geschätzte Abfrageverarbeitung](../relational-databases/performance/intelligent-query-processing.md#approximate-query-processing)|
|Batchmodus bei Rowstore|[Batchmodus bei Rowstore](../relational-databases/performance/intelligent-query-processing.md#batch-mode-on-rowstore) |
|Verzögerte Kompilierung von Tabellenvariablen|[Verzögerte Kompilierung von Tabellenvariablen](../relational-databases/performance/intelligent-query-processing.md#table-variable-deferred-compilation) |
|Java-Spracherweiterung|[Java-Spracherweiterung](../advanced-analytics/java/extension-java.md) |
|Führen Sie Ihre aktuellen Graphdaten aus Knoten- oder Edgetabellen mithilfe der `MATCH`-Prädikate in der `MERGE`-Anweisung mit neuen Daten zusammen. | |
|Edgeeinschränkungen|[Graph-Edgeeinschränkungen](../relational-databases/tables/graph-edge-constraints.md) |
|Datenbankweite Standardeinstellung für Online- und fortsetzbare DDL-Vorgänge| |
|Verfügbarkeitsgruppen unterstützen bis zu fünf synchrone sekundäre Replikate|[Verfügbarkeitsgruppen](../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md) |
|Umleiten der Lese-/Schreibverbindungen vom sekundären zum primären Replikat|[Umleitung von Lese-/Schreibverbindungen vom sekundären zum primären Replikat (Always On-Verfügbarkeitsgruppen)](../database-engine/availability-groups/windows/secondary-replica-connection-redirection-always-on-availability-groups.md) |
|SQL-Datenermittlung und -klassifizierung| [SQL-Datenermittlung und -klassifizierung](../relational-databases/security/sql-data-discovery-and-classification.md) |
|Erweiterte Unterstützung für Geräte mit persistentem Speicher|[Hybrider Pufferpool](../database-engine/configure-windows/hybrid-buffer-pool.md) |
|Unterstützung für Columnstore-Statistiken in `DBCC CLONEDATABASE`|[Statistikblobs für Columnstore-Indizes](../t-sql/database-console-commands/dbcc-clonedatabase-transact-sql.md#ctp23)|
|`sp_estimate_data_compression_savings` führt `COLUMNSTORE` und `COLUMNSTORE_ARCHIVE` ein|[Überlegungen zu Columnstore-Indizes](../relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql.md#considerations-for-columnstore-indexes)|
|Machine Learning Services wird für Windows Server-Failovercluster unterstützt |[Neuerungen in SQL Server-Machine Learning Services](../advanced-analytics/what-s-new-in-sql-server-machine-learning-services.md)|
|Machine Learning-Unterstützung für die partitionsbasierte Modellierung|[Neuerungen in SQL Server-Machine Learning Services](../advanced-analytics/what-s-new-in-sql-server-machine-learning-services.md) |
|Standardmäßig aktivierte LWP-Abfrageinfrastruktur (Lightweight Profiling) |[Einfache Profilerstellungsinfrastruktur für die Abfrageausführungsstatistik v3](../relational-databases/performance/query-profiling-infrastructure.md#lightweight-query-execution-statistics-profiling-infrastructure-v3) |
|Neue PolyBase-Connectors für [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], Oracle, Teradata und MongoDB |[Was ist PolyBase?](../relational-databases/polybase/polybase-guide.md) |
|`sys.dm_db_page_info(database_id, file_id, page_id, mode)` gibt Informationen zu einer Seite in einer Datenbank zurück. |[sys.dm_db_page_info (Transact-SQL)](../relational-databases/system-dynamic-management-views/sys-dm-db-page-info-transact-sql.md)|
|Always Encrypted mit Secure Enclaves |[Always Encrypted mit Secure Enclaves](../relational-databases/security/encryption/always-encrypted-enclaves.md) |
|Erstellen und Neuerstellen eines gruppierten Columnstore-Onlineindex |[Ausführen von Onlineindexvorgängen](../relational-databases/indexes/perform-index-operations-online.md) |
| &nbsp; | &nbsp; |

### <a name="sql-server-on-linux"></a>SQL Server unter Linux

| Neue Funktion oder Update | Details |
|:-----|:-----|
|Replikationsunterstützung |[SQL Server Replication on Linux (SQL Server-Replikation unter Linux)](../linux/sql-server-linux-replication.md)
|Unterstützung für den Microsoft Distributed Transaction Coordinator (MSDTC) |[How to configure MSDTC on Linux (Vorgehensweise: Konfigurieren von MSDTC unter Linux)](../linux/sql-server-linux-configure-msdtc.md) |
|OpenLDAP-Unterstützung für AD-Drittanbieter |[Tutorial: Use Active Directory authentication with SQL Server on Linux (Tutorial: Verwenden der Azure Active Directory-Authentifizierung mit SQL Server unter Linux)](../linux/sql-server-linux-active-directory-authentication.md) |
|Machine Learning unter Linux |[Configure Machine Learning on Linux (Konfigurieren von Machine Learning unter Linux)](../linux/sql-server-linux-setup-machine-learning.md) |
| &nbsp; | &nbsp; |

### <a name="master-data-services"></a>Master Data Services

| Neue Funktion oder Update | Details |
|:-----|:-----|
|Das MDS-Portal (Master Data Services) ist nicht mehr von Silverlight abhängig.| Alle veralteten Silverlight-Komponenten wurden durch HTML-Steuerelemente ersetzt.|
| &nbsp; | &nbsp; |

### <a name="security"></a>Security

| Neue Funktion oder Update | Details |
|:-----|:-----|
|Zertifikatverwaltung im SQL Server-Konfigurations-Manager|[Zertifikatverwaltung (SQL Server-Konfigurations-Manager)](../database-engine/configure-windows/manage-certificates.md)
| &nbsp; | &nbsp; |

### <a name="tools"></a>Tools

| Neue Funktion oder Update | Details |
|:-----|:-----|
|[Azure Data Studio](../azure-data-studio/what-is.md) unterstützt das Verbinden und Verwalten von Big Data-Clustern von [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]. |[What is Azure Data Studio (Was ist Azure Data Studio?)](../azure-data-studio/what-is.md)|
|Unterstützung für Szenarios mit Big Data-Clustern von SQL Server |[Erweiterung von SQL Server 2019 (Vorschau)](../azure-data-studio/sql-server-2019-extension.md)|
|[**SQL Server Management Studio (SSMS) 18.0 (Vorschauversion):** ](../ssms/sql-server-management-studio-ssms.md) Unterstützt [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]| |
|Unterstützung für Always Encrypted mit Secure Enclaves |[Always Encrypted mit Secure Enclaves](../relational-databases/security/encryption/always-encrypted-enclaves.md)|
| &nbsp; | &nbsp; |


## <a name="other-services"></a>Weitere Dienste

Ab CTP 2.4 werden für [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] keine neuen Features für die folgenden Dienste mehr eingeführt:

- [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] (SSIS)
- [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] (SSRS)

## <a name="details"></a>Details

### <a id="bigdatacluster"></a>Big Data-Cluster

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] [Big Data-Cluster](../big-data-cluster/big-data-cluster-overview.md) ermöglichen neue Szenarios wie die Folgenden:

- [GPU-Unterstützung zum Ausführen von Deep Learning mit TensorFlow in Spark](../big-data-cluster/spark-gpu-tensorflow.md) (CTP 2.4)
- Upgrade der Spark-Runtime auf Spark 2.4 (CTP 2.4)
- Unterstützung von `INSERT INTO SELECT` für den Datenpool (CTP 2.4)
- Optionsklauseln `FORCE SCALEOUTEXECUTION` und `DISABLE SCALEOUTEXECUTION` für Abfragen für externe Tabellen (CTP 2.4)
- [Übermitteln von Spark-Aufträgen an Big Data-Cluster von [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] in IntelliJ](../big-data-cluster/spark-submit-job-intellij-tool-plugin.md) (CTP 2.3)
- [Bereitstellen von Anwendungen und Verwalten der Benutzeroberfläche](../big-data-cluster/big-data-cluster-create-apps.md) für viele datenbezogene Apps, einschließlich dem Operationalisieren von Machine Learning-Modellen mithilfe von R und Python sowie der Ausführung von SSIS-Aufträgen (SQL Server Integration Services) und mehr (CTP 2.3)
- [Verwenden von Sparklyr in Big Data-Clustern von [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]](../big-data-cluster/sparklyr-from-RStudio.md) (CTP 2.3)
- Einbinden von externen HDFS-kompatiblen Speichern (Hadoop Distributed File System) in Big Data-Clustern mit dem [HDFS-Tiering](../big-data-cluster/hdfs-tiering.md) (CTP 2.3)
- Verwenden von SparkR von Azure Data Studio in einem Big Data-Cluster (CTP 2.2)
- [Bereitstellen von Python- und R-Apps](../big-data-cluster/big-data-cluster-create-apps.md) (CTP 2.2)
- Bereitstellen eines Big Data-Clusters mit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]- und Spark-Linux-Containern in Kubernetes (CTP 2.0)
- Zugriff auf Big Data über HDFS (CTP 2.0)
- Ausführen von erweiterten Analysen und Machine Learning-Vorgängen mit Spark (CTP 2.0)
- Streamen von Daten an SQL Server-Datenpools mit Spark (CTP 2.0)
- Ausführen von Abfragebüchern zur Bereitstellung einer Notebookumgebung in [**Azure Data Studio**](../sql-operations-studio/what-is.md) (CTP 2.0)
 
[!INCLUDE [Big data clusters preview](../includes/big-data-cluster-preview-note.md)]

### <a id="databaseengine"></a> Datenbank-Engine

Mit [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] werden die folgenden neuen Features für die [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] eingeführt oder verbessert.

#### <a name="new-query_post_execution_plan_profile-extended-event-ctp-24"></a>Neues erweitertes Ereignis query_post_execution_plan_profile (CTP 2.4)

Im Gegensatz zum Ereignis `query_post_execution_showplan`, das die Standardprofilerstellung nutzt, erfasst das neue erweiterte Ereignis `query_post_execution_plan_profile` das Äquivalent eines tatsächlichen Ausführungsplans mithilfe einfacher Profilerstellung. Weitere Informationen finden Sie unter [Profilerstellungsinfrastruktur für Abfragen](../relational-databases/performance/query-profiling-infrastructure.md).

##### <a name="example-1---extended-event-session-using-standard-profiling"></a>Beispiel 1: Erweiterte Ereignissitzung mit der Standardprofilerstellung

```sql
CREATE EVENT SESSION [QueryPlanOld] ON SERVER 
ADD EVENT sqlserver.query_post_execution_showplan(
    ACTION(sqlos.task_time, sqlserver.database_id, 
    sqlserver.database_name, sqlserver.query_hash_signed, 
    sqlserver.query_plan_hash_signed, sqlserver.sql_text))
ADD TARGET package0.event_file(SET filename = N'C:\Temp\QueryPlanStd.xel')
WITH (MAX_MEMORY=4096 KB, EVENT_RETENTION_MODE=ALLOW_SINGLE_EVENT_LOSS, 
    MAX_DISPATCH_LATENCY=30 SECONDS, MAX_EVENT_SIZE=0 KB, 
    MEMORY_PARTITION_MODE=NONE, TRACK_CAUSALITY=OFF, STARTUP_STATE=OFF);
```

##### <a name="example-2---extended-event-session-using-lightweight-profiling"></a>Beispiel 2: Erweiterte Ereignissitzung mit der einfachen Profilerstellung

```sql
CREATE EVENT SESSION [QueryPlanLWP] ON SERVER 
ADD EVENT sqlserver.query_post_execution_plan_profile(
    ACTION(sqlos.task_time, sqlserver.database_id, 
    sqlserver.database_name, sqlserver.query_hash_signed, 
    sqlserver.query_plan_hash_signed, sqlserver.sql_text))
ADD TARGET package0.event_file(SET filename=N'C:\Temp\QueryPlanLWP.xel')
WITH (MAX_MEMORY=4096 KB, EVENT_RETENTION_MODE=ALLOW_SINGLE_EVENT_LOSS, 
    MAX_DISPATCH_LATENCY=30 SECONDS, MAX_EVENT_SIZE=0 KB, 
    MEMORY_PARTITION_MODE=NONE, TRACK_CAUSALITY=OFF, STARTUP_STATE=OFF);
```

#### <a name="new-dmf-sysdm_exec_query_plan_stats-ctp-24"></a>Die neue dynamische Verwaltungsfunktion sys.dm_exec_query_plan_stats (CTP 2.4) 

Die neue dynamische Verwaltungsfunktion `sys.dm_exec_query_plan_stats` gibt das Äquivalent des letzten bekannten tatsächlichen Ausführungsplans für die meisten Abfragen basierend auf der einfachen Profilerstellung zurück. Weitere Informationen finden Sie in den Artikeln zu [sys.dm_exec_query_plan_stats](../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-stats-transact-sql.md) und der [Profilerstellungsinfrastruktur für Abfragen](../relational-databases/performance/query-profiling-infrastructure.md). Sehen Sie sich als Beispiel das folgende Skript an:

```sql
SELECT *
FROM sys.dm_exec_cached_plans
CROSS APPLY sys.dm_exec_query_plan_stats(plan_handle)
WHERE objtype ='Trigger';
GO
```

Hierbei handelt es sich um ein optionales Feature, für das das [Ablaufverfolgungsflag](../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 2451 aktiviert sein muss.

#### <a name="transparent-data-encryption-tde-scan---suspend-and-resume-ctp-24"></a>Anhalten und Fortsetzen des TDE-Scans (CTP 2.4)

[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] muss einen Verschlüsselungsscan durchführen, mit dem alle Seiten aus den Datendateien in den Pufferpool gelesen und die verschlüsselten Seiten dann auf den Datenträger geschrieben werden, um [Transparent Data Encryption (TDE)](../relational-databases/security/encryption/transparent-data-encryption.md) für eine Datenbank zu aktivieren. Mit [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] wurde die Syntax für das Anhalten und Fortsetzen des TDE-Scans eingeführt, mit der Sie den Scan während unternehmenskritischen Zeiten oder hoher Auslastung des Systems anhalten und später fortsetzen können, damit Benutzer über mehr Kontrolle über den Verschlüsselungsscan verfügen.

Verwenden Sie die folgende Syntax, um den TDE-Verschlüsselungsscan anzuhalten:

```sql
ALTER DATABASE <db_name> SET ENCRYPTION SUSPEND;
```

Auf ähnliche Weise können Sie den TDE-Verschlüsselungsscan mithilfe der folgenden Syntax fortsetzen:

```sql
ALTER DATABASE <db_name> SET ENCRYPTION RESUME;
```

`encryption_scan_state` wurde der dynamischen Verwaltungssicht `sys.dm_database_encryption_keys` hinzugefügt, um den aktuellen Status des Verschlüsselungsscans anzuzeigen. Außerdem wurde eine neue Spalte namens `encryption_scan_modify_date` hinzugefügt, die das Datum und die Uhrzeit der letzten Änderung des Status des Verschlüsselungsscans enthält. Beachten Sie außerdem, dass beim Start eine Meldung im Fehlerprotokoll protokolliert wird, die angibt, dass ein vorhandener Scan pausiert wurde, wenn die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Instanz neu gestartet wird, während der Verschlüsselungsscan angehalten ist.

#### <a name="accelerated-database-recovery-ctp-23"></a>Verbesserte Wiederherstellung von Datenbanken (CTP 2.3)

Durch die [verbesserte Wiederherstellung von Datenbanken](/azure/sql-database/sql-database-accelerated-database-recovery/) wird die Verfügbarkeit von Datenbanken enorm verbessert, insbesondere bei zeitintensiven Transaktionen. Hierfür wurde der Wiederherstellungsprozess der SQL Server-Datenbank-Engine vollständig überarbeitet. Die [Datenbankwiederherstellung](../relational-databases/logs/the-transaction-log-sql-server.md?#recovery-of-all-incomplete-transactions-when--is-started) wird von SQL Server für alle Datenbanken verwendet, damit diese Transaktionen im gleichen bzw. fehlerfreien Zustand starten. Eine Datenbank, für die die verbesserte Datenbankwiederherstellung aktiviert wurde, wird nach einem Failover oder einem nicht sauberen Herunterfahren deutlich schneller wiederhergestellt. In CTP 2.3 kann die verbesserte Datenbankwiederherstellung mit folgender Syntax für jede Datenbank einzeln aktiviert werden:

```sql
ALTER DATABASE <db_name> SET ACCELERATED_DATABASE_RECOVERY = {ON | OFF}
```

> [!NOTE]
> Sie benötigen diese Syntax nicht, um das Feature in Azure SQL-Datenbank zu verwenden. Es wurde [auf Wunsch in der öffentlichen Vorschauversion aktiviert](/azure/sql-database/sql-database-accelerated-database-recovery). Nach seiner Aktivierung ist das Feature standardmäßig aktiviert.

Wenn Sie kritische Datenbanken besitzen, die für große Transaktionen anfällig sind, können Sie dieses Feature während der Vorschauphase testen. Senden Sie Feedback an das [[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Team](<https://aka.ms/sqlfeedback>).

#### <a name="query-store-plan-forcing-support-for-fast-forward-and-static-cursors-ctp-23"></a>Durch den Abfragespeicherplan erzwungene Unterstützung für schnelle Vorwärtscursor und statischer Cursor (CTP 2.3)

Mit dem Abfragespeicher können Sie nun Abfrageausführungspläne für schnelle Vorwärtscursor und statische Cursor (T-SQL und API) erzwingen. Das Erzwingen kann über `sp_query_store_force_plan` oder über SQL Server Management Studio-Abfragespeicherberichte erfolgen.

#### <a name="reduced-recompilations-for-workloads-using-temporary-tables-across-multiple-scopes-ctp-23"></a>Weniger Neukompilierungen für Workloads mit temporären Tabellen für mehrere Bereiche (CTP 2.3)

Vor der Einführung dieses Features, konnte das Verweisen auf eine temporäre Tabelle mit einer DML-Anweisung (`SELECT`, `INSERT`, `UPDATE`, `DELETE`) zu einer Neukompilierung der DML-Anweisung bei jeder Ausführung führen, wenn die temporäre Tabelle in einem Batch im äußeren Bereich erstellt wurde. Durch dieses Update führt SQL Server zusätzliche einfache Überprüfungen durch, um unnötige Neukompilierungen zu vermeiden:

- Überprüfung, ob es sich bei dem Modul im äußeren Bereich, das zur Kompilierzeit zur Erstellung der temporären Tabelle verwendet wurde, um das gleiche Modul handelt, das für nachfolgende Ausführungen verwendet wurde 
- Nachverfolgung von Änderungen an der Datendefinitionssprache (Data Definition Language, DDL), die bei der ersten Kompilierung vorgenommen und Vergleich mit den DDL-Vorgängen für nachfolgende Ausführungen 

Dadurch können überflüssige Neukompilierungen vermieden und der CPU-Aufwand reduziert werden.

#### <a name="improved-indirect-checkpoint-scalability-ctp-23"></a>Verbesserter Skalierbarkeit indirekter Prüfpunkte (CTP 2.3)

In früheren Versionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] konnten Scheduler-Fehler ohne Ergebnis auftreten, wenn eine Datenbank viele modifizierte Seiten generiert hat (z.B. tempdb). In [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] wird die Skalierbarkeit für indirekte Prüfpunkte verbessert, um diese Fehler in Datenbanken zu vermeiden, die Workloads mit vielen UPDATE/INSERT-Vorgängen enthalten.

#### <a name="utf-8-support-ctp-23"></a>UTF-8-Unterstützung (CTP 2.3)

Vollständige Unterstützung für die weit verbreitete Zeichencodierung UTF-8 als Import- oder Exportcodierung oder als Sortierung für Textdaten auf Datenbank- oder Spaltenebene. UTF-8 ist für die Datentypen `CHAR` und `VARCHAR` zulässig und ist bei der Erstellung oder Änderung einer Objektsortierung in eine Sortierung mit dem Suffix `UTF8` aktiviert. 

Beispiel: `LATIN1_GENERAL_100_CI_AS_SC` in `LATIN1_GENERAL_100_CI_AS_SC_UTF8`. Die in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] eingeführte UTF-8-Codierung ist nur für Windows-Sortierungen verfügbar, die Sonderzeichen unterstützen. `NCHAR` und `NVARCHAR` lassen nur die UTF-16-Codierung zu und bleiben unverändert.

Dieses Feature kann abhängig von dem verwendeten Zeichensatz beträchtliche Speichereinsparungen ermöglichen. Die Änderung eines vorhandenen Spaltendatentyps mit ASCII-Zeichen (lateinisch) von `NCHAR(10)` in `CHAR(10)` mit einer UTF-8-fähigen Sortierung führt beispielsweise zu einer Verringerung der Speicheranforderungen um 50 %. Diese Verringerung ist darauf zurückzuführen, dass `NCHAR(10)` 20 Byte für den Speicher erfordert, wohingegen `CHAR(10)` 10 Byte für die gleiche Unicode-Zeichenfolge erfordert.

Weitere Informationen finden Sie unter [Collation and Unicode Support](../relational-databases/collations/collation-and-unicode-support.md).

**CTP 2.1** unterstützt nun die Auswahl der UTF-8-Sortierung als Standard während des [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]-Setups.

**CTP 2.2** unterstützt nun die Verwendung von UTF-8-Zeichencodierung mit SQL Server-Replikation.

**CTP 2.3** unterstützt nun die Verwendung von UTF-8-Zeichencodierung mit BIN2-Sortierung (UTF8_BIN2).

#### <a name="scalar-udf-inlining-ctp-21"></a>Inlining benutzerdefinierter Skalarfunktionen (CTP 2.1)

Das Inlining benutzerdefinierter Skalarfunktionen wandelt die entsprechenden Funktionen automatisch in relationale Ausdrücke um und bettet sie in die aufrufende SQL-Abfrage ein. Dadurch wird die Leistung von Workloads verbessert, die benutzerdefinierte Skalarfunktionen verwenden. Das Inlining benutzerdefinierter Skalarfunktionen ermöglicht eine kostenbasierte Optimierung von Vorgängen in benutzerdefinierten Funktionen und erzielt effiziente Pläne, die konkret und parallel sind – im Gegensatz zu ineffizienten, iterativen, seriellen Ausführungsplänen. Dieses Feature ist standardmäßig unter dem Datenbank-Kompatibilitätsgrad 150 aktiviert.

Weitere Informationen finden Sie unter [Inlining benutzerdefinierter Skalarfunktionen](../relational-databases/user-defined-functions/scalar-udf-inlining.md).

#### <a name="a-nametruncation-truncation-error-message-improved-to-include-table-and-column-names-and-truncated-value-ctp-21"></a><a name="truncation" />Verbesserung der Fehlermeldungen für die Kürzung, sodass sie nun die Tabellen- und Spaltennamen sowie den gekürzten Wert enthalten (CTP 2.1)

Viele [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Entwickler und -Administratoren, die Datenverschiebungsworkloads entwickeln oder verwalten, kennen die Fehlermeldung `String or binary data would be truncated` (ID 8152). Der Fehler tritt beim Übertragen von Daten zwischen einer Quelle und einem Ziel mit unterschiedlichen Schemata auf, wenn die Quelldaten zu groß für den Zieldatentyp sind. Das Beheben des Fehlers anhand der Fehlermeldung kann sehr zeitaufwendig sein. [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] führt eine neue, spezifischere Fehlermeldung (2628) für dieses Szenario ein:  

`String or binary data would be truncated in table '%.*ls', column '%.*ls'. Truncated value: '%.*ls'.`

Die neue Fehlermeldung 2628 bietet mehr Kontext zum Abschneiden der Daten und vereinfacht die Problembehandlung. 

**CTP 2.1 und CTP 2.2:** Diese Fehlermeldung ist optional und erfordert, dass das [Ablaufverfolgungsflag](../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 460 aktiviert ist.

**CTP 2.4:** Die Fehlermeldung 2628 ist die Standardmeldung für Kürzungen und ersetzt die Fehlermeldung 8152 bei einem Datenbank-Kompatibilitätsgrad von 150. Die neue datenbankweite Konfiguration `VERBOSE_TRUNCATION_WARNINGS` wurde eingeführt, um die Fehlermeldungen 2628 und 8152 auszutauschen, wenn ein Datenbank-Kompatibilitätsgrad von 150 vorliegt. Weitere Informationen finden Sie unter [ALTER DATABASE SCOPED CONFIGURATION](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md).
Bei einem Datenbank-Kompatibilitätsgrad von 140 oder niedriger ist die Fehlermeldung 2628 weiterhin eine optionale Fehlermeldung, für die das [Ablaufverfolgungsflag 460](../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) aktiviert sein muss.

#### <a name="improved-diagnostic-data-for-stats-blocking-ctp-21"></a>Verbesserte Diagnosedaten für gesperrte Statistiken (CTP 2.1)

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] bietet verbesserte Diagnosedaten für Abfragen mit langer Ausführungszeit, die auf synchrone Updatevorgänge von Statistiken warten. Die Spalte `command` der dynamischen Verwaltungssicht `sys.dm_exec_requests` zeigt `SELECT (STATMAN)` an, wenn ein `SELECT`-Objekt darauf wartet, dass ein synchroner Statistikupdatevorgang abgeschlossen wird, bevor die Abfrage weiter ausgeführt wird. Außerdem wird der neue Wartetyp `WAIT_ON_SYNC_STATISTICS_REFRESH` in der dynamischen Verwaltungssicht `sys.dm_os_wait_stats` angezeigt. Er zeigt die kumulierte Zeit auf Instanzebene für synchrone Statistikaktualisierungen an.

#### <a name="hybrid-buffer-pool-ctp-21"></a>Hybrider Pufferpool (CTP 2.1)

Der hybride Pufferpool ist eine neue Funktion der SQL Server-Datenbank-Engine, mit der Sie bei Bedarf direkt auf Datenbankseiten in Datenbankdateien zugreifen können, die sich auf einem Gerät mit beständigem Arbeitsspeicher (PMEM) befinden. Da PMEM-Geräte eine sehr niedrige Latenz beim Datenzugriff aufweisen, muss die Engine keine Kopie der Daten in einem Pufferpoolbereich für bereinigte Seiten erstellen, sondern kann auf die Seite direkt im beständigen Arbeitsspeicher zugreifen. Der Zugriff erfolgt über im Speicher abgebildete E/A – wie bei Optimierungen. Das bietet Leistungsvorteile, da keine Kopie der Seite im DRAM erstellt und der E/A-Stapel des Betriebssystems für den Seitenzugriff im beständigen Speicher umgangen wird. Diese Funktion ist für SQL Server sowohl unter Windows als auch unter Linux verfügbar.

Weitere Informationen finden Sie unter [Hybrider Pufferpool](../database-engine/configure-windows/hybrid-buffer-pool.md).

#### <a name="static-data-masking-ctp-21"></a>Statische Datenmaskierung (CTP 2.1)

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] führt die statische Datenmaskierung ein. Damit können Sie sensible Daten in Kopien von SQL Server-Datenbanken bereinigen. Die statische Datenmaskierung erstellt eine bereinigte Datenbankkopie, in der alle sensiblen Daten so geändert wurden, dass sie auch für Nichtproduktionsbenutzer freigegeben werden kann. Sie kann für Entwicklung, Tests, Analysen, Geschäftsberichte, Compliance, Fehlerbehandlung und andere Szenarien verwendet werden, in denen bestimmte Daten nicht in verschiedene Umgebungen kopiert werden können.

Die statische Datenmaskierung wird auf Spaltenebene ausgeführt. Wählen Sie die zu maskierenden Spalten aus, und geben Sie für jede ausgewählte Spalte eine Maskierungsfunktion an. Die statische Datenmaskierung kopiert die Datenbank und wendet dann die angegebenen Maskierungsfunktionen auf die Spalten an.

##### <a name="static-data-masking-vs-dynamic-data-masking"></a>Statische vs. dynamische Datenmaskierung

Bei der Datenmaskierung wird eine Maske auf eine Datenbank angewendet, um vertrauliche Informationen auszublenden und mit neuen bzw. bereinigten Daten zu ersetzen. Microsoft bietet zwei Maskierungsoptionen: die statische und die dynamische Datenmaskierung. Die dynamische Datenmaskierung wurde in [!INCLUDE[ssSQL16](../includes/sssql16-md.md)] eingeführt. In dieser Tabelle werden die beiden Ansätze verglichen:

|Statische Datenmaskierung |Dynamische Datenmaskierung|
|:----|:----|
|Verwendung einer Datenbankkopie <br/><br/>Kein Abrufen von Originaldaten<br/><br/>Maskierung erfolgt auf Speicherebene<br/><br/>Alle Benutzer haben Zugriff auf die gleichen maskierten Daten<br/><br/>Konzipiert für permanenten Zugriff für das ganze Team|Verwendung der Originaldatenbank<br/><br/>Intakte Originaldaten<br/><br/>Maskierung erfolgt direkt beim Abfragen<br/><br/>Maskierung variiert je nach Benutzerberechtigung <br/><br/>Konzipiert für punktuellen benutzerspezifischen Zugriff|

#### <a name="database-compatibility-level-ctp-20"></a>Datenbank-Kompatibilitätsgrad (CTP 2.0)

Die Datenbank **COMPATIBILITY_LEVEL 150** wurde hinzugefügt. Um eine bestimmte Benutzerdatenbank verwenden zu können, führen Sie Folgendes aus:

   ```sql
   ALTER DATABASE database_name SET COMPATIBILITY_LEVEL =  150;
   ```

#### <a name="resumable-online-index-create-ctp-20"></a>Erstellung fortsetzbarer Onlineinidizes (CTP 2.0)

Durch die **Erstellung von fortsetzbaren Onlineindizes** kann ein Indexerstellungsvorgang angehalten und zu einem späteren Zeitpunkt an der Stelle fortgesetzt werden, an der der Vorgang angehalten wurde oder an der ein Fehler aufgetreten ist. So muss nicht von Anfang an begonnen werden.

Die Erstellung fortsetzbarer Onlineindizes unterstützt folgende Szenarien:
- Fortsetzen eines Indexerstellungsvorgangs nach einem Fehler bei der Indexerstellung (z.B. nach einem Datenbankfailover oder bei fehlendem Speicherplatz auf dem Datenträger)
- Anhalten eines laufenden Indexerstellungsvorgangs und Fortsetzen zu einem späteren Zeitpunkt, um bei Bedarf vorübergehend Systemressourcen freizugeben und diesen Vorgang zu einem späteren Zeitpunkt fortzusetzen
- Erstellen großer Indizes ohne Inanspruchnahme von umfassendem Protokollspeicherplatz und Transaktionen mit langer Laufzeit, die andere Wartungsaktivitäten blockieren, jedoch mit der Möglichkeit zur Protokollkürzung

Ohne dieses Feature müsste ein Vorgang zur Onlineindexerstellung bei einem Fehler erneut von Anfang an ausgeführt werden.

Bei diesem Release erweitern wir die Funktionen für fortsetzbare Indizes, indem wir dieses Feature für verfügbare [Neuerstellungen von fortsetzbaren Onlineindizes](https://azure.microsoft.com/blog/modernize-index-maintenance-with-resumable-online-index-rebuild/) hinzufügen.

Darüber hinaus kann dieses Feature als Standardwert für eine bestimmte Datenbank mit einer [datenbankweit gültigen Standardeinstellung für Online- und fortsetzbare DDL-Vorgänge](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md) festgelegt werden.

Weitere Informationen finden Sie unter [Erstellung von fortsetzbaren Onlineindizes](../t-sql/statements/create-index-transact-sql.md#resumable-indexes).

#### <a name="build-and-rebuild-clustered-columnstore-indexes-online-ctp-20"></a>Erstellen und erneutes Erstellen von gruppierten Columnstore-Indizes (online) (CTP 2.0)

Konvertieren Sie Rowstore-Tabellen in das Columnstore-Format. Die Erstellung von gruppierten Columnstore-Indizes (Clustered Columnstore Indexes, CCIs) war in früheren Versionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ein Offlinevorgang, bei dem alle Änderungen eingestellt werden mussten, während der CCI erstellt wird. Mit [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] und [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)] können Sie einen CCI online erstellen bzw. neu erstellen. Die Workload wird nicht blockiert und alle Änderungen, die an den zugrunde liegenden Daten vorgenommen werden, werden transparent zur Columnstore-Zieltabelle hinzugefügt. Beispiele für die neuen [!INCLUDE[tsql](../includes/tsql-md.md)]-Anweisungen, die verwendet werden können:

  ```sql
  CREATE CLUSTERED COLUMNSTORE INDEX cci
    ON <tableName>
    WITH (ONLINE = ON);
  ```

  ```sql
  ALTER INDEX cci
    ON <tableName>
    REBUILD WITH (ONLINE = ON);
  ```

#### <a name="always-encrypted-with-secure-enclaves-ctp-20"></a>Always Encrypted mit Secure Enclaves (CTP 2.0)

Die Erweiterung basiert auf Always Encrypted mit direkter Verschlüsselung und umfangreichen Berechnungen. Die Erweiterungen basieren auf der Ermöglichung von Berechnungen auf Grundlage von Klartextdaten, die sich auf Serverseite in einer Secure Enclave befinden.

Kryptografische Vorgänge umfassen die Verschlüsselung von Spalten und das Rotieren von Spaltenverschlüsselungsschlüsseln. Diese Vorgänge können nun mithilfe von [!INCLUDE[tsql](../includes/tsql-md.md)] ausgegeben werden und erfordern kein Entfernen dieser Daten aus der Datenbank. Secure Enclaves bieten Always Encrypted, um ein breiteres Spektrum an Szenarien zu ermöglichen, die folgende Anforderungen nach sich ziehen:  

- Vertrauliche Daten müssen vor Benutzern mit erhöhten Rechten, die jedoch nicht autorisiert sind, geschützt werden (z.B. Datenbankadministratoren, Systemadministratoren, Cloudbetreiber oder Malware).
- Es müssen umfangreiche Berechnungen für geschützte Daten innerhalb des Datenbanksystems unterstützt sein.

Weitere Einzelheiten finden Sie unter [Always Encrypted mit Secure Enclaves](../relational-databases/security/encryption/always-encrypted-enclaves.md).

> [!NOTE]
> Always Encrypted mit Secure Enclaves ist nur unter dem Windows-Betriebssystem verfügbar.

#### <a name="intelligent-query-processing-ctp-20"></a>Intelligente Abfrageverarbeitung (CTP 2.0)

- Das **Feedback zur Speicherzuweisung im Zeilenmodus** erweitert das Feedbackfeature zur Speicherzuweisung, das [!INCLUDE[ssSQL17](../includes/sssql17-md.md)] eingeführt wurde, indem die Größe der Speicherzuweisung sowohl für Batch- als auch für Zeilenmodusoperatoren angepasst wird. Wenn bei einer Bedingung mit einer zu großen Speicherzuweisung der zugewiesene Speicher mehr als doppelt so groß ist als der tatsächlich verwendete Speicher, berechnet das Feedback zur Speicherzuweisung diese neu. Nachfolgende Ausführungen erfordern dann weniger Arbeitsspeicher. Bei zu geringen Speicherzuweisungen, die zu einem Überlauf auf einen Datenträger führen, löst das Feedback zur Speicherzuweisung eine Neuberechnung der Speicherzuweisung aus. Nachfolgende Ausführungen erfordern dann mehr Arbeitsspeicher. Dieses Feature ist standardmäßig unter dem Datenbank-Kompatibilitätsgrad 150 aktiviert.

- **Approximate COUNT DISTINCT** gibt die ungefähre Anzahl von eindeutigen Werten ungleich NULL in einer Gruppe zurück. Diese Funktion ist für den Einsatz in Big Data-Szenarien bestimmt. Diese Funktion ist für Abfragen optimiert, bei denen alle der folgenden Bedingungen zutreffen:
   - Es wird auf Datasets mit Zeilen mindestens im Millionenbereich zugegriffen.
   - Es wird mindestens eine Spalte aggregiert, die eine große Anzahl von unterschiedlichen Werten enthält.
   - Reaktionsschnelligkeit ist wichtiger als absolute Präzision.
      - `APPROX_COUNT_DISTINCT` gibt Ergebnisse zurück, die in der Regel im 2-Prozent-Bereich der genauen Antwort liegen.
      - Zudem wird die ungefähre Antwort in einem Bruchteil der Zeit zurückgegeben, die für die genaue Antwort erforderlich ist.

- Für den **Batchmodus in Rowstore** ist kein Columnstore-Index mehr zur Verarbeitung von Abfragen im Batchmodus erforderlich. Im Batchmodus können Abfrageoperatoren verwendet werden, die die Verarbeitung von einer Gruppe von Zeilen statt nur von einer Zeile ermöglichen. Dieses Feature ist standardmäßig unter dem Datenbank-Kompatibilitätsgrad 150 aktiviert. Der Batchmodus beschleunigt somit Abfragen, die auf Rowstore-Tabellen zugreifen, sofern alle der folgenden Bedingungen zutreffen:
   - Die Abfrage verwendet Analyseoperatoren wie Joins oder Aggregationsoperatoren.
   - Die Abfrage umfasst mindestens 100.000 Zeilen.
   - Die Abfrage ist nicht an Eingabe-/Ausgabedaten gebunden, sondern an die CPU.
   - Die Erstellung und Verwendung eines Columnstore-Index weisen folgende Nachteile auf:
      - Sie würden den Overheadbedarf der Abfrage übersteigen.
      - Sie können nicht durchgeführt werden, da Ihre Anwendung von einem Feature abhängt, das noch nicht bei Columnstore-Indizes unterstützt wird.

- Die **verzögerte Kompilierung von Tabellenvariablen** verbessert die Qualität des Abfrageplans und die Gesamtleistung für Abfragen mit Verweisen auf Tabellenvariablen. Während der Optimierung und der ersten Kompilierung propagiert diese Funktion Kardinalitätsschätzungen, die auf tatsächlichen Tabellenvariablen-Zeilenzahlen basieren. Diese genauen Zeilenzahlinformationen werden für die Optimierung der nachgelagerten Planvorgänge verwendet. Dieses Feature ist standardmäßig unter dem Datenbank-Kompatibilitätsgrad 150 aktiviert.

Um Features der intelligenten Abfrageverarbeitung verwenden zu können, legen Sie die Datenbank `COMPATIBILITY_LEVEL = 150` fest.

#### <a id="programmability"></a> Erweiterungen für die Programmierbarkeit der Java-Sprache (CTP 2.0)

- **Java-Spracherweiterung (Vorschauversion):** Führen Sie Java-Code mithilfe der Java-Spracherweiterung in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] aus. Diese Erweiterung ist in [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] installiert, wenn Sie das Feature „Machine Learning Services (datenbankintern)“ zu Ihrer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Instanz hinzufügen.

#### <a id="sqlgraph"></a> SQL-Graphfeatures (CTP 2.3)

- Sie können **abgeleitete Tabellen- oder Ansichtsaliasse in Graphabgleichabfragen (CTP 2.1) verwenden**. Graphabfragen in der [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]-Vorschauversion verwenden Ansichts- und abgeleitete Tabellenaliasse in der Syntax `MATCH`. Um diese Aliasse in `MATCH` zu verwenden, müssen die Ansichten und abgeleiteten Tabellen entweder in einem Knotensatz oder einem Edgetabellensatz mit dem Operator `UNION ALL` erstellt werden. Der Knoten oder die Edgetabelle können Filter aufweisen. Die Verwendung abgeleiteter Tabellen- und Ansichtsaliasse in `MATCH`-Abfragen kann sehr nützlich sein, wenn Sie heterogene Entitäten bzw. Verbindungen für mindestens zwei Entitäten in Ihrem Graph abfragen möchten.

- Dank des **Supports in `MERGE`-DML (CTP 2.0)** können Sie Graphbeziehungen statt in separaten `INSERT`-, `UPDATE`- oder `DELETE`-Anweisungen in einer einzigen Anweisung angeben. Führen Sie Ihre aktuellen Graphdaten aus Knoten- oder Edgetabellen mithilfe der `MATCH`-Prädikate in der `MERGE`-Anweisung mit neuen Daten zusammen. Dieses Feature ermöglicht `UPSERT`-Szenarien in Edgetabellen. Benutzer können nun eine einzelne MERGE-Anweisung verwenden, um einen neuen Edge einzufügen oder einen vorhandenen Edge zwischen zwei Knoten zu aktualisieren.

- Für Edgetabellen im SQL-Graph wurden **Edgeeinschränkungen (CTP 2.0)**  eingeführt. Edgetabellen können eine Verbindung zwischen beliebigen Knoten in der Datenbank herstellen. Mit der Einführung von Edgeeinschränkungen können Sie ab sofort einige Einschränkungen zu diesem Verhalten anwenden. Mit der neuen `CONNECTION`-Einschränkung kann der Knotentyp angegeben werden, mit dem eine bestimmte Edgetabelle eine Verbindung im Schema herstellen darf. 

  **(CTP 2.3)** Dieses Feature wurde erweitert, sodass Sie nun kaskadierende Deletes für Edgeeinschränkung definieren können. Sie können die Aktionen festlegen, die die Datenbank-Engine ausführt, wenn ein Benutzer die Knoten löscht, die über einen bestimmten Edge verbunden werden.

#### <a name="database-scoped-default-setting-for-online-and-resumable-ddl-operations-ctp-20"></a>Datenbankweite Standardeinstellung für Online- und fortsetzbare DDL-Vorgänge (CTP 2.0)

- Die **datenbankweit gültige Standardeinstellung für Online- und fortsetzbare DDL-Vorgänge** ermöglicht eine Standardverhaltenseinstellung für `ONLINE`- und `RESUMABLE`-Indexvorgänge auf Datenbankebene, statt diese Optionen für jede einzelne DDL-Indexanweisung definieren zu müssen (z.B. Indexerstellung oder -neuerstellung).

- Legen Sie diese Standardeinstellungen mithilfe der datenbankweit gültigen Konfigurationsoptionen `ELEVATE_ONLINE` und `ELEVATE_RESUMABLE` fest. Beide Optionen bewirken, dass die Engine unterstützte Vorgänge automatisch auf die Ausführung von Online- oder fortsetzbaren Indizes erhöht. Mit diesen Optionen können Sie die folgenden Verhaltensweisen ermöglichen:

  - Die Option `FAIL_UNSUPPORTED` ermöglicht alle Onlineindex- oder fortsetzbare und Fehlerindexvorgänge, die nicht für Online- oder fortsetzbare Indizes unterstützt werden.
  - Die Option `WHEN_SUPPPORTED` ermöglicht unterstützte Online- oder fortsetzbare und die Ausführung von nicht unterstützten Offline- oder nicht fortsetzbaren Indexvorgängen.
  - Die Option `OFF` lässt das aktuelle Verhalten zur Ausführung aller Offlineindexvorgänge und nicht fortsetzbare Indexvorgänge zu, sofern dies nicht explizit in der DDL-Anweisung angegeben ist.

Um die Standardeinstellung zu überschreiben, schließen Sie die `ONLINE`- oder die `RESUMABLE`-Option in die Indexerstellungs- und -neuerstellungsbefehle ein. 

Ohne dieses Feature müssen Sie die Onlineoptionen und fortsetzbaren Optionen direkt in der Index-DDL-Anweisung angeben, z.B. die Indexerstellung und -neuerstellung.

Weitere Informationen zu fortsetzbaren Indexvorgängen finden Sie unter [Resumable Online Index Create](https://azure.microsoft.com/blog/resumable-online-index-create-is-in-public-preview-for-azure-sql-db/) (Erstellung fortsetzbarer Onlineindizes).

#### <a id="ha"></a>Always On-Verfügbarkeitsgruppen: Erhöhung der Anzahl synchroner Replikate (CTP 2.0)

- **Bis zu fünf synchrone Replikate:** In [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] wird die maximale Anzahl der synchronen Replikate von ehemals 3 in [!INCLUDE[ssSQL17](../includes/sssql17-md.md)] auf 5 erhöht. Sie können diese Gruppe aus fünf Replikaten für das automatische Failover in der Gruppe konfigurieren. Es gibt ein primäres Replikat sowie vier synchrone sekundäre Replikate.

- **Umleiten der Verbindung vom sekundären zum primären Replikat:** Durch dieses Feature können Clientanwendungsverbindungen zum primären Replikat weitergeleitet werden, unabhängig davon, ob der Zielserver in der Verbindungszeichenfolge angegeben ist. Diese Funktion ermöglicht die Umleitung der Verbindung ohne einen Listener. Leiten Sie in den folgenden Fällen die Verbindung vom sekundären zum primären Replikat um:

  - Die Clustertechnologie bietet keine Listenerfunktion.
  - Es liegt eine Konfiguration mit mehreren Subnetzen vor, die eine komplexe Umleitung erfordert.
  - Im Mittelpunkt stehen Szenarien mit horizontaler Leseskalierung oder Notfallwiederherstellungszenarien mit dem Clustertyp `NONE`.

Weitere Informationen finden Sie unter [Umleitung von Lese-/Schreibverbindungen vom sekundären zum primären Replikat (Always On-Verfügbarkeitsgruppen)](../database-engine/availability-groups/windows/secondary-replica-connection-redirection-always-on-availability-groups.md).

#### <a name="data-discovery-and-classification-ctp-20"></a>Datenermittlung und -klassifizierung (CTP 2.0)

Die Datenermittlung und -klassifizierung bietet erweiterte Funktionen, die nativ in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] integriert sind. Die Klassifizierung und Bezeichnung der wichtigsten vertraulichen Daten bietet folgende Vorteile:
- Bietet Unterstützung, um Datenschutzstandards und gesetzlich geregelte Complianceanforderungen zu erfüllen
- Unterstützt Sicherheitsszenarien, z.B. Überwachung und Benachrichtigung bei anomalem Zugriff auf vertrauliche Daten
- Vereinfacht den Vorgang der Ermittlung, wo sich vertrauliche Daten im Unternehmen befinden, damit Administratoren die richtigen Schritte zum Schutz der Datenbank durchführen können

Weitere Informationen finden Sie unter [Datenermittlung und -klassifizierung in SQL Server](../relational-databases/security/sql-data-discovery-and-classification.md).

Die [Überwachung](../relational-databases/security/auditing/sql-server-audit-database-engine.md) wurde zudem dahingehend verbessert, dass ein neues Feld in das Überwachungsprotokoll `data_sensitivity_information` eingeschlossen wurde, das die Vertraulichkeitsklassifizierungen (Bezeichnungen) der tatsächlichen Daten protokolliert, die von der Abfrage zurückgegeben wurden. Weitere Informationen und Beispiele finden Sie unter [ADD SENSITIVITY CLASSIFICATION (Transact-SQL)](../t-sql/statements/add-sensitivity-classification-transact-sql.md).

>[!NOTE]
>Es wurden keine Änderungen an der Art und Weise vorgenommen, wie die Überwachung aktiviert wird. Den Überwachungsdatensätzen wurde ein neues Feld namens `data_sensitivity_information` hinzugefügt, das die Vertraulichkeitsklassifizierungen (Bezeichnungen) der tatsächlichen Daten protokolliert, die von der Abfrage zurückgegeben wurden. Weitere Informationen finden Sie unter [Überwachen des Zugriffs auf vertrauliche Daten](/azure/sql-database/sql-database-data-discovery-and-classification/#subheading-3).

#### <a name="expanded-support-for-persistent-memory-devices-ctp-20"></a>Erweiterte Unterstützung für Geräte mit beständigem Speicher (CTP 2.0)

[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Dateien, die auf einem Gerät mit persistentem Speicher platziert werden, können ab sofort im *optimierten* Modus betrieben werden. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] greift direkt auf das Gerät zu, wobei der Speicherstapel des Betriebssystems mithilfe von effizienten Speichervorgängen umgangen wird. Dieser Modus verbessert die Leistung, da er Eingaben/Ausgaben mit geringen Latenzen für solche Geräte ermöglicht.
    - Zu [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Dateien zählen beispielsweise Folgende:
        - Datenbankdateien
        - Transaktionsprotokolldateien
        - In-Memory-OLTP-Prüfpunktdateien
    - Persistente Speicher werden auch als Speicherklassenspeicher bezeichnet.
    - Persistente Speicher werden auf Websites, die nicht von Microsoft betrieben werden, gelegentlich informell *pmem* genannt.

> [!NOTE]
> Bei diesem Vorschaurelease ist die Optimierung von Dateien auf Geräten mit persistentem Speicher nur unter Linux verfügbar. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] unter Windows unterstützt Geräte mit persistentem Speicher ab [!INCLUDE[ssSQL15](../includes/sssql15-md.md)].

#### <a name="support-for-columnstore-statistics-in-dbcc-clonedatabase-ctp-20"></a>Unterstützung für Columnstore-Statistiken in DBCC CLONEDATABASE (CTP 2.0)

`DBCC CLONEDATABASE` erstellt eine rein schemabasierte Kopie einer Datenbank, die alle Elemente enthält, die zum Behandeln von Problemen mit der Abfrageleistung erforderlich sind, ohne das Daten kopiert werden. In älteren Versionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] wurden beim Befehl nicht die Statistiken kopiert, die für die Problembehandlung bei Columnstore-Indexabfragen erforderlich sind, weshalb manuelle Schritte zur Erfassung dieser Informationen nötig waren. In [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] erfasst `DBCC CLONEDATABASE` nun automatisch die Statistikblobs für Columnstore-Indizes, sodass keine manuellen Schritte erforderlich sind.

#### <a name="new-options-added-to-sp_estimate_data_compression_savings-ctp-20"></a>Neue Optionen für „sp_estimate_data_compression_savings“ (CTP 2.0)

`sp_estimate_data_compression_savings` gibt die aktuelle Größe des angeforderten Objekts zurück und schätzt die Objektgröße für den angeforderten Komprimierungsstatus. Diese Prozedur unterstützt derzeit drei Optionen: `NONE`, `ROW` und `PAGE`. In [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] werden zwei neue Optionen eingeführt: `COLUMNSTORE` und `COLUMNSTORE_ARCHIVE`. Diese neuen Optionen ermöglichen es Ihnen, die Speicherplatzeinsparungen abzuschätzen, wenn mit der Columnstore-Standard- oder -Archivkomprimierung ein Columnstore-Index für die Tabelle erstellt wird.

#### <a id="ml"></a> Failovercluster für SQL Server Machine Learning Services und partitionsbasierte Modellierung (CTP 2.0)

- **Partitionsbasierte Modellierung:** `sp_execute_external_script` wurde um die partitionsbasierte Verarbeitung von externen Skripts Ihrer Daten mit den neuen Parametern erweitert. Diese Funktion unterstützt anstelle eines großen Modells das Trainieren von einer Vielzahl kleiner Modelle (ein Modell pro Datenpartition).

- **Windows Server-Failovercluster:** Konfigurieren Sie Hochverfügbarkeit für Machine Learning Services in einem Windows Server-Failovercluster.

Weitere Informationen finden Sie unter [Neuigkeiten zu SQL Server Machine Learning Services](../advanced-analytics/what-s-new-in-sql-server-machine-learning-services.md).

#### <a name="lightweight-query-profiling-infrastructure-enabled-by-default-ctp-20"></a>Standardmäßig aktivierte LWP-Abfrageinfrastruktur (CTP 2.0)

Die LWP-Abfrageinfrastruktur (Lightweight Profiling) stellt Abfrageleistungsdaten effizienter bereit als standardmäßige Profilerstellungsmechanismen. Lightweight Profiling ist ab sofort standardmäßig aktiviert. Diese Infrastruktur wurde in [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] SP1 eingeführt. Lightweight Profiling bietet eine Methode zur Sammlung von Statistiken zur Abfrageausführung mit einem erwarteten CPU-Overhead von 2 % im Vergleich zu einem CPU-Overhead von bis zu 75 % für die Standardmethode zur Abfrageprofilerstellung. In älteren Versionen war diese Option standardmäßig deaktiviert. Datenbankadministratoren konnten diese mit dem [Ablaufverfolgungsflag 7412](../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) aktivieren. 

Weitere Informationen zu LWP finden Sie unter [Profilerstellungsinfrastruktur für Abfragen](../relational-databases/performance/query-profiling-infrastructure.md).

**CTP 2.3** Eine neue datenbankbezogene Konfiguration (`LIGHTWEIGHT_QUERY_PROFILING`) wird eingeführt, um die einfache Profilerstellungsinfrastruktur für Abfragen zu aktivieren oder deaktivieren.

#### <a id="polybase"></a>Neue PolyBase-Connectors

- **Neue Connectors für [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], Oracle, Teradata und MongoDB**: In [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] werden neue Connectors für externe Daten für [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], Oracle, Teradata und MongoDB eingeführt.

#### <a name="new-sysdm_db_page_info-system-function-returns-page-information-ctp-20"></a>Rückgabe von Seiteninformationen durch neue „sys.dm_db_page_info“-Systemfunktion (CTP 2.0)

`sys.dm_db_page_info(database_id, file_id, page_id, mode)` gibt Informationen zu einer Seite in einer Datenbank zurück. Die Funktion gibt eine Zeile zurück, die die Headerinformationen der Seite enthält, einschließlich `object_id`, `index_id` und `partition_id`. Dank dieser Funktion ist die Verwendung von `DBCC PAGE` in den meisten Fällen nicht mehr erforderlich. 

Um eine Problembehandlung für die seitenbezogenen Wartevorgänge zu ermöglichen, wurde außerdem eine neue Spalte namens „page_resource“ zu `sys.dm_exec_requests` und `sys.sysprocesses` hinzugefügt. Mit dieser neuen Spalte können Sie `sys.dm_db_page_info` durch eine weitere neue Systemfunktion namens `sys.fn_PageResCracker` mit diesen Ansichten verknüpfen. Sehen Sie sich als Beispiel das folgende Skript an:

```sql
SELECT page_info.* 
FROM sys.dm_exec_requests AS d 
  CROSS APPLY sys.fn_PageResCracker(d.page_resource) AS r
  CROSS APPLY sys.dm_db_page_info(r.db_id, r.file_id, r.page_id,'DETAILED')
    AS page_info;
```

### <a id="sqllinux"></a> SQL Server unter Linux

- **Always On-Verfügbarkeitsgruppe in Docker-Containern mit Kubernetes (CTP 2.2):** Kubernetes kann Container orchestrieren, auf denen [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Instanzen ausgeführt werden, um eine hochverfügbare Gruppe von Datenbanken mit SQL Server Always On-Verfügbarkeitsgruppen bereitzustellen. Ein Kubernetes-Operator stellt ein StatefulSet bereit, einschließlich eines Containers mit einem **mssql-server-Container** und einem Integritätsmonitor.

- **Neue Containerregistrierung (CTP 2.1):** Alle Containerimages für [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] sowie [!INCLUDE[ssSQL17](../includes/sssql17-md.md)] befinden sich nun in Microsoft Container Registry. Microsoft Container Registry ist die offizielle Containerregistrierung für die Verteilung von Microsoft-Produktcontainern. Darüber hinaus werden ab sofort zertifizierte RHEL-basierte Images veröffentlicht.

  - Microsoft Container Registry: `mcr.microsoft.com/mssql/server:vNext-CTP2.0`
  - Zertifizierte RHEL-basierte Containerimages: `mcr.microsoft.com/mssql/rhel/server:vNext-CTP2.0`

- **Replikationsunterstützung (CTP 2.0)** : [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] unterstützt die SQL Server-Replikation unter Linux. Bei einem virtuellen Linux-Computer mit dem SQL Server-Agent kann es sich um einen Verleger, einen Verteiler oder einen Abonnenten handeln. 

  Erstellen Sie die folgenden Arten von Veröffentlichungen:
  - Transaktion
  - Momentaufnahme
  - Merge

  Konfigurieren Sie die Replikation [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] oder verwenden Sie [gespeicherte Replikationsprozeduren](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md).

- **Unterstützung für den Microsoft Distributed Transaction Coordinator (MSDTC) (CTP 2.0):** [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] unter Linux unterstützt den Microsoft Distributed Transaction Coordinator (MSDTC). Weitere Informationen finden Sie unter [Gewusst wie: Konfigurieren des Microsoft Distributed Transaction Coordinator (MSDTC) unter Linux](../linux/sql-server-linux-configure-msdtc.md).

- **OpenLDAP-Unterstützung für AD-Drittanbieter (CTP 2.0):** [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] unter Linux unterstützt OpenLDAP, mit dem Drittanbieter zu Active Directory beitreten können.

- **Machine Learning unter Linux (CTP 2.0):** [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] Machine Learning Services (datenbankintern) wird ab sofort unter Linux unterstützt. Dies umfasst die Unterstützung für die gespeicherte `sp_execute_external_script`-Prozedur. Anweisungen zum Installieren von Machine Learning Services unter Linux finden Sie unter [Install [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] Machine Learning Services R and Python support on Linux (Installieren von SQL Server 2019 Machine Learning Services unter Linux (R, Python))](../linux/sql-server-linux-setup-machine-learning.md).

### <a id="mds"></a> Master Data Services 

- **Ersetzung der Silverlight-Steuerelemente durch HTML (CTP 2.0):** Das MDS-Portal (Master Data Services) ist nicht mehr von Silverlight abhängig. Alle veralteten Silverlight-Komponenten wurden durch HTML-Steuerelemente ersetzt.

### <a id="security"></a>Sicherheit

- **Zertifikatverwaltung im SQL Server-Konfigurations-Manager (CTP 2.0):** SSL/TLS-Zertifikate werden oft dazu verwendet, den Zugriff auf SQL Server-Instanzen zu sichern. Die Zertifikatverwaltung ist ab sofort im SQL Server-Konfigurations-Manager integriert, was allgemeine Aufgaben wie die Folgenden vereinfacht:

  - Anzeigen und Überprüfen der auf einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Instanz installierten Zertifikate 
  - Anzeigen von bald ablaufenden Zertifikaten
  - Bereitstellen von Zertifikaten auf Computern, die Always On-Verfügbarkeitsgruppen angehören (auf dem Knoten, auf dem sich das primäre Replikat befindet)
  - Bereitstellen von Zertifikaten auf Computern, die einer Failoverclusterinstanz angehören (auf dem aktiven Knoten)

  > [!NOTE]
  > Benutzer müssen über Administratorberechtigungen auf allen Clusterknoten verfügen.

### <a id="tools"></a>Tools

- [**Azure Data Studio:** ](../azure-data-studio/what-is.md) Bei Azure Data Studio, das ehemals unter dem Vorschauversionsnamen „SQL Operations Studio“ veröffentlicht wurde, handelt es sich um ein einfaches und modernes, plattformübergreifendes Open Source-Desktoptool für die gängigsten Aufgaben in der Datenentwicklung und -verwaltung. Mit Azure Data Studio und der [Erweiterung für [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] Preview](../azure-data-studio/sql-server-2019-extension.md) können Sie unter Windows, macOS und Linux eine Verbindung mit einer SQL Server-Instanz (lokal und in der Cloud) herstellen. Mit Azure Data Studio können Sie Folgendes:

<a name = "tools-ctp23"></a>

  - AAD wird jetzt unterstützt. (CTP 2.3)
  - Die Benutzeroberfläche für das Anzeigen von Notebooks wurde in Azure Data Studio verschoben. (CTP 2.3)
  - Ein neuer Assistent zum Erstellen externer Datenquellen von HDFS (Hadoop Distributed File System) in Big Data-Clustern von SQL Server wurde hinzugefügt. (CTP 2.3)
  - Verbesserte Benutzeroberfläche für das Anzeigen von Notebooks. (CTP 2.3)
  - Neue Notebook-APIs wurden hinzugefügt. (CTP 2.3)
  - Der Befehl „“ wurde zur Unterstützung beim Aktualisieren von Python-Paketen hinzugefügt. (CTP 2.3)
  - Verbinden und Verwalten von Big Data-Clustern von [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]. (CTP 2.1)
  - Bearbeiten und Ausführen von Abfragen in einer modernen Entwicklungsumgebung mit extrem schnellen IntelliSense-Informationen, Codeausschnitten und integrierter Quellcodeverwaltung. (CTP 2.0) 
  - Schnelles Visualisieren von Daten mit integrierten Diagrammen zu Ihren Resultsets (CTP 2.0)
  - Erstellen von benutzerdefinierten Dashboards für Ihre Server und Datenbanken mithilfe von anpassbaren Widgets (CTP 2.0)  
  - Einfaches Verwalten Ihrer größeren Umgebung mit dem integrierten Terminal (CTP 2.0)
  - Analysieren von Daten in einer integrierten Notebookumgebung, die auf Jupyter basiert (CTP 2.0)
  - Verbessern der Benutzererfahrung durch benutzerdefinierte Designs und Erweiterungen (CTP 2.0)
  - Untersuchen von Azure-Ressourcen mit integriertem Abonnement und Ressourcenbrowser (CTP 2.0)
  - Unterstützung für Szenarios mit SQL Server-Big Data-Clustern (CTP 2.0)
  
  > [!TIP]
  > Weitere Informationen zu den neuesten Verbesserungen an Azure Data Studio finden Sie in den [Versionshinweisen zu Azure Data Studio](../azure-data-studio/release-notes-azure-data-studio.md).

- [**SQL Server Management Studio (SSMS) 18.0 (Vorschauversion):** ](../ssms/sql-server-management-studio-ssms.md) Unterstützt [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]

  - Ermöglicht das Starten von Azure Data Studio über SSMS (CTP 2.3)
  - Unterstützung für Always Encrypted mit Secure Enclaves (CTP 2.0)
  - Geringere Downloadgröße (CTP 2.0)
  - Ab sofort Visual Studio 2017 Isolated Shell als Grundlage (CTP 2.0)
  - Eine vollständige Liste finden Sie unter [SQL Server Management Studio – Änderungsprotokoll (SSMS)](../ssms/release-notes-ssms.md). (CTP 2.0)

- [**Das SQL Server PowerShell-Modul:** ](http://www.powershellgallery.com/packages/SqlServer/21.1.18080) Mit dem PowerShell-Modul „SqlServer“ können SQL Server-Entwickler, -Administratoren und BI-Experten die Datenbankbereitstellung und Serververwaltung automatisieren.

  - SMO v150 wird nach einem Upgrade von Version 21.0 auf Version 21.1 unterstützt.
  - Im aktualisierten SQL Server-Anbieter (SQLRegistration) werden nun AS/IS/RS-Gruppen angezeigt.
  - Korrigiert: Fehler im Cmdlet `New-SqlAvailabilityGroup` bei SQL Server 2014 als Zielversion.
  - Der Parameter `–LoadBalancedReadOnlyRoutingList` wurde zu `Set-SqlAvailabilityReplica` und `New-SqlAvailabilityReplica` hinzugefügt.
  - Das Cmdlet `AnalysisService` wurde aktualisiert und kann nun zwischengespeicherte Anmeldetoken von `Login-AzureAsAccount` für Azure Analysis Services verwenden.

### <a id="ssas"></a>[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Analysis Services (SSAS) 

#### <a name="online-attach-ctp32"></a>Online anfügen (CTP 3.2)

CTP 3.2 bietet die Möglichkeit, ein tabellarisches Modell als Onlinevorgang anzufügen. Das Onlineanfügen kann für die Synchronisierung schreibgeschützter Replikate in horizontal skalierten Umgebungen für lokale Abfragen verwendet werden. Verwenden Sie die Option **AllowOverwrite** des „Attach XMLA“-Befehls, um einen Onlineanfügevorgang auszuführen. 

```xmla
<Attach xmlns="http://schemas.microsoft.com/analysisservices/2003/engine"> 
  <Folder>C:\Program Files\Microsoft SQL Server\MSAS15\OLAP\Data\AdventureWorks.0.db\</Folder> 
  <AllowOverwrite>True</AllowOverwrite> 
</Attach> 
```

Dieser Vorgang erfordert möglicherweise eine *Verdopplung des Modellspeichers*, um die alte Version beim Laden der neuen Version online beizubehalten. 

Ein typisches Verwendungsmuster wäre: 

1. DB1 (Version 1) ist bereits auf einem schreibgeschützten Server B angefügt. 

2. DB1 (Version 2) wird auf dem Schreibserver A verarbeitet. 

3. DB1 (Version 2) wird getrennt und an einem Speicherort platziert, auf den Server B zugreifen kann (entweder über einen freigegebenen Speicherort oder mithilfe von Robocopy usw.). 

4. Der <Attach>-Befehl mit AllowOverwrite=True wird auf Server B mit dem neuen Speicherort von DB1 (Version 2) ausgeführt. 

Ohne dieses Feature müssen Administratoren zunächst die Datenbank trennen und dann die neue Version der Datenbank anfügen. Dies führt zu Ausfallzeiten, wenn die Datenbank für Benutzer nicht verfügbar ist, und bei Abfragen an die Datenbank treten Fehler auf. 

Wenn dieses neue Flag angegeben ist, wird Version 1 der Datenbank atomarisch innerhalb derselben Transaktion gelöscht, ohne dass Ausfallzeiten auftreten. Allerdings werden die beiden Datenbanken gleichzeitig in den Arbeitsspeicher geladen. 


#### <a name="many-to-many-ctp24"></a>m:n-Beziehungen in tabellarischen Modellen (CTP 2.4)

Dieses Feature ermöglicht m:n-Beziehungen zwischen Tabellen, in denen beide Spalten nicht eindeutig sind. Eine Beziehung kann zwischen einer Dimension und einer Faktentabelle mit einer Granularität, die höher als die der Schlüsselspalte der Dimension ist, definiert werden. Dies vermeidet die Normalisierung von Dimensionstabellen und verbessert möglicherweise die Benutzerfreundlichkeit, da das resultierende Modell eine geringere Anzahl von Tabellen mit logisch gruppierten Spalten enthält. In diesem CTP 2.4-Release sind m:n-Beziehungen Engine-spezifische Features. 

Für m:n-Beziehungen müssen Modelle den Kompatibilitätsgrad 1470 aufweisen, der derzeit nur in [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] CTP 2.3 und höher unterstützt wird. In diesem CTP 2.4-Release können m:n-Beziehungen mithilfe der Tabellenobjektmodell-API, Tabular Model Scripting Language (TMSL) und dem Open Source-Tool „Tabular Editor“ erstellt werden. Die Unterstützung in SQL Server Data Tools (SSDT) und die Dokumentation werden in einem späteren Release veröffentlicht. Weitere Informationen zu diesem und anderen Featurereleases für CTP werden auf dem Analysis Services-Blog bekannt gegeben.

#### <a name="property-ctp24"></a>Arbeitsspeichereinstellungen für die Ressourcenkontrolle (CTP 2.4)

Die hier beschriebenen Arbeitsspeichereinstellungen stehen bereits in Azure Analysis Services zur Verfügung. Ab CTP 2.4 werden sie auch von [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] Analysis Services unterstützt. 

- **Memory\QueryMemoryLimit:** Diese Arbeitsspeichereigenschaft kann zum Einschränken von Arbeitsspeicherspools verwendet werden, die mit DAX-Abfragen erstellt werden, die an das Modell übermittelt wurden. 
- **DbpropMsmdRequestMemoryLimit:** Diese XMLA-Eigenschaft kann zum Überschreiben des Servereigenschaftenwerts „Memory\QueryMemoryLimit“ für eine Verbindung verwendet werden.
- **OLAP\Query\RowsetSerializationLimit:** Mit dieser Servereigenschaft wird die Anzahl der zurückgegebenen Zeilen in einem Rowset eingeschränkt, wodurch die Serverressourcen vor der ausgiebigen Nutzung von Datenexporten geschützt werden. Diese Eigenschaft gilt für DAX- und MDX-Abfragen.

Diese Eigenschaften können mit der neuesten Version von SSMS (SQL Server Management Studio) festgelegt werden. Weitere Informationen zu diesem Feature finden Sie im Analysis Services-Blog.

#### <a name="calc-ctp24"></a>Berechnungsgruppen in tabellarischen Modellen (CTP 2.3) 

Berechnungsgruppen werden für das häufig auftretende Problem in komplexen Modellen eingesetzt, dass eine Vielzahl von Measures die gleichen Berechnungen verwenden, z.B. Zeitintelligenzfunktionen. Berechnungsgruppen werden in Berichterstellungsclients als Tabelle mit einer einzigen Spalte angezeigt. Jeder Wert in der Spalte stellt eine wiederverwendbare Berechnung oder ein Berechnungselement dar, das auf beliebige Measures angewendet werden kann.  

In einer Berechnungsgruppe können beliebig viele Berechnungselemente vorhanden sein. Jedes Berechnungselement wird durch einen DAX-Ausdruck definiert. Drei neue DAX-Funktionen wurden für Berechnungsgruppen eingeführt: 

- `SELECTEDMEASURE()`: Gibt einen Verweis auf das Measure zurück, das sich derzeit im Kontext befindet.  

- `SELECTEDMEASURENAME()`: Gibt eine Zeichenfolge zurück, die den Namen des Measures zurück, das sich derzeit im Kontext befindet.  

- `ISSELECTEDMEASURE(M1, M2, …)`: Gibt einen booleschen Wert zurück, der angibt, ob das Measure, das sich derzeit im Kontext befindet, eines der Measures ist, die als Argument angegeben wurden.

Zusätzlich zu den neuen DAX-Funktionen wurden zwei neue dynamische Verwaltungssichten eingeführt:

- `TMSCHEMA_CALCULATION_GROUPS`  
- `TMSCHEMA_CALCULATION_ITEMS`  

##### <a name="limitations-in-this-release"></a>Einschränkungen in diesem Release:

- Die Funktion `ALLSELECTED DAX` wird noch nicht unterstützt.
- Die Sicherheit auf Zeilenebene in der Tabelle der Berechnungsgruppe wird noch nicht unterstützt.
- Die Sicherheit auf Objektebene in der Tabelle der Berechnungsgruppe wird noch nicht unterstützt.
- DetailsRows-Ausdrücke, die auf Berechnungselemente verweisen, werden noch nicht unterstützt.
- MDX wird noch nicht unterstützt.

##### <a name="known-issues-in-this-release"></a>Bekannte Probleme in dieser Version:

- Das Vorhandensein von Berechnungsgruppen in einem Modell kann dazu führen, dass Measures Variant-Datentypen zurückgeben, die zu Aktualisierungsfehlern für berechnete Spalten und Tabellen führen können, die sich auf Measures beziehen.

##### <a name="compatibility-level"></a>Kompatibilitätsgrad

Für Berechnungsgruppen müssen Modelle den Kompatibilitätsgrad 1470 aufweisen, der derzeit nur in [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] CTP 2.3 und höher unterstützt wird. Derzeit können Berechnungsgruppen mithilfe der Tabellenobjektmodell-API, Tabular Model Scripting Language (TMSL) und dem Open Source-Tool „Tabular Editor“ erstellt werden. Die Unterstützung in SQL Server Data Tools (SSDT) und die Dokumentation werden in einem späteren Release veröffentlicht. Weitere Informationen zu diesem und anderen Featurereleases für CTP werden auf dem Analysis Services-Blog bekannt gegeben.

## <a name="see-also"></a>Siehe auch

- [PowerShell-Modul von `SqlServer`](https://www.powershellgallery.com/packages/Sqlserver)
- [SQL Server PowerShell-Dokumentation](../powershell/sql-server-powershell.md)

## <a name="next-steps"></a>Nächste Schritte

- [Versionshinweise zu [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]](sql-server-ver15-release-notes.md)

- [Microsoft [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]: Technical white paper (technisches Whitepaper)](http://info.microsoft.com/rs/157-GQE-382/images/EN-US-CNTNT-white-paper-DBMod-Microsoft-SQL-Server-2019-Technical-white-paper.pdf)<br />Veröffentlicht im September 2018. Gilt für Microsoft [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] CTP 2.0 für Windows-, Linux- und Docker-Container.

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]

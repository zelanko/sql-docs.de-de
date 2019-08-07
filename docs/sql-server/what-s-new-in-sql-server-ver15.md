---
title: Neuigkeiten zu SQL Server 2019 | Microsoft-Dokumentation
ms.date: 07/24/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: release-landing
ms.topic: article
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: caf8b23b823d7863e1bd7c8abd01ef43b0b8ec20
ms.sourcegitcommit: e821cd8e5daf95721caa1e64c2815a4523227aa4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68702896"
---
# <a name="whats-new-in-includesql-server-2019includessssqlv15-mdmd"></a>Neues in [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]

[!INCLUDE[tsql-appliesto-ss-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss-xxxx-xxxx-xxx-md.md)]

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] ist eine Erweiterung der SQL Server-Plattform basierend auf früheren Releases, die Ihnen eine große Auswahl an Entwicklungssprachen, Datentypen und Betriebssystemen sowie die Arbeit mit einer lokalen Umgebung oder der Cloud bietet.

In diesem Artikel werden die neuen Features und Verbesserungen für [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] beschrieben.

Weitere Informationen und bekannte Probleme finden Sie unter [Release Notes zu [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] (Vorschauversion)](sql-server-ver15-release-notes.md).

**Nutzen Sie die [neuesten Tools](what-s-new-in-sql-server-ver15-prerelease.md#tools) für die optimale Verwendung von [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)].**

## <a name="ctp-32-july-2019"></a>CTP 3.2 Juli 2019

CTP 3.2 (Community Technology Preview) ist das neueste öffentliche Release von [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]. Dieses Release beinhaltet Verbesserungen im Vergleich zu vorherigen CTP-Releases zum Beheben von Fehlern, zur Verbesserung der Sicherheit und zur Optimierung der Leistung. Eine Liste der Features, die in den einzelnen CTP-Releases vor [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] CTP 3.2 eingeführt oder verbessert wurden, finden Sie im [[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] CTP-Ankündigungsarchiv](what-s-new-in-sql-server-ver15-prerelease.md).

### <a name="new-in-big-data-clusters"></a>Neu in Big Data-Clustern

|Neue Funktion oder Update | Details |
|:---|:---|
|Public Preview |Vor CTP 3.2 war SQL Server-Big Data-Cluster für registrierte Early Adopter verfügbar. Dieses Release ermöglicht allen Benutzern, die Funktionen von SQL Server-Big Data-Clustern zu nutzen. <br/><br/> Weitere Informationen finden Sie unter [Einstieg in SQL Server-Big Data-Cluster](../big-data-cluster/deploy-get-started.md).|
|`azdata` |CTP 3.2 führt `azdata` ein – ein in Python geschriebenes Befehlszeilenprogramm, das Clusteradministratoren ermöglicht, den Big Data-Cluster über REST-APIs zu starten und zu verwalten. `azdata` ersetzt `mssqlctl`. Siehe [Installieren von `azdata`](../big-data-cluster/deploy-install-azdata.md). |
|PolyBase |Externe Tabellenspaltennamen werden jetzt zum Abfragen von SQL Server-, Oracle-, Teradata-, MongoDB- und ODBC-Datenquellen verwendet. In früheren CTP-Releases wurden die Spalten nur basierend auf der Ordnungszahl im Ziel gebunden und Spaltennamen in der Definition der externen Tabelle wurden nicht verwendet.|
|HDFS-Tieringaktualisierung |Einführung der Aktualisierungsfunktionalität für HDFS-Tiering, sodass eine vorhandene Einbindung für die neueste Momentaufnahme der Remotedaten aktualisiert werden kann. Weitere Informationen finden Sie unter [HDFS-Tiering](../big-data-cluster/hdfs-tiering.md). |
|Notebook-basierte Problembehandlung |CTP 3.2 stellt Jupyter-Notebooks vor, die die [Bereitstellung](../big-data-cluster/deploy-notebooks.md) und [Ermittlung, Diagnose und Problembehandlung](../big-data-cluster/manage-notebooks.md) für Komponenten in einem SQL Server-Big Data-Cluster unterstützen. |
| &nbsp; | &nbsp; |

### <a name="new-in-analysis-services"></a>Neu in Analysis Services

| Neue Funktion oder Update | Details |
|:---|:---| 
| Governanceeinstellung für Power BI-Cacheaktualisierungen.  | Der Power BI-Dienst speichert Dashboardkacheldaten und Berichtsdaten für das anfängliche Laden des Live Connect-Berichts zwischen, was dazu führt, dass eine übermäßige Anzahl von Cacheanfragen an SSAS übermittelt wird und in extremen Fällen den Server überlastet. In diesem Release wird die **ClientCacheRefreshPolicy**-Eigenschaft eingeführt. Diese Eigenschaft ermöglicht Ihnen, dieses Verhalten auf Serverebene zu überschreiben. Weitere Informationen finden Sie unter [Allgemeine Eigenschaften](../analysis-services/server-properties/general-properties.md). |
| Online anfügen  | Diese Funktion bietet die Möglichkeit, ein tabellarisches Modell als Onlinevorgang anzufügen. Onlineanfügen kann für die Synchronisierung schreibgeschützter Replikate in horizontal skalierten Umgebungen für lokale Abfragen verwendet werden. Weitere Informationen finden Sie unter [Online anfügen](what-s-new-in-sql-server-ver15-prerelease.md#online-attach-ctp32). |
| &nbsp; | &nbsp; |

### <a name="new-in-language-extensions"></a>Neu in Spracherweiterungen

|Neue Funktion oder Update | Details |
|:---|:---|
| Neue standardmäßige Java Runtime  | SQL Server umfasst jetzt Zulu Embedded von Azul System für Java-Unterstützung im gesamten Produkt. Weitere Informationen finden Sie unter [Free supported Java in SQL Server 2019 is now available](https://cloudblogs.microsoft.com/sqlserver/2019/07/24/free-supported-java-in-sql-server-2019-is-now-available/) (Kostenlose Java-Unterstützung in SQL Server 2019 jetzt verfügbar). |

### <a name="new-in-sql-server-on-linux"></a>Neu in SQL Server unter Linux

|Neue Funktion oder Update | Details |
|:---|:---|
| Unterstützung von Change Data Capture (CDC) | Change Data Capture (CDC) wird jetzt unter Linux für SQL Server 2019 unterstützt. |

## <a name="includesql-server-2019includessssqlv15-mdmd-features-by-component"></a>Features von [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] nach Komponente

In den folgenden Abschnitten werden neue Komponenten und Features hervorgehoben, die in früheren Releases von [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] verbessert wurden.

## <a name="big-data-clusters"></a>Big Data-Cluster

| Neue Funktion oder Update | Details |
|:---|:---|
| Skalierbare Big Data-Lösung | [Bereitstellen skalierbarer Cluster](../big-data-cluster/deploy-get-started.md) von SQL Server-, Spark- und HDFS-Containern, die auf Kubernetes ausgeführt werden <br/><br/> Lesen, Schreiben und Verarbeiten von Big Data von Transact-SQL oder Spark<br/><br/> Einfaches Kombinieren und Analysieren hochwertiger relationaler Daten mit hochvolumigem Big Data<br/><br/>Abfragen externer Datenquellen<br/><br/>Speichern von Big Data in von SQL Server verwaltetem HDFS<br/><br/>Abfragen von Daten aus mehreren externen Datenquellen über den Cluster<br/><br/> Verwenden der Daten für KI, Machine Learning und andere Analyseaufgaben<br/><br/> Bereitstellen und Ausführen von Anwendungen in Big Data-Clustern <br/>|
| &nbsp; | &nbsp; |

Weitere Informationen finden Sie unter [Was sind SQL Server-Big Data-Cluster?](../big-data-cluster/big-data-cluster-overview.md).

Das [[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]-Ankündigungsarchiv (CTP)](what-s-new-in-sql-server-ver15-prerelease.md) enthält eine Liste der Features, die für alle früheren CTP-Releases dieses Features angekündigt und geändert wurden.

## <a name="database-engine"></a>Datenbank-Engine

### <a name="security"></a>Security

|Neue Funktion oder Update | Details |
|:---|:---|
|Funktionseinschränkungen| Verhindern bei einigen Formen der Einschleusung von SQL-Befehlen auch dann die Offenlegung von Informationen über die Datenbank, wenn die Einschleusung erfolgreich ist. Siehe [Funktionseinschränkungen](../relational-databases/security/feature-restrictions.md).|
|Indizieren verschlüsselter Spalten|Erstellen Sie Indizes für Spalten, die mit einer zufälligen Verschlüsselung und Enclave-fähigen Schlüsseln verschlüsselt wurden, um die Leistung umfangreicher Abfragen (mit `LIKE` und Vergleichsoperatoren) zu verbessern. Weitere Informationen finden Sie unter [Always Encrypted mit Secure Enclaves](../relational-databases/security/encryption/always-encrypted-enclaves.md).
|Anhalten und Fortsetzen der anfänglichen Überprüfung für Transparent Data Encryption (TDE)|Siehe [TDE-Überprüfung (Transparent Data Encryption): Anhalten und Fortsetzen](../relational-databases/security/encryption/transparent-data-encryption.md#scan-suspend-resume).|
|Zertifikatverwaltung im SQL Server-Konfigurations-Manager|Siehe [Zertifikatverwaltung (SQL Server-Konfigurations-Manager)](../database-engine/configure-windows/manage-certificates.md).
| &nbsp; | &nbsp; |


### <a name="graph"></a>Diagramm

|Neue Funktion oder Update | Details |
|:---|:---|
|Kaskadierende Löschaktionen für Edgeeinschränkung |Definieren von kaskadierenden Löschaktionen für eine Edgeeinschränkung in einer Graphdatenbank Siehe [Edgeeinschränkungen](../relational-databases/tables/graph-edge-constraints.md). |
|Neue Graphfunktion: `SHORTEST_PATH` | Verwenden Sie `SHORTEST_PATH` in `MATCH`, um den kürzesten Pfad zwischen zwei Knoten in einem Graph zu ermitteln oder beliebige Längentraversierungen durchzuführen.|
|Partitionierte Tabellen und Indizes| Die Daten partitionierter Tabellen und Indizes werden in Einheiten aufgeteilt, die über mehrere Dateigruppen in einer Graphdatenbank verteilt sein können. |
|Verwenden von abgeleiteten Tabellen- oder Ansichtsaliasen in Graphabgleichsabfragen |Siehe [Graph-Edgeeinschränkungen](../relational-databases/tables/graph-edge-constraints.md). |
| &nbsp; | &nbsp; |

### <a name="indexes"></a>Indizes

|Neue Funktion oder Update | Details |
|:---|:---|
|`OPTIMIZE_FOR_SEQUENTIAL_KEY`|Diese Option aktiviert eine Optimierung in der Datenbank-Engine, die den Durchsatz für Einfügevorgänge mit hoher Parallelität in den Index verbessert. Diese Option ist für Indizes vorgesehen, die anfällig für Konflikte durch Einfügevorgänge auf der letzten Seite sind. Dieser Fall tritt häufig bei Indizes mit fortlaufendem Schlüssel auf. Dazu zählen beispielsweise Identitätsspalten, Sequenzspalten oder Spalten für Datum und Uhrzeit. Weitere Informationen finden Sie unter [CREATE INDEX](../t-sql/statements/create-index-transact-sql.md#sequential-keys).|
|Erstellen und Neuerstellen eines gruppierten Columnstore-Onlineindex | Siehe [Ausführen von Onlineindexvorgängen](../relational-databases/indexes/perform-index-operations-online.md). |
| &nbsp; | &nbsp; |

### <a name="in-memory-databases"></a>In-Memory-Datenbanken

|Neue Funktion oder Update | Details |
|:---|:---|
|DDL-Steuerelement für den hybriden Pufferpool |Mit dem [hybriden Pufferpool](../database-engine/configure-windows/hybrid-buffer-pool.md) kann bei Bedarf direkt auf Datenbankseiten in Datenbankdateien zugegriffen werden, die sich auf einem Gerät mit beständigem Arbeitsspeicher (PMEM) befinden.|
|Speicheroptimierte tempdb-Metadaten|Informationen finden Sie unter [Speicheroptimierte TempDB-Metadaten](../relational-databases/databases/tempdb-database.md#memory-optimized-tempdb-metadata).|
| &nbsp; | &nbsp; |

### <a name="linked-servers"></a>Verbindungsserver

|Neue Funktion oder Update | Details |
|:---|:---|
|Verbindungsserver unterstützen UTF-8-Zeichencodierung. |[Collation and Unicode Support](../relational-databases/collations/collation-and-unicode-support.md) |
| &nbsp; | &nbsp; |

### <a name="polybase"></a>PolyBase

|Neue Funktion oder Update | Details |
|:---|:---|
|PolyBase |Externe Tabellenspaltennamen werden jetzt zum Abfragen von SQL Server-, Oracle-, Teradata-, MongoDB- und ODBC-Datenquellen verwendet. |
| &nbsp; | &nbsp; |

### <a name="collation"></a>Sortierung

|Neue Funktion oder Update | Details |
|:---|:---|
|Unterstützung von UTF-8-Zeichencodierung |Aktiviert für eine BIN2-Sortierung (`Latin1_General_100_BIN2_UTF8`). Siehe [Sortierung und Unicode-Unterstützung](../relational-databases/collations/collation-and-unicode-support.md). |
|Auswahl der UTF-8-Sortierung als Standard beim Setup | Siehe [Sortierung und Unicode-Unterstützung](../relational-databases/collations/collation-and-unicode-support.md#ctp23). |
| &nbsp; | &nbsp; |

### <a name="server-settings"></a>Servereinstellungen

|Neue Funktion oder Update | Details |
|:---|:---|
|Festlegen der Serverarbeitsspeicherwerte `MIN` und `MAX` beim Setup |Während des Setups können Sie die Serverarbeitsspeicherwerte festlegen. Verwenden Sie die Standardwerte, die berechneten empfohlenen Werte, oder geben Sie manuell eigene Werte an, wenn Sie die **empfohlene** Option [Serverkonfigurationsoptionen für den Serverarbeitsspeicher](../database-engine/configure-windows/server-memory-server-configuration-options.md#setting-the-memory-options-manually) ausgewählt haben.|
|SQL Server Setup aktiviert MAXDOP-Einstellungen. |Neue Empfehlungen folgen den dokumentierten Richtlinien. [Konfigurieren der Serverkonfigurationsoption Max. Grad an Parallelität](../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md#Guidelines)|
|Hybrider Pufferpool| Neues Feature der SQL Server-Datenbank-Engine, mit dem Sie bei Bedarf direkt auf Datenbankseiten in Datenbankdateien zugreifen können, die sich auf einem Gerät mit beständigem Arbeitsspeicher (PMEM) befinden. Siehe [Hybrider Pufferpool](../database-engine/configure-windows/hybrid-buffer-pool.md).|
| &nbsp; | &nbsp; |

### <a name="performance-monitoring"></a>Leistungsüberwachung

|Neue Funktion oder Update | Details |
|:---|:---|
|Inlining benutzerdefinierter Skalarfunktionen |Wandelt die entsprechenden benutzerdefinierten Skalarfunktionen (UDF) automatisch in relationale Ausdrücke um und bettet sie in die aufrufende SQL-Abfrage ein. Siehe [Inlining benutzerdefinierter Skalarfunktionen](../relational-databases/user-defined-functions/scalar-udf-inlining.md). |
| `sys.dm_exec_requests`-Spalten-`command` | Zeigt `SELECT (STATMAN)` an, wenn ein `SELECT`-Objekt darauf wartet, dass ein synchroner Statistikupdatevorgang abgeschlossen wird, bevor die Abfrage weiter ausgeführt wird. Siehe [`sys.dm_exec_requests`](../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md).|
|`WAIT_ON_SYNC_STATISTICS_REFRESH` | Neuer Wartetyp in der dynamischen `sys.dm_os_wait_stats`-Verwaltungssicht. Er zeigt die kumulierte Zeit auf Instanzebene für synchrone Statistikaktualisierungen an. Siehe [`sys.dm_os_wait_stats`](../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md).|
|Angepasste Erfassungsrichtlinie für den Abfragespeicher|Bei Aktivierung stehen zusätzliche Abfragespeicherkonfigurationen unter einer neuen Einstellung für die Erfassungsrichtlinie des Abfragespeichers zur Verfügung, um die Datensammlung auf einem bestimmten Server zu optimieren. Weitere Informationen finden Sie unter [ALTER DATABASE SET-Optionen](../t-sql/statements/alter-database-transact-sql-set-options.md).|
|`sys.dm_exec_query_plan_stats` |Die neue dynamische Verwaltungsfunktion gibt das Äquivalent des letzten bekannten tatsächlichen Ausführungsplans für die meisten Abfragen zurück. Siehe [sys.dm_exec_query_plan_stats](../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-stats-transact-sql.md).|
|`LAST_QUERY_PLAN_STATS` | Neue datenbankweite Konfiguration zur Aktivierung von `sys.dm_exec_query_plan_stats`. Finden Sie unter [ALTER ausgelegte DATENBANKKONFIGURATION](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md).|
|`LIGHTWEIGHT_QUERY_PROFILING`|Neue datenbankweite Konfiguration. Siehe [`LIGHTWEIGHT_QUERY_PROFILING`](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md#lqp). |
|`query_post_execution_plan_profile` | Im Gegensatz zum Ereignis `query_post_execution_showplan`, das die Standardprofilerstellung nutzt, erfasst das neue erweiterte Ereignis das Äquivalent eines tatsächlichen Ausführungsplans mithilfe einfacher Profilerstellung. Siehe [Profilerstellungsinfrastruktur für Abfragen](../relational-databases/performance/query-profiling-infrastructure.md).|
|Feedback zur Speicherzuweisung im Zeilenmodus |[Feedback zur Speicherzuweisung im Zeilenmodus](../relational-databases/performance/intelligent-query-processing.md#row-mode-memory-grant-feedback) |
|Verzögerte Kompilierung von Tabellenvariablen|[Verzögerte Kompilierung von Tabellenvariablen](../relational-databases/performance/intelligent-query-processing.md#table-variable-deferred-compilation) |
|Geschätzte `COUNT DISTINCT`-Werte|[Geschätzte Abfrageverarbeitung](../relational-databases/performance/intelligent-query-processing.md#approximate-query-processing)|
|Batchmodus bei Rowstore|[Batchmodus bei Rowstore](../relational-databases/performance/intelligent-query-processing.md#batch-mode-on-rowstore) |

### <a name="language-extensions"></a>Spracherweiterungen

|Neue Funktion oder Update | Details |
|:---|:---|
|Neues Java-Sprach-SDK | Vereinfacht die Entwicklung von Java-Programmen, die von SQL Server ausgeführt werden können. Weitere Informationen finden Sie unter [What's new in SQL Server Machine Learning Services (Neuerungen in SQL Server-Machine Learning Services)](../advanced-analytics/what-s-new-in-sql-server-machine-learning-services.md). |
|SQL Server-Spracherweiterungen – [Java-Spracherweiterung](https://docs.microsoft.com/sql/language-extensions/language-extensions-overview)|Das [Microsoft-SDK für Java-Erweiterung für Microsoft SQL Server](https://docs.microsoft.com/sql/language-extensions/how-to/extensibility-sdk-java-sql-server) ist jetzt Open Source und [auf GitHub verfügbar](https://github.com/microsoft/sql-server-language-extensions).|
|Registrieren externer Sprachen|In einer neuen DDL, `CREATE EXTERNAL LANGUAGE`, werden externe Sprachen (z.B. Java) in SQL Server registriert. Informationen finden Sie unter [CREATE EXTERNAL LANGUAGE](../t-sql/statements/create-external-language-transact-sql.md). |
|Unterstützung für Java-Datentypen|Informationen finden Sie unter [Java-Datentypen](../language-extensions/how-to/java-to-sql-data-types.md).|

### <a name="spatial"></a>Räumlich

|Neue Funktion oder Update | Details |
|:---|:---|
| Neue SRIDs (Spatial Reference Identifiers) |Das [australische GDA2020](http://www.ga.gov.au/scientific-topics/positioning-navigation/geodesy/datums-projections/gda2020) stellt robustere und genauere Datumsangaben bereit, die stärker an GPS-Systemen ausgerichtet sind. Die neuen SRIDs sind:<br/><br/> 7843: geografisches 2D-CRS<br/> 7844: geografisches 3D-CRS <br/><br/>Die Ansicht von [sys.spatial_reference_systems](../relational-databases/system-catalog-views/sys-spatial-reference-systems-transact-sql.md) enthält die Definitionen der neuen SRIDs. |
| &nbsp; | &nbsp; |

### <a name="performance"></a>Leistung

|Neue Funktion oder Update | Details |
|:---|:---|
|Verbesserte Wiederherstellung von Datenbanken | Aktivieren der verbesserten Wiederherstellung von Datenbanken pro Datenbank. Siehe [Verbesserte Wiederherstellung von Datenbanken](../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md#adr).|
|Erzwingen von schnellen Vorwärts- und statischen Cursorn | Durch den Abfragespeicherplan erzwungene Unterstützung für schnelle Vorwärts- und statische Cursor Siehe [Erzwingen eines Plans für schnelle Vorwärts- und statische Cursor](../relational-databases/performance/monitoring-performance-by-using-the-query-store.md#ctp23).|
|Weniger Neukompilierungen für Workloads| Verbessert die Verwendung temporärer Tabellen über mehrere Bereiche hinweg. Siehe [Weniger Neukompilierungen für Workloads](../relational-databases/tables/tables.md#ctp23). |
|Skalierbarkeit indirekter Prüfpunkte |Siehe [Verbesserte Skalierbarkeit indirekter Prüfpunkte](../relational-databases/logs/database-checkpoints-sql-server.md#ctp23).|
| &nbsp; | &nbsp; |

### <a name="availability-groups"></a>Verfügbarkeitsgruppen

|Neue Funktion oder Update | Details |
|:---|:---|
|Bis zu fünf synchrone Replikate|In [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] wird die maximale Anzahl der synchronen Replikate von ehemals 3 in [!INCLUDE[ssSQL17](../includes/sssql17-md.md)] auf 5 erhöht. Sie können diese Gruppe aus fünf Replikaten für das automatische Failover in der Gruppe konfigurieren. Es gibt ein primäres Replikat sowie vier synchrone sekundäre Replikate.|
|Umleiten der Verbindung vom sekundären zum primären Replikat| Durch dieses Feature können Clientanwendungsverbindungen zum primären Replikat weitergeleitet werden, unabhängig davon, ob der Zielserver in der Verbindungszeichenfolge angegeben ist. Weitere Informationen finden Sie unter [Umleitung von Lese-/Schreibverbindungen vom sekundären zum primären Replikat (Always On-Verfügbarkeitsgruppen)](../database-engine/availability-groups/windows/secondary-replica-connection-redirection-always-on-availability-groups.md).|
| &nbsp; | &nbsp; |

### <a name="error-messages"></a>Fehlermeldungen

|Neue Funktion oder Update | Details |
|:---|:---|
|Kürzungswarnungen | Fehlermeldungen für die Kürzung enthalten standardmäßig die Tabellen- und Spaltennamen sowie den gekürzten Wert. Siehe [VERBOSE_TRUNCATION_WARNINGS](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md#verbose-truncation).|
| &nbsp; | &nbsp; |

## <a name="sql-server-on-linux"></a>SQL Server unter Linux

| Neue Funktion oder Update | Details |
|:-----|:-----|
|Neue Containerregistrierung|[Get started with SQL Server containers on Docker (Erste Schritte mit SQL Server-Containern unter Docker)](../linux/quickstart-install-connect-docker.md) |
|Always On-Verfügbarkeitsgruppe in Docker-Containern mit Kubernetes |[Always On Availability Groups for containers (Always On-Verfügbarkeitsgruppen für Container)](../linux/sql-server-ag-kubernetes.md) |
|Replikationsunterstützung |[SQL Server Replication on Linux (SQL Server-Replikation unter Linux)](../linux/sql-server-linux-replication.md)
|Unterstützung für den Microsoft Distributed Transaction Coordinator (MSDTC) |[How to configure MSDTC on Linux (Vorgehensweise: Konfigurieren von MSDTC unter Linux)](../linux/sql-server-linux-configure-msdtc.md) |
|OpenLDAP-Unterstützung für AD-Drittanbieter |[Tutorial: Use Active Directory authentication with SQL Server on Linux (Tutorial: Verwenden der Azure Active Directory-Authentifizierung mit SQL Server unter Linux)](../linux/sql-server-linux-active-directory-authentication.md) |
|Machine Learning unter Linux |[Configure Machine Learning on Linux (Konfigurieren von Machine Learning unter Linux)](../linux/sql-server-linux-setup-machine-learning.md) |
|Tempdb-Verbesserungen | Standardmäßig erstellt eine neue Installation von SQL Server für Linux mehrere tempdb-Datendateien, deren Anzahl sich nach der Anzahl der logischen Kerne richtet (bis zu acht Datendateien). Das gilt nicht für direkte Upgrades der Neben- oder Hauptversion. Jede tempdb-Datei ist 8 MB groß und wird automatisch um 64 MB vergrößert. Dieses Verhalten ähnelt dem der SQL Server-Standardinstallation unter Windows. |
| PolyBase unter Linux | [Installieren Sie PolyBase](../relational-databases/polybase/polybase-linux-setup.md) für Nicht-Hadoop-Connectors unter Linux.<br/><br/>[PolyBase type mapping (Typzuordnung mit PolyBase)](../relational-databases/polybase/polybase-type-mapping.md) |
| &nbsp; | &nbsp; |

## <a id="ml"></a>SQL Server-Machine Learning-Dienste

|Neue Funktion oder Update | Details |
|:---|:---|
|Partitionsbasierte Modellierung|`sp_execute_external_script` wurde um die partitionsbasierte Verarbeitung von externen Skripts Ihrer Daten mit den neuen Parametern erweitert. Diese Funktion unterstützt anstelle eines großen Modells das Trainieren von einer Vielzahl kleiner Modelle (ein Modell pro Datenpartition). Siehe [Erstellen von partitionsbasierten Modellen](../advanced-analytics/tutorials/r-tutorial-create-models-per-partition.md).|
|Windows Server-Failovercluster| Konfigurieren Sie Hochverfügbarkeit für Machine Learning Services in einem Windows Server-Failovercluster.|
| &nbsp; | &nbsp; |

## [!INCLUDE[master-data-services](../includes/ssmdsshort-md.md)]

| Neue Funktion oder Update | Details |
|:---|:---|
|Unterstützt Datenbanken mit verwalteter Azure SQL-Datenbank-Instanz.| Hosten von [!INCLUDE[master-data-services](../includes/ssmdsshort-md.md)] auf einer verwalteten Instanz. Informationen finden Sie unter [[!INCLUDE[master-data-services](../includes/ssmdsshort-md.md)]-Installation und -Konfiguration](../master-data-services/master-data-services-installation-and-configuration.md#SetUpWeb).|
|Neue HTML-Steuerelemente| HTML-Steuerelemente ersetzen alle früheren Silverlight-Komponenten. Die Silverlight-Abhängigkeit wurde aufgehoben.|
| &nbsp; | &nbsp; |

## <a name="analysis-services"></a>Analysis Services

| Neue Funktion oder Update | Details |
|:---|:---|
|Berechnungsgruppen in einem tabellarischen Modell| [Berechnungsgruppen in einem tabellarischen Modell](what-s-new-in-sql-server-ver15-prerelease.md#calc-ctp24) |
|Unterstützung von MDX-Abfragen für tabellarische Modelle mit Berechnungsgruppen | Siehe [Berechnungsgruppen](what-s-new-in-sql-server-ver15-prerelease.md#calc-ctp24). |
|Dynamische Formatierung von Measures mithilfe von Berechnungsgruppen |Mit dieser Funktion können Sie Formatzeichenfolgen für Measures mit [Berechnungsgruppen](what-s-new-in-sql-server-ver15-prerelease.md#calc-ctp24) bedingt ändern. Beispielsweise kann mit der Währungsumrechnung ein Measure in verschiedenen Fremdwährungsformaten angezeigt werden.|
|M:n-Beziehungen in tabellarischen Modellen|[m:n-Beziehungen in tabellarischen Modellen](what-s-new-in-sql-server-ver15-prerelease.md#many-to-many-ctp24)|
|Eigenschafteneinstellungen für die Ressourcenkontrolle|[Eigenschafteneinstellungen für die Ressourcenkontrolle](what-s-new-in-sql-server-ver15-prerelease.md#property-ctp24)|
| &nbsp; | &nbsp; |

[!INCLUDE[ctp-support-exclusion](../includes/ctp-support-exclusion.md)]

Informationen zu bestimmten Funktionen, die vom Support ausgeschlossen sind, finden Sie in den [Release Notes](sql-server-ver15-release-notes.md).

Außerdem wurden die folgenden Funktionen für [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] CTP 3.2 hinzugefügt oder verbessert.

## <a name="see-also"></a>Siehe auch

- [PowerShell-Modul von `SqlServer`](https://www.powershellgallery.com/packages/Sqlserver)
- [SQL Server PowerShell-Dokumentation](../powershell/sql-server-powershell.md)

## <a name="next-steps"></a>Nächste Schritte

- [Versionshinweise zu [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]](sql-server-ver15-release-notes.md)

- [Microsoft [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]: Technical white paper (technisches Whitepaper)](http://info.microsoft.com/rs/157-GQE-382/images/EN-US-CNTNT-white-paper-DBMod-Microsoft-SQL-Server-2019-Technical-white-paper.pdf)<br />Veröffentlicht im September 2018. Gilt für Microsoft [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] CTP 2.0 für Windows-, Linux- und Docker-Container.

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]

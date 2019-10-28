---
title: Neuigkeiten zu SQL Server 2019 | Microsoft-Dokumentation
ms.date: 08/28/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: release-landing
ms.topic: article
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: bb83237e33f477468cd58ea8a692970268bf1d66
ms.sourcegitcommit: f912c101d2939084c4ea2e9881eb98e1afa29dad
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2019
ms.locfileid: "72807471"
---
# <a name="whats-new-in-includesql-server-2019includessssqlv15-mdmd"></a>Neues in [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]

[!INCLUDE[tsql-appliesto-ss-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss-xxxx-xxxx-xxx-md.md)]

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] ist eine Erweiterung der SQL Server-Plattform basierend auf früheren Releases, die Ihnen eine große Auswahl an Entwicklungssprachen, Datentypen und Betriebssystemen sowie die Arbeit mit einer lokalen Umgebung oder der Cloud bietet.

In diesem Artikel werden die neuen Features und Verbesserungen für [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] beschrieben.

Weitere Informationen und bekannte Probleme finden Sie unter [Release Notes zu [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] (Vorschauversion)](sql-server-ver15-release-notes.md).

**Nutzen Sie die [neuesten Tools](what-s-new-in-sql-server-ver15-prerelease.md#tools) für die optimale Verwendung von [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)].**

>[!NOTE]
>Der Inhalt wird für den [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] Release Candidate veröffentlicht. Der Release Candidate ist eine Vorabversion der Software. Änderungen an den bereitgestellten Informationen vorbehalten. Informationen zu Supportszenarien finden Sie unter [Support](#support).
>
>Diese Version umfasst Verbesserungen, die zuvor in Community Technology Preview-Releases (CTP) angekündigt wurden. Zu diesen Verbesserungen gehören neu hinzugefügte Features, behobene Fehler, eine verbesserte Sicherheit und eine optimierte Leistung. Eine Liste der Features, die in den CTP-Releases vor [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] Release Candidate eingeführt oder verbessert wurden, finden Sie im [[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] CTP-Ankündigungsarchiv](what-s-new-in-sql-server-ver15-prerelease.md).

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] führt [!INCLUDE[big-data-clusters](../includes/ssbigdataclusters-nover.md)] für [!INCLUDE[sql-server](../includes/ssnoversion-md.md)] ein. Außerdem werden zusätzliche Funktionen und Verbesserungen für die SQL Server-Datenbank-Engine, SQL Server Analysis Services, SQL Server Machine Learning Services, SQL Server für Linux und SQL Server Master Data Services bereitgestellt.

Die folgenden Abschnitte bieten eine Übersicht über diese Features.

## <a name="data-virtualization-and-includebig-data-clusters-2019includesssbigdataclusters-ver15md"></a>Datenvirtualisierung und [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]

Unternehmen verfügen heute über umfangreiche Datensammlungen bestehend aus Datasets, deren Umfang stetig wächst und die in Datenquellensilos über das gesamte Unternehmen hinweg gehostet werden. Mit [!INCLUDE[big-data-clusters](../includes/ssbigdataclusters-nover.md)] erhalten Sie Einblicke in nahezu Echtzeit in all Ihre Daten. Dies erfolgt über eine vollständige Umgebung für die Arbeit mit umfangreichen Datasets, einschließlich Machine Learning und künstlicher Intelligenz.

| Neue Funktion oder Update | Details |
|:---|:---|
| Skalierbare Big Data-Lösung | [Bereitstellen skalierbarer Cluster](../big-data-cluster/deploy-get-started.md) von SQL Server-, Spark- und HDFS-Containern, die auf Kubernetes ausgeführt werden <br/><br/> Lesen, Schreiben und Verarbeiten von Big Data von Transact-SQL oder Spark<br/><br/> Einfaches Kombinieren und Analysieren hochwertiger relationaler Daten mit hochvolumigem Big Data<br/><br/>Abfragen externer Datenquellen<br/><br/>Speichern von Big Data in von SQL Server verwaltetem HDFS<br/><br/>Abfragen von Daten aus mehreren externen Datenquellen über den Cluster<br/><br/> Verwenden der Daten für KI, Machine Learning und andere Analyseaufgaben<br/><br/> [Bereitstellen und Ausführen von Anwendungen](../big-data-cluster/concept-application-deployment.md) in [!INCLUDE[big-data-clusters](../includes/ssbigdataclusters-nover.md)] <br/><br/> Die SQL Server-Masterinstanz stellt Hochverfügbarkeit und Notfallwiederherstellung für alle Datenbanken mithilfe von Always On-Verfügbarkeitsgruppen bereit.<br/>|
|Datenvirtualisierung mit PolyBase | Abfragen von Daten aus externen Datenquellen in SQL Server, Oracle, Teradata, MongoDB und ODBC mit externen Tabellen, jetzt mit [Unterstützung für UTF-8-Codierung](../relational-databases/collations/collation-and-unicode-support.md). Weitere Informationen finden Sie unter [Was ist PolyBase?](../relational-databases/polybase/polybase-guide.md).|
| &nbsp; | &nbsp; |

Weitere Informationen finden Sie unter [Was sind SQL Server-[!INCLUDE[big-data-clusters](../includes/ssbigdataclusters-nover.md)]?](../big-data-cluster/big-data-cluster-overview.md).

Das [[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]-Ankündigungsarchiv (CTP)](what-s-new-in-sql-server-ver15-prerelease.md) enthält eine Liste der Features, die für alle früheren CTP-Releases dieses Features angekündigt und geändert wurden.

## <a name="intelligent-database"></a>Intelligente Datenbank

### <a name="intelligent-query-processing"></a>Intelligente Abfrageverarbeitung

|Neue Funktion oder Update | Details |
|:---|:---|
|Feedback zur Speicherzuweisung im Zeilenmodus |Erweitert die Feedbackfunktion zur Speicherzuweisung im Batchmodus, indem die Größe der Speicherzuweisung sowohl für Batch- als auch für Zeilenmodusoperatoren angepasst wird. Hierdurch können übermäßige Speicherzuweisungen korrigiert werden, die zu einer Speichervergeudung führen und die Parallelität beeinträchtigen, und es werden unzureichende Speicherzuweisungen korrigiert, die zu teuren Überläufen auf den Datenträger führen. Siehe [Feedback zur Speicherzuweisung im Zeilenmodus](../relational-databases/performance/intelligent-query-processing.md#row-mode-memory-grant-feedback). |
|Verzögerte Kompilierung von Tabellenvariablen|Verbessert die Qualität des Abfrageplans und die Gesamtleistung für Abfragen mit Verweisen auf Tabellenvariablen. Während der Optimierung und der ersten Kompilierung propagiert diese Funktion Kardinalitätsschätzungen, die auf tatsächlichen Tabellenvariablen-Zeilenzahlen basieren. Diese genauen Zeilenzahlinformationen werden für die Optimierung der nachgelagerten Planvorgänge verwendet. Siehe [Verzögerte Kompilierung von Tabellenvariablen](../relational-databases/performance/intelligent-query-processing.md#table-variable-deferred-compilation). |
|Geschätzte Abfrageverarbeitung mit `APPROX_COUNT_DISTINCT `|Für Szenarien, in denen keine absolute Genauigkeit notwendig, die Reaktionsfähigkeit aber entscheidend ist, führt `APPROX_COUNT_DISTINCT` Aggregationen über große Datasets hinweg mit weniger Ressourcen durch als `COUNT(DISTINCT())`, um die Parallelität zu verbessern. Siehe [Geschätzte Abfrageverarbeitung](../relational-databases/performance/intelligent-query-processing.md#approximate-query-processing).|
|Batchmodus bei Rowstore|Ermöglicht die Ausführung im Batchmodus, ohne dass Columnstore-Indizes erforderlich sind. Die Ausführung im Batchmodus führt zu einer effizienteren CPU-Nutzung für Analysearbeitsauslastungen, aber bis [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] wurde sie nur verwendet, wenn eine Abfrage Vorgänge mit Columnstore-Indizes enthielt. Einige Anwendungen verwenden jedoch möglicherweise Features, die keine Columnstore-Indizes unterstützen und den Batchmodus deshalb nicht nutzen können. Ab [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] wird der Batchmodus für berechtigte Analysearbeitsauslastungen aktiviert, deren Abfragen Vorgänge mit beliebigen Indextypen (Rowstore oder Columnstore) umfassen. Siehe [Batchmodus bei Rowstore](../relational-databases/performance/intelligent-query-processing.md#batch-mode-on-rowstore). |
|Inlining benutzerdefinierter Skalarfunktionen|Wandelt benutzerdefinierte Skalarfunktionen (UDF) automatisch in relationale Ausdrücke um und bettet sie in die aufrufende SQL-Abfrage ein. Diese Transformation verbessert die Leistung von Workloads, die skalare UDFs nutzen. Siehe [Inlining benutzerdefinierter Skalarfunktionen](../relational-databases/performance/intelligent-query-processing.md#scalar-udf-inlining).|
| &nbsp; | &nbsp; |


### <a name="in-memory-database"></a>In-Memory Database

|Neue Funktion oder Update | Details |
|:---|:---|
|Hybrider Pufferpool| Neues Feature von [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)], mit dem bei Bedarf direkt auf Datenbankseiten in Datenbankdateien zugegriffen werden, die sich auf einem Gerät mit beständigem Arbeitsspeicher (PMEM) befinden. Siehe [Hybrider Pufferpool](../database-engine/configure-windows/hybrid-buffer-pool.md).|
|Speicheroptimierte TempDB-Metadaten| Mit [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] wird eine neue Funktion eingeführt, die Teil der [In-Memory Database](../relational-databases/in-memory-database.md)-Featurefamilie ist. Hierbei handelt es sich um speicheroptimierte TempDB-Metadaten, durch die dieser Engpass effektiv behoben wird und sich eine neue Ebene der Skalierbarkeit für TempDB-intensive Workloads ergibt. In [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] können die Systemtabellen, die an der Verwaltung von Metadaten temporärer Tabellen beteiligt sind, in nicht dauerhafte speicheroptimierte Tabellen ohne Latches verschoben werden. Informationen finden Sie unter [Speicheroptimierte TempDB-Metadaten](../relational-databases/databases/tempdb-database.md#memory-optimized-tempdb-metadata).|
| Unterstützung von In-Memory-OLTP für Datenbank-Momentaufnahmen | [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] führt Unterstützung für das Erstellen von [Datenbank-Momentaufnahmen](../relational-databases/databases/database-snapshots-sql-server.md) von Datenbanken mit speicheroptimierten Dateigruppen ein. |
| &nbsp; | &nbsp; |

### <a name="intelligent-performance"></a>Intelligente Leistung

|Neue Funktion oder Update | Details |
|:---|:---|
|`OPTIMIZE_FOR_SEQUENTIAL_KEY`|Diese Option aktiviert eine Optimierung in der [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)], die den Durchsatz für Einfügevorgänge mit hoher Parallelität in den Index verbessert. Diese Option ist für Indizes vorgesehen, die anfällig für Konflikte durch Einfügevorgänge auf der letzten Seite sind. Dieser Fall tritt häufig bei Indizes mit fortlaufendem Schlüssel auf. Dazu zählen beispielsweise Identitätsspalten, Sequenzspalten oder Spalten für Datum und Uhrzeit. Weitere Informationen finden Sie unter [CREATE INDEX](../t-sql/statements/create-index-transact-sql.md#sequential-keys).|
|Erzwingen von schnellen Vorwärts- und statischen Cursorn | Durch den Abfragespeicherplan erzwungene Unterstützung für schnelle Vorwärts- und statische Cursor Siehe [Erzwingen eines Plans für schnelle Vorwärts- und statische Cursor](../relational-databases/performance/monitoring-performance-by-using-the-query-store.md#ctp23).|
|Ressourcengovernance| Der Datentyp des konfigurierbaren Werts für die Option `REQUEST_MAX_MEMORY_GRANT_PERCENT` von `CREATE WORKLOAD GROUP` und `ALTER WORKLOAD GROUP` wurde geändert und entspricht nun nicht mehr einem Integer, sondern einer Gleitkommazahl. Dadurch können Speichergrößen präziser festgelegt werden. Weitere Informationen finden Sie unter [ALTER WORKLOAD GROUP](../t-sql/statements/alter-workload-group-transact-sql.md) und [CREATE WORKLOAD GROUP](../t-sql/statements/create-workload-group-transact-sql.md).|
|Weniger Neukompilierungen für Workloads| Verbessert die Verwendung temporärer Tabellen über mehrere Bereiche hinweg. Siehe [Weniger Neukompilierungen für Workloads](../relational-databases/tables/tables.md#ctp23). |
|Skalierbarkeit indirekter Prüfpunkte |Siehe [Verbesserte Skalierbarkeit indirekter Prüfpunkte](../relational-databases/logs/database-checkpoints-sql-server.md#ctp23).|
|Parallele PFS-Aktualisierungen|[PFS-Seiten](https://techcommunity.microsoft.com/t5/SQL-Server/Under-the-covers-GAM-SGAM-and-PFS-pages/ba-p/383125) sind spezielle Seiten innerhalb einer Datenbankdatei, die SQL Server verwendet, um beim Zuweisen von Speicherplatz für ein Objekt freien Speicherplatz zu ermitteln. Latchkonflikte für PFS-Seiten stehen häufig in Zusammenhang mit [`tempdb`](https://support.microsoft.com/en-us/help/2154845/recommendations-to-reduce-allocation-contention-in-sql-server-tempdb-d), können aber auch für Benutzerdatenbanken auftreten, wenn viele parallele Threads zur Objektzuweisung vorliegen. Diese Verbesserung ändert die Verwaltung paralleler Vorgänge bei PFS-Aktualisierungen, sodass die Aktualisierung nicht mit einem exklusiven Latch, sondern über einen gemeinsamen Latch erfolgen kann. Dieses Verhalten ist ab [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] in allen Datenbanken (`tempdb` eingeschlossen) standardmäßig aktiviert.|
| &nbsp; | &nbsp; |

### <a name="monitoring"></a>Überwachung

|Neue Funktion oder Update | Details |
|:---|:---|
|`WAIT_ON_SYNC_STATISTICS_REFRESH` | Neuer Wartetyp in der dynamischen `sys.dm_os_wait_stats`-Verwaltungssicht. Er zeigt die kumulierte Zeit auf Instanzebene für synchrone Statistikaktualisierungen an. Siehe [`sys.dm_os_wait_stats`](../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md).|
|Angepasste Erfassungsrichtlinie für den Abfragespeicher|Bei Aktivierung stehen zusätzliche Abfragespeicherkonfigurationen unter einer neuen Einstellung für die Erfassungsrichtlinie des Abfragespeichers zur Verfügung, um die Datensammlung auf einem bestimmten Server zu optimieren. Weitere Informationen finden Sie unter [ALTER DATABASE SET-Optionen](../t-sql/statements/alter-database-transact-sql-set-options.md).|
|`LIGHTWEIGHT_QUERY_PROFILING`|Neue datenbankweite Konfiguration. Siehe [`LIGHTWEIGHT_QUERY_PROFILING`](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md#lqp). |
|`sys.dm_exec_requests`-Spalten-`command` | Zeigt `SELECT (STATMAN)` an, wenn ein `SELECT`-Objekt darauf wartet, dass ein synchroner Statistikupdatevorgang abgeschlossen wird, bevor die Abfrage weiter ausgeführt wird. Siehe [`sys.dm_exec_requests`](../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md).|
|`sys.dm_exec_query_plan_stats` |Die neue dynamische Verwaltungsfunktion gibt das Äquivalent des letzten bekannten tatsächlichen Ausführungsplans für die meisten Abfragen zurück. Siehe [sys.dm_exec_query_plan_stats](../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-stats-transact-sql.md).|
|`LAST_QUERY_PLAN_STATS` | Neue datenbankweite Konfiguration zur Aktivierung von `sys.dm_exec_query_plan_stats`. Finden Sie unter [ALTER ausgelegte DATENBANKKONFIGURATION](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md).|
|`query_post_execution_plan_profile` | Im Gegensatz zum Ereignis `query_post_execution_showplan`, das die Standardprofilerstellung nutzt, erfasst das neue erweiterte Ereignis das Äquivalent eines tatsächlichen Ausführungsplans mithilfe einfacher Profilerstellung. Siehe [Profilerstellungsinfrastruktur für Abfragen](../relational-databases/performance/query-profiling-infrastructure.md).|
|`sys.dm_db_page_info(database_id, file_id, page_id, mode)` | New DMF gibt Informationen über eine Seite in einer Datenbank zurück. Weitere Informationen finden Sie unter [sys.dm_db_page_info (Transact-SQL)](../relational-databases/system-dynamic-management-views/sys-dm-db-page-info-transact-sql.md).|
| &nbsp; | &nbsp; |

## <a name="developer-experience"></a>Entwicklerumgebung

### <a name="graph"></a>Diagramm

|Neue Funktion oder Update | Details |
|:---|:---|
|Kaskadierende Löschaktionen für Edgeeinschränkung |Definieren von kaskadierenden Löschaktionen für eine Edgeeinschränkung in einer Graphdatenbank Siehe [Edgeeinschränkungen](../relational-databases/tables/graph-edge-constraints.md). |
|Neue Graphfunktion: `SHORTEST_PATH` | Verwenden Sie `SHORTEST_PATH` in `MATCH`, um den kürzesten Pfad zwischen zwei Knoten in einem Graph zu ermitteln oder beliebige Längentraversierungen durchzuführen.|
|Partitionierte Tabellen und Indizes| Die Daten partitionierter Tabellen und Indizes werden in Einheiten aufgeteilt, die über mehrere Dateigruppen in einer Graphdatenbank verteilt sein können. |
|Verwenden von abgeleiteten Tabellen- oder Ansichtsaliasen in Graphabgleichsabfragen |Siehe [MATCH-Graphabfrage](../t-sql/queries/match-sql-graph.md). |
| &nbsp; | &nbsp; |

### <a name="unicode-support"></a>Unicode-Unterstützung

|Neue Funktion oder Update | Details |
|:---|:---|
|Unterstützung der UTF-8-Zeichencodierung |Unterstützung von UTF-8-Zeichen für die Import- und Exportcodierung sowie für die Sortierung von Zeichenfolgendaten auf Datenbank- oder Spaltenebene. Damit können Anwendungen auf globale Ebene ausgeweitet werden, für die globale mehrsprachige Datenbankanwendungen und -dienste bereitgestellt werden müssen, um die Kundenanforderungen und spezifischen Marktbedingungen zu erfüllen. Siehe [Sortierung und Unicode-Unterstützung](../relational-databases/collations/collation-and-unicode-support.md).<br/><br/> [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] Release Candidate bietet UTF-8-Unterstützung für externe PolyBase-Tabellen und für Always Encrypted (sofern nicht mit Enclaves verwendet).|
| &nbsp; | &nbsp; |

### <a name="language-extensions"></a>Spracherweiterungen

|Neue Funktion oder Update | Details |
|:---|:---|
|Neues Java-Sprach-SDK | Vereinfacht die Entwicklung von Java-Programmen, die von SQL Server ausgeführt werden können. Siehe [Microsoft-SDK für Java-Erweiterung für SQL Server](../language-extensions/how-to/extensibility-sdk-java-sql-server.md). |
|Java-Sprach-SDK ist Open Source |Das [Microsoft-SDK für Java-Erweiterung für Microsoft SQL Server](https://docs.microsoft.com/sql/language-extensions/how-to/extensibility-sdk-java-sql-server) ist jetzt Open Source und [auf GitHub verfügbar](https://github.com/microsoft/sql-server-language-extensions).|
|Unterstützung für Java-Datentypen|Informationen finden Sie unter [Java-Datentypen](../language-extensions/how-to/java-to-sql-data-types.md).|
|Neue standardmäßige Java Runtime | SQL Server umfasst jetzt Zulu Embedded von Azul System für Java-Unterstützung im gesamten Produkt. Weitere Informationen finden Sie unter [Free supported Java in SQL Server 2019 is now available](https://cloudblogs.microsoft.com/sqlserver/2019/07/24/free-supported-java-in-sql-server-2019-is-now-available/) (Kostenlose Java-Unterstützung in SQL Server 2019 jetzt verfügbar). |
|SQL Server-Spracherweiterungen| Ausführung von externem Code mit dem Erweiterungsframework. Siehe [SQL Server-Spracherweiterungen](https://docs.microsoft.com/sql/language-extensions/language-extensions-overview).
|Registrieren externer Sprachen|In einer neuen DDL, `CREATE EXTERNAL LANGUAGE`, werden externe Sprachen (z.B. Java) in SQL Server registriert. Informationen finden Sie unter [CREATE EXTERNAL LANGUAGE](../t-sql/statements/create-external-language-transact-sql.md). |
| &nbsp; | &nbsp; |

### <a name="spatial"></a>Räumlich

|Neue Funktion oder Update | Details |
|:---|:---|
| Neue SRIDs (Spatial Reference Identifiers) |Das [australische GDA2020](http://www.ga.gov.au/scientific-topics/positioning-navigation/geodesy/datums-projections/gda2020) stellt robustere und genauere Datumsangaben bereit, die stärker an GPS-Systemen ausgerichtet sind. Die neuen SRIDs sind:<br/><br/> 7843: geografische 2D-Darstellung<br/> 7844: geografische 3D-Darstellung <br/><br/>Die Ansicht von [sys.spatial_reference_systems](../relational-databases/system-catalog-views/sys-spatial-reference-systems-transact-sql.md) enthält die Definitionen der neuen SRIDs. |
| &nbsp; | &nbsp; |

### <a name="error-messages"></a>Fehlermeldungen

|Neue Funktion oder Update | Details |
|:---|:---|
|Kürzungswarnungen | Fehlermeldungen für die Kürzung enthalten standardmäßig die Tabellen- und Spaltennamen sowie den gekürzten Wert. Siehe [VERBOSE_TRUNCATION_WARNINGS](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md#verbose-truncation).|
| &nbsp; | &nbsp; |

## <a name="mission-critical-security"></a>Unternehmenskritische Sicherheitsfunktionen

|Neue Funktion oder Update | Details |
|:---|:---|
|Always Encrypted mit Secure Enclaves|Erweitert auf Always Encrypted mit direkter Verschlüsselung und umfangreichen Berechnungen, indem es Berechnungen von Klartextdaten innerhalb einer serverseitigen sicheren Enclave-Instanz ermöglicht. Die direkte Verschlüsselung verbessert die Leistung und die Zuverlässigkeit kryptografischer Vorgänge (Verschlüsseln von Spalten, Rotieren von Verschlüsselungsschlüsseln für Spalten usw.), da dadurch das Verschieben von Daten aus der Datenbank vermieden wird. Durch die Unterstützung für umfangreiche Berechnungen (Musterabgleich und Vergleichsvorgänge) wird Always Encrypted für weitaus mehr Szenarios und Anwendungen entsperrt, die einen sensiblen Datenschutz erfordern, während gleichzeitig umfangreichere Funktionen in Transact-SQL-Abfragen erforderlich ist. Weitere Informationen finden Sie unter [Always Encrypted mit Secure Enclaves](../relational-databases/security/encryption/always-encrypted-enclaves.md).|
|Zertifikatverwaltung im SQL Server-Konfigurations-Manager|Siehe [Zertifikatverwaltung (SQL Server-Konfigurations-Manager)](../database-engine/configure-windows/manage-certificates.md).|
| &nbsp; | &nbsp; |

## <a name="high-availability"></a>Hohe Verfügbarkeit

### <a name="availability-groups"></a>Verfügbarkeitsgruppen

|Neue Funktion oder Update | Details |
|:---|:---|
|Bis zu fünf synchrone Replikate|In [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] wird die maximale Anzahl der synchronen Replikate von ehemals 3 in [!INCLUDE[ssSQL17](../includes/sssql17-md.md)] auf 5 erhöht. Sie können diese Gruppe aus fünf Replikaten für das automatische Failover in der Gruppe konfigurieren. Es gibt ein primäres Replikat sowie vier synchrone sekundäre Replikate.|
|Umleiten der Verbindung vom sekundären zum primären Replikat| Durch dieses Feature können Clientanwendungsverbindungen zum primären Replikat weitergeleitet werden, unabhängig davon, ob der Zielserver in der Verbindungszeichenfolge angegeben ist. Weitere Informationen finden Sie unter [Umleitung von Lese-/Schreibverbindungen vom sekundären zum primären Replikat (Always On-Verfügbarkeitsgruppen)](../database-engine/availability-groups/windows/secondary-replica-connection-redirection-always-on-availability-groups.md).|
| &nbsp; | &nbsp; |

### <a name="recovery"></a>Wiederherstellung

|Neue Funktion oder Update | Details |
|:---|:---|
|Verbesserte Wiederherstellung von Datenbanken | Aktivieren der verbesserten Wiederherstellung von Datenbanken pro Datenbank. Siehe [Verbesserte Wiederherstellung von Datenbanken](../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md#adr).|
| &nbsp; | &nbsp; |

### <a name="resumable-operations"></a>Fortsetzbare Vorgänge

|Neue Funktion oder Update | Details |
|:---|:---|
|Erstellen und Neuerstellen eines gruppierten Columnstore-Onlineindexes | Siehe [Ausführen von Onlineindexvorgängen](../relational-databases/indexes/perform-index-operations-online.md). |
|Erstellen eines fortsetzbaren Rowstore-Onlineindexes | Siehe [Ausführen von Onlineindexvorgängen](../relational-databases/indexes/perform-index-operations-online.md). |
|Anhalten und Fortsetzen der anfänglichen Überprüfung für Transparent Data Encryption (TDE)|Siehe [TDE-Überprüfung (Transparent Data Encryption): Anhalten und Fortsetzen](../relational-databases/security/encryption/transparent-data-encryption.md#scan-suspend-resume).|
| &nbsp; | &nbsp; |

## <a name="setup"></a>Einrichten 

|Neue Funktion oder Update | Details | 
|:---|:---| 
|Neue Optionen für die Arbeitsspeichereinrichtung | Legt die Serverkonfigurationseinstellungen *Min. Serverarbeitsspeicher (MB)* und *Max. Serverarbeitsspeicher (MB)* während der Installation fest. Weitere Informationen finden Sie unter [Konfiguration der Datenbank-Engine – Seite „Arbeitsspeicher“](https://docs.microsoft.com/sql/sql-server/install/instance-configuration?view=sql-server-ver15#memory) und in [Installieren von SQL Server von der Eingabeaufforderung](../database-engine/install-windows/install-sql-server-from-the-command-prompt.md#Install) in den Abschnitten zu den Parametern `USESQLRECOMMENDEDMEMORYLIMITS`, `SQLMINMEMORY` und `SQLMAXMEMORY`. Der vorgeschlagene Wert entspricht den Richtlinien für die Arbeitsspeicherkonfiguration in [Konfigurationsoptionen für den Serverarbeitsspeicher](../database-engine/configure-windows/server-memory-server-configuration-options.md#setting-the-memory-options-manually).| 
|Neue Optionen für die Nebenläufigkeitseinrichtung | Legt die Serverkonfigurationsoption *Max. Grad an Parallelität* während der Installation fest. Weitere Informationen finden Sie unter [Konfiguration der Datenbank-Engine – Seite „MaxDOP“](https://docs.microsoft.com/sql/sql-server/install/instance-configuration?view=sql-server-ver15#maxdop) und im Abschnitt zum `SQLMAXDOP`-Parameter in [Installieren von SQL Server von der Eingabeaufforderung](../database-engine/install-windows/install-sql-server-from-the-command-prompt.md#Install). Der Standardwert entspricht den Richtlinien für die maximale Nebenläufigkeit in [Konfigurieren der Serverkonfigurationsoption „Max. Grad an Parallelität“](../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md#Guidelines).| 
| &nbsp; | &nbsp; |

## <a name="platform-choice"></a>Plattformauswahl

### <a id="sql-server-on-linux"></a>Linux

| Neue Funktion oder Update | Details |
|:-----|:-----|
|Neue Containerregistrierung|[Get started with SQL Server containers on Docker (Erste Schritte mit SQL Server-Containern unter Docker)](../linux/quickstart-install-connect-docker.md) |
|Replikationsunterstützung |[SQL Server Replication on Linux (SQL Server-Replikation unter Linux)](../linux/sql-server-linux-replication.md)
|Unterstützung für den Microsoft Distributed Transaction Coordinator (MSDTC) |[How to configure MSDTC on Linux (Vorgehensweise: Konfigurieren von MSDTC unter Linux)](../linux/sql-server-linux-configure-msdtc.md) |
|OpenLDAP-Unterstützung für AD-Drittanbieter |[Tutorial: Use Active Directory authentication with SQL Server on Linux (Tutorial: Verwenden der Azure Active Directory-Authentifizierung mit SQL Server unter Linux)](../linux/sql-server-linux-active-directory-authentication.md) |
|Machine Learning unter Linux |[Configure Machine Learning on Linux (Konfigurieren von Machine Learning unter Linux)](../linux/sql-server-linux-setup-machine-learning.md) |
|TempDB-Verbesserungen | Standardmäßig erstellt eine neue Installation von SQL Server für Linux mehrere TempDB-Datendateien, deren Anzahl sich nach der Anzahl der logischen Kerne richtet (bis zu acht Datendateien). Das gilt nicht für direkte Upgrades der Neben- oder Hauptversion. Jede TempDB-Datei ist 8 MB groß und wird automatisch um 64 MB vergrößert. Dieses Verhalten ähnelt dem der SQL Server-Standardinstallation unter Windows. |
| PolyBase unter Linux | [Installieren Sie PolyBase](../relational-databases/polybase/polybase-linux-setup.md) für Nicht-Hadoop-Connectors unter Linux.<br/><br/>[PolyBase type mapping (Typzuordnung mit PolyBase)](../relational-databases/polybase/polybase-type-mapping.md) |
| Unterstützung von Change Data Capture (CDC) | Change Data Capture (CDC) wird jetzt unter Linux für SQL Server 2019 unterstützt. |
| &nbsp; | &nbsp; |

### <a name="containers"></a>Container

|Neue Funktion oder Update | Details |
|:---|:---|
| Microsoft Container Registry | [Microsoft Container Registry](https://www.ntweekly.com/2019/09/23/microsoft-container-registry-to-replace-docker-hub-for-new-images/) ersetzt nun Docker Hub für neue offizielle Microsoft-Containerimages, einschließlich [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]. |
| Container ohne Root-Berechtigung | Mit [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] wird die Möglichkeit eingeführt, sicherere Container zu erstellen, indem der [!INCLUDE[sql-server](../includes/ssnoversion-md.md)]-Prozess standardmäßig als Nicht-Root-Benutzer gestartet wird. Weitere Informationen finden Sie unter [Erstellen und Ausführen von SQL Server-Containern als Nicht-Root-Benutzer](../linux/sql-server-linux-configure-docker.md#buildnonrootcontainer). |
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

## <a name="sql-server-analysis-services"></a>SQL Server Analysis Services

| Neue Funktion oder Update | Details |
|:---|:---|
|Abfrageüberlappung| Siehe [Abfrageüberlappung](https://docs.microsoft.com/analysis-services/tabular-models/query-interleaving). |
|Unterstützung von MDX-Abfragen für tabellarische Modelle mit Berechnungsgruppen | Siehe [Berechnungsgruppen](what-s-new-in-sql-server-ver15-prerelease.md#calc-ctp24). |
|Berechnungsgruppen in einem tabellarischen Modell| [Berechnungsgruppen in einem tabellarischen Modell](what-s-new-in-sql-server-ver15-prerelease.md#calc-ctp24) |
|Unterstützung von MDX-Abfragen für tabellarische Modelle mit Berechnungsgruppen | Siehe [Berechnungsgruppen](what-s-new-in-sql-server-ver15-prerelease.md#calc-ctp24). |
|Dynamische Formatierung von Measures mithilfe von Berechnungsgruppen |Mit dieser Funktion können Sie Formatzeichenfolgen für Measures mit [Berechnungsgruppen](what-s-new-in-sql-server-ver15-prerelease.md#calc-ctp24) bedingt ändern. Beispielsweise kann mit der Währungsumrechnung ein Measure in verschiedenen Fremdwährungsformaten angezeigt werden.|
|M:n-Beziehungen in tabellarischen Modellen|[m:n-Beziehungen in tabellarischen Modellen](what-s-new-in-sql-server-ver15-prerelease.md#many-to-many-ctp24)|
|Eigenschafteneinstellungen für die Ressourcenkontrolle|[Eigenschafteneinstellungen für die Ressourcenkontrolle](what-s-new-in-sql-server-ver15-prerelease.md#property-ctp24)|
| Governanceeinstellung für Power BI-Cacheaktualisierungen.  | Der Power BI-Dienst speichert Dashboardkacheldaten und Berichtsdaten für das anfängliche Laden des Live Connect-Berichts zwischen, was dazu führt, dass eine übermäßige Anzahl von Cacheanfragen an SSAS übermittelt wird und in extremen Fällen den Server überlastet. In diesem Release wird die **ClientCacheRefreshPolicy**-Eigenschaft eingeführt. Diese Eigenschaft ermöglicht Ihnen, dieses Verhalten auf Serverebene zu überschreiben. Weitere Informationen finden Sie unter [Allgemeine Eigenschaften](https://docs.microsoft.com/analysis-services/server-properties/general-properties). |
| Online anfügen  | Diese Funktion bietet die Möglichkeit, ein tabellarisches Modell als Onlinevorgang anzufügen. Onlineanfügen kann für die Synchronisierung schreibgeschützter Replikate in horizontal skalierten Umgebungen für lokale Abfragen verwendet werden. Weitere Informationen finden Sie unter [Online anfügen](what-s-new-in-sql-server-ver15-prerelease.md#online-attach-ctp32). |
| &nbsp; | &nbsp; |

[!INCLUDE[ctp-support-exclusion](../includes/ctp-support-exclusion.md)]

Informationen zu bestimmten Funktionen, die vom Support ausgeschlossen sind, finden Sie in den [Release Notes](sql-server-ver15-release-notes.md).

Außerdem wurden die folgenden Funktionen für [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] CTP 3.2 hinzugefügt oder verbessert.

## <a name="see-also"></a>Siehe auch

- [PowerShell-Modul von `SqlServer`](https://www.powershellgallery.com/packages/Sqlserver)
- [SQL Server PowerShell-Dokumentation](../powershell/sql-server-powershell.md)

## <a name="next-steps"></a>Nächste Schritte

- [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]-Versionshinweise](sql-server-ver15-release-notes.md)

- [Microsoft [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]: Technical white paper (technisches Whitepaper)](http://info.microsoft.com/rs/157-GQE-382/images/EN-US-CNTNT-white-paper-DBMod-Microsoft-SQL-Server-2019-Technical-white-paper.pdf)<br />Veröffentlicht im September 2018. Gilt für Microsoft [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] CTP 2.0 für Windows-, Linux- und Docker-Container.

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]

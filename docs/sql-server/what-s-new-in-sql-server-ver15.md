---
title: Neuigkeiten zu SQL Server 2019 | Microsoft-Dokumentation
ms.date: 03/01/2019
ms.prod: sql-server-2019
ms.reviewer: ''
ms.technology: release-landing
ms.topic: article
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 8f7302384bbf264061c73b79a919855aa762994f
ms.sourcegitcommit: 8bc5d85bd157f9cfd52245d23062d150b76066ef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/07/2019
ms.locfileid: "57579770"
---
# <a name="whats-new-in-includesql-server-2019includessssqlv15-mdmd"></a>Neues in [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] ist eine Erweiterung der SQL Server-Plattform basierend auf früheren Releases, die Ihnen eine große Auswahl an Entwicklungssprachen, Datentypen und Betriebssystemen sowie die Arbeit mit einer lokalen Umgebung oder der Cloud bietet. Dieser Artikel beschreibt die Neuigkeiten zu [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]. Weitere Informationen und bekannte Probleme finden Sie unter [Release Notes zu [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] (Vorschauversion)](sql-server-ver15-release-notes.md).

**Versuchen Sie Folgendes[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]:**
- [![Download aus dem Evaluation Center](../includes/media/download2.png)](https://go.microsoft.com/fwlink/?LinkID=862101) [Laden Sie [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] für die Installation unter Windows](https://go.microsoft.com/fwlink/?LinkID=862101) herunter.
- Installieren Sie die Version unter Linux für [Red Hat Enterprise Server](../linux/quickstart-install-connect-red-hat.md), [SUSE Linux Enterprise Server](../linux/quickstart-install-connect-suse.md) und [Ubuntu](../linux/quickstart-install-connect-ubuntu.md).
- [Ausführen von [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] auf Docker](../linux/quickstart-install-connect-docker.md)

**Nutzen Sie SQL Server 2019 mit den [neuesten Tools](#tools) optimal.**

## <a name="ctp-23"></a>CTP 2.3

Community Technology Preview (CTP) 2.3 ist das neueste öffentliche Release von [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]. Dieses Release beinhaltet Verbesserungen im Vergleich zu vorherigen CTP-Releases zum Beheben von Fehlern, zur Verbesserung der Sicherheit und zur Optimierung der Leistung. Außerdem wurden die folgenden Features für [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] CTP 2.3 hinzugefügt oder verbessert.

- [Big Data-Cluster](#bigdatacluster)
  - Übermitteln von Spark-Aufträgen an Big Data-Cluster von SQL Server 2019 in IntelliJ
  - Bereitstellen von Anwendungen und Verwalten der Benutzeroberfläche für viele datenbezogene Apps, einschließlich dem Operationalisieren von Machine Learning-Modellen mithilfe von R und Python und dem Ausführen von SSIS-Aufträgen
  - Verwenden von Sparklyr in Big Data-Clustern von SQL Server 2019
  - Einbinden von externen HDFS-kompatiblen Speichern (Hadoop Distributed File System) in Big Data-Cluster mit dem HDFS-Tiering

- [Datenbank-Engine](#databaseengine)
  - Verbesserte Wiederherstellung von Datenbanken
  - Weniger Neukompilierungen für Workloads mit temporären Tabellen für mehrere Bereiche
  - Verbesserter Skalierbarkeit indirekter Prüfpunkte
  - Durch den Abfragespeicherplan erzwungene Unterstützung für schnelle Vorwärtscursor und statischer Cursor
  - Das SQL-Graphfeature ermöglicht kaskadierende Deletes für Edges beim Löschen von Knoten
  - Unterstützung externer Java- und Python-Bibliothek unter Windows

- [[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Analysis Services (SSAS)](#ssas)
  - Durch Berechnungsgruppen in tabellarischen Modellen wird die Anzahl der Measures durch das Wiederverwenden der Berechnungslogik reduziert.

## <a name="previous-ctps"></a>Vorherige CTPs

In früheren CTP-Releases wurden für [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] folgende Features hinzugefügt oder verbessert.

- [Big Data-Cluster](#bigdatacluster) 
  - Bereitstellen eines Big Data-Clusters mit SQL und Spark-Linux-Containern in Kubernetes (CTP 2.0)
  - Zugriff auf Big Data über HDFS (CTP 2.0)
  - Ausführen von erweiterten Analysen und Vorgängen des maschinellen Lernens mit Spark (CTP 2.0)
  - Streamen von Daten an SQL-Datenpools mit Spark (CTP 2.0)
  - Ausführen von Abfragebüchern zur Bereitstellung einer Notebookumgebung mit Azure Data Studio (CTP 2.0)
  - Verwenden von SparkR über Azure Data Studio in einem Big Data-Cluster (CTP 2.2)
  - Bereitstellen von Python- und R-Apps (CTP 2.2)

- [Datenbank-Engine](#databaseengine)
  - UTF-8-Unterstützung (CTP 2.0)
  - Fortsetzen der Indexerstellung nach einer Unterbrechung durch die Erstellung von fortsetzbaren Onlineindizes (CTP 2.0)
  - Erstellung und Neuerstellung von gruppierten Columnstore-Onlineindizes (CTP 2.0)
  - Always Encrypted mit Secure Enclaves (CTP 2.0)
  - Intelligente Abfrageverarbeitung (CTP 2.0)
  - Erweiterung für die Programmierbarkeit der Java-Sprache (CTP 2.0)
  - SQL-Graphfeatures (CTP 2.0)
  - Datenbankweit gültige Konfigurationseinstellung für Online- und fortsetzbare DDL-Vorgänge (CTP 2.0)
  - Always On-Verfügbarkeitsgruppen: Umleitung von Verbindungen mit sekundären Replikaten (CTP 2.0)
  - Nativ in SQL Server integrierte Datenermittlung und -klassifizierung (CTP 2.0)
  - Erweiterte Unterstützung für Geräte mit beständigem Speicher (CTP 2.0)
  - Unterstützung für Columnstore-Statistiken in `DBCC CLONEDATABASE` (CTP 2.0)
  - Neue Optionen für `sp_estimate_data_compression_savings` (CTP 2.0)
  - Failovercluster in SQL Server Machine Learning Services (CTP 2.0)
  - Standardmäßig aktivierte LWP-Abfrageinfrastruktur (CTP 2.0)
  - Neue PolyBase-Connectors (CTP 2.0)
  - Rückgabe von Seiteninformationen durch neue `sys.dm_db_page_info`-Systemfunktion (CTP 2.0)
  - Hinzufügen von Inlining für benutzerdefinierte Skalarfunktionen durch intelligente Abfrageverarbeitung (CTP 2.1)
  - Verbesserte Fehlermeldung beim Abschneiden von Daten mit Tabellen- und Spaltennamen sowie abgeschnittenen Werten (CTP 2.1)
  - Verwendung abgeleiteter Tabellen- oder Ansichtsaliasse in Graphabgleichsabfragen (CTP 2.1)
  - Verbesserte Diagnosedaten für gesperrte Statistiken (CTP 2.1)
  - Hybrider Pufferpool (CTP 2.1)
  - Statische Datenmaskierung (CTP 2.1)

- [SQL Server unter Linux](#sqllinux)
  - Replikationsunterstützung (CTP 2.0)
  - Unterstützung für den Microsoft Distributed Transaction Coordinator (MSDTC) (CTP 2.0)
  - Always On-Verfügbarkeitsgruppe in Docker-Containern mit Kubernetes (CTP 2.0)
  - OpenLDAP-Unterstützung für AD-Drittanbieter (CTP 2.0)
  - Machine Learning unter Linux (CTP 2.0)
  - Neue Containerregistrierung (CTP 2.0)
  - Neue RHEL-basierte Containerimages (CTP 2.0)
  - Benachrichtigung zur Speicherauslastung (CTP 2.0)

- [Master Data Services](#mds)
  - Ersetzung der Silverlight-Steuerelemente (CTP 2.0)

- [Sicherheit](#security)
  - Zertifikatverwaltung im SQL Server-Konfigurations-Manager (CTP 2.0)

- [Tools](#tools)
  - Azure Data Studio
  - SQL Server Management Studio (SSMS) 18.0 (Vorschau)

Weitere Informationen zu diesen Features finden Sie weiter unten.

## <a id="bigdatacluster"></a>Big Data-Cluster

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] [Big Data-Cluster](../big-data-cluster/big-data-cluster-overview.md) ermöglichen neue Szenarios wie die Folgenden:

- [Übermitteln von Spark-Aufträgen an Big Data-Cluster von SQL Server 2019 in IntelliJ](../big-data-cluster/spark-submit-job-intellij-tool-plugin.md) (CTP 2.3)
- [Bereitstellen von Anwendungen und Verwalten der Benutzeroberfläche](../big-data-cluster/big-data-cluster-create-apps.md) für viele datenbezogene Apps, einschließlich dem Operationalisieren von Machine Learning-Modellen mithilfe von R und Python und dem Ausführen von SSIS-Aufträgen (CTP 2.3)
- [Verwenden von Sparklyr in Big Data-Clustern von SQL Server 2019](../big-data-cluster/sparklyr-from-RStudio.md) (CTP 2.3)
- Einbinden von externen HDFS-kompatiblen Speichern (Hadoop Distributed File System) in Big Data-Cluster mit dem [HDFS-Tiering](../big-data-cluster/hdfs-tiering.md) (CTP 2.3)
- Verwenden von SparkR über Azure Data Studio in einem Big Data-Cluster (CTP 2.2)
- [Bereitstellen von Python- und R-Apps](../big-data-cluster/big-data-cluster-create-apps.md) (CTP 2.2)
- Bereitstellen eines Big Data-Clusters mit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]- und Spark-Linux-Containern in Kubernetes (CTP 2.0)
- Zugriff auf Big Data über HDFS (CTP 2.0)
- Ausführen von erweiterten Analysen und Vorgängen des maschinellen Lernens mit Spark (CTP 2.0)
- Streamen von Daten an SQL-Datenpools mit Spark (CTP 2.0)
- Ausführen von Abfragebüchern zur Bereitstellung einer Notebookumgebung in [**Azure Data Studio**](../sql-operations-studio/what-is.md) (CTP 2.0)
 
[!INCLUDE [Big data clusters preview](../includes/big-data-cluster-preview-note.md)]

## <a id="databaseengine"></a> Datenbank-Engine

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] führt die folgenden neuen Features für [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] ein oder verbessert sie:

### <a name="accelerated-database-recovery-ctp-23"></a>Verbesserte Wiederherstellung von Datenbanken (CTP 2.3)

Durch die [verbesserte Wiederherstellung von Datenbanken](http://docs.microsoft.com/azure/sql-database/sql-database-accelerated-database-recovery
) wird die Verfügbarkeit von Datenbanken enorm verbessert, insbesondere bei zeitintensiven Transaktionen. Hierfür wurde der Wiederherstellungsprozess der SQL Server-Datenbank-Engine vollständig überarbeitet. Die [Datenbankwiederherstellung](../relational-databases/logs/the-transaction-log-sql-server.md?#recovery-of-all-incomplete-transactions-when--is-started) wird von SQL Server für alle Datenbanken verwendet, damit diese Transaktionen im gleichen bzw. fehlerfreien Zustand starten. Eine Datenbank, für die die verbesserte Datenbankwiederherstellung aktiviert wurde, wird nach einem Failover oder einem nicht sauberen Herunterfahren deutlich schneller wiederhergestellt. In CTP 2.3 kann die verbesserte Datenbankwiederherstellung mit folgender Syntax für jede Datenbank einzeln aktiviert werden:

```sql
ALTER DATABASE <db_name> SET ACCELERATED_DATABASE_RECOVERY = {ON | OFF}
```

>[!NOTE]
>Sie benötigen diese Syntax nicht, um das Feature in Azure SQL-Datenbank zu verwenden. Dort ist es standardmäßig aktiviert.

Wenn Sie kritische Datenbanken besitzen, die für große Transaktionen anfällig sind, können Sie dieses Feature während der Vorschauphase testen. Senden Sie Feedback an das [[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Team](<https://aka.ms/sqlfeedback>).

### <a name="query-store-plan-forcing-support-for-fast-forward-and-static-cursors-ctp-23"></a>Durch den Abfragespeicherplan erzwungene Unterstützung für schnelle Vorwärtscursor und statischer Cursor (CTP 2.3)

Mit dem Abfragespeicher können Sie nun Abfrageausführungspläne für schnelle Vorwärtscursor und statische Cursor (T-SQL und API) erzwingen. Das Erzwingen kann über `sp_query_store_force_plan` oder über SQL Server Management Studio-Abfragespeicherberichte erfolgen.

### <a name="reduced-recompilations-for-workloads-using-temporary-tables-across-multiple-scopes-ctp-23"></a>Weniger Neukompilierungen für Workloads mit temporären Tabellen für mehrere Bereiche (CTP 2.3)

Bevor dieses Feature verfügbar war, konnte das Verweisen auf eine temporäre Tabelle mit einer DML-Anweisung (`SELECT`, `INSERT`, `UPDATE`, `DELETE`) zu einer Neukompilierung der DML-Anweisung bei jeder Ausführung führen, wenn die temporäre Tabelle in einem Batch im äußeren Bereich erstellt wurde. Durch dieses Update führt SQL Server zusätzliche einfache Überprüfungen durch, um unnötige Neukompilierungen zu vermeiden:

- Überprüfung, ob es sich bei dem Modul im äußeren Bereich, das zur Kompilierzeit zur Erstellung der temporären Tabelle verwendet wurde, um das gleiche Modul handelt, das für nachfolgende Ausführungen verwendet wurde 
- Nachverfolgung von Änderungen an der Datendefinitionssprache (Data Definition Language, DDL), die bei der ersten Kompilierung vorgenommen und Vergleich mit den DDL-Vorgängen für nachfolgende Ausführungen 

Dadurch können überflüssige Neukompilierungen vermieden und der CPU-Aufwand reduziert werden.

### <a name="improved-indirect-checkpoint-scalability-ctp-23"></a>Verbesserter Skalierbarkeit indirekter Prüfpunkte (CTP 2.3)

In früheren Versionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] konnten Scheduler-Fehler ohne Ergebnis auftreten, wenn eine Datenbank viele modifizierte Seiten generiert hat (z.B. tempdb). In [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] wird die Skalierbarkeit für indirekte Prüfpunkte verbessert, um diese Fehler in Datenbanken zu vermeiden, die Workloads mit vielen UPDATE/INSERT-Vorgängen enthalten.

### <a name="scalar-udf-inlining-ctp-21"></a>Inlining benutzerdefinierter Skalarfunktionen (CTP 2.1)

Das Inlining benutzerdefinierter Skalarfunktionen wandelt die entsprechenden Funktionen automatisch in relationale Ausdrücke um und bettet sie in die aufrufende SQL-Abfrage ein. Dadurch wird die Leistung von Workloads verbessert, die benutzerdefinierte Skalarfunktionen verwenden. Das Inlining benutzerdefinierter Skalarfunktionen ermöglicht eine kostenbasierte Optimierung von Vorgängen in benutzerdefinierten Funktionen und erzielt effiziente Pläne, die konkret und parallel sind – im Gegensatz zu ineffizienten, iterativen, seriellen Ausführungsplänen. Dieses Feature ist standardmäßig unter dem Datenbank-Kompatibilitätsgrad 150 aktiviert.

Weitere Informationen finden Sie unter [Inlining benutzerdefinierter Skalarfunktionen](../relational-databases/user-defined-functions/scalar-udf-inlining.md).

### <a name="truncation-error-message-improved-to-include-table-and-column-names-and-truncated-value-ctp-21"></a>Verbesserte Fehlermeldung beim Abschneiden von Daten mit Tabellen- und Spaltennamen sowie abgeschnittenen Werten (CTP 2.1)

Viele [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Entwickler und -Administratoren, die Datenverschiebungsworkloads entwickeln oder verwalten, kennen die Fehlermeldung `String or binary data would be truncated` (ID 8152). Der Fehler tritt beim Übertragen von Daten zwischen einer Quelle und einem Ziel mit unterschiedlichen Schemata auf, wenn die Quelldaten zu groß für den Zieldatentyp sind. Das Beheben des Fehlers anhand der Fehlermeldung kann sehr zeitaufwendig sein. [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] führt eine neue, spezifischere Fehlermeldung (2628) für dieses Szenario ein:  

`String or binary data would be truncated in table '%.*ls', column '%.*ls'. Truncated value: '%.*ls'.`

Die neue Fehlermeldung 2628 bietet mehr Kontext zum Abschneiden der Daten und vereinfacht die Problembehandlung. Für CTP 2.1 und CTP 2.2 ist dies eine optionale Fehlermeldung, für die das [Ablaufverfolgungsflag](../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) 460 aktiviert sein muss.

### <a name="improved-diagnostic-data-for-stats-blocking-ctp-21"></a>Verbesserte Diagnosedaten für gesperrte Statistiken (CTP 2.1)

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] bietet verbesserte Diagnosedaten für Abfragen mit langer Ausführungszeit, die auf synchrone Updatevorgänge von Statistiken warten. Die Spalte `command` der dynamischen Verwaltungssicht `sys.dm_exec_requests` zeigt `SELECT (STATMAN)` an, wenn ein `SELECT`-Objekt darauf wartet, dass ein synchroner Statistikupdatevorgang abgeschlossen wird, bevor die Abfrage weiter ausgeführt wird. Außerdem wird der neue Wartetyp `WAIT_ON_SYNC_STATISTICS_REFRESH` in der dynamischen Verwaltungssicht `sys.dm_os_wait_stats` angezeigt. Er zeigt die kumulierte Zeit auf Instanzebene für synchrone Statistikaktualisierungen an.

### <a name="static-data-masking-ctp-21"></a>Statische Datenmaskierung (CTP 2.1)

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] führt die statische Datenmaskierung ein. Damit können Sie sensible Daten in Kopien von SQL Server-Datenbanken bereinigen. Die statische Datenmaskierung erstellt eine bereinigte Datenbankkopie, in der alle sensiblen Daten so geändert wurden, dass sie auch für Nichtproduktionsbenutzer freigegeben werden kann. Sie kann für Entwicklung, Tests, Analysen, Geschäftsberichte, Compliance, Fehlerbehandlung und andere Szenarien verwendet werden, in denen bestimmte Daten nicht in verschiedene Umgebungen kopiert werden können.

Die statische Datenmaskierung wird auf Spaltenebene ausgeführt. Wählen Sie die zu maskierenden Spalten aus, und geben Sie für jede ausgewählte Spalte eine Maskierungsfunktion an. Die statische Datenmaskierung kopiert die Datenbank und wendet dann die angegebenen Maskierungsfunktionen auf die Spalten an.

#### <a name="static-data-masking-vs-dynamic-data-masking"></a>Statische vs. dynamische Datenmaskierung

Bei der Datenmaskierung wird eine Maske auf eine Datenbank angewendet, um vertrauliche Informationen auszublenden und mit neuen bzw. bereinigten Daten zu ersetzen. Microsoft bietet zwei Maskierungsoptionen: die statische und die dynamische Datenmaskierung. Die dynamische Datenmaskierung wurde in [!INCLUDE[ssSQL16](../includes/sssql16-md.md)] eingeführt. In dieser Tabelle werden die beiden Ansätze verglichen:

|Statische Datenmaskierung |Dynamische Datenmaskierung|
|:----|:----|
|Verwendung einer Datenbankkopie <br/><br/>Kein Abrufen von Originaldaten<br/><br/>Maskierung erfolgt auf Speicherebene<br/><br/>Alle Benutzer haben Zugriff auf die gleichen maskierten Daten<br/><br/>Konzipiert für permanenten Zugriff für das ganze Team|Verwendung der Originaldatenbank<br/><br/>Intakte Originaldaten<br/><br/>Maskierung erfolgt direkt beim Abfragen<br/><br/>Maskierung variiert je nach Benutzerberechtigung <br/><br/>Konzipiert für punktuellen benutzerspezifischen Zugriff|

### <a name="database-compatibility-level-ctp-20"></a>Datenbank-Kompatibilitätsgrad (CTP 2.0)

Die Datenbank **COMPATIBILITY_LEVEL 150** wurde hinzugefügt. Um eine bestimmte Benutzerdatenbank verwenden zu können, führen Sie Folgendes aus:

   ```sql
   ALTER DATABASE database_name SET COMPATIBILITY_LEVEL =  150;
   ```

### <a name="utf-8-support-ctp-22"></a>UTF-8-Unterstützung (CTP 2.2)

Vollständige Unterstützung für die weit verbreitete Zeichencodierung UTF-8 als Import- oder Exportcodierung oder als Sortierung für Textdaten auf Datenbank- oder Spaltenebene. UTF-8 ist für die Datentypen `CHAR` und `VARCHAR` zulässig und ist bei der Erstellung oder Änderung einer Objektsortierung in eine Sortierung mit dem Suffix `UTF8` aktiviert. 

Beispiel: `LATIN1_GENERAL_100_CI_AS_SC` in `LATIN1_GENERAL_100_CI_AS_SC_UTF8`. Die in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] eingeführte UTF-8-Codierung ist nur für Windows-Sortierungen verfügbar, die Sonderzeichen unterstützen. `NCHAR` und `NVARCHAR` lassen nur die UTF-16-Codierung zu und bleiben unverändert.

Dieses Feature kann abhängig von dem verwendeten Zeichensatz beträchtliche Speichereinsparungen ermöglichen. Die Änderung eines vorhandenen Spaltendatentyps mit lateinischen Zeichen von `NCHAR(10)` in `CHAR(10)` mit einer UTF-8-fähigen Sortierung führt beispielsweise zu einer Verringerung der Speicheranforderungen um 50 %. Diese Verringerung ist darauf zurückzuführen, dass `NCHAR(10)` 20 Byte für den Speicher erfordert, wohingegen `CHAR(10)` 10 Byte für die gleiche Unicode-Zeichenfolge erfordert.

Weitere Informationen finden Sie unter [Collation and Unicode Support](../relational-databases/collations/collation-and-unicode-support.md).

CTP 2.1 unterstützt nun die Auswahl der UTF-8-Sortierung als Standard während des [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]-Setups.

CTP 2.2 unterstützt nun die Verwendung von UTF-8-Zeichencodierung mit SQL Server-Replikation.

### <a name="resumable-online-index-create-ctp-20"></a>Erstellung fortsetzbarer Onlineinidizes (CTP 2.0)

- Durch die **Erstellung von fortsetzbaren Onlineindizes** kann ein Indexerstellungsvorgang angehalten und zu einem späteren Zeitpunkt an der Stelle fortgesetzt werden, an der der Vorgang angehalten wurde oder an der ein Fehler aufgetreten ist. So muss nicht von Anfang an begonnen werden.

  Die Erstellung fortsetzbarer Onlineindizes unterstützt folgende Szenarien:
  - Fortsetzen eines Indexerstellungsvorgangs nach einem Fehler bei der Indexerstellung (z.B. nach einem Datenbankfailover oder bei fehlendem Speicherplatz auf dem Datenträger)
  - Anhalten eines laufenden Indexerstellungsvorgangs und Fortsetzen zu einem späteren Zeitpunkt, um bei Bedarf vorübergehend Systemressourcen freizugeben und diesen Vorgang zu einem späteren Zeitpunkt fortzusetzen
  - Erstellen großer Indizes ohne Inanspruchnahme von umfassendem Protokollspeicherplatz und Transaktionen mit langer Laufzeit, die andere Wartungsaktivitäten blockieren, jedoch mit der Möglichkeit zur Protokollkürzung

  Ohne dieses Feature müsste ein Vorgang zur Onlineindexerstellung bei einem Fehler erneut von Anfang an ausgeführt werden.

Bei diesem Release erweitern wir die Funktionen für fortsetzbare Indizes, indem wir dieses Feature für verfügbare [Neuerstellungen von fortsetzbaren Onlineindizes](https://azure.microsoft.com/blog/modernize-index-maintenance-with-resumable-online-index-rebuild/) hinzufügen.

Darüber hinaus kann dieses Feature als Standardwert für eine bestimmte Datenbank mit einer [datenbankweit gültigen Standardeinstellung für Online- und fortsetzbare DDL-Vorgänge](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md) festgelegt werden.

Weitere Informationen finden Sie unter [Erstellung von fortsetzbaren Onlineindizes](../t-sql/statements/create-index-transact-sql.md#resumable-indexes).

### <a name="build-and-rebuild-clustered-columnstore-indexes-online-ctp-20"></a>Erstellen und erneutes Erstellen von gruppierten Columnstore-Indizes (online) (CTP 2.0)

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

### <a name="always-encrypted-with-secure-enclaves-ctp-20"></a>Always Encrypted mit Secure Enclaves (CTP 2.0)

Die Erweiterung basiert auf Always Encrypted mit direkter Verschlüsselung und umfangreichen Berechnungen. Die Erweiterungen basieren auf der Ermöglichung von Berechnungen auf Grundlage von Klartextdaten, die sich auf Serverseite in einer Secure Enclave befinden.

Kryptografische Vorgänge umfassen die Verschlüsselung von Spalten und das Rotieren von Spaltenverschlüsselungsschlüsseln. Diese Vorgänge können nun mithilfe von [!INCLUDE[tsql](../includes/tsql-md.md)] ausgegeben werden und erfordern kein Entfernen dieser Daten aus der Datenbank. Secure Enclaves bieten Always Encrypted, um ein breiteres Spektrum an Szenarien zu ermöglichen, die folgende Anforderungen nach sich ziehen:  

- Vertrauliche Daten müssen vor Benutzern mit erhöhten Rechten, die jedoch nicht autorisiert sind, geschützt werden (z.B. Datenbankadministratoren, Systemadministratoren, Cloudbetreiber oder Malware).
- Es müssen umfangreiche Berechnungen für geschützte Daten innerhalb des Datenbanksystems unterstützt sein.

Weitere Einzelheiten finden Sie unter [Always Encrypted mit Secure Enclaves](../relational-databases/security/encryption/always-encrypted-enclaves.md).

> [!NOTE]
> Always Encrypted mit Secure Enclaves ist nur unter dem Windows-Betriebssystem verfügbar.

### <a name="intelligent-query-processing-ctp-20"></a>Intelligente Abfrageverarbeitung (CTP 2.0)

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

### <a id="programmability"></a> Erweiterungen für die Programmierbarkeit der Java-Sprache (CTP 2.0)

- **Java-Spracherweiterung (Vorschauversion):** Führen Sie Java-Code mithilfe der Java-Spracherweiterung in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] aus. Diese Erweiterung ist in [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] installiert, wenn Sie das Feature „Machine Learning Services (datenbankintern)“ zu Ihrer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Instanz hinzufügen.

### <a id="sqlgraph"></a> SQL-Graphfeatures

- Sie können **abgeleitete Tabellen- oder Ansichtsaliasse in Graphabgleichabfragen (CTP 2.1) verwenden**. Graphabfragen in der [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]-Vorschauversion verwenden Ansichts- und abgeleitete Tabellenaliasse in der Syntax `MATCH`. Um diese Aliasse in `MATCH` zu verwenden, müssen die Ansichten und abgeleiteten Tabellen entweder in einem Knotensatz oder einem Edgetabellensatz mit dem Operator `UNION ALL` erstellt werden. Der Knoten oder die Edgetabelle können Filter aufweisen. Die Verwendung abgeleiteter Tabellen- und Ansichtsaliasse in `MATCH`-Abfragen kann sehr nützlich sein, wenn Sie heterogene Entitäten bzw. Verbindungen für mindestens zwei Entitäten in Ihrem Graph abfragen möchten.

- Dank des **Supports in `MERGE`-DML (CTP 2.0)** können Sie Graphbeziehungen statt in separaten `INSERT`-, `UPDATE`- oder `DELETE`-Anweisungen in einer einzigen Anweisung angeben. Führen Sie Ihre aktuellen Graphdaten aus Knoten- oder Edgetabellen mithilfe der `MATCH`-Prädikate in der `MERGE`-Anweisung mit neuen Daten zusammen. Dieses Feature ermöglicht `UPSERT`-Szenarien in Edgetabellen. Benutzer können nun eine einzelne MERGE-Anweisung verwenden, um einen neuen Edge einzufügen oder einen vorhandenen Edge zwischen zwei Knoten zu aktualisieren.

- Für Edgetabellen im SQL-Graph wurden **Edgeeinschränkungen (CTP 2.0)**  eingeführt. Edgetabellen können eine Verbindung zwischen beliebigen Knoten in der Datenbank herstellen. Mit der Einführung von Edgeeinschränkungen können Sie ab sofort einige Einschränkungen zu diesem Verhalten anwenden. Mit der neuen `CONNECTION`-Einschränkung kann der Knotentyp angegeben werden, mit dem eine bestimmte Edgetabelle eine Verbindung im Schema herstellen darf. 

  **(CTP 2.3)** Sie können mit diesem Feature aus kaskadierende Deletes für eine Edgeeinschränkung festlegen. Sie können die Aktionen festlegen, die die Datenbank-Engine ausführt, wenn ein Benutzer die Knoten löscht, die über einen bestimmten Edge verbunden werden.

### <a name="database-scoped-default-setting-for-online-and-resumable-ddl-operations--ctp-20"></a>Datenbankweit gültige Standardeinstellung für Online- und fortsetzbare DDL-Vorgänge (CTP 2.0)

- Die **datenbankweit gültige Standardeinstellung für Online- und fortsetzbare DDL-Vorgänge** ermöglicht eine Standardverhaltenseinstellung für `ONLINE`- und `RESUMABLE`-Indexvorgänge auf Datenbankebene, statt diese Optionen für jede einzelne DDL-Indexanweisung definieren zu müssen (z.B. Indexerstellung oder -neuerstellung).

- Legen Sie diese Standardeinstellungen mithilfe der datenbankweit gültigen Konfigurationsoptionen `ELEVATE_ONLINE` und `ELEVATE_RESUMABLE` fest. Beide Optionen bewirken, dass die Engine unterstützte Vorgänge automatisch auf die Ausführung von Online- oder fortsetzbaren Indizes erhöht. Mit diesen Optionen können Sie die folgenden Verhaltensweisen ermöglichen:

  - Die Option `FAIL_UNSUPPORTED` ermöglicht alle Onlineindex- oder fortsetzbare und Fehlerindexvorgänge, die nicht für Online- oder fortsetzbare Indizes unterstützt werden.
  - Die Option `WHEN_SUPPPORTED` ermöglicht unterstützte Online- oder fortsetzbare und die Ausführung von nicht unterstützten Offline- oder nicht fortsetzbaren Indexvorgängen.
  - Die Option `OFF` lässt das aktuelle Verhalten zur Ausführung aller Offlineindexvorgänge und nicht fortsetzbare Indexvorgänge zu, sofern dies nicht explizit in der DDL-Anweisung angegeben ist.

Um die Standardeinstellung zu überschreiben, schließen Sie die `ONLINE`- oder die `RESUMABLE`-Option in die Indexerstellungs- und -neuerstellungsbefehle ein. 

Ohne dieses Feature müssen Sie die Onlineoptionen und fortsetzbaren Optionen direkt in der Index-DDL-Anweisung angeben, z.B. die Indexerstellung und -neuerstellung.

Weitere Informationen zu fortsetzbaren Indexvorgängen finden Sie unter [Resumable Online Index Create](https://azure.microsoft.com/blog/resumable-online-index-create-is-in-public-preview-for-azure-sql-db/) (Erstellung fortsetzbarer Onlineindizes).

### <a id="ha"></a>Always On-Verfügbarkeitsgruppen: Erhöhung synchroner Replikate (CTP 2.0)

- **Bis zu fünf synchrone Replikate:** In [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] wird die maximale Anzahl der synchronen Replikate von ehemals 3 in [!INCLUDE[ssSQL17](../includes/sssql17-md.md)] auf 5 erhöht. Sie können diese Gruppe aus fünf Replikaten für das automatische Failover in der Gruppe konfigurieren. Es gibt ein primäres Replikat sowie vier synchrone sekundäre Replikate.

- **Umleiten der Verbindung vom sekundären zum primären Replikat:** Durch dieses Feature können Clientanwendungsverbindungen zum primären Replikat weitergeleitet werden, unabhängig davon, ob der Zielserver in der Verbindungszeichenfolge angegeben ist. Diese Funktion ermöglicht die Umleitung der Verbindung ohne einen Listener. Leiten Sie in den folgenden Fällen die Verbindung vom sekundären zum primären Replikat um:

  - Die Clustertechnologie bietet keine Listenerfunktion.
  - Es liegt eine Konfiguration mit mehreren Subnetzen vor, die eine komplexe Umleitung erfordert.
  - Im Mittelpunkt stehen Szenarien mit horizontaler Leseskalierung oder Notfallwiederherstellungszenarien mit dem Clustertyp `NONE`.

Weitere Informationen finden Sie unter [Umleitung von Lese-/Schreibverbindungen vom sekundären zum primären Replikat (Always On-Verfügbarkeitsgruppen)](../database-engine/availability-groups/windows/secondary-replica-connection-redirection-always-on-availability-groups.md).

### <a name="data-discovery-and-classification-ctp-20"></a>Datenermittlung und -klassifizierung (CTP 2.0)

Die Datenermittlung und -klassifizierung bietet erweiterte Funktionen, die nativ in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] integriert sind. Die Klassifizierung und Bezeichnung der wichtigsten vertraulichen Daten bietet folgende Vorteile:
- Bietet Unterstützung, um Datenschutzstandards und gesetzlich geregelte Complianceanforderungen zu erfüllen
- Unterstützt Sicherheitsszenarien, z.B. Überwachung und Benachrichtigung bei anomalem Zugriff auf vertrauliche Daten
- Vereinfacht den Vorgang der Ermittlung, wo sich vertrauliche Daten im Unternehmen befinden, damit Administratoren die richtigen Schritte zum Schutz der Datenbank durchführen können

Weitere Informationen finden Sie unter [Datenermittlung und -klassifizierung in SQL Server](../relational-databases/security/sql-data-discovery-and-classification.md).

Die [Überwachung](../relational-databases/security/auditing/sql-server-audit-database-engine.md) wurde zudem dahingehend verbessert, dass ein neues Feld in das Überwachungsprotokoll `data_sensitivity_information` eingeschlossen wurde, das die Vertraulichkeitsklassifizierungen (Bezeichnungen) der tatsächlichen Daten protokolliert, die von der Abfrage zurückgegeben wurden. Weitere Informationen und Beispiele finden Sie unter [ADD SENSITIVITY CLASSIFICATION (Transact-SQL)](../t-sql/statements/add-sensitivity-classification-transact-sql.md).

>[!NOTE]
>Es wurden keine Änderungen an der Art und Weise vorgenommen, wie die Überwachung aktiviert wird. Den Überwachungsdatensätzen wurde ein neues Feld namens `data_sensitivity_information` hinzugefügt, das die Vertraulichkeitsklassifizierungen (Bezeichnungen) der tatsächlichen Daten protokolliert, die von der Abfrage zurückgegeben wurden. Weitere Informationen finden Sie unter [Überwachen des Zugriffs auf vertrauliche Daten](https://docs.microsoft.com/azure/sql-database/sql-database-data-discovery-and-classification#subheading-3).

### <a name="expanded-support-for-persistent-memory-devices-ctp-20"></a>Erweiterte Unterstützung für Geräte mit beständigem Speicher (CTP 2.0)

[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Dateien, die auf einem Gerät mit persistentem Speicher platziert werden, können ab sofort im *optimierten* Modus betrieben werden. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] greift direkt auf das Gerät zu, wobei der Speicherstapel des Betriebssystems mithilfe von effizienten Speichervorgängen umgangen wird. Dieser Modus verbessert die Leistung, da er Eingaben/Ausgaben mit geringen Latenzen für solche Geräte ermöglicht.
    - Zu [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Dateien zählen beispielsweise Folgende:
        - Datenbankdateien
        - Transaktionsprotokolldateien
        - In-Memory-OLTP-Prüfpunktdateien
    - Persistente Speicher werden auch als Speicherklassenspeicher bezeichnet.
    - Persistente Speicher werden auf Websites, die nicht von Microsoft betrieben werden, gelegentlich informell *pmem* genannt.

> [!NOTE]
> Bei diesem Vorschaurelease ist die Optimierung von Dateien auf Geräten mit persistentem Speicher nur unter Linux verfügbar. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] unter Windows unterstützt Geräte mit persistentem Speicher ab [!INCLUDE[ssSQL15](../includes/sssql15-md.md)].

### <a name="hybrid-buffer-pool-ctp-21"></a>Hybrider Pufferpool (CTP 2.1)

Der hybride Pufferpool ist eine neue Funktion der SQL Server-Datenbank-Engine, mit der Sie bei Bedarf direkt auf Datenbankseiten in Datenbankdateien zugreifen können, die sich auf einem Gerät mit beständigem Arbeitsspeicher (PMEM) befinden. Da PMEM-Geräte eine sehr niedrige Latenz beim Datenzugriff aufweisen, muss die Engine keine Kopie der Daten in einem Pufferpoolbereich für bereinigte Seiten erstellen, sondern kann auf die Seite direkt im beständigen Arbeitsspeicher zugreifen. Der Zugriff erfolgt über im Speicher abgebildete E/A – wie bei Optimierungen. Das bietet Leistungsvorteile, da keine Kopie der Seite im DRAM erstellt und der E/A-Stapel des Betriebssystems für den Seitenzugriff im beständigen Speicher umgangen wird. Diese Funktion ist für SQL Server sowohl unter Windows als auch unter Linux verfügbar.

Weitere Informationen finden Sie unter [Hybrider Pufferpool](../database-engine/configure-windows/hybrid-buffer-pool.md).

### <a name="support-for-columnstore-statistics-in-dbcc-clonedatabase-ctp-20"></a>Unterstützung für Columnstore-Statistiken in DBCC CLONEDATABASE (CTP 2.0)

`DBCC CLONEDATABASE` erstellt eine rein schemabasierte Kopie einer Datenbank, die alle Elemente enthält, die zum Behandeln von Problemen mit der Abfrageleistung erforderlich sind, ohne das Daten kopiert werden. In älteren Versionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] wurden beim Befehl nicht die Statistiken kopiert, die für die Problembehandlung bei Columnstore-Indexabfragen erforderlich sind, weshalb manuelle Schritte zur Erfassung dieser Informationen nötig waren. In [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] erfasst `DBCC CLONEDATABASE` nun automatisch die Statistikblobs für Columnstore-Indizes, sodass keine manuellen Schritte erforderlich sind.

### <a name="new-options-added-to-spestimatedatacompressionsavings-ctp-20"></a>Neue Optionen für „sp_estimate_data_compression_savings“ (CTP 2.0)

`sp_estimate_data_compression_savings` gibt die aktuelle Größe des angeforderten Objekts zurück und schätzt die Objektgröße für den angeforderten Komprimierungsstatus. Diese Prozedur unterstützt derzeit drei Optionen: `NONE`, `ROW` und `PAGE`. In [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] werden zwei neue Optionen eingeführt: `COLUMNSTORE` und `COLUMNSTORE_ARCHIVE`. Diese neuen Optionen ermöglichen es Ihnen, die Speicherplatzeinsparungen abzuschätzen, wenn mit der Columnstore-Standard- oder -Archivkomprimierung ein Columnstore-Index für die Tabelle erstellt wird.

### <a id="ml"></a> Failovercluster für SQL Server Machine Learning Services und partitionsbasierte Modellierung (CTP 2.0)

- **Partitionsbasierte Modellierung:** `sp_execute_external_script` wurde um die partitionsbasierte Verarbeitung von externen Skripts Ihrer Daten mit den neuen Parametern erweitert. Diese Funktion unterstützt anstelle eines großen Modells das Trainieren von einer Vielzahl kleiner Modelle (ein Modell pro Datenpartition).

- **Windows Server-Failovercluster:** Konfigurieren Sie Hochverfügbarkeit für Machine Learning Services in einem Windows Server-Failovercluster.

Weitere Informationen finden Sie unter [Neuigkeiten zu SQL Server Machine Learning Services](../advanced-analytics/what-s-new-in-sql-server-machine-learning-services.md).

### <a name="lightweight-query-profiling-infrastructure-enabled-by-default-ctp-20"></a>Standardmäßig aktivierte LWP-Abfrageinfrastruktur (CTP 2.0)

Die LWP-Abfrageinfrastruktur (Lightweight Profiling) stellt Abfrageleistungsdaten effizienter bereit als standardmäßige Profilerstellungsmechanismen. Lightweight Profiling ist ab sofort standardmäßig aktiviert. Diese Infrastruktur wurde in [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] SP1 eingeführt. Lightweight Profiling bietet eine Methode zur Sammlung von Statistiken zur Abfrageausführung mit einem erwarteten CPU-Overhead von 2 % im Vergleich zu einem CPU-Overhead von bis zu 75 % für die Standardmethode zur Abfrageprofilerstellung. In älteren Versionen war diese Option standardmäßig deaktiviert. Datenbankadministratoren konnten diese mit dem [Ablaufverfolgungsflag 7412](../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) aktivieren. 

Weitere Informationen zu LWP finden Sie unter [Profilerstellungsinfrastruktur für Abfragen](../relational-databases/performance/query-profiling-infrastructure.md).

### <a id="polybase"></a>Neue PolyBase-Connectors

- **Neue Connectors für [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], Oracle, Teradata und MongoDB**: In [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] werden neue Connectors für externe Daten für [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], Oracle, Teradata und MongoDB eingeführt.

### <a name="new-sysdmdbpageinfo-system-function-returns-page-information-ctp-20"></a>Rückgabe von Seiteninformationen durch neue „sys.dm_db_page_info“-Systemfunktion (CTP 2.0)

`sys.dm_db_page_info(database_id, file_id, page_id, mode)` gibt Informationen zu einer Seite in einer Datenbank zurück. Die Funktion gibt eine Zeile zurück, die die Headerinformationen der Seite enthält, einschließlich `object_id`, `index_id` und `partition_id`. Dank dieser Funktion ist die Verwendung von `DBCC PAGE` in den meisten Fällen nicht mehr erforderlich. 

Um eine Problembehandlung für die seitenbezogenen Wartevorgänge zu ermöglichen, wurde außerdem eine neue Spalte namens „page_resource“ zu `sys.dm_exec_requests` und `sys.sysprocesses` hinzugefügt. Mit dieser neuen Spalte können Sie `sys.dm_db_page_info` durch eine weitere neue Systemfunktion namens `sys.fn_PageResCracker` mit diesen Ansichten verknüpfen. Sehen Sie sich als Beispiel das folgende Skript an:

```sql
SELECT page_info.* 
FROM sys.dm_exec_requests AS d 
  CROSS APPLY sys.fn_PageResCracker(d.page_resource) AS r
  CROSS APPLY sys.dm_db_page_info(r.db_id, r.file_id, r.page_id,'DETAILED')
    AS page_info;
```

## <a id="sqllinux"></a> SQL Server unter Linux

- **Replikationsunterstützung (CTP 2.0)**: [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] unterstützt die SQL Server-Replikation unter Linux. Bei einem virtuellen Linux-Computer mit dem SQL Server-Agent kann es sich um einen Verleger, einen Verteiler oder einen Abonnenten handeln. 

  Erstellen Sie die folgenden Arten von Veröffentlichungen:
  - Transaktion
  - Momentaufnahme
  - Merge

  Konfigurieren Sie die Replikation [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] oder verwenden Sie [gespeicherte Replikationsprozeduren](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md).

- **Unterstützung für den Microsoft Distributed Transaction Coordinator (MSDTC) (CTP 2.0):** [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] unter Linux unterstützt den Microsoft Distributed Transaction Coordinator (MSDTC). Weitere Informationen finden Sie unter [Gewusst wie: Konfigurieren des Microsoft Distributed Transaction Coordinator (MSDTC) unter Linux](../linux/sql-server-linux-configure-msdtc.md).

- **Always On-Verfügbarkeitsgruppe in Docker-Containern mit Kubernetes (CTP 2.2):** Kubernetes kann Container orchestrieren, auf denen [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Instanzen ausgeführt werden, um eine hochverfügbare Gruppe von Datenbanken mit SQL Server Always On-Verfügbarkeitsgruppen bereitzustellen. Ein Kubernetes-Operator stellt ein StatefulSet bereit, einschließlich eines Containers mit einem **mssql-server-Container** und einem Integritätsmonitor.

- **OpenLDAP-Unterstützung für AD-Drittanbieter (CTP 2.0):** [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] unter Linux unterstützt OpenLDAP, mit dem Drittanbieter zu Active Directory beitreten können.

- **Machine Learning unter Linux (CTP 2.0):** [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] Machine Learning Services (datenbankintern) wird ab sofort unter Linux unterstützt. Dies umfasst die Unterstützung für die gespeicherte `sp_execute_external_script`-Prozedur. Anweisungen zum Installieren von Machine Learning Services unter Linux finden Sie unter [Install [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] Machine Learning Services R and Python support on Linux (Installieren von SQL Server 2019 Machine Learning Services unter Linux (R, Python))](../linux/sql-server-linux-setup-machine-learning.md).

- **Neue Containerregistrierung (CTP 2.1):** Alle Containerimages für [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] sowie [!INCLUDE[ssSQL17](../includes/sssql17-md.md)] befinden sich nun in Microsoft Container Registry. Microsoft Container Registry ist die offizielle Containerregistrierung für die Verteilung von Microsoft-Produktcontainern. Darüber hinaus werden ab sofort zertifizierte RHEL-basierte Images veröffentlicht.

  - Microsoft Container Registry: `mcr.microsoft.com/mssql/server:vNext-CTP2.0`
  - Zertifizierte RHEL-basierte Containerimages: `mcr.microsoft.com/mssql/rhel/server:vNext-CTP2.0`

## <a id="mds"></a> Master Data Services 

- **Ersetzung der Silverlight-Steuerelemente durch HTML (CTP 2.0):** Das MDS-Portal (Master Data Services) ist nicht mehr von Silverlight abhängig. Alle veralteten Silverlight-Komponenten wurden durch HTML-Steuerelemente ersetzt.

## <a id="security"></a>Sicherheit

- **Zertifikatverwaltung im SQL Server-Konfigurations-Manager (CTP 2.0):** SSL/TLS-Zertifikate werden oft dazu verwendet, den Zugriff auf SQL Server-Instanzen zu sichern. Die Zertifikatverwaltung ist ab sofort im SQL Server-Konfigurations-Manager integriert, was allgemeine Aufgaben wie die Folgenden vereinfacht:

  - Anzeigen und Überprüfen der auf einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Instanz installierten Zertifikate 
  - Anzeigen von bald ablaufenden Zertifikaten
  - Bereitstellen von Zertifikaten auf Computern, die Always On-Verfügbarkeitsgruppen angehören (auf dem Knoten, auf dem sich das primäre Replikat befindet)
  - Bereitstellen von Zertifikaten auf Computern, die einer Failoverclusterinstanz angehören (auf dem aktiven Knoten)

  > [!NOTE]
  > Benutzer müssen über Administratorberechtigungen auf allen Clusterknoten verfügen.

## <a id="tools"></a>Tools

- [**Azure Data Studio:**](../azure-data-studio/what-is.md) Bei Azure Data Studio, das ehemals unter dem Vorschauversionsnamen „SQL Operations Studio“ veröffentlicht wurde, handelt es sich um ein einfaches und modernes, plattformübergreifendes Open Source-Desktoptool für die gängigsten Aufgaben in der Datenentwicklung und -verwaltung. Mit Azure Data Studio und der [Erweiterung für SQL Server 2019 Preview](../azure-data-studio/sql-server-2019-extension.md) können Sie unter Windows, macOS und Linux eine Verbindung mit einer SQL Server-Instanz (lokal und Cloud) herstellen. Mit Azure Data Studio können Sie Folgendes:

  - AAD wird jetzt unterstützt. (CTP 2.3)
  - Die Benutzeroberfläche für das Anzeigen von Notebooks wurde in Azure Data Studio verschoben. (CTP 2.3)
  - Ein neuer Assistent zum Erstellen externer Datenquellen von HDFS in Big Data-Cluster von SQL Server wurde hinzugefügt. (CTP 2.3)
  - Verbesserte Benutzeroberfläche für das Anzeigen von Notebooks. (CTP 2.3)
  - Neue Notebook-APIs wurden hinzugefügt. (CTP 2.3)
  - Der Befehl „“ wurde zur Unterstützung beim Aktualisieren von Python-Paketen hinzugefügt. (CTP 2.3)
  - Verbinden und Verwalten von Big Data-Clustern von SQL Server 2019. (CTP 2.1)
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

- [**SQL Server Management Studio (SSMS) 18.0 (Vorschauversion):**](../ssms/sql-server-management-studio-ssms.md) Unterstützt [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]

  - Ermöglicht das Starten von Azure Data Studio über SSMS (CTP 2.3)
  - Unterstützung für Always Encrypted mit Secure Enclaves (CTP 2.0)
  - Geringere Downloadgröße (CTP 2.0)
  - Ab sofort Visual Studio 2017 Isolated Shell als Grundlage (CTP 2.0)
  - Eine vollständige Liste finden Sie unter [SQL Server Management Studio – Änderungsprotokoll (SSMS)](../ssms/sql-server-management-studio-changelog-ssms.md). (CTP 2.0)

- [**Das SQL Server PowerShell-Modul:**](https://www.powershellgallery.com/packages/SqlServer/21.1.18080) Mit dem PowerShell-Modul „SqlServer“ können SQL Server-Entwickler, -Administratoren und BI-Experten die Datenbankbereitstellung und Serververwaltung automatisieren.

  - SMO v150 wird nach einem Upgrade von Version 21.0 auf Version 21.1 unterstützt.
  - Im aktualisierten SQL Server-Anbieter (SQLRegistration) werden nun AS/IS/RS-Gruppen angezeigt.
  - Korrigiert: Fehler im Cmdlet `New-SqlAvailabilityGroup` bei SQL Server 2014 als Zielversion.
  - Der Parameter `–LoadBalancedReadOnlyRoutingList` wurde zu `Set-SqlAvailabilityReplica` und `New-SqlAvailabilityReplica` hinzugefügt.
  - Das Cmdlet `AnalysisService` wurde aktualisiert und kann nun zwischengespeicherte Anmeldetoken von `Login-AzureAsAccount` für Azure Analysis Services verwenden.

## <a id="ssas"></a>[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Analysis Services (SSAS) 

### <a name="calculation-groups-in-tabular-models-ctp-23"></a>Berechnungsgruppen in tabellarischen Modellen (CTP 2.3) 

Berechnungsgruppen werden für das häufig auftretende Problem in komplexen Modellen eingesetzt, dass eine Vielzahl von Measures die gleichen Berechnungen verwenden, z.B. Zeitintelligenzfunktionen. Berechnungsgruppen werden in Berichterstellungsclients als Tabelle mit einer einzigen Spalte angezeigt. Jeder Wert in der Spalte stellt eine wiederverwendbare Berechnung oder ein Berechnungselement dar, das auf beliebige Measures angewendet werden kann.  

In einer Berechnungsgruppe können beliebig viele Berechnungselemente vorhanden sein. Jedes Berechnungselement wird durch einen DAX-Ausdruck definiert. Drei neue DAX-Funktionen wurden für Berechnungsgruppen eingeführt: 

- `SELECTEDMEASURE()`: Gibt einen Verweis auf das Measure zurück, das sich derzeit im Kontext befindet.  

- `SELECTEDMEASURENAME()`: Gibt eine Zeichenfolge zurück, die den Namen des Measures zurück, das sich derzeit im Kontext befindet.  

- `ISSELECTEDMEASURE(M1, M2, …)`: Gibt einen booleschen Wert zurück, der angibt, ob das Measure, das sich derzeit im Kontext befindet, eines der Measures ist, die als Argument angegeben wurden.

Zusätzlich zu den neuen DAX-Funktionen wurden zwei neue dynamische Verwaltungssichten eingeführt:

- `TMSCHEMA_CALCULATION_GROUPS`  
- `TMSCHEMA_CALCULATION_ITEMS`  

In diesem Release gelten folgende Einschränkungen für Berechnungsgruppen:

- Die Funktion `ALLSELECTED DAX` wird noch nicht unterstützt.
- Die Sicherheit auf Zeilenebene in der Tabelle der Berechnungsgruppe wird noch nicht unterstützt.
- Die Sicherheit auf Objektebene in der Tabelle der Berechnungsgruppe wird noch nicht unterstützt.
- DetailsRows-Ausdrücke, die auf Berechnungselemente verweisen, werden noch nicht unterstützt.
- MDX wird noch nicht unterstützt.

Für Berechnungsgruppen müssen Modelle den Kompatibilitätsgrad 1470 aufweisen, der derzeit nur in SQL Server 2019 CTP 2.3 und höher unterstützt wird. Derzeit können Berechnungsgruppen mithilfe der Tabellenobjektmodell-API, Tabular Model Scripting Language (TMSL) und dem Open Source-Tool „Tabular Editor“ erstellt werden. Die Unterstützung in SQL Server Data Tools (SSDT) und die Dokumentation werden in einem späteren Release veröffentlicht. Weitere Informationen zu diesem und anderen Featurereleases für CTP werden auf dem Analysis Services-Blog bekannt gegeben.

## <a name="other-services"></a>Weitere Dienste

Ab CTP 2.3 werden für [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] keine neuen Features für die folgenden Dienste mehr eingeführt:

- [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] (SSIS)
- [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] (SSRS)

## <a name="next-steps"></a>Nächste Schritte

- [Release Notes zu [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] (Vorschauversion)](sql-server-ver15-release-notes.md)

- [Microsoft [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]: Technical white paper (technisches Whitepaper)](https://info.microsoft.com/rs/157-GQE-382/images/EN-US-CNTNT-white-paper-DBMod-Microsoft-SQL-Server-2019-Technical-white-paper.pdf)<br />Veröffentlicht im September 2018. Gilt für Microsoft [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] CTP 2.0 für Windows-, Linux- und Docker-Container.

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]

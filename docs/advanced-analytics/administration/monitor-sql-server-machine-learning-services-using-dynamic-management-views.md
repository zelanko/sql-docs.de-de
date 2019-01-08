---
title: 'Überwachung von R und Python-skriptausführung mit dynamischen Verwaltungssichten (DMVs): SQL Server-Machine Learning'
description: Verwenden Sie dynamische Verwaltungssichten (DMVs), um R und Python externen skriptausführung in SQL Server-Machine Learning-Dienste überwachen.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/29/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 0d07288bccc641f67644a37cd027e093fc3967c8
ms.sourcegitcommit: ee76332b6119ef89549ee9d641d002b9cabf20d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2018
ms.locfileid: "53645549"
---
# <a name="monitor-sql-server-machine-learning-services-using-dynamic-management-views-dmvs"></a>Überwachen von SQL Server Machine Learning Services mit dynamischen Verwaltungssichten (DMVs)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Verwenden dynamischer Verwaltungssichten (DMVs) zum Überwachen der Ausführung externer Skripts (R- und Python), Ressourcen, die verwendet wird, Diagnostizieren von Problemen und Optimieren der Leistung in SQL Server-Machine Learning-Dienste.

In diesem Artikel finden Sie die DMVs, die spezifisch für SQL Server-Machine Learning-Dienste sind. Sie finden auch Beispiele für Abfragen, die anzeigen:

+ Einstellungen und Konfigurationsoptionen für Machine learning
+ Aktive Sitzungen, die externe R oder Python-Skripts ausführen
+ Statistiken zur abfrageausführung für die externe-Laufzeit für R und Python
+ Leistungsindikatoren für externe Skripts
+ Speicherauslastung für das Betriebssystem, SQL Server und externen Ressourcenpools
+ Speicherkonfiguration für SQL Server und externen Ressourcenpools
+ Ressourcenpools der Ressourcenkontrolle, einschließlich externe Ressourcenpools
+ Installierte Pakete für R und Python

Weitere allgemeine Informationen zu DMVs finden Sie unter [dynamische Systemverwaltungssichten](../../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md).

> [!TIP]
> Sie können auch die benutzerdefinierten Berichte zur Überwachung von SQL Server-Machine Learning-Dienste verwenden. Weitere Informationen finden Sie unter [Überwachen von Machine Learning mithilfe von benutzerdefinierten Berichten in Management Studio](../../advanced-analytics/r/monitor-r-services-using-custom-reports-in-management-studio.md).

## <a name="dynamic-management-views"></a>Dynamische Verwaltungssichten

Die folgenden dynamischen Verwaltungssichten können verwendet werden, bei der Überwachung von Machine Learning-Workloads in SQL Server. Die DMVs abgefragt werden soll, müssen Sie `VIEW SERVER STATE` Berechtigung für die Instanz.

| Dynamische Verwaltungssicht | Typ | Description |
|-------------------------|------|-------------|
| [sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md) | Ausführung | Gibt eine Zeile für jedes aktive Workerkonto zurück, das ein externes Skript ausführt. |
| [sys.dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md) | Ausführung | Gibt eine Zeile für jeden Typ von externer Skriptanforderung zurück. |
| [sys.dm_os_performance_counters](../../relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql.md) | Ausführung | Gibt eine Zeile pro Leistungsindikator zurück, der vom Server verwaltet wird. Wenn Sie die Suchbedingung verwenden `WHERE object_name LIKE '%External Scripts%'`, Sie können diese Informationen verwenden, um festzustellen, wie viele Skripts ausgeführt wurden, die Skripts ausgeführt wurden, mit welchem Authentifizierungsmodus oder wie viele R oder Python-Aufrufe für die gesamte Instanz ausgegeben wurden. |
| [sys.dm_resource_governor_external_resource_pools](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pools.md) | Resource Governor | Gibt Informationen zu den aktuellen Status der externen Ressource Pool in der Ressourcenkontrolle, die aktuelle Konfiguration der Ressourcenpools sowie Statistiken für Ressourcenpools zurück. |
| [sys.dm_resource_governor_external_resource_pool_affinity](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md) | Resource Governor | Gibt Informationen zur CPU-Affinität über die aktuelle external Resource Pool-Konfiguration in der Ressourcenkontrolle zurück. Gibt eine Zeile pro Zeitplanungsmodul in [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] zurück, wobei jedes Zeitplanungsmodul einem einzelnen Prozessor zugeordnet ist. Mithilfe dieser Sicht können Sie den Zustand eines Zeitplanungsmoduls überwachen oder Endlostasks identifizieren. |

Informationen zur Überwachung [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] -Instanzen finden Sie unter [Katalogsichten](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md) und [Resource Governor dynamische Verwaltungssichten in Verbindung](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md).

## <a name="settings-and-configuration"></a>Einstellungen und Konfigurationen

Zeigen Sie die Machine Learning Services Installation-Einstellung und Konfiguration-Optionen.

![Ausgabe von den Einstellungen und die Konfiguration Abfrage](media/dmv-settings-and-configuration.png "Ausgabe von den Einstellungen und die Konfiguration-Abfrage")

Führen Sie die Abfrage unten, um diese Ausgabe. Weitere Informationen zu den Sichten und Funktionen, die verwendet werden, finden Sie unter [dm_server_registry](../../relational-databases/system-dynamic-management-views/sys-dm-server-registry-transact-sql.md), [sys.configurations](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md), und [SERVERPROPERTY](../../t-sql/functions/serverproperty-transact-sql.md).

```sql
SELECT CAST(SERVERPROPERTY('IsAdvancedAnalyticsInstalled') AS INT) AS IsMLServicesInstalled
    , CAST(value_in_use AS INT) AS ExternalScriptsEnabled
    , COALESCE(SIGN(SUSER_ID(CONCAT (
                    CAST(SERVERPROPERTY('MachineName') AS NVARCHAR(128))
                    , '\SQLRUserGroup'
                    , CAST(serverproperty('InstanceName') AS NVARCHAR(128))
                    ))), 0) AS ImpliedAuthenticationEnabled
    , COALESCE((
            SELECT CAST(r.value_data AS INT)
            FROM sys.dm_server_registry AS r
            WHERE r.registry_key LIKE 'HKLM\Software\Microsoft\Microsoft SQL Server\%\SuperSocketNetLib\Tcp'
            AND r.value_name = 'Enabled'
            ), - 1) AS IsTcpEnabled
FROM sys.configurations
WHERE name = 'external scripts enabled';
```

Die Abfrage gibt die folgenden Spalten zurück:

| Spalte | Description |
|--------|-------------|
| IsMLServicesInstalled | Gibt 1 zurück, wenn SQL Server-Machine Learning-Dienste für die Instanz installiert ist. Andernfalls wird 0 zurückgegeben. |
| ExternalScriptsEnabled | Gibt 1 zurück, wenn externe Skripts für die Instanz aktiviert ist. Andernfalls wird 0 zurückgegeben. |
| ImpliedAuthenticationEnabled | Gibt 1, wenn implizite Authentifizierung aktiviert ist. Andernfalls wird 0 zurückgegeben. Die Konfiguration für die implizite Authentifizierung wird überprüft, indem Sie überprüfen, wenn eine Anmeldung für SQLRUserGroup vorhanden ist. |
| IsTcpEnabled | Gibt 1 zurück, wenn das TCP/IP-Protokoll für die Instanz aktiviert ist. Andernfalls wird 0 zurückgegeben. Weitere Informationen finden Sie unter [standardmäßig SQL Server-Protokoll Netzwerkkonfiguration](../../database-engine/configure-windows/default-sql-server-network-protocol-configuration.md). |

## <a name="active-sessions"></a>Aktive Sitzungen

Zeigen Sie die aktiven Sitzungen, die Ausführung externer Skripts.

![Ausgabe der Abfrage für die aktive Einstellungen](media/dmv-active-sessions.png "Ausgabe der Abfrage der active-Einstellungen")

Führen Sie die Abfrage unten, um diese Ausgabe. Weitere Informationen zu den dynamischen Verwaltungssichten verwendet, finden Sie unter [Sys. dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md), [Sys. dm_external_script_requests](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md), und [Sys. dm_exec_sessions](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md).

```sql
SELECT r.session_id, r.blocking_session_id, r.status, DB_NAME(s.database_id) AS database_name
    , s.login_name, r.wait_time, r.wait_type, r.last_wait_type, r.total_elapsed_time, r.cpu_time
    , r.reads, r.logical_reads, r.writes, er.language, er.degree_of_parallelism, er.external_user_name
FROM sys.dm_exec_requests AS r
INNER JOIN sys.dm_external_script_requests AS er
ON r.external_script_request_id = er.external_script_request_id
INNER JOIN sys.dm_exec_sessions AS s
ON s.session_id = r.session_id;
```

Die Abfrage gibt die folgenden Spalten zurück:

| Spalte | Description |
|--------|-------------|
| session_id | Identifiziert die einer aktiven primären Verbindung zugeordnete Sitzung. |
| blocking_session_id | ID der Sitzung, die die Anforderung blockiert. Wenn diese Spalte den Wert NULL aufweist, wird die Anforderung nicht blockiert, oder die Sitzungsinformationen der blockierenden Sitzung sind nicht verfügbar (bzw. können nicht identifiziert werden). |
| status | Status der Anforderung. |
| database_name | Der Name der aktuellen Datenbank für jede Sitzung. |
| login_name | SQL Server-Anmeldename, der unter dem die Sitzung gegenwärtig ausgeführt wird. |
| wait_time | Wenn die Anforderung zurzeit blockiert wird, gibt diese Spalte die Dauer des aktuellen Wartevorgangs in Millisekunden an. Lässt keine NULL-Werte zu. |
| wait_type | Wenn die Anforderung zurzeit blockiert wird, gibt diese Spalte den Wartetyp zurück. Weitere Informationen zu Wartetypen finden Sie unter [Sys. dm_os_wait_stats](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md). |
| last_wait_type | Wenn diese Anforderung zuvor bereits blockiert war, gibt diese Spalte den Typ des letzten Wartevorgangs zurück. |
| total_elapsed_time | Gesamtzeit seit dem Eintreffen der Anforderung (in Millisekunden). |
| cpu_time | Von der Anforderung beanspruchte CPU-Zeit (in Millisekunden). |
| reads | Anzahl der von dieser Anforderung ausgeführten Lesevorgänge. |
| logical_reads | Anzahl der von dieser Anforderung ausgeführten logischen Lesevorgänge. |
| writes | Anzahl der von dieser Anforderung ausgeführten Schreibvorgänge. |
| language | Schlüsselwort, das einer unterstützten Skriptsprache entspricht. |
| degree_of_parallelism | Zahl, die die Anzahl von parallelen Prozessen angibt, die erstellt wurden. Dieser Wert kann sich von der Anzahl von parallelen Prozessen unterscheiden, die angefordert wurden. |
| external_user_name | Das Windows-Workerkonto, unter dem das Skript ausgeführt wurde. |

## <a name="execution-statistics"></a>Ausführungsstatistiken

Anzeigen der Ausführungsstatistiken für die externe-Laufzeit für R und Python. Nur Statistiken von RevoScaleR, Revoscalepy oder Microsoftml-Paket-Funktionen sind derzeit verfügbar.

![Die Ausgabe der Ausführung Statistiken Abfrage](media/dmv-execution-statistics.png "Ausgabe der Ausführung Statistiken-Abfrage")

Führen Sie die Abfrage unten, um diese Ausgabe. Weitere Informationen zu der dynamischen verwaltungssicht verwendet, finden Sie unter [dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md). Die Abfrage gibt nur die Funktionen, die mehr als einmal ausgeführt wurden.

```sql
SELECT language, counter_name, counter_value
FROM sys.dm_external_script_execution_stats
WHERE counter_value > 0
ORDER BY language, counter_name;
```

Die Abfrage gibt die folgenden Spalten zurück:

| Spalte | Description |
|--------|-------------|
| language | Name der registrierten externen Skriptsprache. |
| counter_name | Name einer registrierten externen Skriptfunktion. |
| counter_value | Gesamtanzahl der Instanzen, die von der registrierten externen Skriptfunktion auf dem Server aufgerufen wurden. Dieser Wert ist kumulativ und beginnt mit dem Zeitpunkt, zu dem das Feature auf der Instanz installiert wurde. Der Wert kann nicht zurückgesetzt werden. |

## <a name="performance-counters"></a>Leistungsindikatoren

Zeigen Sie die Leistungsindikatoren im Zusammenhang mit der Ausführung externer Skripts.

![Ausgabe von der Leistung die Abfrage der Leistungsindikatoren](media/dmv-performance-counters.png "Ausgabe von der Leistung die Abfrage der Leistungsindikatoren")

Führen Sie die Abfrage unten, um diese Ausgabe. Weitere Informationen zu der dynamischen verwaltungssicht verwendet, finden Sie unter [dm_os_performance_counters](../../relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql.md).

```sql
SELECT counter_name, cntr_value
FROM sys.dm_os_performance_counters 
WHERE object_name LIKE '%External Scripts%'
```

**dm_os_performance_counters** gibt die folgenden Leistungsindikatoren für externe Skripts:

| Leistungsindikator | Description |
|---------|-------------|
| Total Executions | Anzahl externer Prozesse, die von lokalen oder remote-Aufrufe gestartet. |
| Parallel Executions | Anzahl der Fälle, in denen ein Skript enthalten die _@parallel_ -Spezifikation und die [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] konnte zum Generieren und verwenden einen parallelen Abfrageplan. |
| Streaming Executions | Anzahl der Fälle, in denen die streaming-Funktion aufgerufen wurde. |
| SQL CC Executions | Anzahl externer Skripts ausführen, in dem der Aufruf Remote instanziiert wurde und SQL Server wurde als computekontext verwendet. |
| Implied Auth. Anmeldungen | Die Anzahl der Wiederholungen, die ein ODBC-Loopback-Aufruf erfolgt über die implizite Authentifizierung; d. h. die [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] den Aufruf im Auftrag der Benutzer die skriptanforderung sendet. |
| Total Execution Time (ms) | Die verstrichene Zeit zwischen dem Aufruf und der Abschluss des Aufrufs. |
| Execution Errors | Die Anzahl wie oft Skripts Fehler gemeldet. Diese Zahl umfasst keine R oder Python-Fehler. |

## <a name="memory-usage"></a>Speicherauslastung

Zeigen Sie Informationen zu den vom Betriebssystem, SQL Server und die externen Pools verwendeten Arbeitsspeicher an.

![Ausgabe von der Speicher-verwendungsabfrage](media/dmv-memory-usage.png "Ausgabe aus der Abfrage der Speicher-Verwendung")

Führen Sie die Abfrage unten, um diese Ausgabe. Weitere Informationen zu den dynamischen Verwaltungssichten verwendet, finden Sie unter [sys.dm_resource_governor_external_resource_pools](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pools.md) und [Sys. dm_os_sys_info](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md).

```sql
SELECT physical_memory_kb, committed_kb
    , (SELECT SUM(peak_memory_kb)
        FROM sys.dm_resource_governor_external_resource_pools AS ep
        ) AS external_pool_peak_memory_kb
FROM sys.dm_os_sys_info;
```

Die Abfrage gibt die folgenden Spalten zurück:

| Spalte | Description |
|--------|-------------|
| physical_memory_kb | Die Gesamtmenge des Arbeitsspeichers auf dem Computer. |
| committed_kb | Den verwendeten zugesicherten Speicher in Kilobyte (KB) im Speicher-Manager. Reservierter Arbeitsspeicher im Speicher-Manager ist nicht eingeschlossen. |
| external_pool_peak_memory_kb | Die Summe aus der die maximale Arbeitsspeichermenge in Kilobyte, der für alle externen Ressourcenpools verwendet. |

## <a name="memory-configuration"></a>Konfiguration des Arbeitsspeichers

Informationen über die Konfiguration der maximalen Arbeitsspeicher in Prozent von SQL Server und externen Ressourcenpools anzeigen. Wenn SQL Server, mit dem Standardwert von ausgeführt wird `max server memory (MB)`, gilt dies als 100 % des Arbeitsspeichers OS.

![Die Ausgabe der Abfrage der Speicher-Konfiguration](media/dmv-memory-configuration.png "Ausgabe der Abfrage der Speicher-Konfiguration")

Führen Sie die Abfrage unten, um diese Ausgabe. Weitere Informationen zu den Ansichten verwendet, finden Sie unter [sys.configurations](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md) und [sys.dm_resource_governor_external_resource_pools](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pools.md).

```sql
SELECT 'SQL Server' AS name
    , CASE CAST(c.value AS BIGINT)
        WHEN 2147483647 THEN 100
        ELSE (SELECT CAST(c.value AS BIGINT) / (physical_memory_kb / 1024.0) * 100 FROM sys.dm_os_sys_info)
        END AS max_memory_percent
FROM sys.configurations AS c
WHERE c.name LIKE 'max server memory (MB)'
UNION ALL
SELECT CONCAT ('External Pool - ', ep.name) AS pool_name, ep.max_memory_percent
FROM sys.dm_resource_governor_external_resource_pools AS ep;
```

Die Abfrage gibt die folgenden Spalten zurück:

| Spalte | Description |
|--------|-------------|
| NAME | Der Name des externen Ressourcenpools oder SQL Server. |
| max_memory_percent | Der maximale Arbeitsspeicher, den SQL Server oder den externen Ressourcenpool verwendet werden kann. |

## <a name="resource-pools"></a>Ressourcenpools

In [SQL Server-Ressourcenkontrolle](../../relational-databases/resource-governor/resource-governor.md), [Ressourcenpool](../../relational-databases/resource-governor/resource-governor-resource-pool.md) stellt eine Teilmenge der physischen Ressourcen einer Instanz dar. Sie können Einschränkungen angeben, für die Menge an CPU, physische e/a und Arbeitsspeicher, der eingehende anwendungsanforderungen, einschließlich der Ausführung externer Skripts im Ressourcenpool zur Verfügung stehen. Zeigen Sie die Ressourcenpools, die für die SQL Server und externen Skripts verwendet.

![Ausgabe von der Ressource pools Abfrage](media/dmv-resource-pools.png "Ausgabe aus der Ressource pools Abfrage")

Führen Sie die Abfrage unten, um diese Ausgabe. Weitere Informationen zu den dynamischen Verwaltungssichten verwendet, finden Sie unter [Sys. dm_resource_governor_resource_pools](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql.md) und [sys.dm_resource_governor_external_resource_pools](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pools.md).

```sql
SELECT CONCAT ('SQL Server - ', p.name) AS pool_name
    , p.total_cpu_usage_ms, p.read_io_completed_total, p.write_io_completed_total
FROM sys.dm_resource_governor_resource_pools AS p
UNION ALL
SELECT CONCAT ('External Pool - ', ep.name) AS pool_name
    , ep.total_cpu_user_ms, ep.read_io_count, ep.write_io_count
FROM sys.dm_resource_governor_external_resource_pools AS ep;
```

Die Abfrage gibt die folgenden Spalten zurück:

| Spalte | Description |
|--------|-------------|
| pool_name | Name des Ressourcenpools. SQL Server-Ressourcenpools werden mit dem Präfix `SQL Server` und externe Ressourcenpools werden mit dem Präfix `External Pool`.
| total_cpu_usage_hours | Die kumulierte CPU-Verwendung in Millisekunden, seitdem die ressourcenkontrollstatistiken zurückgesetzt wurden. |
| read_io_completed_total | Die Gesamtanzahl der E/A-Lesevorgänge, die seit dem Zurücksetzen der Ressourcenkontrollstatistiken abgeschlossen wurden. |
| write_io_completed_total | Die Gesamtanzahl der E/A-Schreibvorgänge, die seit dem Zurücksetzen der Ressourcenkontrollstatistiken abgeschlossen wurden. |

## <a name="installed-packages"></a>Installierte Pakete

Sie können die R- und Python-Pakete anzeigen, die in SQL Server-Machine Learning-Dienste installiert sind, indem Sie ein R- oder Python-Skript, das diese Ausgaben ausführen.

### <a name="installed-packages-for-r"></a>Installierte Pakete für R

Zeigen Sie die R-Pakete in SQL Server-Machine Learning-Dienste installiert.

![Die installierten Pakete für R-Abfrage die Ausgabe](media/dmv-installed-packages-r.png "Ausgabe von der installierten Pakete für R-Abfrage")

Führen Sie die Abfrage unten, um diese Ausgabe. Die Verwendung der Abfrage ein R-Skript, um R-Pakete zu ermitteln, die mit SQL Server installiert werden.

```sql
EXEC sp_execute_external_script @language = N'R'
, @script = N'
OutputDataSet <- data.frame(installed.packages()[,c("Package", "Version", "Depends", "License", "LibPath")]);'
WITH result sets((Package NVARCHAR(255), Version NVARCHAR(100), Depends NVARCHAR(4000)
    , License NVARCHAR(1000), LibPath NVARCHAR(2000)));
```

Spalten, die zurückgegeben werden:

| Spalte | Description |
|--------|-------------|
| Package | Der Name des installierten Pakets. |
| Version | Die Version des Pakets. |
| Depends (Abhängig) | Listet die Pakete, von denen das installierte Paket abhängt. |
| License (Lizenz) | Die Lizenz für das installierte Paket. |
| LibPath | Das Verzeichnis, in dem Sie das Paket finden können. |

### <a name="installed-packages-for-python"></a>Installierte Pakete für Python

Zeigen Sie die Python-Pakete, die in SQL Server-Machine Learning-Dienste installiert.

![Ausgabe von den installierten Paketen für Python-Abfrage](media/dmv-installed-packages-python.png "Ausgabe aus den installierten Paketen für Python-Abfrage")

Führen Sie die Abfrage unten, um diese Ausgabe. Die Abfrage verwenden ein Python-Skript, um zu bestimmen, die Python-Pakete, die mit SQL Server installiert.

```sql
EXEC sp_execute_external_script @language = N'Python'
, @script = N'
import pip
OutputDataSet = pandas.DataFrame([(i.key, i.version, i.location) for i in pip.get_installed_distributions()])'
WITH result sets((Package NVARCHAR(128), Version NVARCHAR(128), Location NVARCHAR(1000)));
```

Spalten, die zurückgegeben werden:

| Spalte | Description |
|--------|-------------|
| Package | Der Name des installierten Pakets. |
| Version | Die Version des Pakets. |
| Speicherort | Das Verzeichnis, in dem Sie das Paket finden können. |

## <a name="next-steps"></a>Nächste Schritte

+ [Verwalten und Überwachen von Machine Learning-Lösungen](../../advanced-analytics/r/managing-and-monitoring-r-solutions.md)
+ [Erweiterte Ereignisse für Machine learning](../../advanced-analytics/r/extended-events-for-sql-server-r-services.md)
+ [Dynamische Verwaltungssichten in Verbindung mit der Ressourcenkontrolle](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md)
+ [Dynamische Systemverwaltungssichten](../../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)
+ [Überwachen von Machine Learning mithilfe von benutzerdefinierten Berichten in Management Studio](../../advanced-analytics/r/monitor-r-services-using-custom-reports-in-management-studio.md)